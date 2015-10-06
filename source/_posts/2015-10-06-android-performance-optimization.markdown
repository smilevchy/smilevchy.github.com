---
layout: post
title: "Android Performance Optimization"
date: 2015-10-06 10:05:16 +0800
comments: true
categories: Android
---

*Collections of all kinds of tricks of optimizing app performance.*

<!-- more -->

Memory Performance Tools:


* Memory Monitor：查看整个app所占用的内存，以及发生GC的时刻，短时间内发生大量的GC操作是一个危险的信号
* Allocation Tracker：使用此工具来追踪内存的分配，
* Heap Tool：查看当前内存快照，便于对比分析哪些对象有可能是泄漏了的

--------

Overall Performance Tools:

* Lint Tool
* Strict Mode Tool

--------

The Performance Lifecyle

* Gather：收集数据

    * 我们可以通过Android SDK里面提供的诸多工具来收集CPU、GPU、内存、电量等性能数据。

* Insight：分析数据

    * 通过上面的步骤，我们获取到了大量的数据，下一步就是分析这些数据。工具帮我们生成了很多可读性强的表格，我们需要事先了解如何查看表格的数据，每一项代表的含义，这样才能够快速定位问题。如果分析数据之后还是没有找到问题，那么就只能不停的重新收集数据，再进行分析，如此循环。

* Action：解决问题

    * 定位到问题之后，我们需要采取行动来解决问题。解决问题之前一定要先有个计划，评估这个解决方案是否可行，是否能够及时的解决问题。

--------

Ui Layer

* 优化布局文件
    * tools: hierarchy viewer

    * 减少布局层次，保持层次扁平化
    * 删除不必要的组件

* 查看 GPU 过度渲染
    * tools: gpu overdraw display

    * 利用 cliprect
    * 取消设置背景 
        * 移除Window默认的Background(每个 Activity 调用 setBackgroundDrawable(null))
        * 移除XML布局文件中非必需的Background
        * 按需显示占位背景图片

* GPU 显示配置文件
    * 查看 GPU 绘制图形时是否有异样（如界面某个组件一直在循环绘制）

* 使用 GPU 渲染 View

* 自定义 View 覆盖 hasOverlappingRendering() 并返回 false

* Avoiding allocations in onDraw()
    * 把分配对象操作移到 onDraw() 方法外面

* Custom View
    * Useless calls to onDraw() : 第1个是仅仅在View的内容发生改变的时候才去触发invalidate方法，第2个是尽量使用ClipRect等方法来提高绘制的性能 
    * Useless pixels : 减少绘制时不必要的绘制元素，对于那些不可见的元素，我们需要尽量避免重绘
    * Wasted CPU cycles : 对于不在屏幕上的元素，可以使用Canvas.quickReject把他们给剔除，避免浪费CPU资源。另外尽量使用GPU来进行UI的渲染，这样能够极大的提高程序的整体表现性能

* Smaller Pixel Formats

* Pre-scaling Bitmaps 
    * 避免直接调用createScaledBitmap()，应该通过设置 bitmapOption 的 inSampleSize 来进行缩放图像

* Re-using Bitmaps
    * 使用 inBitmap 属性

--------

Memory Layer

* 避免 GC 操作过于频繁
    * tools: Memory Monitor / Heap and Allocation Tracker

    * reason 1: memory churn
    * reason 2: 瞬间产生大量的对象占用了内存区域，导致各种类型的 GC

* 避免 Memory Leak
    * tools: Heap tool / Allocation Track
    
    * method of checking leak: observed activity(use heap tool to capture current memory state) -> blank activity(call gc() actively , then use heap tool to capture current memory state, now it should not have previous activity's memory footprint. If not, then leak...)
    * method of finding leaked memory footprint: blank activity(use tool of Allocation Track , begin track) -> observed activity -> blank activity(end track, then find the objects still alive)

    * do not leak views
        * beware callbacks(only if callback uses some context related objects)
        * beware static objects

* 使用 Object Pools 
* 使用 LRU Cache

--------

Battery Layer

* tools: Battery Historian Tool / JobScheduler API (since level 20)

* 我们应该尽量减少唤醒屏幕的次数与持续的时间，使用WakeLock来处理唤醒的问题，能够正确执行唤醒操作并根据设定及时关闭操作进入睡眠状态
* 某些非必须马上执行的操作，例如上传歌曲，图片处理等，可以等到设备处于充电状态或者电量充足的时候才进行
* 触发网络请求的操作，每次都会保持无线信号持续一段时间，我们可以把零散的网络请求打包进行一次操作，避免过多的无线信号引起的电量消耗

--------

Network Layer

* Batch and delay HTTP requests
    * tools: JobScheduler API
* Prefetch and Compressed

--------

Bussiness Layer

* Batching Background Work Until Later
    * AlarmManager：使用AlarmManager设置定时任务，可以选择精确的间隔时间，也可以选择非精确时间作为参数。除非程序有很强烈的需要使用精确的定时唤醒，否者一定要避免使用他，我们应该尽量使用非精确的方式
    * SyncAdapter：我们可以使用SyncAdapter为应用添加设置账户，这样在手机设置的账户列表里面可以找到我们的应用
    * JobSchedulor：这是最简单高效的方法，我们可以设置任务延迟的间隔，执行条件，还可以增加重试机制

--------

Code Layer

* 基于场景选择合适的数据结构
    *  尝试使用官方提供的数据结构(ArrayMap, SparseArray等)
    *  判断是否使用 enum

* colors.xml 不要采用业务来命名,直接使用颜色命名



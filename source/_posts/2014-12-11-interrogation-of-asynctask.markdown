---
layout: post
title: "Interrogation of AsyncTask"
date: 2014-12-11 20:48:12 +0800
comments: true
categories: Android
---

当需要进行一项耗时久的任务时（下载文件、访问网络等），一般都知道必须在 worker thread 中进行。但是在现实场景中不可能单纯新建一个线程那么简单，大部分时候需要和 main thread 进行交互、或者说还要保证任务能够成功进行，不会遇到被销毁的情况。可是，单纯的 thread 并不具备这些能力。

那怎么办呢？

<!-- more -->

以上说的场景交互在 Android 开发中形成了一种 pattern，而 Android 团队就把这种 pattern 提取成了一个工具类出来给开发者使用，即 AsyncTask。

关于 AsyncTask 的使用方法可参见[官方文档](http://developer.android.com/reference/android/os/AsyncTask.html)。

一般情况下，AsyncTask 的确就是那么容易使用。但在某些情况下，你会发现这个类出问题了。

这个是因为 AsyncTask 的本质缺陷导致。

Android 的基本组件 Activity/Receiver/Service 本身具有一定的生命周期管理（Life Circle Management），而 AsyncTask 并不具备与之对应的生命周期管理。

假设一个场景如下，你编写了一个 AsyncTask，然后在一个 Activity 里调用该 AsyncTask，并且把自身引用传递进去，为了后续的一些函数调用。大部分情况下是没有问题，但是当设备转换屏幕方向时，Android 系统会销毁这个 Activity 再重建一个新的，此时之前传进去 AsyncTask 里的引用已经“无效”了，因为它指向了一个被销毁的 Activity，你再也不可能对其做任何 UI 操作，甚至会抛出 NullPointerException。即是说，你需要注意传进给 AsyncTask 的任何具有生命周期管理的引用，下一秒这个引用可能就失效了。

解决方法？ 

对于此类具有生命周期管理的引用统一使用 WeakReference，当引用指向的对象被系统销毁时，可以让这些对象被 GC 处理，同时在使用到引用的代码处再判断是否非空来决定怎么处理。

此外，当外部发生生命周期状态改变时（按返回键、Home键、取消进度框等），若对应的 AsyncTask 需要做相应的反应时（取消任务进行、继续任务进行等），还需要监听外部的生命周期状态改变事件。

总之，AsyncTask 看起来很简单，但需要在实际场景中考虑是否可能会出现问题。





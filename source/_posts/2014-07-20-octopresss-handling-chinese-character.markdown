---
layout: post
title: "octopress 下中文的处理"
date: 2014-07-20 21:24:11 +0800
comments: true
categories: 
---

安装好 Octopress 后，想要发布一篇带有中文字符的文章，结果发现在 "rake generate" 阶段就遇到错误。
在网上搜寻一番，大家给出的几种处理方式大致如下：

1. 设置环境变量 
   
    >LC_ALL=zh_CN.UTF-8
	
	>LANG=zh_CN.UTF-8
	
	或者
	
	>LC_ALL=en_US.UTF-8
	
	>LANG=en_US.UTF-8
	
	<!-- more -->
2. 修改 Ruby 安装目录下的 convertible.rb 和 include.rb
  
    分别在其中找到一句代码类似 self.content = File.read(File.join(base, name), ...) 的，这句代码的行数依据不同版本会不一样的。
	将其改为self.content = File.read(File.join(base, name), :encoding => 'utf-8')
3. 转换该文章的编码格式为 UTF-8 无 BOM 编码格式

本人都试验了以上的方法，发现 1 和 2 对于我的配置不设置也可以，而 3 则是必须的。这个可能看个人的配置而有所变化。

目前也只是一种 workaround，具体的处理还需要花点时间学习下这个框架。
	


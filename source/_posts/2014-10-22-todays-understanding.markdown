---
layout: post
title: "Today's Understanding"
date: 2014-10-22 15:37:26 +0800
comments: true
categories: Understanding
---

在设计模块接口时，入口参数绝对要设计成数值形式啊，之前居然设计成了字符串形式，由于有其他模块也调用到，现在造成的局面就是根本没有扩展性，而且要修改的话还要让其他调用模块也进行相应修改。

悲剧......

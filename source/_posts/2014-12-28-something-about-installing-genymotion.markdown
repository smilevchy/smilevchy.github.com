---
layout: post
title: "Something about Installing Genymotion"
date: 2014-12-28 16:21:48 +0800
comments: true
categories: Android
---

趁着有时间安装了 Genymotion，它需要依据 Oracle 的 VirtualBox 来工作，所以就是说你还需要安装 Oracle VM VirtualBox 这个软件。

一般设计上来说，Genymotion 应该要提供一个位置来设置指向 VirtualBox 软件路径的，可是找了它的安装目录、软件界面设置都没有发现这个位置，所以就是说，它可能是固定指向 VirtualBox 的。

即，需要按照它给定的固定路径来安装 VirtualBox ，不然就无法启动成功。至于那个固定路径是什么，可以去它的日志文件里查找，如果没什么改变的话，位置一般是在用户数据文件夹里，名字为 genymotion.log。通过查看它的错误日志，找到指向 VirtualBox 时发生错误的日志记录，那里就有写该固定路径。

这是我自己遇到的错误，因为在安装 Genymotion 前我就一直使用 VirtualBox ，而且是自定义路径。 -_-所以需要卸载重装，安装它的固定路径。



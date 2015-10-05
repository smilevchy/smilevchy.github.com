---
layout: post
title: "Something about Inflation"
date: 2015-10-05 22:41:19 +0800
comments: true
categories: Android
---

When using view inflation, there are something we should know.

<!-- more -->

How to inflate a view? Usually by calling...

* View#inflate(Context context, int resource, ViewGroup root)
* LayoutInflater#inflate(int resource, ViewGroup root)
* LayoutInflater#inflate(int resource, ViewGroup root, boolean attachToRoot)

Calling is simple. The problem is *which one should you call and what arguments should you pass*.

To solve these questions, the key is to *take insight in the method signature and dive into the source code*.

Taking a brief example here:

    // A view which presents container
    ViewGroup parent = (ViewGroup) findViewById(R.id.container);
	
	// result: layout_height = wrap_content, layout_width = match_parent
    view = LayoutInflater.from(this).inflate(R.layout.item, null);
    parent.addView(view);

    // result: layout_height = 100, layout_width = 100
    view = LayoutInflater.from(this).inflate(R.layout.item, null);
    parent.addView(view, 100, 100);

    // result: layout_height = 25dp, layout_width = 25dp
    // returned view is the root view of R.layout.item due to attachRoot = false
    view = LayoutInflater.from(this).inflate(R.layout.item, parent, false);
    parent.addView(view);

    // result: layout_height = 25dp, layout_width = 25dp 
    // parent.addView is not necessary as this is already done by attachRoot = true
    // returned view is parent due to parent supplied as hierarchy root and attachRoot = true
    view = LayoutInflater.from(this).inflate(R.layout.red, parent, true);
	
Above code explains the results of different methods.

[Here is another useful resource](https://possiblemobile.com/2013/05/layout-inflation-as-intended/)
	




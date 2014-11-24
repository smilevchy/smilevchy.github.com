---
layout: post
title: "Leetcode_Sqrt(x)"
date: 2014-11-24 18:04:08 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/sqrtx/

<!-- more -->

    public int sqrt(int x) {
		if (x < 0) return -1;
		if (x == 0) return 0;
		
		int low = 1;
		int high = x / 2 + 1;
	
		while (low <= high) {
			int mid = (low + high) / 2;
			
			if (mid <= x / mid && x / (mid + 1) < mid + 1) {
				return mid;
			} else if (mid < x / mid) {
				low = mid + 1;
			} else {
				high = mid - 1;
			}
		}
		
		return 0;
    }
	
求平方根的方法还有 "牛顿迭代法求平方根", "卡马克快速平方根"。

---
layout: post
title: "Leetcode_Climbing Stairs"
date: 2014-11-20 11:52:56 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/climbing-stairs/

<!-- more -->

    public int climbStairs(int n) {
		if (n <= 0) return 0;
		
		if (n == 1) {
			return 1;
		} else if (n == 2) {
			return 2;
		}

		int a = 1;
		int b = 2;
		int c = 0;
		
		for (int i = 3; i <= n; i++) {
			c = a + b;
			a = b;
			b = c;
		}
		
		return c;
    }
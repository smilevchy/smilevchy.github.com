---
layout: post
title: "Leetcode_Single Number"
date: 2014-11-21 15:23:48 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/single-number/

<!-- more -->

    PS: 利用异或运算可以用来加解密.

    public int singleNumber(int[] A) {
		int num = 0;
		
		for (int i = 0, length = A.length; i < length; i++) {
			num ^= A[i];
		}
		
		return num;
    }
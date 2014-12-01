---
layout: post
title: "Leetcode_Maximum Subarray"
date: 2014-12-01 10:21:42 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/maximum-subarray/

<!-- more -->

    public int maxSubArray(int[] A) {
		if (A == null || A.length == 0) return 0;

		int localMax = A[0];
		int globalMax = A[0];
		
		for (int i = 1, len = A.length; i < len; i++) {
			localMax = Math.max(A[i], localMax + A[i]);
			globalMax = Math.max(localMax, globalMax);
		}
		
		return globalMax;
    }

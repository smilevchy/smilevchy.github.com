---
layout: post
title: "Leetcode_Find Minimum in Rotated Sorted Array"
date: 2014-12-04 14:33:54 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/find-minimum-in-rotated-sorted-array/

<!-- more -->

    public int findMin(int[] num) {
		if (num == null || num.length == 0) return 0;
		
		return findMinHelper(num, 0, num.length - 1);
    }
	
	public int findMinHelper(int[] num, int low, int high) {
		if (low > high) return 0;
		
		if (high - low <= 1) return Math.min(num[low], num[high]);
		
		int mid = (low + high) / 2;
		int result = Math.min(num[mid], Math.min(findMinHelper(num, low, mid - 1), findMinHelper(num, mid + 1, high)));
		
		return result;
	}

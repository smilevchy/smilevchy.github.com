---
layout: post
title: "Leetcode_Search Insert Position"
date: 2014-11-25 17:45:19 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/search-insert-position/

<!-- more -->

    public int searchInsert(int[] A, int target) {
		if (A == null || A.length == 0) return 0;
		
		int length = A.length;
		int low = 0;
		int high = length - 1;
		int mid = 0;
		
		while (low <= high) {
			mid = (low + high) / 2;
			
			if (A[mid] == target) {
				return mid;
			} else if (A[mid] < target) {
				low = mid + 1;
			} else {
				high = mid - 1;
			}
		}
		
		return low;
    }

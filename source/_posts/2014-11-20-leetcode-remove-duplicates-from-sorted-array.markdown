---
layout: post
title: "Leetcode_Remove Duplicates from Sorted Array"
date: 2014-11-20 10:24:22 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/remove-duplicates-from-sorted-array/

<!-- more -->

    public int removeDuplicates(int[] A) {
		if (A == null || A.length == 0) return 0;
		
		int index = 1;
		
		for (int i = 1, length = A.length; i < length; i++) {
			if (A[i] != A[i - 1]) {
				A[index] = A[i];
				index++;
			}
		}
		
		return index;
    }
---
layout: post
title: "Leetcode_Remove Element"
date: 2014-11-20 11:19:55 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/remove-element/

<!-- more -->

    public int removeElement(int[] A, int elem) {
		if (A == null || A.length == 0) return 0;
		
		int length = A.length;
		int index = 0;
		
		for (int i = 0; i < length; i++) {
			if (A[i] == elem) {
				A[index] = A[length - 1];
				i--;
				length--;
			} else {
				index++;
			}
		}
		
		return index;
    }

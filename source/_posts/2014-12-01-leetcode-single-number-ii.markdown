---
layout: post
title: "Leetcode_Single Number II"
date: 2014-12-01 11:17:40 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/single-number-ii/

<!-- more --> 

    public int singleNumberII(int[] A) {
		if (A == null || A.length == 0) return 0;
		
		// the solving key is to regard the number as binary number, not decimal number,
		// so when a num exists 'n' times , the bits of it will multiply 'n' time too.

		int len = A.length;
		int[] digits = new int[32];
		
		for (int i = 0; i < 32; i++) {
			for (int j = 0; j < len; j++) {
				digits[i] += A[j] >> i & 1;    // get the i-th bit of every number of A
			}
		}
		
		int result = 0;
		
		for (int i = 0; i < 32; i++) {
			result += digits[i] % 3 << i;
		}
		
		return result;
    }

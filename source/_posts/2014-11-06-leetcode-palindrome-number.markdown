---
layout: post
title: "Leetcode_Palindrome Number"
date: 2014-11-06 15:59:14 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/palindrome-number/

    public boolean isPalindrome(int x) {
		if (x < 0) return false;

		// get length of digit
		int carryLength = 1;
		while (x / carryLength >= 10) {
			carryLength *= 10;
		}
		
		while (x > 0) {
			// test if the first and the end digit is equal; if not, return false
			if (x / carryLength != x % 10) return false;
			
			x = x % carryLength / 10;    // get the new number without the first and the end digit
			carryLength /= 100;    // for cutting the first and the end digit, we need to shrink carry length by 2 times
		}
		
		return true;
    }

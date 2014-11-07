---
layout: post
title: "Leetcode_Valid Palindrome"
date: 2014-11-07 16:28:29 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/valid-palindrome/

    public boolean isPalindrome(String s) {
		if (s == null) return false;
		
		s = s.trim();
		
		if (s.equals("")) return true;
		
		int i = 0;
		int j = s.length() - 1;
		char leftChar;
		char rightChar;
		
		while (i < j) {
			leftChar = s.charAt(i);
			
			if ((leftChar < 'a' || leftChar > 'z') && (leftChar < 'A' || leftChar > 'Z') && (leftChar < '0' || leftChar > '9')) {
				i++;
				continue;
			}
			
			rightChar = s.charAt(j);
			
			if ((rightChar < 'a' || rightChar > 'z') && (rightChar < 'A' || rightChar > 'Z') && (rightChar < '0' || rightChar > '9')) {
				j--;
				continue;
			}
			
			if (leftChar > rightChar) {
				if (leftChar - 32 != rightChar) return false;
			} else if (leftChar < rightChar) {
				if (leftChar + 32 != rightChar) return false;
			}
			
			i++;
			j--;
		}
		
		return true;
    }

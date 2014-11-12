---
layout: post
title: "Leetcode_Valid Number"
date: 2014-11-05 18:29:57 +0800
comments: true
categories: Algorithm
---

原题链接：https://oj.leetcode.com/problems/valid-number/

<!-- more -->

这道题主要是注意 "+"/"-"/"e"/"E"/"." 的位置，遍历字符串，当遇到上述几种符号时就判断位置是否正确，不正确则退出遍历过程，正确则继续，遇到非数字则退出遍历过程。

    public boolean isNumber(String s) {
		if (s == null) {
			return false;
		}

		String str = s.trim();
		
		if (str.length() == 0) {
			return false;
		}

		boolean result = true;
		int length = str.length();
		char c;
		boolean exponentialExisted = false;
		boolean dotExisted = false;
		boolean quitLoop = false;
		boolean digitExisted = false;
		
		for (int i = 0; i < length; i++) {
			c = str.charAt(i);
			
			if ('0' <= c && c <= '9') {
				digitExisted = true;
			} else {
				switch (c) {
					case '+':
					case '-':
						if (i == length - 1 || i != 0 && str.charAt(i - 1) != 'e' && str.charAt(i - 1) != 'E') {
							result = false;
							
							quitLoop = true;
						}
						
						break;
					
					case 'e':
					case 'E':
						if (exponentialExisted || i == 0 || i == length - 1 || ((str.charAt(i - 1) < '0' || str.charAt(i - 1) > '9') && str.charAt(i - 1) != '.') || !digitExisted) {
							result = false;
							
							quitLoop = true;
						}
						
						exponentialExisted = true;
						
						break;
					
					case '.':
						if (dotExisted || exponentialExisted || length == 1 || (i == length - 1 && (str.charAt(i - 1) < '0' || str.charAt(i - 1) > '9')) || 
							(i == 0 && ((str.charAt(i + 1) < '0' || str.charAt(i + 1) > '9') && (str.charAt(i + 1) != 'e' && str.charAt(i + 1) != 'E')))) {
							result =  false;
							
							quitLoop = true;
						}
						
						dotExisted = true;
						
						break;
						
					default:
						result = false;
						quitLoop = true;
				}
			}
			
			if (quitLoop) break;
		}
		
		return result;
    }

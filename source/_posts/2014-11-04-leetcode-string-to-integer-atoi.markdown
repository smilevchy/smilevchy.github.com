---
layout: post
title: "Leetcode_String to Integer(atoi)"
date: 2014-11-04 21:10:18 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/string-to-integer-atoi/

这道题目着重点是 corner case 的处理，一串字符串在转换为整数时，需要考虑它的正负号，以及是否溢出。

    public int atoi(String str) {
		long resultNum = 0; 
		
		if (str == null || str.equals("")) {
			return (int) resultNum;
		} 
		
		str = str.trim();
		boolean negative = false;
		char c;
		
		for (int i = 0, length = str.length(); i < length; i++) {
			c = str.charAt(i);
			
			if (i == 0 && (c == '-' || c == '+')) {
				if (c == '-') {
					negative = true;				
				}
			} else if ('0' <= c && c <= '9') {
				resultNum = resultNum * 10 + (c - '0');
				
				if (resultNum > Integer.MAX_VALUE && !negative) {
					resultNum = Integer.MAX_VALUE;
				} else if (negative && resultNum * -1 < Integer.MIN_VALUE) {
					resultNum = Integer.MIN_VALUE;
				}
			} else {
				break;
			}
		}
		
		return (int) (negative == true ? resultNum * -1 : resultNum); 			
	}

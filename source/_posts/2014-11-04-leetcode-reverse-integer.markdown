---
layout: post
title: "Leetcode_Reverse Integer"
date: 2014-11-04 21:16:33 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/reverse-integer/

    public int reverse(int x) {
		String str = Integer.toString(x);
		StringBuilder sb = new StringBuilder(str.length());
		char c;
		
		if (str.indexOf('-') == 0) {
			sb.append('-');
		}
		for (int i = str.length() - 1; i >= 0; i--) {
			c = str.charAt(i);
			
			if (c == '-') {
				break;
			}
			
			sb.append(c);
		}
		
		return Integer.parseInt(sb.toString());
    }

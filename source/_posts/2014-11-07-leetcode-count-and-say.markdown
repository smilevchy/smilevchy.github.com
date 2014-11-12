---
layout: post
title: "Leetcode_Count and Say"
date: 2014-11-07 15:53:37 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/count-and-say/

<!-- more -->

    public String countAndSay(int n) {
		if (n < 0) return "";
		
		StringBuilder sb = new StringBuilder();
		
		if (n == 1) {
			return sb.append("1").toString();
		}
		
		String prevStr = countAndSay(n - 1);
		int length = prevStr.length();
		char prevChar = ' '; 
		int accumulator = 0;

		for (int i = 0; i < length; i++) {
			char c = prevStr.charAt(i);
			
			if (c == prevChar) {
				accumulator++;
			} else {
				if (prevChar == ' ') {
					prevChar = c;
					accumulator = 1;
					continue;
				}
				
				sb.append("" + accumulator + prevChar);
				
				prevChar = c;
				accumulator = 1;
			}
		}
		
		if (accumulator > 0) sb.append("" + accumulator + prevChar);
		
		return sb.toString();
    }
---
layout: post
title: "Leetcode_Longest Common Prefix"
date: 2014-11-08 13:51:55 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/longest-common-prefix/

    public String longestCommonPrefix(String[] strs) {
		if (strs == null) return null;
		if (strs.length == 0) return "";
				
		String shortestStr = null;
		
		// find the shortest string element
		for (int i = 0, s = strs.length; i < s; i++) {
			if (shortestStr == null) {
				shortestStr = strs[i];
			} else if (strs[i].length() < shortestStr.length()) {
				shortestStr = strs[i];
			}
		}
		
		StringBuilder longestCommonPrefix = new StringBuilder("");
		int shortestStrLen = shortestStr.length();
		char c;
		boolean quitMatch = false;
		
		for (int i = 0; i < shortestStrLen; i++) {
			c = shortestStr.charAt(i);
			
			for (int j = 0, s = strs.length; j < s; j++) {
				if (strs[j].charAt(i) != c) {
					quitMatch = true;
					break;
				}

				if (j == strs.length - 1) {
					longestCommonPrefix.append(c);
				}
			}
			
			if (quitMatch) break;
		}
		
		return longestCommonPrefix.toString();
    }
---
layout: post
title: "Leetcode_Word Break"
date: 2014-11-14 17:45:56 +0800
comments: true
categories: Algorithm
---

原题链接：https://oj.leetcode.com/problems/word-break/

<!-- more -->

-_- 一开始用的是穷举法，结果遇到超长字符串时 online-judge system 就会报 limited time exceed 的错。

    public boolean wordBreak(String s, Set<String> dict) {
		if (s == null || s.length() == 0) return true;
		
		int length = s.length();
		boolean[] res = new boolean[length + 1];
		res[0] = true;
		
		for (int i = 0; i < length; i++) {
			StringBuilder sb = new StringBuilder(s.substring(0, i + 1));
			
			for (int j = 0; j <= i; j++) {
				if (res[j] && dict.contains(sb.toString())) {
					res[i + 1] = true;
					
					break;
				}
				
				sb.deleteCharAt(0);
			}
		}
		
		return res[length];
	}
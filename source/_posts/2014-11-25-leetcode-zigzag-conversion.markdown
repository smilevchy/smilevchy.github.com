---
layout: post
title: "Leetcode_ZigZag Conversion"
date: 2014-11-25 15:20:09 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/zigzag-conversion/

<!-- more -->

    public String convert(String s, int nRows) {
		if (s == null || nRows <= 1) return s;
		
		StringBuilder sb = new StringBuilder();
		int length = s.length();
		int span = 2 * nRows - 2;

		for (int i = 0; i < nRows; i++) {
			for (int j = i; j < length; j += span) {
				sb.append(s.charAt(j));
				
				if (i != 0 && i != nRows - 1 && j + span - 2 * i < length) {
					sb.append(s.charAt(j + span - 2 * i));
				}
			}
		}
		
		return sb.toString();
    }
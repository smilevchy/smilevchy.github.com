---
layout: post
title: "Leetcode_Length of Last Word"
date: 2014-11-21 15:07:42 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/length-of-last-word/

<!-- more -->

    public int lengthOfLastWord(String s) {
		if (s == null) return 0;
		
		int lengthOfLastWord = 0;
		boolean meetSpace = false;
		char c;
		
		for (int i = 0, length = s.length(); i < length; i++) {
			c = s.charAt(i);
			
			switch (c) {
				case ' ':
					meetSpace = true;
					
					break;
					
				default:
					if (meetSpace) {
						lengthOfLastWord = 0;
						lengthOfLastWord++;
						meetSpace = false;
					} else {
						lengthOfLastWord++;
					}
					
					break;
			}
		}
		
		return lengthOfLastWord;
    }

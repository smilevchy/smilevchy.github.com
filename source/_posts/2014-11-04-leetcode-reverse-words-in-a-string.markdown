---
layout: post
title: "Leetcode_Reverse Words in a String"
date: 2014-11-04 21:30:38 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/reverse-words-in-a-string/

<!-- more -->

    public String reverseWords(String s) {
		String[] words = s.trim().split("\\s+");
		StringBuilder sb = new StringBuilder("");
		
		for (int i = words.length - 1; i >= 0; i--) {
			sb.append(words[i]);
			
			if (i >= 1) {
				sb.append(" ");
			}
		}
		
		return sb.toString();
    }

---
layout: post
title: "Leetcode_Implement strStr()"
date: 2015-01-15 15:06:59 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/implement-strstr/

<!-- more -->

    public int strStr(String haystack, String needle) {
        if (haystack == null || needle == null) return -1;
        
        int haystackLen = haystack.length();
        int needleLen = needle.length();

        if (needleLen > haystackLen) return -1;
        if (needleLen == 0) return 0;
        
        char[] haystackChars = haystack.toCharArray();
        char[] needleChars = needle.toCharArray();

        int index = 0;
        boolean found = false;
        while (index < haystackLen) {
        	if (haystackLen - index < needleLen) {
        		break;
        	}
        	
        	int i = index;
        	
        	for (int j = 0; j < needleLen; j++) {
        		if (needleChars[j] != haystackChars[i]) {
        			break;
        		}
        		
        		i++;
        		
        		if (j == needleLen - 1) {
        			found = true;
        		}
        	}

        	if (found) {
        		break;
        	} else {
        		index++;
        	}
        }
		
		return found ? index : -1;
    }

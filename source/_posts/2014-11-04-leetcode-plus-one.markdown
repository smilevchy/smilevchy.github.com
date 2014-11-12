---
layout: post
title: "Leetcode_Plus One"
date: 2014-11-04 21:19:18 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/plus-one/

<!-- more -->

    public byte[] plusOne(byte[] num) {
    	if (num == null || num.length == 0) {
    		return num;
    	}
    	
    	byte[] result = num.clone();
    	int length = num.length;

    	for (int i = length - 1; i >= 0; i--) {
    		byte digit = result[i];
    		result[i] = (byte) (digit + 1);
    		
    		if (result[i] < 10) {
    			break;
    		} else {
    			result[i] = 0;
    			
    			if (i == 0) {
    				
    				byte[] expandedNum = new byte[length + 1];
    				expandedNum[0] = 1;
    				
    				return expandedNum;
    			}
    		}
    	}
    	
    	return result;
    }

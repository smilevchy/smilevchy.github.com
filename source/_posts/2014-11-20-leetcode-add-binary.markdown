---
layout: post
title: "Leetcode_Add Binary"
date: 2014-11-20 14:51:16 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/add-binary/

<!-- more -->

    public String addBinary(String a, String b) {
		if (a == null && b == null) return null;
		
		StringBuilder sb = new StringBuilder(a);
		
		int i = sb.length() - 1;
		int j = b.length() - 1;
		int carry = 0;
		char ac;
		char bc;
		
		while (i >= 0 && j >= 0) {
			ac = sb.charAt(i);
			bc = b.charAt(j);
			
			sb.setCharAt(i, (char) ('0' + (ac - '0' + bc - '0' + carry) % 2));
			carry = (ac - '0' + bc - '0' + carry) / 2;
			
			i--;
			j--;
		}

		while (i >= 0) {
			ac = sb.charAt(i);
			sb.setCharAt(i, (char) ('0' + (ac - '0' + carry) % 2));
			carry = (ac - '0' + carry) / 2;
			i--;
		}
		
		while (j >= 0) {
			bc = b.charAt(j);
			sb.insert(0, (char) ('0' + (bc - '0' + carry) % 2));
			carry = (bc - '0' + carry) / 2;
			j--;
		}
		
		if (carry > 0) {
			sb.insert(0, '1');
		}
		
		return sb.toString();
    }

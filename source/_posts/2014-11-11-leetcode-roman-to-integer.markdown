---
layout: post
title: "Leetcode_Roman to Integer"
date: 2014-11-11 18:31:43 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/roman-to-integer/

    // I(1) V(5) X(10) L(50) C(100) D(500) M(1000)
	public int romanToInt(String s) {
		if (s == null) return 0;
		
		s = s.trim();
		
		if (s.equals("")) return 0;
		
		int num = 0;
		int length = s.length();
		char cur;
		char next;
		
		for (int i = 0; i < length; i++) {
			cur = s.charAt(i);
			
			switch (cur) {
				case 'I':
					if (i + 1 != length) {
						next = s.charAt(i + 1);
						
						if (next == 'V') {
							num += 4;
							i++;
							continue;
						} else if (next == 'X') {
							num += 9;
							i++;
							continue;
						}
					}

					num += 1;
					
					break;
					
				case 'V':
					num += 5;
					
					break;
					
				case 'X':
					if (i + 1 != length) {
						next = s.charAt(i + 1);
						
						if (next == 'L') {
							num += 40;
							i++;
							continue;
						} else if (next == 'C') {
							num += 90;
							i++;
							continue;
						}
					}
					
					num += 10;
					
					break;
					
				case 'L':
					num += 50;
					
					break;
					
				case 'C':
					if (i + 1 != length) {
						next = s.charAt(i + 1);
						
						if (next == 'D') {
							num += 400;
							i++;
							continue;
						} else if (next == 'M') {
							num += 900;
							i++;
							continue;
						}
					}
					
					num += 100;
					
					break;
					
				case 'D':
					num += 500;
					break;
					
				case 'M':
					num += 1000;
					break;
			}
		}
		
		return num;
    }

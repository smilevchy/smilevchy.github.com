---
layout: post
title: "Leetcode_Valid Parentheses"
date: 2014-11-19 18:19:46 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/valid-parentheses/

<!-- more -->

    public boolean isValid(String s) {
		if (s == null) return false;
		
		int length = s.length();
		char c;
		Stack<Character> stack = new Stack<Character>();
		
		for (int i = 0; i < length; i++) {
			c = s.charAt(i);
			
			switch (c) {
				case '(':
				case '{':
				case '[':
					stack.push(c);
					
					break;
					
				case ')':
					try {
						char prevChar = stack.pop();
						if (prevChar != '(') return false;	
					} catch (Exception e) {
						return false;
					}
					
					break;
					
				case '}':
					try {
						char prevChar = stack.pop();
						if (prevChar != '{') return false;	
					} catch (Exception e) {
						return false;
					}
					
					break;
					
				case ']':
					try {
						char prevChar = stack.pop();
						if (prevChar != '[') return false;	
					} catch (Exception e) {
						return false;
					}
					
					break;
					
				default:
					return false;
			}
		}
		
		if (!stack.isEmpty()) return false;
			
		return true;
    }

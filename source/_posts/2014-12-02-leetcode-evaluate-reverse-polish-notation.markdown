---
layout: post
title: "Leetcode_Evaluate Reverse Polish Notation"
date: 2014-12-02 11:05:13 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/evaluate-reverse-polish-notation/

<!-- more -->

    public int evalRPN(String[] tokens) {
		if (tokens == null || tokens.length == 0) return 0;

		LinkedList<Integer> stack = new LinkedList<Integer>();
		int result = 0;
		String ele = null;
		
		for (int i = 0, len = tokens.length; i < len; i++) {
			ele = tokens[i];
			
			if ("+".equals(ele) || "-".equals(ele) || "*".equals(ele) || "/".equals(ele)) {
				if (stack.isEmpty()) return result;
				Integer right = stack.pop();
				
				if (stack.isEmpty()) return result;
				Integer left = stack.pop();
				
				if ("+".equals(ele)) {
					stack.push(left + right);					
				} else if ("-".equals(ele)) {
					stack.push(left - right);
				} else if ("*".equals(ele)) {
					stack.push(left * right);
				} else if ("/".equals(ele)) {
					stack.push(left / right);
				}
			} else {
				stack.push(Integer.valueOf(ele));
			}
		}
		
		if (!stack.isEmpty()) result = Integer.valueOf(stack.pop());
		
		return result;
    }

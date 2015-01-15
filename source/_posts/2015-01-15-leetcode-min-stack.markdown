---
layout: post
title: "Leetcode_Min Stack"
date: 2015-01-15 10:04:07 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/min-stack/

<!-- more -->

    class MinStack {
		private List<Integer> normalStack = new ArrayList<Integer>();
		private List<Integer> minNumStack = new ArrayList<Integer>();
		
		
	    public void push(int x) {
	    	normalStack.add(x);
	    	
	    	if (minNumStack.isEmpty() || minNumStack.get(minNumStack.size() - 1) >= x) {
	    		minNumStack.add(x);
	    	}
	    }

	    public void pop() {
	    	if (normalStack.isEmpty()) return;
	    	
	    	int x = normalStack.get(normalStack.size() - 1);
	    	normalStack.remove(normalStack.size() - 1);
	    	
	    	if (!minNumStack.isEmpty() && x == minNumStack.get(minNumStack.size() - 1)) {
	    		minNumStack.remove(minNumStack.size() - 1);
	    	}
	    }

	    public int top() {
	    	if (normalStack.isEmpty()) return 0;
	    	
	    	return normalStack.get(normalStack.size() - 1);
	    }

	    public int getMin() {
	    	if (minNumStack.isEmpty()) return 0;
	    	
	    	return minNumStack.get(minNumStack.size() - 1);
	    }
	}
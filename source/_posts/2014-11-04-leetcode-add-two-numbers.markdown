---
layout: post
title: "Leetcode_Add Two Numbers"
date: 2014-11-04 21:21:13 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/add-two-numbers/

    public ListNode addTwoNumbers(ListNode left, ListNode right) {
    	if (left == null && right == null) {
    		return null;
    	}
    	
    	ListNode result = new ListNode(0);
    	ListNode cursor = result;
    	int carry = 0;
    	
    	while (left != null || right != null) {
    		int val = 0;
    		
    		if (left != null) {
    			val += left.val;
    			left = left.next;
    		}
    		
    		if (right != null) {
    			val += right.val;
    			right = right.next;
    		}
    		
    		val += carry;
    		int digit = val % 10;
    		carry = val / 10;
    		
    		cursor.val = digit;
    		
    		if (left != null || right != null) {
    			cursor.next = new ListNode(0);
        		cursor = cursor.next;    			
    		}
    	}
    	
    	if (carry > 0) {
    		cursor.next = new ListNode(1);
    	}
    	
    	return result;
    }

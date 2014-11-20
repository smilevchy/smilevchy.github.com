---
layout: post
title: "Leetcode_Merge Two Sorted Lists"
date: 2014-11-20 15:41:09 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/merge-two-sorted-lists/

<!-- more -->

    public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
		if (l1 == null) return l2;
		if (l2 == null) return l1;
		
		ListNode cursorLeft = l1;
		ListNode cursorRight = l2;
		ListNode prevLeft = null;
		
		while (cursorRight != null) {
			while (cursorLeft != null && cursorLeft.val <= cursorRight.val) {
				prevLeft = cursorLeft;
				cursorLeft = cursorLeft.next;
			}
			
			if (prevLeft == null) {
				l2 = cursorRight.next;
				cursorRight.next = l1;
				l1 = cursorRight;
				cursorRight = l2;
			} else if (cursorLeft == null) {
				l2 = cursorRight.next;
				cursorRight.next = null;
				prevLeft.next = cursorRight;
				cursorRight = l2;
			} else {
				l2 = cursorRight.next;
				cursorRight.next = cursorLeft;
				prevLeft.next = cursorRight;
				cursorRight = l2;
			}
			
			cursorLeft = l1;
		}
		
		return l1;
    }

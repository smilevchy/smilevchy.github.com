---
layout: post
title: "Leetcode_Rotate List"
date: 2014-11-04 21:32:39 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/rotate-list/

    public ListNode rotateRight(ListNode head, int n) {
		if (head == null) {
			return head;
		}
			
		ListNode cursor = head;
		
		int length = 0;
		while (cursor != null) {
			cursor = cursor.next;
			length++;
		}
		
		if (n % length == 0) {
			return head;
		}
		
		int targetIndex = length - n % length;
		
		int currentIndex = 0;
		cursor = head;
		ListNode prev = null;
		
		while (currentIndex < targetIndex) {
			prev = cursor;
			cursor = cursor.next;
			currentIndex++;
		}
		
		ListNode cursorTail = cursor;
		while (cursorTail.next != null) {
			cursorTail = cursorTail.next;
		}
		
		prev.next = null;
		cursorTail.next = head;
		head = cursor;

		return head;
	}

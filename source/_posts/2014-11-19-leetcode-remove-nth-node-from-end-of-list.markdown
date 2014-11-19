---
layout: post
title: "Leetcode_Remove Nth Node From End of List"
date: 2014-11-19 17:55:05 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/remove-nth-node-from-end-of-list/

<!-- more -->

    public ListNode removeNthFromEnd(ListNode head, int n) {
		if (head == null) return null;
		if (n == 0) return head;
		
		ListNode cursor = head;
		int size = 0;
		
		while (cursor != null) {
			cursor = cursor.next;
			size++;
		}
		
		cursor = head;
		int targetIndex = size - n;
		int cursorIndex = 0;
		ListNode prevNode = null;
		
		while (cursorIndex < targetIndex) {
			prevNode = cursor;
			cursor = cursor.next;
			cursorIndex++;
		}
		
		if (prevNode == null) {
			head = cursor.next;
		} else {
			prevNode.next = cursor.next;
		}
		
		return head;
    }

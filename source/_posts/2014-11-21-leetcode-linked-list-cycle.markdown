---
layout: post
title: "Leetcode_Linked List Cycle"
date: 2014-11-21 16:17:54 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/linked-list-cycle/

<!-- more -->

    public boolean hasCycle(ListNode head) {
		if (head == null) return false;
		
		ListNode slowCursor = head;
		ListNode quickCursor = head;

		while (quickCursor.next != null && quickCursor.next.next != null) {
			slowCursor = slowCursor.next;
			quickCursor = quickCursor.next.next;

			if (slowCursor != null && quickCursor != null && (quickCursor == slowCursor || quickCursor.next == slowCursor)) {
				return true;
			}
		}
		
		return false;
    }
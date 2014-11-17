---
layout: post
title: "Leetcode_Remove Duplicates from Sorted List"
date: 2014-11-17 17:25:01 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/remove-duplicates-from-sorted-list/

<!-- more -->

    public ListNode deleteDuplicates(ListNode head) {
		if (head == null) return null;
		
		ListNode slowCursor = head;
		ListNode quickCursor = head.next;

		while (quickCursor != null) {
			if (quickCursor.val != slowCursor.val) {
				slowCursor = slowCursor.next;
				quickCursor = quickCursor.next;
				
				continue;
			}
			
			slowCursor.next = quickCursor.next;
			quickCursor = quickCursor.next;
		}
		
		return head;
    }

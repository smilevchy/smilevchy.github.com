---
layout: post
title: "Leetcode_Partition List"
date: 2014-11-24 11:20:23 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/partition-list/

    public ListNode partition(ListNode head, int x) {
		if (head == null) return null;

		ListNode lastSmallerNumCursor = null;
		ListNode prev = null;
		ListNode cur = head;

		while (cur != null) {
			if (cur.val < x) {
				if (prev == null) {
					lastSmallerNumCursor = cur;
					cur = cur.next;
					
					continue;
				}
				
				prev.next = cur.next;
				if (lastSmallerNumCursor == null) {
					cur.next = head;
					head = cur;
				} else {
					cur.next = lastSmallerNumCursor.next;
					lastSmallerNumCursor.next = cur;
				}
				
				lastSmallerNumCursor = cur;
			}
			
			prev = cur;
			cur = cur.next;
		}
		
		return head;
    }

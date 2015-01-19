---
layout: post
title: "Intersection of Two Linked Lists"
date: 2015-01-19 10:36:39 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/intersection-of-two-linked-lists/

<!-- more -->

    public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
		if (headA == null || headB == null) return null;
		if (headA == headB) return headA;

		ListNode cursorA = headA;
		ListNode cursorB = headB;
		while (cursorA != null && cursorB != null) {
			cursorA = cursorA.next;
			cursorB = cursorB.next;
		}
		
		ListNode longCursorStart = null;
		ListNode longCursorEnd = null;
		ListNode shortCursor = null;
		if (cursorA != null) {
			longCursorStart = headA;
			longCursorEnd = cursorA;
			shortCursor = headB;
		} else if (cursorB != null) {
			longCursorStart = headB;
			longCursorEnd = cursorB;
			shortCursor = headA;
		} else {
			longCursorStart = headA;
			longCursorEnd = null;
			shortCursor = headB;
		}
		
		while (longCursorStart != null && longCursorEnd != null) {
			longCursorStart = longCursorStart.next;
			longCursorEnd = longCursorEnd.next;
		}
		
		while (longCursorStart != shortCursor) {
			longCursorStart = longCursorStart.next;
			shortCursor = shortCursor.next;
		}
		
		return longCursorStart;
    }

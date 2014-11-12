---
layout: post
title: "Leetcode_Insertion Sort List"
date: 2014-11-12 16:32:44 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/insertion-sort-list/

<!-- more -->

一开始的解法有考虑到当前待插节点的后续节点，其实是没必要的

    public ListNode insertionSortList(ListNode head) {
		if (head == null) return null;

		ListNode cursorOut = head.next;
		ListNode cursorOutPrev = head;
		
		while (cursorOut != null) {
			ListNode cursorIn = head;
			ListNode cursorInPrev = null;
			ListNode cursorOutNext = cursorOut.next;
			
			while (cursorIn != null && cursorIn != cursorOut) {
				if (cursorIn.val > cursorOut.val) {
					if (cursorInPrev != null) {
						cursorInPrev.next = cursorOut;
					} else {
						head = cursorOut;
					}
					cursorOutPrev.next = cursorOutNext;
					cursorOut.next = cursorIn;
					cursorOut = cursorOutPrev;
					
					break;
				}
				
				cursorInPrev = cursorIn;
				cursorIn = cursorIn.next;
			}
			
			cursorOutPrev = cursorOut;
			cursorOut = cursorOutNext;
		}
    }

	
使用额外的一个节点来记录遍历位置

    public ListNode insertionSortList(ListNode head) {
		if (head == null) return null;
		
		ListNode insertedNode = head;
		ListNode cursor = new ListNode(0);
		ListNode prev = null;
		
		while (insertedNode != null) {
			ListNode insertedNodeNext = insertedNode.next;
			prev = cursor;
			
			while (prev.next != null && prev.next.val <= insertedNode.val) {
				prev = prev.next;
			}

			insertedNode.next = prev.next;
			prev.next = insertedNode;
			insertedNode = insertedNodeNext;
		}
		
		return cursor.next;
    } 		
  
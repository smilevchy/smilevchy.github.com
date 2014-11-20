---
layout: post
title: "Leetcode_Sort List"
date: 2014-11-20 17:51:47 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/sort-list/

<!-- more -->

    public ListNode sortList(ListNode head) {
		if (head == null) return null;
		if (head.next == null) return head;
		
		ListNode slowCursor = head;
		ListNode quickCursor = head;
		
		while (quickCursor.next != null && quickCursor.next.next != null) {
			slowCursor = slowCursor.next;
			quickCursor = quickCursor.next.next;
		}

		ListNode headRight = slowCursor.next;
		ListNode headLeft = head;
		slowCursor.next = null;
		
		return mergeTwoLists(sortList(headLeft), sortList(headRight));
    }
	
	private ListNode mergeTwoLists(ListNode l1, ListNode l2) {
	    ListNode helper = new ListNode(0);
	    helper.next = l1;
	    ListNode pre = helper;
	    
	    while (l1 != null && l2 != null) {
	        if (l1.val < l2.val) {
	            l1 = l1.next;
	        } else {
	            ListNode next = l2.next;
	            l2.next = pre.next;
	            pre.next = l2;
	            l2 = next;
	        }
	        
	        pre = pre.next;
	    }
	    
	    if (l2 != null) {
	        pre.next = l2;
	    }
	    
	    return helper.next;
	}

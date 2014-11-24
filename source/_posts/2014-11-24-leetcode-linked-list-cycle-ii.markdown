---
layout: post
title: "Leetcode_Linked List Cycle II"
date: 2014-11-24 10:40:28 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/linked-list-cycle-ii/

<!-- more -->

    public ListNode detectCycle(ListNode head) {
		if (head == null) return null;

		ListNode slowCursor = head;
	    ListNode quickCursor = head;
	    boolean hasCycle = false;
	    
	    while (quickCursor != null && quickCursor.next!=null) {
	        slowCursor = slowCursor.next;
	        quickCursor = quickCursor.next.next;
	        
	        if (slowCursor == quickCursor) {
	        	hasCycle = true;
	        	
	        	break;
	        }
	    }
	    
	    if (!hasCycle) return null;

	    // reset either reference to head
	    slowCursor = head;
	    
	    // iterate again until both references meet again, then getting the wanted node
	    while (slowCursor != quickCursor) {
	    	slowCursor = slowCursor.next;
	    	quickCursor = quickCursor.next;
	    }
	    
		return slowCursor;
    }

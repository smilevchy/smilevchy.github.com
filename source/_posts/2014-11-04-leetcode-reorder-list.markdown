---
layout: post
title: "Leetcode_Reorder List"
date: 2014-11-04 21:23:58 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/reorder-list/

正是这道题，让我知道了有 “快慢指针” 这种好东西。以前每当要做类似遍历链表的操作时，比如取中点，总是先遍历完一遍链表来获得长度，求得中点再遍历一次，实在是不雅观。而通过 “快慢指针”，只要写一次遍历就可以拿到中点。

    public void reorderList(ListNode head) {
    	if (head == null || head.next == null) {
    		return;
    	}
    	
    	ListNode slowCursor = head;
    	ListNode quickCursor = head;
    	
    	while (quickCursor != null && quickCursor.next != null && quickCursor.next.next != null && slowCursor != null && slowCursor.next != null) {
    		slowCursor = slowCursor.next;
    		quickCursor = quickCursor.next.next;
    	}
    	
    	ListNode head1 = head;
    	ListNode head2 = slowCursor.next;

    	head2 = reverseList(head2);
    	
    	while (head1 != null && head2 != null) {
    		ListNode head2Next = head2.next;
    		head2.next = head1.next;
    		head1.next = head2;
    		head1 = head2.next;
    		head2 = head2Next;
    		
    		if (head2 == null) {
    			head1.next = null;
    		}
    	}
    }
    
    public ListNode reverseList(ListNode head) {
    	ListNode prev = null;
    	ListNode cursor = head;
    	ListNode next = null;
    	
    	while (cursor != null) {
    		next = cursor.next;
    		cursor.next = prev;
    		prev = cursor;
    		cursor = next;
    	}
    	
    	return prev;
    }

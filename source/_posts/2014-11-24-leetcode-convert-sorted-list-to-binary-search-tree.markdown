---
layout: post
title: "Leetcode_Convert Sorted List to Binary Search Tree"
date: 2014-11-24 17:01:36 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/convert-sorted-list-to-binary-search-tree/

<!-- more -->

    public TreeNode sortedListToBST(ListNode head) {
		if (head == null) return null;

		ListNode cur = head;
		int size = 0;
		
		while (cur != null) {
			size++;
			cur = cur.next;
		}
		
		List<ListNode> list = new ArrayList<ListNode>();
		list.add(head);
		TreeNode tree = sortedListToBSTHelper(list, 0, size - 1);
		
		return tree;
    }
	
	public TreeNode sortedListToBSTHelper(List<ListNode> list, int low, int high) {
		if (low > high) return null;
		
		int mid = (low + high) / 2;
		
		TreeNode left = sortedListToBSTHelper(list, low, mid - 1);
		
		TreeNode root = new TreeNode(list.get(0).val);
		root.left = left;
		
		list.set(0, list.get(0).next);
		TreeNode right = sortedListToBSTHelper(list, mid + 1, high);
		root.right = right;
		
		return root;
	}

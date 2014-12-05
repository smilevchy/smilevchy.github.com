---
layout: post
title: "Leetcode_Convert Sorted Array to Binary Search Tree"
date: 2014-12-05 10:56:37 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/convert-sorted-array-to-binary-search-tree/

<!-- more -->

    public TreeNode sortedArrayToBST(int[] num) {
		if (num == null || num.length == 0) return null;
		
		List<Integer> cursor = new ArrayList<Integer>(1);
		cursor.add(0);
		
		return sortedArrayToBSTHelper(num, 0, num.length - 1, cursor);
    }
	
	public TreeNode sortedArrayToBSTHelper(int[] num, int low, int high, List<Integer> cursor) {
		if (low > high) return null;
		
		int mid = (low + high) / 2;
		
		TreeNode left = sortedArrayToBSTHelper(num, low, mid - 1, cursor);
		
		TreeNode root = new TreeNode(num[cursor.get(0)]);
		root.left = left;
		
		cursor.set(0, cursor.get(0) + 1);
		
		TreeNode right = sortedArrayToBSTHelper(num, mid + 1, high, cursor);
		root.right = right;
		
		return root;
	}

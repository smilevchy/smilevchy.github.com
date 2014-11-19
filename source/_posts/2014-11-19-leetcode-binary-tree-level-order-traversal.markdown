---
layout: post
title: "Leetcode_Binary Tree Level Order Traversal"
date: 2014-11-19 15:22:05 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/binary-tree-level-order-traversal/

<!-- more -->

    public List<List<Integer>> levelOrder(TreeNode root) {
		if (root == null) return new ArrayList<List<Integer>>();

		List<List<Integer>> result = new ArrayList<List<Integer>>();
		List<Integer> row = new ArrayList<Integer>();
		
		row.add(root.val);
		result.add(row);
		
		row = new ArrayList<Integer>();

		List<List<Integer>> leftList = null;
		if (root.left != null) {
			row.add(root.left.val);
			leftList = levelOrder(root.left);
		}
		
		List<List<Integer>> rightList = null;
		if (root.right != null) {
			row.add(root.right.val);
			rightList = levelOrder(root.right);
		}
		
		if (row.size() > 0) {
			result.add(row);
		}
		
		if (leftList != null) {
			leftList = leftList.subList(1, leftList.size());
		}
		
		if (rightList != null) {
			rightList = rightList.subList(1, rightList.size());
		}
		
		int i = 0;
		int leftSize = leftList != null ? leftList.size() : 0;
		int rightSize = rightList != null ? rightList.size() : 0;
		
		for (; i < leftSize; i++) {
			row = new ArrayList<Integer>();
			
			row.addAll(leftList.get(i));
			if (i < rightSize) row.addAll(rightList.get(i)); 
			
			result.add(row);
		}
		for (; i < rightSize; i++) {
			row = new ArrayList<Integer>();
			
			row.addAll(rightList.get(i));
			
			result.add(row);
		}
		
		return result;
    }
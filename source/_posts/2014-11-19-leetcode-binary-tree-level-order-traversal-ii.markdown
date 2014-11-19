---
layout: post
title: "Leetcode_Binary Tree Level Order Traversal II"
date: 2014-11-19 15:46:19 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/binary-tree-level-order-traversal-ii/

<!-- more -->

    public List<List<Integer>> levelOrderBottom(TreeNode root) {
		LinkedList<List<Integer>> result = new LinkedList<List<Integer>>();
		
		if (root == null) return result;
		
		ArrayDeque<TreeNode> queue = new ArrayDeque<TreeNode>();
		
		queue.offer(root);
		
		int lastNum = 1;
		int curNum = 0;
		List<Integer> row = new LinkedList<Integer>();
		
		while (!queue.isEmpty()) {
			lastNum--;
			
			TreeNode node = queue.poll();
			row.add(node.val);
			
			if (node.left != null) {
				curNum++;
				queue.offer(node.left);
			}
			
			if (node.right != null) {
				curNum++;
				queue.offer(node.right);
			}
			
			if (lastNum == 0) {
				result.addFirst(row);
				
				lastNum = curNum;
				curNum = 0;
				row = new LinkedList<Integer>();
			}
		}
		
		return result;
    }

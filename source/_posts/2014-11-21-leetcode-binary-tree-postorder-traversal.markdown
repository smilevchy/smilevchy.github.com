---
layout: post
title: "Leetcode_Binary Tree Postorder Traversal"
date: 2014-11-21 14:44:22 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/binary-tree-postorder-traversal/

<!-- more -->

    public List<Integer> postorderTraversal(TreeNode root) {
		List<Integer> result = new ArrayList<Integer>();
		
		if (root == null) return result;
		
		LinkedList<TreeNode> stack = new LinkedList<TreeNode>();
		TreeNode prev = null;
		
		while (root != null || !stack.isEmpty()) {
			if (root != null) {
				stack.push(root);
				root = root.left;
			} else {
				TreeNode peek = stack.peek();
				
				if (peek.right != null && peek.right != prev) {
					root = peek.right;
				} else {
					stack.pop();
					result.add(peek.val);
					prev = peek;
				}
			}
		}
		
		return result;
    }
	
	public List<Integer> postorderTraversal(TreeNode root) {
        List<Integer> result = new ArrayList<Integer>();
		
		if (root == null) return result;
		
		result.addAll(postorderTraversal(root.left));
		result.addAll(postorderTraversal(root.right));
		result.add(root.val);
		
		return result;
    }

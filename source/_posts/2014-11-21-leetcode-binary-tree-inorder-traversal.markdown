---
layout: post
title: "Leetcode_Binary Tree Inorder Traversal"
date: 2014-11-21 11:26:30 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/binary-tree-inorder-traversal/

<!-- more -->

    public List<Integer> inorderTraversal(TreeNode root) {
		List<Integer> result = new ArrayList<Integer>();
		
		if (root == null) return result;
		
		LinkedList<TreeNode> stack = new LinkedList<TreeNode>();
		
		while (root != null || !stack.isEmpty()) {
			if (root != null) {
				stack.push(root);
				root = root.left;
			} else {
				root = stack.pop();
				result.add(root.val);
				root = root.right;
			}
		}
		
		return result;
    }
	
	public List<Integer> inorderTraversal(TreeNode root) {
        List<Integer> result = new ArrayList<Integer>();
		
		if (root == null) return result;
		
		result.addAll(inorderTraversal(root.left));
		result.add(root.val);
		result.addAll(inorderTraversal(root.right));
		
		return result;
    }
	

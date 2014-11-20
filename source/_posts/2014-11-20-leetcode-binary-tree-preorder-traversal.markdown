---
layout: post
title: "Leetcode_Binary Tree Preorder Traversal"
date: 2014-11-20 18:17:38 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/binary-tree-preorder-traversal/

<!-- more -->

    public List<Integer> preorderTraversal(TreeNode root) {
		List<Integer> result = new ArrayList<Integer>();
		
		if (root == null) return result;
		
		LinkedList<TreeNode> stack = new LinkedList<TreeNode>();
		
		while (root != null || !stack.isEmpty()) {
			if (root != null) {
				result.add(root.val);
				stack.push(root);
				root = root.left;
			} else {
				root = stack.pop();
				root = root.right;
			}
		}
		
		return result;
    }
	
	public List<Integer> preorderTraversal(TreeNode root) {
		List<Integer> result = new ArrayList<Integer>();
		
		if (root == null) return result;
		
		result.add(root.val);
		result.addAll(preorderTraversal(root.left));
		result.addAll(preorderTraversal(root.right));
		
		return result;
    }
	
	

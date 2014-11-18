---
layout: post
title: "Leetcode_Balanced Binary Tree"
date: 2014-11-18 11:36:33 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/balanced-binary-tree/

<!-- more -->

    public boolean isBalanced(TreeNode root) {
		if (root == null) return true;
		
		int left = maxDepth(root.left);
		int right = maxDepth(root.right);
		
		if (Math.abs(left - right) > 1) {
			return false;
		}
		
		return isBalanced(root.left) && isBalanced(root.right);
    }
	
	public int maxDepth(TreeNode root) {
		if (root == null) return 0;
		
		if (root.left == null && root.right == null) {
			return 1;
		}
			
		return Math.max(maxDepth(root.left), maxDepth(root.right)) + 1;
    }

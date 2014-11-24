---
layout: post
title: "Leetcode_Flatten Binary Tree to Linked List"
date: 2014-11-24 14:42:54 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/flatten-binary-tree-to-linked-list/

<!-- more -->

    public void flatten(TreeNode root) {
        if (root == null) return;
        
        List<TreeNode> pre = new ArrayList<TreeNode>(1);
        pre.add(null);
        flattenHelper(root, pre);
    }
	
	private void flattenHelper(TreeNode root, List<TreeNode> pre) {
		if (root == null) return;

		if (pre.get(0) != null) {
			pre.get(0).left = null;
			pre.get(0).right = root;
		}
		
		TreeNode rootRight = root.right;
		pre.set(0, root);
		flattenHelper(root.left, pre);
		flattenHelper(rootRight, pre);
	}

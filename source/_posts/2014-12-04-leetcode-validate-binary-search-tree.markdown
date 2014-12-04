---
layout: post
title: "Leetcode_Validate Binary Search Tree"
date: 2014-12-04 11:04:02 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/validate-binary-search-tree/

<!-- more -->

    public boolean isValidBST(TreeNode root) {
		if (root == null) return true;
		
		LinkedList<TreeNode> inorderNodes = new LinkedList<TreeNode>();
		List<Integer> vals = new ArrayList<Integer>();
		
		while (root != null || !inorderNodes.isEmpty()) {
			if (root != null) {
				inorderNodes.push(root);
				root = root.left;
			} else {
				TreeNode top = inorderNodes.pop(); 
				vals.add(top.val);
				root = top.right;
			}
		}
		
		for (int i = 1, s = vals.size(); i < s; i++) {
			if (vals.get(i) <= vals.get(i -1)) return false;
		}
		
		return true;
    }

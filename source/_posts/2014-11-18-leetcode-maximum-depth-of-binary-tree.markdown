---
layout: post
title: "Leetcode_Maximum Depth of Binary Tree"
date: 2014-11-18 10:39:00 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/maximum-depth-of-binary-tree/

<!-- more -->

    public int maxDepth(TreeNode root) {
		if (root == null) return 0;
		
		if (root.left == null && root.right == null) {
			return 1;
		}
			
		return Math.max(maxDepth(root.left), maxDepth(root.right)) + 1;
    }

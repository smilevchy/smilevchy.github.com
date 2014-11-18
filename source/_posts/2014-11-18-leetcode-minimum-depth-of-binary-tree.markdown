---
layout: post
title: "Leetcode_Minimum Depth of Binary Tree"
date: 2014-11-18 10:30:14 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/minimum-depth-of-binary-tree/

<!-- more -->

    public int minDepth(TreeNode root) {
		if (root == null) return 0;
		
		if (root.left == null && root.right == null) {
			return 1;
		}  else if (root.left != null && root.right != null) {
			return Math.min(minDepth(root.left) + 1, minDepth(root.right) + 1);
		} else if (root.left != null) {
			return minDepth(root.left) + 1;
		} else {
			return minDepth(root.right) + 1;
		}
    }

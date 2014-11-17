---
layout: post
title: "Leetcode_Path Sum"
date: 2014-11-17 18:18:32 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/path-sum/

<!-- more -->

    public boolean hasPathSum(TreeNode root, int sum) {
		if (root == null) return false;

		if (root.left == null && root.right == null && root.val == sum) {
			return true;
		} if (hasPathSum(root.left, sum - root.val) || hasPathSum(root.right, sum - root.val)) {
			return true;
		}
		
		return false;
    }

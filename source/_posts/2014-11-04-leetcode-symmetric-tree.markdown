---
layout: post
title: "Leetcode_Symmetric Tree"
date: 2014-11-04 21:00:07 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/symmetric-tree/

<!-- more -->

一般涉及到树的问题我都喜欢用递归解法。

    public boolean isSymmetric(TreeNode root) {
        if (null == root) {
        	return true;
        }
        
        if (root.left == null && root.right == null) {
        	return true;
        } 
        
        if (root.left == null || root.right == null) {
        	return false;
        }
        
        TreeNode mirrorRootNodeOfLeft = new TreeNode(0);
        mirrorRootNodeOfLeft.left = root.left.left;
        mirrorRootNodeOfLeft.right = root.right.right;
        if (!isSymmetric(mirrorRootNodeOfLeft)) return false;
        
        TreeNode mirrorRootNodeOfRight = new TreeNode(0);
        mirrorRootNodeOfRight.left = root.left.right;
        mirrorRootNodeOfRight.right = root.right.left;
        if (!isSymmetric(mirrorRootNodeOfRight)) return false;
        
        if (root.left.val == root.right.val) return true; 
        
		return false;
    }
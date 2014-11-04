---
layout: post
title: "Leetcode_Same Tree"
date: 2014-11-04 21:08:15 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/same-tree/

    public boolean isSameTree(TreeNode p, TreeNode q) {
        if (p == null && q == null || p == q) {
        	return true;
        } else if (p == null || q == null) {
        	return false;
        }

        if (!isSameTree(p.left, q.left)) return false;
        if (!isSameTree(p.right, q.right)) return false;
        if (p.val == q.val) return true;
        
		return false;
    }

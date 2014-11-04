---
layout: post
title: "Leetcode_Jump Game"
date: 2014-11-04 21:34:32 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/jump-game/

~_~ 这道题是看别人的解法的（当然，我不是照抄那种，看过理解了自己再写的）
    
	public boolean canJump(int[] A) {
		if (A == null || A.length == 0) {
			return false;
		}
		
		int size = A.length;
		int dstPosition = size - 1;
		int maxReachPosition = 0;
		
		for (int i = 0; i <= maxReachPosition && i < size; i++) {
			maxReachPosition = Math.max(i + A[i], maxReachPosition);
		}
		
		if (maxReachPosition < dstPosition) {
			return false;
		}
		
		return true;
	}
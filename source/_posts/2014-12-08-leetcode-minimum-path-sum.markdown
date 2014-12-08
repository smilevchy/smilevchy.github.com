---
layout: post
title: "Leetcode_Minimum Path Sum"
date: 2014-12-08 11:08:51 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/minimum-path-sum/

<!-- more -->

    public int minPathSum(int[][] grid) {
        if (grid == null || grid.length == 0) return 0;
		
        int rows = grid.length;
        int cols = grid[0].length;
        int[] res = new int[cols];
        res[0] = grid[0][0];
        
        for (int i = 1; i < cols; i++) {
        	res[i] = res[i - 1] + grid[0][i];
        }
        
        for (int i = 1; i < rows; i++) {
        	for (int j = 0; j < cols; j++) {
        		int top = res[j];
        		int left = j == 0 ? Integer.MAX_VALUE : res[j - 1];
        		res[j] = Math.min(top, left) + grid[i][j];
        	}
        }
        
		return res[cols - 1];
    }

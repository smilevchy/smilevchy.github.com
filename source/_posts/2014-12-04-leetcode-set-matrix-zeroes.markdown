---
layout: post
title: "Leetcode_Set Matrix Zeroes"
date: 2014-12-04 12:03:59 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/set-matrix-zeroes/

<!-- more -->

    public void setZeroes(int[][] matrix) {
		if (matrix == null) return;
		
		int m = matrix.length;
		int n = matrix[0].length;
		
		boolean[] row = new boolean[m];
		boolean[] col = new boolean[n];
		
		for (int i = 0; i < m; i++) {
			for (int j = 0; j < n; j++) {
				if (matrix[i][j] == 0) {
					row[i] = true;
					col[j] = true;
				}
			}
		}
		
		for (int i = 0; i < m; i++) {
			for (int j = 0; j < n; j++) {
				if (row[i] || col[j]) {
					matrix[i][j] = 0;					
				}
			}
		}
    }
	
	public void setZeroesV2(int[][] matrix) {
		if (matrix == null) return;
		
		int m = matrix.length;
		int n = matrix[0].length;
		
		boolean firstRowZero = false;
		boolean firstColZero = false;
		
		for (int i = 0; i < m; i++) {
			for (int j = 0; j < n; j++) {
				if (matrix[i][j] == 0) {
					matrix[i][0] = 0;
					matrix[0][j] = 0;
					
					if (i == 0) firstRowZero = true;
					if (j == 0) firstColZero = true;
				}
			}
		}
		
		for (int i = 1; i < m; i++) {
			for (int j = 1; j < n; j++) {
				if (matrix[0][j] == 0 || matrix[i][0] == 0) matrix[i][j] = 0;
			}
		}
		
		if (firstRowZero) {
			for (int i = 0; i < n; i++) matrix[0][i] = 0;
		}
		
		if (firstColZero) {
			for (int i = 0; i < m; i++) matrix[i][0] = 0;
		}
	}
---
layout: post
title: "Leetcode_Rotate Image"
date: 2014-12-02 15:04:29 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/rotate-image/

<!-- more -->

    /*
	 * [1, 1, 1, 1, 1]
	 * [1, 2, 2, 2, 1]
	 * [1, 2, 3, 2, 1]
	 * [1, 2, 2, 2, 1]
	 * [1, 1, 1, 1, 1]
	 * 
	 * Like shown above, take the 2-dim array as it has some layers wrapping each other, layer 1 wraps layer 2, layer 2 wraps layer 3......
	 * For each layer, we can divide it into four blocks : top row, right col, bottom row, left col.
	 * What we have to do is : move top row to right col, right col to bottom row, bottom row to left col, left col to top row.
	 * And, we do this for times of numbers of layers(matrix's length / 2).  
	 */
	public void rotate(int[][] matrix) {
		if (matrix == null || matrix.length == 0 || matrix[0].length == 0) return;
		
		int matrixSize = matrix.length;
		int layerNum = matrixSize / 2;
		
		for (int i = 0; i < layerNum; i++) {
			for (int low = i, high = matrixSize - i - 1; low < high; low++) {
				int temp = matrix[i][low];

				// move left col to top row
				matrix[i][low] = matrix[matrixSize - low - 1][i];
				
				// move bottom row to left col
				matrix[matrixSize - low - 1][i] = matrix[high][matrixSize - low - 1];
				
				// move right col to bottom row
				matrix[high][matrixSize - low - 1] = matrix[low][high];
				
				// move top row to right col
				matrix[low][high] = temp; 
			}
		}
    }

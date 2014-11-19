---
layout: post
title: "Leetcode_Merge Sorted Array"
date: 2014-11-19 17:00:17 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/merge-sorted-array/

<!-- more -->

    public void merge(int A[], int m, int B[], int n) {
		int size = m + n;
		int[] workspace = new int[size];
		
		int i = 0;
		int j = 0;
		int k = 0;
		
		while (i < m && j < n) {
			if (A[i] < B[j]) {
				workspace[k++] = A[i++];
			} else {
				workspace[k++] = B[j++];
			}
		}
		
		while (i < m) {
			workspace[k++] = A[i++];
		}
		
		while (j < n) {
			workspace[k++] = B[j++];
		}
		
		for (k = 0; k < size; k++) {
			A[k] = workspace[k];
		}
    }

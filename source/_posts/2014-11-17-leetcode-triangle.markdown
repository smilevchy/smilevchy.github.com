---
layout: post
title: "Leetcode_Triangle"
date: 2014-11-17 17:08:01 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/triangle/

    public int minimumTotal(List<List<Integer>> triangle) {
		if (triangle == null) return 0;
		
		int size = triangle.size();
		int[] res = new int[triangle.get(size - 1).size()];

		for (int i = 0, s = triangle.get(size - 1).size(); i < s; i++) {
			res[i] = triangle.get(size - 1).get(i);
		}
		
		for (int i = size - 2; i >= 0; i--) {
			for (int j = 0; j <= i; j++) {
				res[j] = Math.min(res[j], res[j + 1]) + triangle.get(i).get(j);
			}
		}
		
		return res[0];
    }

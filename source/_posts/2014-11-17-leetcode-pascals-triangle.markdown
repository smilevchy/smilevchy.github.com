---
layout: post
title: "Leetcode_Pascal's Triangle"
date: 2014-11-17 18:42:09 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/pascals-triangle/

<!-- more -->

    public List<List<Integer>> generate(int numRows) {
		if (numRows <= 0) return new ArrayList<List<Integer>>();
		
		List<List<Integer>> pascalNums = new ArrayList<List<Integer>>(numRows);
		
		List<Integer> row = new ArrayList<Integer>(1);
		row.add(1);
		pascalNums.add(row);
		
		for (int i = 1; i < numRows; i++) {
			row = new ArrayList<Integer>(i + 1);
			
			for (int j = 0; j <= i; j++) {
				if (j == 0) {
					row.add(pascalNums.get(i - 1).get(0));
				} else if (j == i) {
					row.add(pascalNums.get(i - 1).get(pascalNums.get(i - 1).size() - 1));
				} else {
					row.add(pascalNums.get(i - 1).get(j - 1) + pascalNums.get(i - 1).get(j));
				}
			}
			
			pascalNums.add(row);
		}
		
		return pascalNums;
    }
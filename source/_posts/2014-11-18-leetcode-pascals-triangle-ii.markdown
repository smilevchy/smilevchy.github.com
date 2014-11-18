---
layout: post
title: "Leetcode_Pascal's Triangle II"
date: 2014-11-18 10:11:53 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/pascals-triangle-ii/

<!-- more -->

    public List<Integer> getRow(int rowIndex) {
		if (rowIndex < 0) return new ArrayList<Integer>();
		
		List<Integer> row = new ArrayList<Integer>(rowIndex + 1);
		
		if (rowIndex == 0) {
			row.add(1);
		} else {
			List<Integer> upRow = getRow(rowIndex - 1);
			
			for (int i = 0; i <= rowIndex; i++) {
				if (i == 0 || i == rowIndex) {
					row.add(1);
				} else {
					row.add(upRow.get(i - 1) + upRow.get(i));
				}
			}
		}
		
		return row;
    }

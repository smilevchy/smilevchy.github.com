---
layout: post
title: "Leetcode_Permutations"
date: 2014-12-03 10:48:28 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/permutations/

<!-- more --> 

    public List<List<Integer>> permute(int[] num) {
		List<List<Integer>> result = new ArrayList<List<Integer>>();
		
		if (num == null || num.length == 0) return result;

		List<Integer> first = new ArrayList<Integer>();
		for (int e : num) {
			first.add(e);
		}
		result.add(first);

		for (int pos = 0, len = num.length; pos < len; pos++) {
			for (int i = 0, s = result.size(); i < s; i++) {
				for (int j = pos + 1; j < len; j++) {
					List<Integer> ele = new ArrayList<Integer>(result.get(i));					
					
					ele.set(j, ele.get(j) ^ ele.get(pos));
					ele.set(pos, ele.get(j) ^ ele.get(pos));
					ele.set(j, ele.get(j) ^ ele.get(pos));

					result.add(ele);
				}
			}
		}
		
		return result;
    }

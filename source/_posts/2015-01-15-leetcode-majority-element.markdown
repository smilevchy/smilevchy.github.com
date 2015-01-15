---
layout: post
title: "Leetcode_Majority Element"
date: 2015-01-15 11:33:16 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/majority-element/

<!-- more -->

    public int majorityElement(int[] num) {
		Map<Integer, Integer> numToCount = new HashMap<Integer, Integer>();

		for (int i = 0, len = num.length; i < len; i++) {
			if (numToCount.get(num[i]) != null) {
				numToCount.put(num[i], numToCount.get(num[i]) + 1);
			} else {
				numToCount.put(num[i], 1);
			}
		}
		
		int majorityNum = 0;
		int maxLen = Integer.MIN_VALUE;
		
		Iterator<Integer> itr = numToCount.keySet().iterator();
		
		while (itr.hasNext()) {
			int key = itr.next();
			if (numToCount.get(key) > maxLen) {
				maxLen = numToCount.get(key);
				majorityNum = key;
			}
		}
		
		return majorityNum;
    }

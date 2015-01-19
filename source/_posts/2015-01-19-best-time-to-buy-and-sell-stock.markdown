---
layout: post
title: "Best Time to Buy and Sell Stock"
date: 2015-01-19 14:12:40 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/best-time-to-buy-and-sell-stock/

<!-- more -->

    public int maxProfit(int[] prices) {
		int local = 0;
		int global = 0;
		for (int i = 1, len = prices.length; i < len; i++) {
			local = Math.max(local + prices[i] - prices[i - 1], 0);
			global = Math.max(local, global);
		}
		
		return global;
    }

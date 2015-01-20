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
		if (prices == null || prices.length == 0) return 0;
	
		int local = 0;
		int global = 0;
		for (int i = 1, len = prices.length; i < len; i++) {
			local = Math.max(local + prices[i] - prices[i - 1], 0);
			global = Math.max(local, global);
		}
		
		return global;
    }
	
	// brute force (time limit exceed)
	public int maxProfit(int[] prices) {
		if (prices == null || prices.length == 0) return 0;
	
		int maxProfit = 0;
		int localProfit = 0;
		for (int i = 0, len = prices.length; i < len - 1; i++) {
			int max = 0;
			for (int j = i + 1; j < len; j++) {
				if (prices[j] > max) max = prices[j];
			}
			
			localProfit = max - prices[i];
			if (localProfit > maxProfit) maxProfit = localProfit;
		}
		
		return maxProfit;
    }

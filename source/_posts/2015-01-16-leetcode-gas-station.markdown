---
layout: post
title: "Leetcode_Gas Station"
date: 2015-01-16 18:05:34 +0800
comments: true
categories: Algorithm
---

原题链接: https://oj.leetcode.com/problems/gas-station/

<!-- more -->

    public int canCompleteCircuit(int[] gas, int[] cost) {
		if (gas == null || cost == null || gas.length != cost.length) {
			return -1;
		}
		
		int totalGas = 0;
		int subSeqGas = 0;
		int start = 0;
		for (int i = 0, numGasStation = gas.length; i < numGasStation; i++) {
			subSeqGas += gas[i] - cost[i];
			totalGas += gas[i] - cost[i];
			
			if (subSeqGas < 0) {
				subSeqGas = 0;
				start = i + 1;
			}
		}
		
		return totalGas >= 0 ? start : -1;
    }
	
	public int canCompleteCircuit(int[] gas, int[] cost) {
		// brute force (will meet time limit exceed)
		
		if (gas == null || cost == null || gas.length != cost.length) return -1;
		
		int numGasStation = gas.length;
		int remainGas = 0;
		int start = 0;
		boolean found = false;

		while (!found && start < numGasStation) {
			remainGas = 0;
			
			for (int index = start;;) {
				remainGas += gas[index];
				
				if (remainGas >= cost[index]) {
					remainGas -= cost[index];
					
					if (index == numGasStation - 1) {
						index = 0;
					} else {
						index++;
					}
					
					if (index == start) {
						found = true;
						break;
					}
				} else {
					start++;
					break;
				}
			}
			
		}
		
        return found ? start : -1;
    }
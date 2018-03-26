---
layout: post
title: 'GO练习（三）'
date: 2018-03-26 18:19
categories: 技术
tags: GO
---

## 题目

Given an array S of n integers, find three integers in S such that the sum is closest to a given number, target.
Return the sum of the three integers. You may assume that each input would have exactly one solution.

## 代码

```GO
package main
import (
	"fmt"
	"sort"
)
func main() {
	nums := []int{1, 2, 5, 13, -1, 3}
	fmt.Println(threeSumClosest(nums, 6))
}
func threeSumClosest(nums []int, target int) int {
	sort.Ints(nums)
	arrLen := len(nums)
	result := nums[0] + nums[1] + nums[arrLen-1]
	var sum int
	if len(nums) < 3 {
		return 0
	}
	for i := 0; i < arrLen; i++ {
		low, high := i+1, arrLen-1
		for low < high {
			sum = nums[i] + nums[low] + nums[high]
			if sum > target {
				high--
			} else {
				low++
			}
			if abs(sum-target) < abs(result-target) {
				result = sum
			}
		}
	}
	return result
}
func abs(a int) int {
	if a < 0 {
		return -a
	} else if a == 0 {
		return 0
	}
	return a
}
```

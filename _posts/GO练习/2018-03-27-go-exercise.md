---
layout: post
title: 'GO练习（四）'
date: 2018-03-27 21:04
categories: 技术
tags: GO
---

## 题目

Given an array S of n integers, are there elements a, b, c, and d in S such that a + b + c + d = target?
Find all unique quadruplets in the array which gives the sum of target.
Note: The solution set must not contain duplicate quadruplets.

## 代码

```GO
package main
import (
	"fmt"
	"sort"
)
func main() {
	nums := []int{-3, -2, -1, 0, 0, 1, 2, 3}
	fmt.Println(fourSum(nums, 0))
}
func fourSum(nums []int, target int) [][]int {
	sort.Ints(nums)
	arrLen := len(nums)
	result := make([][]int, 0, 0)
	temp := make([]int, 4, 4)
	var sum int
	for i := 0; i < arrLen-3; i++ {
		if i > 0 && nums[i] == nums[i-1] {
			continue
		}
		for j := i + 1; j < arrLen-2; j++ {
			if j > i+1 && nums[j] == nums[j-1] {
				continue
			}
			low, high := j+1, arrLen-1
			for low < high {
				sum = nums[i] + nums[j] + nums[low] + nums[high]
				if sum == target {
					temp = []int{nums[i], nums[j], nums[low], nums[high]}
					result = append(result, temp)
					for low < high && nums[low] == nums[low+1] {
						low++
					}
					for low < high && nums[high] == nums[high-1] {
						high--
					}
					low++
					high--
				} else if sum > target {
					high--
				} else {
					low++
				}
			}
		}
	}
	return result
}
```

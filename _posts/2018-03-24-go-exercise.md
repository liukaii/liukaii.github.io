---
layout: post
title: 'GO练习（一）'
date: 2018-03-24 12:05:08
categories: 技术
tags: GO
---

## 题目

Given an array of integers, return indices of the two numbers such that they add up to a specific target.
You may assume that each input would have exactly one solution, and you may not use the same element twice.

## 代码

```GO
package main
import (
	"fmt"
)
func main() {
	nums := []int{2, 7, 11, 15}
	fmt.Println(twoSum(nums, 9))
}
func twoSum(nums []int, target int) []int {
	arr := []int{}
	container := make(map[int]int)
	for i := 0; i < len(nums); i++ {
		if xy, ok := container[target-nums[i]]; ok && xy != 1 {
			arr = []int{container[target-nums[i]], i}
			return arr
		}
		container[nums[i]] = i
	}
	return arr
}
```

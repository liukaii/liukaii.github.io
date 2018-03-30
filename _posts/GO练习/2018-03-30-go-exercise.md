---
layout: post
title: 'GO练习（七）'
date: 2018-03-30 22:31
categories: 技术
tags: GO
---

## 题目

Given a sorted array, remove the duplicates in place such that each element appear only once and return the new length.
Do not allocate extra space for another array, you must do this in place with constant memory.

## 代码

```GO
package main
import (
	"fmt"
)
func main() {
	nums := []int{1, 1, 2, 3, 3, 3, 4, 5, 6, 6}
	fmt.Println(removeDuplicates(nums))
}
func removeDuplicates(nums []int) int {
	count := 0
	for i := 1; i < len(nums); i++ {
		if nums[i] == nums[i-1] {
			count++
		} else {
			nums[i-count] = nums[i]
		}
	}
	fmt.Println(nums)
	return len(nums) - count
}
```

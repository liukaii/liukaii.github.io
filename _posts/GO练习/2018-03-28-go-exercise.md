---
layout: post
title: 'GO练习（五）'
date: 2018-03-28 20:20
categories: 技术
tags: GO
---

## 题目

Implement next permutation, which rearranges numbers into the lexicographically next greater permutation of numbers.
If such arrangement is not possible, it must rearrange it as the lowest possible order (ie, sorted in ascending order).
The replacement must be in-place, do not allocate extra memory.

## 代码

```GO
package main
import (
	"fmt"
)
func main() {
	nums := []int{1, 3, 1, 3, 2}
	nextPermutation(nums)
	fmt.Println(nums)
}
func nextPermutation(nums []int) {
	arrLen := len(nums)
	if arrLen < 2 {
		return
	}
	index := -1
	for i := arrLen - 1; i > 0; i-- {
		if nums[i-1] < nums[i] {
			index = i - 1
			break
		}
	}
	if index == -1 {
		reverse(nums)
		return
	}
	for i := arrLen - 1; i > 0; i-- {
		if nums[i] > nums[index] {
			nums[i], nums[index] = nums[index], nums[i]
			reverse(nums[index+1:])
			break
		}
	}
	return
}
func reverse(nums []int) {
	for i, j := 0, len(nums)-1; i < j; i, j = i+1, j-1 {
		nums[i], nums[j] = nums[j], nums[i]
	}
	return
}
```

---
layout: post
title: 'GO练习（六）'
date: 2018-03-29 20:59
categories: 技术
tags: GO
---

## 题目

Given an array and a value, remove all instances of that value in place and return the new length.
Do not allocate extra space for another array, you must do this in place with constant memory.
The order of elements can be changed. It doesn't matter what you leave beyond the new length.

## 代码

```GO
package main
import (
	"fmt"
)
func main() {
	nums := []int{1, 2, 1, 3, 5, 2}
	fmt.Println(removeElement(nums, 2))
}
func removeElement(nums []int, val int) int {
	var result int
	for i := 0; i < len(nums); i++ {
		if nums[i] != val {
			nums[result] = nums[i]
			result++
		}
	}
	return result
}
```

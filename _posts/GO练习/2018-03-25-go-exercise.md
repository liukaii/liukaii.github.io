---
layout: post
title: 'GO练习（二）'
date: 2018-03-25 22:42
categories: 技术
tags: GO
---

## 题目

There are two sorted arrays nums1 and nums2 of size m and n respectively.
Find the median of the two sorted arrays. The overall run time complexity should be O(log (m+n)).
不过本代码复杂度并没有达到要求。不过可以作参考。

## 代码

```GO
package main
import (
	"fmt"
)
func main() {
	nums1 := []int{1, 87, 9}
	nums2 := []int{2, 5, 6}
	fmt.Println(findMedianSortedArrays(nums1, nums2))
}
func findMedianSortedArrays(nums1 []int, nums2 []int) float64 {
	l1, l2 := len(nums1), len(nums2)
	numbers1 := make([]float64, l1)
	numbers2 := make([]float64, l2)
	mergeArr := make([]float64, l1+l2)
	for i, val := range nums1 {
		numbers1[i] = float64(val)
	}
	for i, val := range nums2 {
		numbers2[i] = float64(val)
	}
	copy(mergeArr, numbers1)
	copy(mergeArr[l1:], numbers2)
	var temp float64
	var middle float64
	length := len(mergeArr)
	for i := 0; i < length-1; i++ {
		for j := 0; j < length-i-1; j++ {
			if mergeArr[j] > mergeArr[j+1] {
				temp = mergeArr[j]
				mergeArr[j] = mergeArr[j+1]
				mergeArr[j+1] = temp
			}
		}
	}
	if length == 0 {
		middle = 0
	} else if length%2 == 0 {
		fmt.Println((mergeArr[length/2] + mergeArr[length/2-1]) / 2)
		middle = (mergeArr[length/2] + mergeArr[length/2-1]) / 2
	} else {
		middle = mergeArr[length-1/2]
	}
	return middle
}
```

---
layout: post
title: 'GO练习（八）'
date: 2018-03-31 20:18
categories: 技术
tags: GO
---

## 题目

Fibonacci数列的简单实现

## 代码

```GO
package main
import (
	"fmt"
)
func fibonacci(n int) int {
	if n <= 2 {
		return 1
	}
	return fibonacci(n-1) + fibonacci(n-2)
}
func main() {
	for i := 1; i <= 10; i++ {
		fmt.Println(fibonacci(i))
	}
}
```

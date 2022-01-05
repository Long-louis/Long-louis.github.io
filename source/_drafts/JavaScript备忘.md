---
title: JavaScript备忘
author: 下龙湾
categories: 后端
tags:
  - 前端
  - JavaScript
toc: true
date: 2022-01-05 15:51:4
---

# 获得body标签的方法

1. 使用`getElementById`得到body类数组结构，由于文档中仅有一个`<body>`标签，故[0]号为body标签
2. ==推荐方法==：直接使用`document`中的`body`属性获得`body`标签
# 获得html根标签的方法
​			使用`document`中的`documentElement`属性

# 获得页面中的所有元素

1. `document.all`属性获得所有元素

2. 
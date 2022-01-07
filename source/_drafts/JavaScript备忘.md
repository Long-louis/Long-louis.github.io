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
2. `document.getElementsByTagName("*")`获得所有元素
# 获取同一`class`的元素
1. `document.getElementsByClassName()`
> 此方法不兼容IE8
2. `document.querySelector()`使用css的选择器语法
> 1. 此方法兼容IE8
> 2. 使用该方法总会返回唯一的一个元素，如果满足条件的元素有多个，那么它只会返回第一个
3. `document.querySelectorAll()`使用css的选择器语法获得所有的符合选择器的元素所构成的list
> 支持IE8
> 即使符合条件的元素只有一个，它也会返回数组				 
# 详解a标签中`href="javascript:;"`的几种用法
> 参考自[博客园](https://www.cnblogs.com/newones/p/12688580.html)

a标签的一种写法`<a href="JavaScript:;"></a>`，所以就来整理下a标签中href的几种用法。

一、js 伪协议的几种调用方法（参考总结的）

1. `"a href="javascript:js_method();"`

这是常用的方法，但是这种方法在传递`this`等参数的候很容易出问题，而且`javascript:`协议作为a的href属性的时候不仅会导致不必要的触发`windowonbeforeunload`事件，在IE里面更会使gif动画图片止播放。W3C标准不推荐在href里面执行javascript句

2. `"a href="javascript:void(0);"onclick="js_method()"`

这种方法是很多网站最常用的方法，也是最周全的法，onclick方法负责执行js函数，而void是一个操符，void(0)返回undefined，地址不发生跳转。而这种方法不会像第一种方法一样直接将js方法暴露在览器的状态栏。

3. `"a href="javascript:;" onclick="js_method()"`

这种方法跟跟2种类似，区别只是执行了一条空的js码。
    
4. `"a href="#" onclick="js_method()"`

 这种方法也是网上很常见的代码，#是标签内置的一个方法，代表top的作用。所以用这种方法点击后网页后返回到页面的最顶端。

5. `"a href="#" onclick="js_method();return false;"`

这种方法点击执行了js函数后return false，页面不发生跳转，执行后还是在页面的当前位置,不会跳转至顶部。

6. `<a href='javascript:todoFun(void)'>删除</a>`

这种方法在点击 a 标签时，执行一个 js 另外自定义函数 todoFun(void)。并传参 void。

  **综合上述，在a中调用js函数最适当的方法推荐使用:**
```html
1. <a href="javascript:void(0);" onclick="js_method()"></a> 
2. <a href="javascript:;" onclick="js_method()"></a> 
3. <a href="#" onclick="js_method();return false;"></a>
```
# `input`文本框输入内容
文本框的`value`属性即为用户输入的内容
# 元素样式获取
`getComputedStyle`获得的元素宽度和高度只包含内容区
`clientHeight`获得的元素宽度和高度包含内容区和内边距（padding）
满足`scrollHeight - scrollTop == clientHeight`说明垂直滚动条触底，同理可得水平滚动条到达右侧的等式
# 尚硅谷JS基础p112`clientX`问题
`clientX`是鼠标相对于当前显示区域的坐标，而绝对定位的div坐标是相对于整个文档的右上角进行计算，故当网页文档长度超过当前可视窗口时，会产生鼠标位置和div相偏移的问题。

解决方法：采用`pageX`来获取鼠标相对于整个文档的坐标。
# js中四种不同的函数调用方法及this的区别
[脚本之家JavaScript函数的4种调用方法详解](https://www.jb51.net/article/49230.htm)
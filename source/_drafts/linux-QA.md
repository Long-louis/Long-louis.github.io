---
title: linux_QA
date: 2021-12-04 22:25:30
toc: true
tags:
  - linux
---

# shell 内部命令&外部命令
## 内部命令
> 集成于Shell解释器程序内部的一些特殊指令，也称内建（Built-in）命令，属于Shell的一部分，没有单独对应的系统文件，自动载入内存，可以直接使用
## 外部命令
> Linux系统中能够完成特定功能的脚本文件或二进制程序，属于Shell解释器程序之外的命令，每个外部命令对于了系统中的一个文件，必须知道其文件位置，由Shell加载后才能执行`/bin,/usr/bin,/usr/local/bin`等

- `help`和`enable`可判断命令为内或外部命令

```
help + 参数
命令 + enable
```
- `type`可查询到指令的内外部命令信息：有路径是外部命令，内部则会告知内嵌

```
type + 参数
```

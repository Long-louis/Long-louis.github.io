---
title: conda使用方法
author: 下龙湾
top: true
categories: 后端
tags:
  - anaconda
  - python
toc: true
date: 2021-09-29 14:30:41
---


```
activate // 切换到base环境

activate learn // 切换到learn环境

deactivate 环境名 //退出当前环境

conda create -n learn python=3 // 创建一个名为learn的环境并指定python版本为3(的最新版本)

conda env list // 列出conda管理的所有环境

conda list // 列出当前环境的所有包

conda install requests //安装requests包

pip install requests //安装requests包

conda remove requests //卸载requets包

conda remove -n py36 tqdm //更新环境py36中的tqdm包

conda remove -n learn --all // 删除learn环境及下属所有包
conda env remove -n dev //删除不含包的dev环境

conda update requests 更新requests包

conda update anaconda  //更新anaconda

conda env export > environment.yaml // 导出当前环境的包信息

conda env create -f environment.yaml // 用配置文件创建新的虚拟环境

作者：AC手环
链接：https://www.jianshu.com/p/eaee1fadc1e9
来源：简书
```

```
//切换到文件所在目录
cd + space + 目录
```


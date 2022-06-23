---
title: 在conda虚拟环境下的PyQt配置及Pycharm相关设置
tags:
  - anaconda
  - python
  - PyQt
toc: true
author: 下龙湾
date: 2022-03-09 15:40:08
---

# 在conda虚拟环境中的PyQt配置
作者：葛煜龙
## 背景环境介绍
anaconda安装文件夹：`D:\anaconda`

需要配置PyQt的虚拟环境名：`AIClass`

需要配置PyQt的虚拟环境路径：`D:\anaconda\envs\AIClass`
## PyQt依赖包及PyQt-tools的下载
1. 在`anaconda navigator`中添加哈工大镜像源：`http://mirrors.hit.edu.cn/anaconda/pkgs/main/`
   ![](https://gitee.com/ninestars-lake/picgo-pictures/raw/master/blog/channel%20settings2.png)
2. 在左侧`environments`选项卡中切换conda环境为`AIClass`，并在`Search Pakages` 一栏搜索`pyqt`。在此我安装了5.92的版本
   ![](https://gitee.com/ninestars-lake/picgo-pictures/raw/master/blog/aiclass.png)
3. 打开`Anaconda Prompt`命令行窗口，执行`activate AIClass`命令切换到需要安装PyQt的虚拟环境。
4. > 通常在我们安装完Anoconda后，只有PyQt5库，而没有PyQt5-tools，点进去没有Qt Designer，具体可以查看Anoconda的路径。
   
   执行`pip install PyQt5-tools -i https://mirrors.hit.edu.cn/pypi/web/simple`命令，安装`PyQt5-tools`

5. 安装完成后命令行界面内会有`successful`字样。
## Pycharm进行PyQt的相关配置
1. 依次点击**文件>设置>外部工具**，进行`QtDesigner,PyUIC,Pyrcc`三个工具的添加。
![](https://gitee.com/ninestars-lake/picgo-pictures/raw/master/blog/20220309152520.png)
2. 首先添加`QtDesigner`。名称一栏可自己任意设置，建议设置为`QtDesigner`。程序一栏设置为`QtDesigner`的路径，5.92版本的路径大概如下`D:\anaconda\envs\AIClass\Lib\site-packages\qt5_applications\Qt\bin\designer.exe`。工作目录设置为`$FileDir$`,可点击后面的加号快捷设置。
   ![](https://gitee.com/ninestars-lake/picgo-pictures/raw/master/blog/20220309152754.png)
3. 第二步设置`PyUIC`。名称一栏可自己任意设置，建议设置为`PyUIC`。程序一栏设置为`QtDesigner`的安装路径中的`python.exe`文件，举例如下`D:\anaconda\envs\AIClass\python.exe`。实参设置为`-m PyQt5.uic.pyuic $FileName$ -o $FileNameWithoutExtension$.py`。工作目录设置为`$FileDir$`,可点击后面的加号快捷设置。
![](https://gitee.com/ninestars-lake/picgo-pictures/raw/master/blog/20220309153225.png)
4. 第三步设置`Pyrcc`。名称一栏可自己任意设置，建议设置为`Pyrcc`。程序一栏设置为`pycc.exe`文件，举例如下`D:\anaconda\Scripts\pycc.exe`。实参设置为`$FileName$ -o $FileNameWithoutExtension$_rc.py`。工作目录设置为`$FileDir$`,可点击后面的加号快捷设置。
   ![](https://gitee.com/ninestars-lake/picgo-pictures/raw/master/blog/20220309153516.png)
## 结语
到此，在conda虚拟环境下的PyQt配置及Pycharm相关设置进行完毕。至于设置是否成功的测试，百度即可找到，在此不再赘述。
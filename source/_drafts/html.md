# 一、第一个HTML页面

![第一个页面](https://gitee.com/ninestars-lake/picgo-pictures/raw/master/blog/%E7%AC%AC%E4%B8%80%E4%B8%AA%E9%A1%B5%E9%9D%A2.png)

`<title>` 标签中的内容为浏览器标签页显示的标题

`<!DOCTYPE html>` 声明用哪种版本的HTML生成网页

> 必须在html文档开头

`<html lang="zh-CN">` 规定网站语言

`<meta charset="UTF-8">` 规定字符集

# 二、HTML常用标签

## 标题标签

```html
<h1></h1>
<h2></h2>
........
```

## 段落标签

```html
<p>
</p>
```

## 换行标签

```html
<br />                                                                                      #break
```

## 文本格式化标签

|  语义  |                   标签                    |
| :----: | :---------------------------------------: |
|  加粗  | `<strong></strong>` 或 `<b></b>` *(bold)* |
|  倾斜  |    `<em></em>` 或`<i></i>` *(italic)*     |
| 删除线 |  `<del></del>` 或`<s></s>` *(Strikeout)*  |
| 下划线 |  `<ins></ins>` 或`<u></u>` *(underline)*  |

## `<div>` 和`<span>` 标签

### `<div>` 

> 意为division ，`<div>` 标签用来布局,但是一行只能放一个`<div>` *大盒子*

### `<span>`

>  `<span>` 标签用来布局,一行上可以多个`<span>` *小盒子*

## 图像标签和路径

### 图像标签

```html
< img src="图像URL"/>
```

> src属性必须有，指定图像文件路径和文件名

![图像标签属性](https://gitee.com/ninestars-lake/picgo-pictures/raw/master/blog/%E5%9B%BE%E5%83%8F%E6%A0%87%E7%AD%BE%E5%B1%9E%E6%80%A7.png)

> alt替换文本      即图像不能正常显示时，屏幕显示的文字

#### 图像标签属性注意点

1. 图像标签可以拥有多个属性,必须写在标签名的后面。
2. 属性之间不分先后顺序,标签名与属性、属性与属性之间均以空格分开。
3. 属性采取键值对的格式,即key="vaue"的格式,属性=“属性值

### 路径

#### 根目录

打开目录文件夹的第一层就是根目录

#### 相对路径

以引用文件所在位置为参考基础,而建立出的目录路径。这里简单来说,图片相对于HTML页面的位置。

![relative path](https://gitee.com/ninestars-lake/picgo-pictures/raw/master/blog/Relative%20path.png)

#### 绝对路径

例：`D: Web\img\logo.gif` 或完整的网络地址` http//www.itcast.cn/images/logo.gif`

***注意***：绝对路径用"`\`" ，相对路径和网络地址用"`/`"

## 超链接标签

```html
< a href="跳转目标" target="目标窗口的弹出方式">文本或图像</a>
```

> a意思为anchor（锚）

![Hyperlink tag properties](https://gitee.com/ninestars-lake/picgo-pictures/raw/master/blog/Hyperlink%20tag%20properties.png)

*self与blank前面只有一个下划线*

1. 外部链接:例如`<a href="htp://www.baiducom">`百度`</a>`
2. 内部链接网站内部页面之间的相互链接.直接链接内部页面名称即可,例如`< a href=" indexhtm">`首页`</a>`。
3. 空链接:如果当时没有确定链接目标时,`< a href="#">` 首页`</a>`。
4. 下载链接:如果`href`里面地址是一个文件或者压缩包,会下载这个文件
5. 网页元素链接:在网页的各种网页元素,如文本、图像、表格、音频、视频等都可以添加超链接 。
6. 锚点链接:点我们点击链接可以快速定位到页面中的某个位置
   -  在链接文本的`href`属性中, 设置属性值为 # 名字的形式,如`< a href="#wo">`第2集`</a>`
   - 找到目标位置标签,里面添加个`id`属性 = 刚才的名字,如:`<h3 id="two">`第2集介绍`</h3>`

## 注释和特殊字符

### 注释

`<!--注释语句-->  或  快捷键:ctrl+ / `

![special character](https://gitee.com/ninestars-lake/picgo-pictures/raw/master/blog/Special%20characters.png)

1. no-break space
2. less than
3. greater than


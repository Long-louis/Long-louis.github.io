---
title: CSS学习笔记(4)
author: 下龙湾
categories: 前端
tags:
  - css
toc: true 
description: css学习笔记
---

# HTML5和CSS3提高

## HTML5新特性

### HTML5新增的语义化标签

`< header>`:头部标签
`<nav>`:导航标签
`< article>`:内容标签
`< section`>:定义文档某个区域
`< aside>`:侧边栏标签
`< footer>`:尾部标签

![html5新增标签](https://gitee.com/ninestars-lake/picgo-pictures/raw/master/blog/image-20210826203239327.png)

> **注意** 
> 这种语义化标准主要是针对搜索引擎的
> 这些新标签页面中可以使用多次
> 在IE9中,需要把这些元素转换为块级元素
> 其实，我们移动端更喜欢使用这些标签
> HTML5还增加了很多其他标签，我们后面再慢慢学

### HTML5新增的多媒体标签

HTML5在不使用插件的情况下,也可以原生的支持视频格式文件的播放

#### 视频`<video>`

当前`< video>`元素支持三种视频格式：尽量使用mp4格式(所有浏览器都支持mp4，但并不都支持webm，ogg格式)

```css
< video src="文件地址" controls="controls"></ video>
```
```css
<video controls="controls" width="300">
<source src="move.ogg" type="video/ogg">
<source src="move.mp4" type="video/mp4">
您的浏览器暂不支持<video>标签播放视频
<video>
```

#### `<video>`常见属性

![image-20210826212158427](https://gitee.com/ninestars-lake/picgo-pictures/raw/master/blog/image-20210826212158427.png)

#### 音频`<audio>`
```css
< audio src="文件地址" controls="controls"></ audio>
```
```css
<audio controls="controls" width="300">
<source src="move.mp3" type="audio/mpeg">
<source src="move.ogg" type="audio/ogg">
您的浏览器暂不支持<audio>标签播放视频
<audio>
```

![audio](https://gitee.com/ninestars-lake/picgo-pictures/raw/master/blog/audio.png)

谷歌把音频的自动播放关闭了

#### 新增`<input>`类型

![image-20210827145550095](https://gitee.com/ninestars-lake/picgo-pictures/raw/master/blog/input.png)

#### HTML新增表单属性

![image-20210827160100208](https://gitee.com/ninestars-lake/picgo-pictures/raw/master/blog/html%E8%A1%A8%E5%8D%95%E5%B1%9E%E6%80%A7.png)

修改placeholder的默认颜色：

```css
 input::placeholder {
            color: turquoise;
        }
```

## CSS3新特性

### 新增选择器

1. 属性选择器

![image-20210827163630814](https://gitee.com/ninestars-lake/picgo-pictures/raw/master/blog/%E5%B1%9E%E6%80%A7%E9%80%89%E6%8B%A9%E5%99%A8.png)

**类选择器和属性选择器 伪类选择器 权重都是 0010**

***注意：***

```css
        div[class^=icon] {
            color: red;
        }        /* 权重为0011 */
```

### 结构伪类选择器

结构伪类选择器主要根据文档结构来选择器元素,常用于根据父级选择器里面的子元素

![image-20210827164943112](C:\Users\NH55\AppData\Roaming\Typora\typora-user-images\image-20210827164943112.png)

**区别:**

1. `nth-child`对父元素里面所有孩子排序选择(序号是固定的)先找到第n个孩子,然后看看是否和E匹配
2. `nth-of-type`对父元素里面指定子元素进行排序选择。先去匹配E,然后再根据E找第n个孩子

小结
- 结构伪类选择器一般用于选择父级里面的第几个孩子
- `nth-child`对父元素里面所有孩子排序选择(序号是固定的)先找到第n个孩子,然后看看是否和E匹配
- `nth-of-type`对父元素里面指定子元素进行排序选择。先去匹配E,然后再根据E找第n个孩子
关于`nth- child(n)`要知道n是从0开始计算的,要记住常用的公式
- 如果是无序列表,我们肯定用 `nth-child`更多
- 类选择器、属性选择器、伪类选择器,权重为0010

### 伪元素选择器

伪元素选择器可以帮助我们利用CSS创建新标签元素,而不需要HTML标签,从而简化HTML结构

| 选择符   | 简介                     |
| -------- | ------------------------ |
| ::before | 在元素内部的前面插入内容 |
| ::after  | 在元素内部的后面插入内容 |

- `before`和`after`创建一个元素,但是属于行内元素
- 新创建的这个元素在文档树中是找不到的,所以我们称为伪元素
- 语法: `element::before{}`
- `before`和 `after`必须有 `content`属性（可以为空白）
- 伪元素选择器和标签选择器一样,权重为0001

![image-20210906142928612](https://gitee.com/ninestars-lake/picgo-pictures/raw/master/blog/%E4%BC%AA%E5%85%83%E7%B4%A0%E5%9B%BE%E7%A4%BA.png)

```CSS
        /* 当我们鼠标经过了 土豆这个盒子，就让里面before遮罩层显示出来 */
        .tudou:hover::before {
            /* 而是显示元素 */
            display: block;
        }
```

### css3盒子模型

CSS3中可以通过`box-sizing`来指定盒子模型,有2个值:即可指定为 content-box、border-box，这样我们计算盒子大小的方式就发生了改变，可以分成两种情况

1. `box-sizing; content-box`盒子大小为`width+padding+border`(css3之前默认的）
2. `box-sizing: border-box`盒子大小为`width` 如果盒子模型我们改为了`box-sizing: border-box`,那 `padding`和 `border`就不会撑大盒子了(前提` padding`和 `border`不会超过`width`宽度)

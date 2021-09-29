---
title: CSS学习笔记(3)
author: 下龙湾
top: true
categories: 前端
tags:
  - css
toc: true 
date: 2021-08-25 14:46:00
---

# CSS定位

## 定位组成

定位：将盒子定在某一个位置,所以定位也是在摆放盒子,按照定位的方式移动盒子。
**定位=定位模式+边偏移**
定位模式用于指定一个元素在文档中的定位方式。边偏移则决定了该元素的最终位置。

### 定位模式

定位模式决定元素的定位方式,它通过CSS的 position属性来设置,其值可以分为四个：

| 值         | 语义     |
| ---------- | -------- |
| `static`   | 静态定位 |
| `relative` | 相对定位 |
| `absolute` | 绝对定位 |
| `fixed`    | 固定定位 |

### 边偏移
边偏移就是定位的盒子移动到最终位置。有`top、 bottom、lef`t和 `right `4个属性

![边偏移](https://gitee.com/ninestars-lake/picgo-pictures/raw/master/blog/%E8%BE%B9%E5%81%8F%E7%A7%BB.png)

## 静态定位
静态定位是元素的*默认定位方式,无定位的意思*。了解即可

- 静态定位按照标准流特性摆放位置,它没有边偏移
- 静态定位在布局时很少用到

## 相对定位

**相对定位**是元素在移动位置的时候，是相对于它原来的位置来说的(自恋型)。
语法

```css
选择器 {position:relative;}
```


相对定位的特点：(务必记住）

1. 它是相对于自己原来的位置来移动的(移动位置的时候参照点是自己原来的位置)。
2. ***原来在标准流的位置继续占有***,后面的盒子仍然以标准流的式对待它(不脱标,继续保留原来位置)。因此,相对定位并没有脱标。它最典型的应用是给绝对定位当爹的。

## 绝对定位 absolute(重要)
**绝对定位**是元素在移动位置的时候,是相对于它*祖先元素*来说的(拼爹型)。
语法

```css
选择器{ position: absolute;}
```
绝对定位的特点:(务必记住)

1. 如果没有祖先元素或者祖先元素没有定位,则以浏览器为准定位( Document文档)。
2. 如果祖先元素有定位(相对、绝对、固定定位),则以最近级的有定位祖先元素为参考点移动位置。
3. ***绝对定位不再占有原先的位置。***(脱标)

## 子绝父相
这句话的意思是:子级是绝对定位的话,父级要用相对定位。
①子级绝对定位,不会占有位置,可以放到父盒子里面的任何一个地方,不会影响其他的兄弟盒子。
②父盒子需要加定位限制子盒子只在在父盒子内显示。（如果父盒子没有定位，子盒子会以整个页面为参照）
③父盒子布局时,需要占有位置,因此父亲只能是相对定位这就是子绝父相的由来,所以相对定位经常用来作为绝对定位的父级。
总结:因为父级需要占有位置,因此是相对走位,子盒子不需要占有位置,则是绝对定位

## 固定定位 fixed(重要)

固定定位是元素固定于浏览器可视区的位置。主要使用场景:可以在浏览器页面滚动时元素的位置不会改变。
语法

```css
选择器{ position:fixed }
```
**固定定位的特点:(务必记住)**

1. 以浏览器的可视窗口为参照点移动元素，跟父元素没有任何关系，不随滚动条滚动
2. 固定定位不在占有原先的位置
3. 固定定位也是脱标的,其实固定定位也可以看做是一种特殊的绝对定位

***固定定位小技巧:固定在版心右侧位置***
方法；

1. 让固定定位的盒子left:50%.走到浏览器可视区(也可以看做版心)的一半位置
2. 让固定定位的盒子 margin-left:版心宽度的一半距离。多走版心宽度的一半位置就可以让固定定位的盒子贴着版心右侧对齐了。

## 粘性定位 sticky

粘性定位可以被认为是相对定位和固定定位的混合。 
语法

```css
选择器{ position: sticky;top:10px;}
```

粘性定位的特点
1.以浏览器的可视窗口为参照点移动元素(固定定位特点)
2.粘性定位**占有原先的位置**(相对定位特点)
3.必须添加top、left、 right、 bottom其中一个才有效
跟页面滚动搭配使用。兼容性较差,IE不支持。

## 定位叠放次序z- - index

在使用定位布局时,可能会出现盒子重叠的情况。此时,可以使用z- index来控制盒子的前后次序（z轴）
语法

```css
选择器{z- index:1;}
```

![定位总结](https://gitee.com/ninestars-lake/picgo-pictures/raw/master/blog/%E5%AE%9A%E4%BD%8D%E6%80%BB%E7%BB%93.png)

- 数值可以是正整数、负整数或0,默认是auto,数值越大,盒子越靠上
- 如果属性值相同,则按照书写顺序,后来居上
- 数字后面不能加单位
- 只有定位的盒子才有z- index属性

## 定位的拓展

### 绝对定位的盒子居中

加了绝对定位的盒子不能通过` margin:0 auto`水平居中,但是可以通过以下计算方法实现水平和垂直居中。
①left:50%；：让盒子的左侧移动到父级元素的水平中心位置
② margin-left:-100px:让盒子向左移动自身宽度的一半

### 定位特殊特性

绝对定位和固定定位也和浮动类似

1. 行内元素添加绝对或者固定定位,可以直接设置高度和宽度
2. 块级元素添加绝对或者固定定位,如果不给宽度或者高度,默认大小是内容的大小。

### 脱标的盒子不会触发外边距塌陷

浮动元素、绝对定位、固定定位元素的盒子都不会触发外边距合并的问题

### 绝对定位(固定定位)会完全压住盒子

浮动元素不同,只会压住它下面标准流的盒子,但是不会压住下面标准流盒子里面的文字(图片)
但是绝对定位(固定定位)会压住下面标准流所有的内容。
浮动之所以不会压住文字,因为浮动产生的目的最初是为了做文字环绕效果的。文字会围绕浮动元素

### 如果一个盒子既有left属性也有right属性，则默认会执行left属性。同理优先执行top属性

# 元素的显示与隐藏

## display属性

`display`属性用于设置一个元素应如何显示。
`display:none;`隐藏对象
`display:block;`除了转换为块级元素之外,同时还有显示元素的意思
`display`隐藏元素后,**不再占有原来的位置**
后面应用及其广泛,搭配JS可以做很多的网页特效。

## visibility可见性

`visibility`属性用于指定一个元素应可见还是隐藏
`visibility: visible;`元素可视
`visibility: hidden;`元素隐藏
`visibility`**隐藏元素后,继续占有原来的位置**
如果隐藏元素想要原来位置,就用 `visibility: hidden`
如果隐藏元素不想要原来位置,就用` display:none`(用处更多重点)

## overflow溢出

![overflow](https://gitee.com/ninestars-lake/picgo-pictures/raw/master/blog/overflow.png)

一般情况下,我们都不想让溢出的内容显示出来,因为溢出的部分会影响布局
但是如果有定位的盒子,请慎用 `overflow: hidden`因为它会隐藏多余的部分。

## 土豆网鼠标经过案例

当我们鼠标经过了士豆这个盒子,就让里面黑色遮罩层显示出来。

```css
.tudou:hover .mask {
    display:block;
}
```

# css高级技巧

## 为什么需要精灵图

一个网页中往往会应用很多小的背景图像作为修饰,当网页中的图像过多时,服务器就会频繁地接收和发送请求图片,造成服务器请求压力过大,这将大大降低页面的加载速度。因此,为了有效地减少服务器接收和发送请求的次数,提高页面的加载速度,出现了CSS精灵技术(也称CSS Sprites、CSS雪碧)。
核心原理:将网页中的一些小背景图像整合到一张大图中,这样服务器只需要一次请求就可以了。

## 精灵图( sprites)的使用

使用精灵图核心

1. 精灵技术主要针对于背景图片使用。就是把多个小背景图片整合到张大图片中。
2. 这个大图片也称为 sprites精灵图或者雪碧图
3. 移动背景图片位置,此时可以使用 background- position。
4. 移动的距离就是这个目标图片的x和y坐标。注意网页中的坐标左上角为原点，向下和向左为正方向。
5. 因为一般情况下都是往上往左移动,所以数值是负值。
6. 使用精灵图的时候需要精确测量,每个小背景图片的大小和位置
7. 精灵图使用原理就是设置一个小div，只让大合成图片中的一部分正好在`div`里面显示。

例：

```css
.box {
    width: 60px;
    height: 60px;
    margin: 100px auto;
    background: url(images/sprites.png) no-repeat -182px -244px;
}
```

## 字体图标

### 字体图标的产生

字体图标使用场景:主要用于显示网页中通用、常用的些小图标
精灵图是有诸多优点的,但是缺点很明显

1. 图片文件还是比较大的。
2. 图片本身放大和缩小会失真
3. 一个图片制作完毕想要更换非常复杂
   此时,有一种技术的出现很好的解决了以上问题,就是字体图标` iconfont` 字体图标可以为前端工程师提供种方便高效的图标使用方式,展示的是图标,本质属于字体

### 字体图标的优点

- 轻量级:一个图标字体要比一系列的图像要小一旦字体加载了,图标就会马上渲染出来,减少了服务器请求

- 灵活性:本质其实是文字,可以很随意的改变颜色产生阴影、透明效果、旋转等

- 兼容性:几乎支持所有的浏览器,请放心使用

**注意:**字体图标不能替代精灵技术,只是对工作中图标部分技术的提升和优化
  **总结:**

1. 如果遇到一些结构和样式比较简单的小图标，就用字体图标。
2. 如果遇到一些结构和样式复杂一点的小图片，就用精灵图。

推荐下载网站
[icomoon字库](http://icomoon.io)
icomoon成立于2011年推出了第一个自定义图标字体生成器,它允许用户选择所需要的图标,使它们成
字型。该字库内容种类繁多,非常全面,唯的遗憾是国外服务器,打开网速较慢。
[阿里iconfont字库](http://www.iconfont.cn/)
这个是阿里M2UX的个 iconfont字体图标字库,包含了淘宝图标库和阿里妈玛妈图标库。可以使用AI
制作图标上传生成。重点是,免费!

### 字体图标的追加

如果工作中,原来的字体图标不够用了,我们需要添加新的字体图标到原来的字体文件中。
把压缩包里面的`selection. json`从新上传,然后选中自己想要新的图标,从新下载压缩包,并替换原来的文件即可。

## CSS三角

![css三角](https://gitee.com/ninestars-lake/picgo-pictures/raw/master/blog/css%E4%B8%89%E8%A7%92.png)

```css
 .box1 {
            width: 0;
            height: 0;
            /* border: 10px solid pink; */
            border-top: 10px solid pink;
            border-right: 10px solid red;
            border-bottom: 10px solid blue;
            border-left: 10px solid green;
        }
<div class="box1"></div>
```

实现左侧三角形

```css
 .box2 {
            width: 0;
            height: 0;
     		line-height: 0;
     		font-size: 0;
            border: 50px solid transparent;
            border-left-color: pink;
            margin: 100px auto;
        }
 <div class="box2"></div>
```

## CSS用户界面样式

### 鼠标样式

```css
li {cursor: pointer;}
```

| 属性值      | 描述      |
| ----------- | --------- |
| default     | 小白 默认 |
| pointer     | 小手      |
| move        | 移动      |
| text        | 文本      |
| not-allowed | 禁止      |

### 表单轮廓线outline

```css
input {outline: none;}
```

### 防止拖拽文本域rersize

```css
textarea {resize: none; }
```

## vertical-align属性应用

CSS的`vertical-align`属性使用场景：经常用于设置图片或者表单(行内块素)和文字垂直对齐。(图片和表单都属于行内块元素)
官方解释:用于设置一个元素的垂直对齐方式,但是它只针对于*行内元素或者行内块元素有效*
语法:

```css
display: inline-block
vertical-align: baseline /top/ middle/ bottom/
```

![vertical-align](https://gitee.com/ninestars-lake/picgo-pictures/raw/master/blog/vertical-align.png)

![字符线](https://gitee.com/ninestars-lake/picgo-pictures/raw/master/blog/%E5%AD%97%E7%AC%A6%E7%BA%BF.png)

### 解决图片底部默认空白缝隙的问题

bug:图片底侧会有一个空白缝隙,原因是行内块元素会和文字的基线对齐。
主要解决方法有两种:

1. 给图片添加 vertical- align; middle top bottom等。(提倡使用的)
2. 把图片转换为块级元素 display: block；（因为块级元素没有vertical-align属性）

## 溢出的文字省略号显示

### 单行文本显示省略号

```css
/*1.先强制一行内显示文本*/
white-space: nowrap;(默认norma1自动换行)
/*2.超出的部分隐藏*/
overflow: hidden;
/*3.文字用省略号替代超出的部分*/
text-overflow: ellipsis;
```

### 多行文本显示省略号

```css
			overflow: hidden;
            text-overflow: ellipsis;
            /* 弹性伸缩盒子模型显示 */
            display: -webkit-box;
            /* 限制在一个块元素显示的文本的行数 */
            -webkit-line-clamp: 3;
            /* 设置或检索伸缩盒对象的子元素的排列方式 */
            -webkit-box-orient: vertical;
```

更推荐让后台人员来做这个效果,因为后台人员可以设置显示多少个字,操作更简单。

## 常见布局技巧

### margin负值的巧妙运用

#### 一

![margin负值巧妙运用](https://gitee.com/ninestars-lake/picgo-pictures/raw/master/blog/margin%E8%B4%9F%E5%80%BC%E5%B7%A7%E5%A6%99%E8%BF%90%E7%94%A8.png)

要实现每一个盒子的四周都有相同的橙色边框，可以令所有边框`margin-left:-1px`，这样子原本重合导致加粗的边框会变成正常宽度的边框，实现完美的显示效果。

#### 二

实现当鼠标经过时，盒子的边框全都变色

```css
        ul li:hover {
           /* 1. 如果盒子没有定位，则鼠标经过添加相对定位即可 */
        position: relative;
        border: 1px solid blue;

       } 
        ul li:hover {
            /* 2.如果li都有定位，则利用 z-index提高层级 */
            z-index: 1;
            border: 1px solid blue;
```

### 文字围绕浮动元素巧妙运用

```css
    <style>
        * {
            margin: 0;
            padding: 0;
        }
        .box {
            width: 300px;
            height: 70px;
            background-color: pink;
            margin: 0 auto;
            padding: 5px;
        }
        .pic {
            float: left;
            width: 120px;
            height: 60px;
            margin-right: 5px;
        }
        .pic img {
            width: 100%;
        }
    </style>
<body>
    <div class="box">
        <div class="pic">
            <img src="images/img.png" alt="">
        </div>
        <p>【集锦】热身赛-巴西0-1秘鲁 内马尔替补两人血染赛场</p>
    </div>
</body>
```

### 行内块巧妙运用

![image-20210826124020823](https://gitee.com/ninestars-lake/picgo-pictures/raw/master/blog/%E8%A1%8C%E5%86%85%E5%9D%97%E5%B7%A7%E5%A6%99%E8%BF%90%E7%94%A8.png)

```css
<style>
        * {
            margin: 0;
            padding: 0;
        }
        .box {
            text-align: center;
        }
        .box a {
            display: inline-block;
            width: 36px;
            height: 36px;
            background-color: #f7f7f7;
            border: 1px solid #ccc;
            text-align: center;
            line-height: 36px;
            text-decoration: none;
            color: #333;
            font-size: 14px;
        }
       .box .prev,
        .box .next {
            width: 85px;
        }
        .box .current,
        .box .elp {
            background-color: #fff;
            border: none;
        }
        .box input {
            height: 36px;
            width: 45px;
            border: 1px solid #ccc;
            outline: none;
        }
        .box button {
           width: 60px;
           height: 36px;
           background-color: #f7f7f7;
            border: 1px solid #ccc;
            
        }
    </style>
<body>
    <div class="box">
        <a href="#" class="prev">&lt;&lt;上一页</a>
        <a href="#" class="current">2</a>
        <a href="#">3</a>
        <a href="#">4</a>
        <a href="#">5</a>
        <a href="#">6</a>
        <a href="#" class="elp">...</a>
        <a href="#" class="next">&gt;&gt;下一页</a>
        到第 
        <input type="text">
        页
        <button>确定</button>
    </div>
</body>
```

### css三角强化的巧妙运用

![三角运用](https://gitee.com/ninestars-lake/ninestars-lake/raw/bd3453c42711dda44aa25753bb296e8598ccb071/blog/image-20210825164837215.png)



```css
 .box1 {
            width: 0;
            height: 0;
            /* 把上边框宽度调大 */
            /* border-top: 100px solid transparent;
            border-right: 50px solid skyblue; */
            /* 左边和下边的边框宽度设置为0 */
            /* border-bottom: 0 solid blue;
            border-left: 0 solid green; */
           /* 1.只保留右边的边框有颜色 */
           border-color: transparent blue  transparent transparent;
            /* 2. 样式都是solid */
            border-style: solid;
            /* 3. 上边框宽度要大， 右边框 宽度稍小， 其余的边框该为 0 */
            border-width: 100px 50px 0 0 ;

        }
```

## CSS初始化

不同浏览器对有些标签的默认值是不同的,为了消除不同浏览器对HTML文本呈现的差异,照顾浏览器的兼容,我们需要对CSS初始化。
简单理解:CSS初始化是指重设浏览器的样式。(也称为 CSS reset)
每个网页都必须首先进行CS初始化。

> **Unicode编码字体：**
> 把中文字体的名称用相应的Unicode编码来代替,这样就可以有效的避免浏览器解释CSS代码时候出现乱码的问题。
> 比如
> 黑体\9ED1\4F53
> 宋体\5B8B\4F53
> 微软雅黑\5FAE\8F6F\96C5\9ED1 

以京东初始化代码为例子

```css
/* 把我们所有标签的内外边距清零 */
* {
    margin: 0;
    padding: 0
}
/* em 和 i 斜体的文字不倾斜 */
em,
i {
    font-style: normal
}
/* 去掉li 的小圆点 */
li {
    list-style: none
}

img {
    /* border 0 照顾低版本浏览器 如果 图片外面包含了链接会有边框的问题 */
    border: 0;
    /* 取消图片底侧有空白缝隙的问题 */
    vertical-align: middle
}

button {
    /* 当我们鼠标经过button 按钮的时候，鼠标变成小手 */
    cursor: pointer
}

a {
    color: #666;
    text-decoration: none
}

a:hover {
    color: #c81623
}

button,
input {
    /* "\5B8B\4F53" 就是宋体的意思 这样浏览器兼容性比较好 */
    font-family: Microsoft YaHei, Heiti SC, tahoma, arial, Hiragino Sans GB, "\5B8B\4F53", sans-serif
}

body {
    /* CSS3 抗锯齿形 让文字显示的更加清晰 */
    -webkit-font-smoothing: antialiased;
    background-color: #fff;
    font: 12px/1.5 Microsoft YaHei, Heiti SC, tahoma, arial, Hiragino Sans GB, "\5B8B\4F53", sans-serif;
    color: #666
}

.hide,
.none {
    display: none
}
/* 清除浮动 */
.clearfix:after {
    visibility: hidden;
    clear: both;
    display: block;
    content: ".";
    height: 0
}

.clearfix {
    *zoom: 1
}
```


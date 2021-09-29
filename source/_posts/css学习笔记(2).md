---
title: CSS学习笔记(2)
author: 下龙湾
categories: 前端学习
tags:
  - css
toc: true 
date: 2021-08-18 14:46:00
---

# CSS盒子模型

**网页布局过程：**

1. 先准备好相关的网页元素,网页元素基本都是盒子Box。

2. 利用CSS设置好盒子样式,然后摆放到相应位置。

3. 往盒子里面装内容

*网页布局的核心本质:就是利用CSS摆盒子*

所谓盒子模型:就是把HTML页面中的布局元素看作是一个短形的盒子,也就是一个盛装内容的容器。

CSS盒子模型本质上是一个盒子,封装周围的HTML元素,它包括:边框、外边距、内边距、和实际内容

![css盒子](https://gitee.com/ninestars-lake/ninestars-lake/raw/master/blog/cssbox.png)

## 盒子边框

```css
border : border-width || border-style || border-color  #具体参数见css3手册
```

### 边框复合写法


```css
border: 1px solid red; 没有顺序
```

### 边框分开写发

```css
border-top: 1px solid red;/*只写上边框，其他同理*/
```

### 表格细线边框

```css
table,
td,th {
    border: 1px solid pink;
    /*合并表格相邻的边框*/
	border-collapse: collapse;
    font-size: 14px;
    text-align: center;
}
```

***注意边框会影响盒子的实际大小***，即加上边框之后盒子会比设置的width和height变大

## 盒子模型内边距

| 属性           | 作用         |
| -------------- | ------------ |
| padding-left   | 盒子左内边距 |
| padding-right  | 盒子右内边距 |
| padding-top    | 盒子上内边距 |
| padding-bottom | 盒子下内边距 |



#### padding复合属性

![padding复合属性](https://gitee.com/ninestars-lake/ninestars-lake/raw/master/blog/padding%E5%A4%8D%E5%90%88%E8%BE%B9%E8%B7%9D.png)

***注意padding会影响盒子的实际大小***，即加上padding之后盒子会比设置的width和height变大

#### padding不会影响盒子大小的情况

盒子性质的标签本身没有指定width/height属性，则不会影响盒子大小，盒子大小一直和内容有关

例：

```css
h1 {
    height: 200px;
    background-color: pink;
    padding: 30px;
}/*则最终只有高度发生改变，宽度不变*/
```



```css
/*div里面放了p标签*/
div {
    width: 300px;
    height: 100px;
    background-color: purple;
}
div p {
    padding: 30px;
}/*则最终只有高度发生改变变为60px，宽度不会超过div的宽度*/
```

## 盒子模型外边距

| 属性          | 作用     |
| ------------- | -------- |
| margin-left   | 左外边距 |
| margin-right  | 右外边距 |
| margin-top    | 上外边距 |
| margin-bottom | 下外边距 |

### margin复合属性

写法与padding相同

### 外边距典型应用

***让块级元素在页面居中显示：***

1. 盒子必须指定了宽度(width)
2. 盒子左右的外边距都设置为auto。

```css
.header{ width:960px; margin:0 auto;}
```

常见的三种写法：

- margin-left: auto；margin-right: auto；
- margin: auto；
- margin: 0 auto；

**注意:**以上方法是让块级元素水平居中,*行内元素或者行内块元素水平居中给其父元素添加 text-align: center即可*

例：

```css
.header {
    width: 90px;
    height: 200px;
    margin: 100px auto;
    text-align: center;
}
<body>
	<div class="header">
		<span>insideword</span>
	<div>
<body>
```

### 外边距合并

#### 1.相邻块元素垂直外边距的合并

当上下相邻的两个块元素(兄弟关系)相遇时,如果上面的元素有下外边距 margin-bottom,下面的元素有上外边距 margIn-top,则他们之间的垂直间距不是 margIn- bottom与 margIn-top之和而是取两个值中的
较大者。这种现象被称为相邻块元素垂直外边距的合并。
**解决方案：**尽量只给一个盒子添加margin值

#### 2.嵌套块元素垂直外边距的塌陷

对于两个嵌套关系(父子关系)的块元素,父元素有上外边距同时子元素也有上外边距,此时父元素会塌陷二者之中较大的外边距值。

> 浮动的盒子不会发生塌陷

**解决方法：**
①可以为父元素定义上边框。这样子元素的margin会产生效果

②可以为父元素定义上内边距。

③可以为父元素添加 overflow: hidden。

![外边距的塌陷](https://gitee.com/ninestars-lake/ninestars-lake/raw/master/blog/%E5%A4%96%E8%BE%B9%E8%B7%9D%E7%9A%84%E5%A1%8C%E9%99%B7.png)

## 清除内外边距

网页元素很多都带有默认的内外边距,而且不同浏览器默认的也不—致。因此我们在布局前,首先要清除下网页元素的内外边距。

```css
/*css的第一行代码*/
* {
    padding: 0;內边距为零
    margin: 0;外边距为零
}
```

**注意:**行内元素为了照顾兼容性,尽量只设置左右内外边距,不要设置上下内外边距。但是转换为块级和行内块元素就可以了.

## 总结问答

1. 布局为啥用不同盒子我只想用dv?
   标签都是有语义的合理的地方用合理的标签。比如产品标题就用h,大量文字段落就用p
2. 为啥用辣么多类名?
   类名就是给每个盒子起了一个名字可以更好的找到这个盒子选取盒子更容易后期维护也方便。
3. 到底用 margin还是 padding?
   大部分情况两个可以混用,两者各有优缺点,但是根据实际情况,总是有更简单的方法实现。
4. 自己做没有思路?
   布局有很多种实现方式,同学们可以开始先模仿我的写法,然后再做出自己的风格。最后同学们一定多运用辅助工具比如屏幕画笔，ps等等

***去掉`<li>`前面的小圆点***

```css
list-style: none;
```

## 圆角边框

```css
border-radius: length;   /*length为圆角半径*/
```

**应用：**

1. 制作圆形边框 

```css
div {
    width:200px;
    height: 200px;
    border-radius: 100px/50%
}/*即正方形边框再加上边长一半的圆角*/
```

2. 制作边为半圆的矩形

```css
div {
    width: 400px;
    height: 200px;
    border-radius: 100px
}/*即长方形边框再加上高一半的圆角*/
```

3. 该属性是一个简写属性,可以跟四个值,分别代表左上角、右上角、右下角、左下角
4. 分开写: `border- top-left-radius、 border-top- right- radius、 border-bottom-right-radius和border-bottom -left-radius`

## 盒子阴影

```css
box-shadow: h-shadow v-shadow blur spread color inset;
```

![盒子阴影](https://gitee.com/ninestars-lake/ninestars-lake/raw/master/blog/%E7%9B%92%E5%AD%90%E9%98%B4%E5%BD%B1.png)

*默认为outset，但不可以写出来outset，否则不会有阴影效果*

> 盒子阴影不占用空间，不会影响其他盒子的排列

## 文字阴影

```css
text-shadow: h-shadow v-shadow blur color
```

*参数具体意义同上*

# css浮动

传统网页布局的三种方式：

- 普通流

- 浮动

- 定位

## 普通流（标准流/文档流）

所谓的标准流:就是标签按照规定好默认方式排列

1. 块级元素会独占一行,从上向下顺序排列。常用元素:`div、hr、p、h1~h6、ul、ol、dl、 form、table`

2. 行内元素会按照顺序,从左到右顺序排列,碰到父元素边缘则自动换行。常用元素:span、a、i、em等


以上都是标准流布局,我们前面学习的就是标准流,标准流是最基本的布局方式。

**注意:**实际开发中,一个页面基本都包含了这三种布局方式（后面移动端学习新的布局方式）

## 浮动

### 为什么需要浮动

浮动可以改变标签默认的排列方式

**浮动最典型的应用:**可以让多个块级元素行内排列显示。
**网页布局第一准则:**多个块级元素纵向排列找标准流,多个块级元素横向排列找浮动

### 什么是浮动

```css
选择器 {float: 属性值}
```

| 属性值 | 描述                 |
| ------ | -------------------- |
| none   | 元素不浮动（默认值） |
| left   | 元素向左浮动         |
| right  | 元素向右浮动         |

### 浮动特性(重难点)
加了浮动之后的元素会具有很多特性需要我们掌握的：

特性一：***浮动元素会脱离标准流***（脱标)

特性二：浮动的元素会行内显示并且元素顶部对齐

特性三：浮动的元素会具有行内块元素的特性

#### 特性一

设置了浮动(float)的元素**最重要特性**：

1. 脱离标准普通流的控制(浮)移动到指定位置(动),(俗称脱标)

2. 浮动的盒子不再保留原先的位置。

   > 第二条的意思即为设置为浮动后的盒子原有位置不再保留，而是被其他的盒子占据

粉色盒子未加浮动时：

![粉色盒子未加浮动时](https://gitee.com/ninestars-lake/ninestars-lake/raw/master/blog/%E7%B2%89%E8%89%B2%E7%9B%92%E5%AD%90%E6%9C%AA%E5%8A%A0%E6%B5%AE%E5%8A%A8%E6%97%B6.png)

粉色盒子加浮动时：

![粉色盒子加浮动时](https://gitee.com/ninestars-lake/ninestars-lake/raw/master/blog/%E7%B2%89%E8%89%B2%E7%9B%92%E5%AD%90%E5%8A%A0%E6%B5%AE%E5%8A%A8%E6%97%B6.png)

#### 特性二

如果多个盒子都设置了浮动,则它们会按照属性值一行内显示并且顶端对齐排列。

注意:浮动的元素是互相贴靠在一起的(不会有缝隙),如果父级宽度装不下这些浮动的盒子,多出的盒子会另起一行对齐

#### 特性三

浮动元素会具有行内块元素特性。

任何元素都可以浮动。不管原先是什么模式的元素,添加浮动之后具有行内块元素相似的特性

- 如果块级盒子没有设置完度,默认宽度和父级一样宽,但是添加浮动后,它的大小根据内容来决定
- 浮动的盒子中间是没有缝隙的,是紧挨着一起的
- 行内元素同理

```css
  span {
            float: left;
            width: 200px;
            height: 100px;
            background-color: pink;
        }/*任何元素都可以浮动，不管原先是什么模式的元素，添加浮动之后都具有行内块元素相似的特性*/
```

```css
div {
            float: left;
            width: 200px;
            height: 100px;
            background-color: pink;
      }
<div>1234<div>/*添加浮动之后，行内元素不需要转化为行内块元素或块元素即可直接设置宽高，若未设置，则盒子大小由内容决定*/
```

### 浮动元素经常和标准流父级搭配使用

为了约束浮动元素位置我们网页布局般采取的策略是:先用标准流的父元素排列上下位置之后内部子元素采取浮动排列左右位置。符合网页布局第一准则

网页布局第二准则:先设置盒子大小,之后设置盒子的位置
## 浮动布局注意点
1. 浮动和标准流的父盒子搭配。
    先用标准流的父元素排列上下位置之后内部子元素采取浮动排列左右位置

2. 一个元素浮动了,理论上其余的兄弟元素也要浮动
    一个父盒子里面有多个子盒子,如果其中一个盒子浮动了,那么其他兄弟也应该浮动,以防止引起问题
    *浮动的盒子只会影响浮动盒子后面的标准流不会影响前面的标准流*

## 清除浮动

我们前面浮动元素有一个标准流的父元素,他们有一个共同的特点都是有高度的.但是所有的父盒子都必须有高度吗?

![清除浮动](https://gitee.com/ninestars-lake/ninestars-lake/raw/master/blog/%E6%B8%85%E6%A5%9A%E6%B5%AE%E5%8A%A8.png)

![清除浮动](https://gitee.com/ninestars-lake/ninestars-lake/raw/master/blog/%E6%B8%85%E9%99%A4%E6%B5%AE%E5%8A%A8.png)

### 原因

由于父级盒子很多情况下,不方便给高度,但是子盒子浮动又不占有位置,最后父级盒子高度为0时,就会影响下面的标准流盒子。

![子盒子浮动](https://gitee.com/ninestars-lake/ninestars-lake/raw/master/blog/%E5%AD%90%E7%9B%92%E5%AD%90%E6%B5%AE%E5%8A%A8.png)

### 本质

- 清除浮动的本质是清除浮动元素造成的影响

- 如果父盒子本身有高度,则不需要清除浮动

- 清除浮动之后,父级就会根据浮动的子盒子自动检测高度。**父级有了高度,就不会影响下面的标准流了**

```css
选择器{clear:属性值}
```

| 属性值 | 描述                                     |
| ------ | ---------------------------------------- |
| left   | 不允许左侧有浮动元素(清除左侧浮动的影响) |
| right  | 不允许右侧有浮动元素(清除右侧浮动的影响) |
| both   | 同时清除左右两侧浮动的影响               |

***实际工作中，几乎只用`both`，清除浮动的策略是：闭合浮动***

### 方法

#### 额外标签法

额外标签法也称为隔墙法,是W3C推荐的做法。额外标签法会在浮动元素末尾添加个空的标签。例如`< div style=" clear:both"></div>`,或者其他标签(如`<br/>`等)。

- 优点:通俗易懂,书写方便
- 缺点:添加许多无意义的标签,结构化较差
- ***注意:要求这个新的空标签必须是块级元素***

#### 父级添加overflow

可以给父级添加 overflow属性,将其属性值设置为 hidden、auto或 scroll。子不教父之过，注意是给父元素添加代码

- 优点:代码简洁
- 缺点:无法显示溢出的部分 

#### after伪元素法

：after方式是额外标签法的升级版。也是给父元素添加

```css
.clearfix::after {
    content: "";
    display: block;
    height: 0;
    clear: both;
    visibility: hidden;
}
.clearfix {/*IE6,7专有*/
    *zoom: 1;
}
```



#### 双伪元素清除浮动

```css
.clearfix::before,.clearfix::after {
    content:"";
    display:table; /* 转换为块级元素并在一行显示 */
}
.clearfix:after {
    clear:both;
}
.clearfix {
    *zoom: 1;
}
```




# 常见网页布局

![常见网页布局](https://gitee.com/ninestars-lake/ninestars-lake/raw/master/blog/%E5%B8%B8%E8%A7%81%E7%BD%91%E9%A1%B5%E5%B8%83%E5%B1%80.png)

![常见网页布局](https://gitee.com/ninestars-lake/ninestars-lake/raw/master/blog/%E5%B8%B8%E8%A7%81%E7%BD%91%E9%A1%B5%E5%B8%83%E5%B1%802.png)

> 只要是通栏的盒子都和浏览器一样宽，不需要指定width

# ps切图

## 常见图像类型
2. 1. jpg图像格式:JPEG(JPG)对色彩的信息保留较好,高清,颜色铋多,我们产品类的图片经常用jpg格 式的
2. qi图像格式:GF格式最多只能储存256色,所以通常用来显示简单图形及字体,但是可以保存透明背景和动画效果实际经常用于一些图片小动画效果
3. png图像格式是—种新兴的网络图形格式,结合了G和PEG的优点,具有存储形式丰富的特点,能够保持透明背景如果想要切成背景透明的图片,请选择ρng格式
4. PSD图像格式PSD格式是 Photoshop的专用格式,里面可以存放图层、通道、遮罩等多种设计稿对我们前端人员来说最大的优点我们可以直接从上面复制文字获得图片,还可以测量大小和距离

## 图层切图

选中想要导出的图层，右键导出为png

但是很多情况下我们需要合并图层再导出:

1. 选中需要的图层:图层菜单→合并图层(trl+e)

2. 右击→快速导出为PNG

## 切片切图

1. 利用切片选中图片
   利用切片工具手动划出
2. 导出选中的图片
   文件菜单→导出→存储为web设备所用格式→选择我们要的图片格式→存储。
   注意想要保存为透明背景需要在图层栏隐藏背景色在导出为png格式。
   

# 学成在线网站案例制作

## css属性书写顺序(重点)

1. 布局定位属性: `display/ position/float/clear/visibility/overflow`(建议 display第一个写,毕竟关系到横式)
2. 自身属性:`width/ height/ margIn/ padding/ border/ background`
3. 文本属性: `color/font/text-decoration/text-align/vertical-align/white-space/break-word`
4. 其他属性( CSS3): `content/cursor/border-radius/box-shadow/text-shadow/background: linear-gradient`

## 页面布局整体思路

为了提高网页制作的效率,布局时通常有以下的整体思路

1. 必须确定页面的版心(可视区),我们测量可得知具体大小。
2. 分析页面中的行模块,以及每个行模块中的列模块。其实就是页面布局第一准则。
3. —行中的列模块经常浮动布局,先确定每个列的大小之后确定列的位置.页面布局第二准则。
4. 制作HTML结构。我们还是遵循,先有结构,后有样式的原则。结构永远最重要
    所以先理清楚布局结构再写代码尤为重要这需要我们多写多积累

## 头部制作

![导航栏](https://gitee.com/ninestars-lake/ninestars-lake/raw/master/blog/%E5%AD%A6%E6%88%90%E5%9C%A8%E7%BA%BFnav%E5%AF%BC%E8%88%AA%E6%A0%8F.png)

实际开发中,我们不会直接用链接`a`而是`li`包含链接(`li+a`)的做法
1. `li+a`语义更清晰,一看这就是有条理的列表型内容
2. 如果直接用`a`,搜索引擎容易辨别为有堆砌关键字嫌疑(故意堆砌关键字容易被搜索引攣有降权的风险)从而影响网站排名
3. 让导航栏一行显示，给`li`加浮动因为`li`是块级元素需要一行显示
4. 这个nav导航栏可以不给宽度将来可以继续添加其余文字
5. 因为导航栏里面文字不一样多所以最好给链接a左右 padding撑开盒子而不是指定宽度

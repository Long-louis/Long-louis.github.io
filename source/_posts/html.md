---
title: html学习笔记
author: 下龙湾
toc: true
categories: 前端学习
tags:
  - html
date: 2021-08-07 14:37:00
---




**参考链接**

1. 标签缩写查询网站：[MDN](https://developer.mozilla.org/en-US/docs/Web/HTML)
   
2. 学习视频教程网站：[bilibili黑马pink老师HTML](https://www.bilibili.com/video/BV14J4114768?p=42&amp;spm_id_from=pageDriver)

   

   


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

### 特殊字符

![special character](https://gitee.com/ninestars-lake/picgo-pictures/raw/master/blog/Special%20characters.png)

1. no-break space
2. less than
3. greater than

## 表格标签

### 表格的基本语法

```html
<table>
	<tr>
		<td>单元格内的文字</ td>
	</tr>
</table>
```

1. `< table></table>`是用于定义表格的标签。
2. `<tr></tr>`标签用于定义表格中的行,必须嵌套在`< table></ table>`标签中。
3. `<td></td>`用于定义表格中的单元格,必须嵌套在`<tr></tr>`标签中。
4. 字母`td`指表格数据( `table data`),即数据单元格的内容。

#### 标签属性

![table tag properties](https://gitee.com/ninestars-lake/picgo-pictures/raw/master/blog/table%20tag%20properties.png)

> 只需熟悉属性名即可，更详细的对表格的操作使用css

#### 表头标签

> 一般表头单元格位于表格的第一行或第一列,表头单元格里面的文本内容加粗居中显示
> `<th>`标签表示HTML表格的表头部分( `table head`)的缩写

#### 表格结构标签

1. `< thead></ thead>`:用定义表格的头部。`< thead>`内部必须拥有`<tr>`标签。一般是位于第一行。

2. `< tbody></ tbody>`:用于定义表格的主体,主要用于放数据本体。

3. 以上标签都是放在`< table></table>`标签中。
#### 合并单元格

##### 属性

- 跨行:最上侧单元格为目标单元格,写合并代码		`rowspan`

- 跨列:最左侧单元格为目标单元格,写合并代码        `colspan`

##### 步骤
1. 先确定是跨行还是跨列合并。
2. 找到目标单元格写上合并方式=合并的单元格数量。比如:`< td colspan="2"> </td>`
3. 删除多余的单元格

## 列表标签

### 无序列表

`<ul>`:unordered list

`<li>`:list item

```html
<ul>
	<li>列表项1</li>
	<li>列表项2</li>
	<li>列表项3</li>
</ul>
```

1. 无序列表的各个列表项之间没有顺序级别之分,是并列的。

2. `<ul></ul>`中只能嵌套`<li></li>`,直接在`<ul></ul>`标签中输入其他标签或者文字的做法是不被允许的。

3. `<i>`与`</i>`之间相当于一个容器,可以容纳所有元素。

4. 无序列表会带有自己的样式属性,但在实际使用时,我们会使用CSS来设置

### 有序列表

```html
<ol>
	<li>列表项1</li>
	<li>列表项2</li>
	<li>列表项3</li>
</ol>
```

> 注意事项同无序列表

*有序列表实际开发使用不多*

### 自定义列表

```html
<dl>
	<dt>名词1</dt>
	<dd>名词1解释1</dd>
	<dd>名词1解释2</dd>
</dl>
```

`<dl>`:defined list

`<dt>`:Description Term

`<dd>`:Description Details

> `<dl>`里面只能有`<dt>`，`<dd>`。`<dt>`，`<dd>`里面可以包含任何元素

## 表单标签

在HTML中,一个完整的表单通常由表单域、表单控件(也称为表单元素)和提示信息3个部分构成。

### 表单域

表单域是一个包含表单元素的区域。
在HTML标签中,`<form>`标签用于定义表单域,以实现用户信息的收集和传递
`<form>`会把它范围内的表单元素信息提交给服务器

 ```html
 < form action="url地址" method="提交方式"name="表单域名称">
 各种表单元素控件
 </form>
 ```

![form tag properties](https://gitee.com/ninestars-lake/picgo-pictures/raw/master/blog/form%20tag%20properties.png)
### 表单控件
#### `<input>`输入表单标签

在英文单词中, input是输入的意思,而在表单元素中< input>标签用于收集用户信息。
在< input>标签中,包含-个type属性,根据不同的type属性值,输入字段拥有很多种形式(可以是文本
字段、复选框、掩码后的文本控件、单选按钮、按钮等)。

```html
< Input type="属性值"/>
```

* `< input/>`标签为单标签
* type属性设置不同的属性值用来指定不同的控件类型

![input tag type prooerties](https://gitee.com/ninestars-lake/picgo-pictures/raw/master/blog/input%20tag%20type%20prooerties.png)

![input tag properties](https://gitee.com/ninestars-lake/picgo-pictures/raw/master/blog/input%20tag%20properties.png)

***要实现radio单选按钮的多选一，所有的相关radio控件必须具有相同的name。复选框同理***

> value即input框中的提示语，radio和checkbox在页面中不显示value，但在后台代码可见

1. name和value是每个表单元素都有的属性值主要给后台人员使用
2. name表单元素的名字要求*单选按钮和复选框要有相同的name值*

#### `<label>`标签

`< label>`标签为` input`元素定义标注(标签)。
`<lable>`标签用于绑定一个表单元素当点击`<lable>`标签内的文本时,浏览器就会自动将焦点光标转到或者
选择对应的表单元素上用来增加用户体验

```html
<label for=sex">男</label>
<input type="radio" name="sex" id="sex"/>
```

**核心:`< label>`标签的`for`属性应当与相关元素的`id`属性相同。**

#### `<select>`下拉表单标签

```html
<select>
	< option>选项1</ option>
	< option>选项2</ option>
	< option>选项3</ option>
</select>
```

1. `< select>`中至少包含一对`< option>`。
2. 在`< option>`中定义 `selected=" selected"`时,当前项即为默认选中项。

#### `<textarea>`文本域标签

用于输入多行大段文本

```html
<textarea rows="3" cols="20">
文本内容(可以在此填写想要默认显示的内容)
</textarea>
```

* rows规定可填写的总行数（但实际上填写时按回车即可继续添加）

* cols规定每行的字符数


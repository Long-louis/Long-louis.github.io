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
# 判断
  * `typeof`:
    * **可以判断**: `undefined/ 数值 / 字符串 / 布尔值 / function`
    * **不能判断**:`null与object  array与object`
      > null 有属于自己的类型 Null，而不属于Object类型，typeof 之所以会判定为 Object 类型，是因为JavaScript 数据类型在底层都是以二进制的形式表示的，二进制的前三位为 0 会被 typeof 判断为对象类型，而 null 的二进制位恰好都是 0 ，因此，null 被误判断为 Object 类型
      
      > 初始赋值为null，表明该变量将要赋值为对象

      > 当对象使用完毕之后，将指向的变量再次赋值为null，可以让无用对象被浏览器回收
  * `instanceof`:
    * 判断对象的具体类型
  * `===`
    * 可以判断: undefined, null
      > 因为二者的值都只有一种情况
# 原型与原型链
![](https://gitee.com/ninestars-lake/picgo-pictures/raw/master/blog/%E5%8E%9F%E5%9E%8B%E9%93%BE.png)
1. 每个函数function都有一个prototype，即显式原型(属性)。函数的prototype属性是在定义函数时自动添加的, 默认值是一个空Object实例对象。
2. 每个实例对象都有一个__proto__，可称为隐式原型(属性)
3. 对象的隐式原型的值为其对应构造函数的显式原型的值

 * 访问一个对象的属性时，
    * 先在自身属性中查找，找到返回
    * 如果没有, 再沿着__proto__这条链向上查找, 找到返回
    * 如果最终没找到, 返回undefined
  * 别名: 隐式原型链
  * 作用: 查找对象的属性(方法)
![](https://gitee.com/ninestars-lake/picgo-pictures/raw/master/blog/%E5%8E%9F%E5%9E%8B%E4%B8%8E%E5%8E%9F%E5%9E%8B%E9%93%BE.png)
1. instanceof是如何判断的?
    >  * 表达式: A instanceof B
    >  * 如果B函数的显式原型对象在A对象的原型链上, 返回true, 否则返回false
2. Function是通过new自己产生的实例
# 变量提升与函数提升

```javascript
function fun() {
  
}
var fun = function () {
  
}
```
**两种函数声明方式有所区别**：*第一种*是进行函数提升，在后文声明过的函数可在前文使用。*第二种*是进行变量提升，在后文声明的函数在前文无法使用，而是显示`undefined`。

先执行变量提升，后执行函数提升
 #  继承模式
   ## 原型链的继承
   步骤：

  1. 定义父类型构造函数
  2. 给父类型的原型添加方法
  3. 定义子类型的构造函数
  4. **创建父类型的实例对象赋值给子类型的原型对象**
  5. **将子类型原型的构造属性设置为子类型**
  6. 给子类型原型添加方法
  7. 创建子类型的对象: 可以调用父类型的方法
   
   关键：
   
   子类型的原型为父类型的一个实例对象
   ```javascript
    //父类型
  function Supper() {
    this.supProp = 'Supper property'
  }
  Supper.prototype.showSupperProp = function () {
    console.log(this.supProp)
  }

  //子类型
  function Sub() {
    this.subProp = 'Sub property'
  }

  // 子类型的原型为父类型的一个实例对象
  Sub.prototype = new Supper()
  // 让子类型的原型的constructor指向子类型
  Sub.prototype.constructor = Sub
  Sub.prototype.showSubProp = function () {
    console.log(this.subProp)
  }

  var sub = new Sub()
  sub.showSupperProp()
  // sub.toString()
  sub.showSubProp()

  console.log(sub)  // Sub
  ```
## 实际应用所采用的方法——组合继承

```javascript
function Person(name, age) {
    this.name = name
    this.age = age
  }
  Person.prototype.setName = function (name) {
    this.name = name
  }

  function Student(name, age, price) {
    Person.call(this, name, age)  // 为了得到属性
    this.price = price
  }
  Student.prototype = new Person() // 为了能看到父类型的方法
  Student.prototype.constructor = Student //修正constructor属性
  Student.prototype.setPrice = function (price) {
    this.price = price
  }

  var s = new Student('Tom', 24, 15000)
  s.setName('Bob')
  s.setPrice(16000)
  console.log(s.name, s.age, s.price)
  ```

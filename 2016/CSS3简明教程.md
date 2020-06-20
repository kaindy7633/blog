<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [第一章 初识CSS3](#%E7%AC%AC%E4%B8%80%E7%AB%A0-%E5%88%9D%E8%AF%86css3)
  - [什么是CSS3？](#%E4%BB%80%E4%B9%88%E6%98%AFcss3)
  - [CSS3能做什么](#css3%E8%83%BD%E5%81%9A%E4%BB%80%E4%B9%88)
- [第2章 边框](#%E7%AC%AC2%E7%AB%A0-%E8%BE%B9%E6%A1%86)
  - [圆角效果 border-radius](#%E5%9C%86%E8%A7%92%E6%95%88%E6%9E%9C-border-radius)
  - [阴影 box-shadow](#%E9%98%B4%E5%BD%B1-box-shadow)
  - [参数介绍](#%E5%8F%82%E6%95%B0%E4%BB%8B%E7%BB%8D)
  - [为颜色设置外阴影：](#%E4%B8%BA%E9%A2%9C%E8%89%B2%E8%AE%BE%E7%BD%AE%E5%A4%96%E9%98%B4%E5%BD%B1)
  - [阴影模糊半径与阴影扩展半径的区别](#%E9%98%B4%E5%BD%B1%E6%A8%A1%E7%B3%8A%E5%8D%8A%E5%BE%84%E4%B8%8E%E9%98%B4%E5%BD%B1%E6%89%A9%E5%B1%95%E5%8D%8A%E5%BE%84%E7%9A%84%E5%8C%BA%E5%88%AB)
  - [X轴偏移量和Y轴偏移量值可以设置为负数](#x%E8%BD%B4%E5%81%8F%E7%A7%BB%E9%87%8F%E5%92%8Cy%E8%BD%B4%E5%81%8F%E7%A7%BB%E9%87%8F%E5%80%BC%E5%8F%AF%E4%BB%A5%E8%AE%BE%E7%BD%AE%E4%B8%BA%E8%B4%9F%E6%95%B0)
  - [为边框应用图片 border-image](#%E4%B8%BA%E8%BE%B9%E6%A1%86%E5%BA%94%E7%94%A8%E5%9B%BE%E7%89%87-border-image)
- [第3章 颜色相关](#%E7%AC%AC3%E7%AB%A0-%E9%A2%9C%E8%89%B2%E7%9B%B8%E5%85%B3)
  - [颜色之RGBA](#%E9%A2%9C%E8%89%B2%E4%B9%8Brgba)
  - [渐变色彩](#%E6%B8%90%E5%8F%98%E8%89%B2%E5%BD%A9)
- [第4章 文字与字体](#%E7%AC%AC4%E7%AB%A0-%E6%96%87%E5%AD%97%E4%B8%8E%E5%AD%97%E4%BD%93)
  - [text-overflow与word-wrap](#text-overflow%E4%B8%8Eword-wrap)
  - [嵌入字体@font-face](#%E5%B5%8C%E5%85%A5%E5%AD%97%E4%BD%93font-face)
  - [文本阴影text-shadow](#%E6%96%87%E6%9C%AC%E9%98%B4%E5%BD%B1text-shadow)
- [第5章 与背景相关的样式](#%E7%AC%AC5%E7%AB%A0-%E4%B8%8E%E8%83%8C%E6%99%AF%E7%9B%B8%E5%85%B3%E7%9A%84%E6%A0%B7%E5%BC%8F)
  - [background-origin](#background-origin)
  - [background-clip](#background-clip)
  - [background-size](#background-size)
  - [multiple backgrounds](#multiple-backgrounds)
- [第6章 征服CSS3选择器](#%E7%AC%AC6%E7%AB%A0-%E5%BE%81%E6%9C%8Dcss3%E9%80%89%E6%8B%A9%E5%99%A8)
  - [属性选择器](#%E5%B1%9E%E6%80%A7%E9%80%89%E6%8B%A9%E5%99%A8)
  - [结构性伪类选择器 root](#%E7%BB%93%E6%9E%84%E6%80%A7%E4%BC%AA%E7%B1%BB%E9%80%89%E6%8B%A9%E5%99%A8-root)
  - [结构性伪类选择器 not](#%E7%BB%93%E6%9E%84%E6%80%A7%E4%BC%AA%E7%B1%BB%E9%80%89%E6%8B%A9%E5%99%A8-not)
  - [结构性伪类选择器 empty](#%E7%BB%93%E6%9E%84%E6%80%A7%E4%BC%AA%E7%B1%BB%E9%80%89%E6%8B%A9%E5%99%A8-empty)
  - [结构性伪类选择器 target](#%E7%BB%93%E6%9E%84%E6%80%A7%E4%BC%AA%E7%B1%BB%E9%80%89%E6%8B%A9%E5%99%A8-target)
  - [结构性伪类选择器 first-child](#%E7%BB%93%E6%9E%84%E6%80%A7%E4%BC%AA%E7%B1%BB%E9%80%89%E6%8B%A9%E5%99%A8-first-child)
  - [结构性伪类选择器 last-child](#%E7%BB%93%E6%9E%84%E6%80%A7%E4%BC%AA%E7%B1%BB%E9%80%89%E6%8B%A9%E5%99%A8-last-child)
  - [结构性伪类选择器 nth-child(n)](#%E7%BB%93%E6%9E%84%E6%80%A7%E4%BC%AA%E7%B1%BB%E9%80%89%E6%8B%A9%E5%99%A8-nth-childn)
  - [结构性伪类选择器 nth-last-child(n)](#%E7%BB%93%E6%9E%84%E6%80%A7%E4%BC%AA%E7%B1%BB%E9%80%89%E6%8B%A9%E5%99%A8-nth-last-childn)
  - [first-of-type选择器](#first-of-type%E9%80%89%E6%8B%A9%E5%99%A8)
  - [nth-of-type(n)选择器](#nth-of-typen%E9%80%89%E6%8B%A9%E5%99%A8)
  - [last-of-type选择器](#last-of-type%E9%80%89%E6%8B%A9%E5%99%A8)
  - [nth-last-of-type(n)选择器](#nth-last-of-typen%E9%80%89%E6%8B%A9%E5%99%A8)
  - [only-child选择器](#only-child%E9%80%89%E6%8B%A9%E5%99%A8)
  - [only-of-type选择器](#only-of-type%E9%80%89%E6%8B%A9%E5%99%A8)
  - [:enabled选择器](#enabled%E9%80%89%E6%8B%A9%E5%99%A8)
  - [:disabled选择器](#disabled%E9%80%89%E6%8B%A9%E5%99%A8)
  - [:checked选择器](#checked%E9%80%89%E6%8B%A9%E5%99%A8)
  - [::selection选择器](#selection%E9%80%89%E6%8B%A9%E5%99%A8)
  - [:read-only选择器](#read-only%E9%80%89%E6%8B%A9%E5%99%A8)
  - [:read-write选择器](#read-write%E9%80%89%E6%8B%A9%E5%99%A8)
  - [::before和::after](#before%E5%92%8Cafter)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# 第一章 初识CSS3

## 什么是CSS3？

> CSS3是CSS2的升级版本，3只是版本号，它在CSS2.1的基础上增加了很多强大的新功能。 目前主流浏览器chrome、safari、firefox、opera、甚至360都已经支持了CSS3大部分功能了，IE10以后也开始全面支持CSS3了。

在编写CSS3样式时，不同的浏览器可能需要不同的前缀。它表示该CSS属性或规则尚未成为W3C标准的一部分，是浏览器的私有属性，虽然目前较新版本的浏览器都是不需要前缀的，但为了更好的向前兼容前缀还是少不了的。  

前缀|浏览器
---|---
-webkit|chrome和safari
-moz|firefox
-ms|IE
-o|opera

## CSS3能做什么

> CSS3给我们带来了什么好处呢？简单的说，CSS3把很多以前需要使用图片和脚本来实现的效果、甚至动画效果，只需要短短几行代码就能搞定。比如圆角，图片边框，文字阴影和盒阴影，过渡、动画等。

CSS3简化了前端开发工作人员的设计过程，加快页面载入速度。

CSS3都有哪些强大功能呢？

* 选择器: 以前我们通常用`class`、 `ID` 或 `tagname` 来选择HTML元素，CSS3的选择器强大的难以置信。它们可以减少在标签中的class和ID的数量更方便的维护样式表、更好的实现结构与表现的分离。
* 圆角效果:以前做圆角通常使用背景图片，或繁琐的元素拼凑，现在很简单了 `border-radius` 帮你轻松搞定。
* 块阴影与文字阴影:可以对任意DIV和文字增加投影效果。
* 色彩:CSS3支持更多的颜色和更广泛的颜色定义。新颜色CSS3支持HSL、CMYK、HSLA and RGBA。
* 渐变效果:以前只能用Photoshop做出的图片渐变效果，现在可以用CCS写出来了。IE中的滤镜也可以实现。
* 个性化字体:网页上的字体太单一？使用`@Font-Face` 轻松实现定制字体。
* 多背景图:一个元素上添加多层背景图片。
* 边框背景图:边框应用背景图片。
* 变形处理:你可以对HTML元素进行旋转、缩放、倾斜、移动、甚至以前只能用JavaScript实现的强大动画。
* 多栏布局:可以让你不用使用多个div标签就能实现多栏布局。浏览器解释这个属性并生成多栏，让文本实现一个仿报纸的多栏结构。
* 媒体查询:针对不同屏幕分辨率，应用不同的样式。

# 第2章 边框

## 圆角效果 border-radius

`border-radius` 是向样式添加圆角边框，使用方法：

```css
E {
  border-radius: 10px;  // 所有角都使用半径为10px的圆角
}
```

```css
E {
  border-radius: 5px 4px 3px 2px;  // 四个半径值分别是左上角、右上角、右下角和左下角，顺时针
}
```

不要以为border-radius的值只能用px单位，你还可以用百分比或者em，但兼容性目前还不太好。

实心上半圆：把高度(height)设为宽度（width）的一半，并且只设置左上角和右上角的半径与元素的高度一致（大于也是可以的）

```css
div {
  height: 50px;  // 是width的一半
  width: 100px;
  background: #9da;
  border-radius: 50px 50px 0 0;  // 半径至少设置为height的值
}
```

实心圆：把宽度（width）与高度(height)值设置为一致（也就是正方形），并且四个圆角值都设置为它们值的一半

```css
div {
  height: 100px;  // 与width设置一致
  width: 100px;
  background: #9da;
  border-radius: 50px;  // 四个圆角值都设置为宽度或高度的一半
}
```

## 阴影 box-shadow

`box-shadow`是向盒子添加阴影。支持添加一个或者多个,用法如下：

```css
box-shadow: X轴偏移量 Y轴偏移量 [阴影模糊半径] [阴影扩展半径] [阴影颜色] [投影方式];
```

## 参数介绍

值|描述
---|---
X轴偏移量|必需，水平阴影的位置，允许负值
Y轴偏移量|必需，垂直阴影的位置，允许负值
阴影模糊半径|可选，模糊距离
阴影扩展半径|可选，阴影的尺寸
阴影颜色|可选，阴影的颜色，省略默认为黑色
投影方式|可选，设置inset时为内部阴影，省略则为外部阴影

## 为颜色设置外阴影：

```css
.box_shadow {
  box-shadow: 4px 2px 6px #333;
}
```css

## 为元素设置内阴影：

```css
.box_shadow {
  box-shadow: 4px 2px 6px #333 inset;
}
```css

## 添加多个阴影，只需用逗号隔开即可

```css
.box_shadow {
  box-shadow:4px 2px 6px #f00, -4px -2px 6px #000, 0px 0px 12px 5px #33CC00 inset;
}
```

## 阴影模糊半径与阴影扩展半径的区别

阴影模糊半径：此参数可选，其值只能是为正值，如果其值为0时，表示阴影不具有模糊效果，其值越大阴影的边缘就越模糊；

阴影扩展半径：此参数可选，其值可以是正负值，如果值为正，则整个阴影都延展扩大，反之值为负值时，则缩小；

## X轴偏移量和Y轴偏移量值可以设置为负数

* X轴偏移量为负数：

```css
.boxshadow-outset {
  width:100px;
  height:100px;
  box-shadow:-4px 4px 6px #666;
}
```

* Y轴偏移量为负数：

```css
.boxshadow-outset{
  width:100px;
  height:100px;
  box-shadow:4px -4px 6px #666;
}
```

## 为边框应用图片 border-image

```css
#border-image{
   background:#F4FFFA;
   width:210px; height:210px; border:70px solid #ddd;
   border-image:url(borderimg.png) 70 repeat  
}
```

# 第3章 颜色相关

## 颜色之RGBA

> RGB是一种色彩标准，是由红(R)、绿(G)、蓝(B)的变化以及相互叠加来得到各式各样的颜色。RGBA是在RGB的基础上增加了控制alpha透明度的参数。

语法：

```css
color：rgba(R,G,B,A)
```

以上R、G、B三个参数，正整数值的取值范围为：0 - 255。百分数值的取值范围为：0.0% - 100.0%。超出范围的数值将被截至其最接近的取值极限。并非所有浏览器都支持使用百分数值。A为透明度参数，取值在0~1之间，不可为负值。

```css
background-color:rgba(100,120,60,0.5);
```

## 渐变色彩 

> CSS3 Gradient 分为线性渐变(linear)和径向渐变(radial)。由于不同的渲染引擎实现渐变的语法不同，这里我们只针对线性渐变的 W3C 标准语法来分析其用法，其余大家可以查阅相关资料。W3C 语法已经得到了 IE10+、Firefox19.0+、Chrome26.0+ 和Opera12.1+等浏览器的支持。

```css
linear-gradient(to bottom, #fff, #999);
```

参数：

第一个参数:指定渐变方向，可以用“角度”的关键词或“英文”来表示：

角度|用英文表示|作用
---|---|---
0deg|to top|从下向上
90deg|to right|从左向右
180deg|to bottom|从上向下
270deg|to left|从右向左
|to top left|右下角到左上角
|to top right|左下角到右上角

第一个参数省略时，默认为“180deg”，等同于“to bottom”。

第二个和第三个参数，表示颜色的起始点和结束点，可以有多个颜色值。

```css
background-image:linear-gradient(to left, red, orange,yellow,green,blue,indigo,violet);
```

# 第4章 文字与字体

## text-overflow与word-wrap

> `text-overflow`用来设置是否使用一个省略标记（...）标示对象内文本的溢出。

语法：

```css
// clip表示剪切， ellipsis表示显示省略标记
text-overflow: clip | ellipsis
```

但是`text-overflow`只是用来说明文字溢出时用什么方式显示，要实现溢出时产生省略号的效果，还须定义强制文本在一行内显示（`white-space:nowrap`）及溢出内容为隐藏（`overflow:hidden`），只有这样才能实现溢出文本显示省略号的效果，代码如下：

```css
div {
  text-overflow:ellipsis; 
  overflow:hidden; 
  white-space:nowrap; 
}
```

同时，word-wrap也可以用来设置文本行为，当前行超过指定容器的边界时是否断开转行。

```css
//normal表示控制连续文本换行， break-word表示内容将在边界内换行
word-wrap: normal | break-word
```

normal为浏览器默认值，break-word设置在长单词或 URL地址内部进行换行，此属性不常用，用浏览器默认值即可。

## 嵌入字体@font-face

> `@font-face`能够加载服务器端的字体文件，让浏览器端可以显示用户电脑里没有安装的字体。

```css
@font-face {
  font-family: 字体名称;
  src: 字体文件在服务器上的相对或绝对路径;
}
```

这样设置之后，就可以像使用普通字体一样在（font-*）中设置字体样式。  

```css
p {
    font-size :12px;
    font-family : "My Font";
    /*必须项，设置@font-face中font-family同样的值*/
}
```

## 文本阴影text-shadow

> `text-shadow`可以用来设置文本的阴影效果。

```css
text-shadow: X-Offset Y-Offset blur color;
```

* `X-Offset`：表示阴影的水平偏移距离，其值为正值时阴影向右偏移，反之向左偏移；      

* `Y-Offset`：是指阴影的垂直偏移距离，如果其值是正值时，阴影向下偏移，反之向上偏移；

* `Blur`：是指阴影的模糊程度，其值不能是负值，如果值越大，阴影越模糊，反之阴影越清晰，如果不需要阴影模糊可以将Blur值设置为0；

* `Color`：是指阴影的颜色，其可以使用rgba色。

```css
p {
  text-shadow: 0 1px 1px #fff;
}
```

# 第5章 与背景相关的样式

## background-origin

> `background-origin`设置元素背景图片的原始起始位置。

```css
background-origin: border-box | padding-box | content-box;
```

参数分别表示背景图片是从边框，还是内边距（默认值），或者是内容区域开始显示。

需要注意的是，如果背景不是no-repeat，这个属性无效，它会从边框开始显示。

## background-clip

> 用来将背景图片做适当的裁剪以适应实际需要。

```css
background-clip: border-box | padding-box | content-box | no-clip
```

参数分别表示从边框、或内填充，或者内容区域向外裁剪背景。no-clip表示不裁切，和参数border-box显示同样的效果。backgroud-clip默认值为border-box。

## background-size

设置背景图片的大小，以长度值或百分比显示，还可以通过cover和contain来对图片进行伸缩。

```css
background-size: auto | <长度值> | <百分比> | cover | contain
```

1. auto：默认值，不改变背景图片的原始高度和宽度；

2. <长度值>：成对出现如200px 50px，将背景图片宽高依次设置为前面两个值，当设置一个值时，将其作为图片宽度值来等比缩放；

3. <百分比>：0％~100％之间的任何值，将背景图片宽高依次设置为所在元素宽高乘以前面百分比得出的数值，当设置一个值时同上；

4. cover：顾名思义为覆盖，即将背景图片等比缩放以填满整个容器；

5. contain：容纳，即将背景图片等比缩放至某一边紧贴容器边缘为止。

## multiple backgrounds

> 多重背景，也就是CSS2里background的属性外加origin、clip和size组成的新background的多次叠加，缩写时为用逗号隔开的每组值；用分解写法时，如果有多个背景图片，而其他属性只有一个（例如background-repeat只有一个），表明所有背景图片应用该属性值。

```css
background ： [background-color] | [background-image] | [background-position][/background-size] | [background-repeat] | [background-attachment] | [background-clip] | [background-origin],...
```

可以把上面的缩写拆解成以下形式：

```css
background-image:url1,url2,...,urlN;
```

```css
background-repeat : repeat1,repeat2,...,repeatN;
backround-position : position1,position2,...,positionN;
background-size : size1,size2,...,sizeN;
background-attachment : attachment1,attachment2,...,attachmentN;
background-clip : clip1,clip2,...,clipN;
background-origin : origin1,origin2,...,originN;
background-color : color;
```

注意：

1. 用逗号隔开每组 background 的缩写值；
2. 如果有 size 值，需要紧跟 position 并且用 "/" 隔开；
3. 如果有多个背景图片，而其他属性只有一个（例如 background-repeat 只有一个），表明所有背景图片应用该属性值。
4. background-color 只能设置一个。

# 第6章 征服CSS3选择器

## 属性选择器

> 在HTML中，通过各种各样的属性可以给元素增加很多附加的信息。例如，通过id属性可以将不同div元素进行区分。

在CSS2中引入了一些属性选择器，而CSS3在CSS2的基础上对属性选择器进行了扩展，新增了3个属性选择器，使得属性选择器有了通配符的概念，这三个属性选择器与CSS2的属性选择器共同构成了CSS功能强大的属性选择器。如下表所示：

属性选择器|功能描述
--------|--------
E[att^='val']|选择匹配元素E，且E元素定义了属性att，其属性值以val开头的任何字符串
E[att$='val']|选择匹配元素E，且E元素定义了属性att，其属性值以val结尾的任何字符串
E[att*='val']|选择匹配元素E,且E元素定义了属性att，其属性值的任意位置包含了val

示例：

```css
<a href="xxx.pdf">我链接的是PDF文件</a>
<a href="#" class="icon">我类名是icon</a>
<a href="#" title="我的title是more">我的title是more</a>
```

```css
a[class^=icon]{
  background: green;
  color:#fff;
}
a[href$=pdf]{
  background: orange;
  color: #fff;
}
a[title*=more]{
  background: blue;
  color: #fff;
}
```

## 结构性伪类选择器 root

> `:root`选择器，从字面上我们就可以很清楚的理解是根选择器，他的意思就是匹配元素E所在文档的根元素。在HTML文档中，根元素始终是`<html>`

通过“:root”选择器设置背景颜色

```css
:root {
  background:orange;
}
```

## 结构性伪类选择器 not

> `:not`选择器称为否定选择器，和`jQuery`中的`:not`选择器一模一样，可以选择除某个元素之外的所有元素。就拿`form`元素来说，比如说你想给表单中除`submit`按钮之外的`input`元素添加红色边框

```css
form {
  width: 200px;
  margin: 20px auto;
}
div {
  margin-bottom: 20px;
}
input:not([type="submit"]){
  border:1px solid red;
}
```

## 结构性伪类选择器 empty

> `:empty`选择器表示的就是空。用来选择没有任何内容的元素，这里没有内容指的是一点内容都没有，哪怕是一个空格

比如说，你的文档中有三个段落p元素，你想把没有任何内容的P元素隐藏起来。我们就可以使用`:empty`选择器来控制

```css
p{
 background: orange;
 min-height: 30px;
}
p:empty {
  display: none;
}​
```

## 结构性伪类选择器 target

> `:target`选择器称为目标选择器，用来匹配文档(页面)的url的某个标志符的目标元素

点击链接显示隐藏的段落

html代码：

 ```html
 <h2><a href="#brand">Brand</a></h2>
 <div class="menuSection" id="brand">
     content for Brand
 </div>
 ```

css代码：

```css
.menuSection{
  display: none;
}
:target{  /*这里的:target就是指id="brand"的div对象*/
  display:block;
}
```

分析：

1. 具体来说，触发元素的URL中的标志符通常会包含一个#号，后面带有一个标志符名称，上面代码中是：`#brand`

2. `:target`就是用来匹配id为`brand`的元素（`id="brand"`的元素）,上面代码中是那个div元素。

多个`url`(多个`target`)的处理：

同一个页面上有很多的url的时候你可以取不同的名字，只要#号后对的名称与id=""中的名称对应就可以了

html代码：

 ```html
 <h2><a href="#brand">Brand</a></h2>
 <div class="menuSection" id="brand">
   content for Brand
 </div>
 <h2><a href="#jake">Brand</a></h2>
 <div class="menuSection" id="jake">
   content for jake
 </div>
 <h2><a href="#aron">Brand</a></h2>
 <div class="menuSection" id="aron">
    content for aron
 </div>
 ```
 
CSS代码：

```css
#brand:target {
  background: orange;
  color: #fff;
}
#jake:target {
  background: blue;
  color: #fff;
}
#aron:target {
  background: red;
  color: #fff;
}
```

## 结构性伪类选择器 first-child

`:first-child`选择器表示的是选择父元素的第一个子元素的元素E

示例演示:

通过`:first-child`选择器定位列表中的第一个列表项，并将序列号颜色变为红色。

html代码：

 ```html
 <ol>
  <li><a href="##">Link1</a></li>
  <li><a href="##">Link2</a></li>
  <li><a href="##">link3</a></li>
 </ol>
 ```

CSS代码：

```css
ol > li{
  font-size:20px;
  font-weight: bold;
  margin-bottom: 10px;
}

ol a {
  font-size: 16px;
  font-weight: normal;
}

ol > li:first-child{
  color: red;
}
```

## 结构性伪类选择器 last-child

`:last-child`选择器选择的是元素的最后一个子元素

html代码：

 ```html
 <div class="post">
  <p>第一段落</p>
  <p>第二段落</p>
  <p>第三段落</p>
  <p>第四段落</p>
  <p>第五段落</p>
 </div>​
 ```
 
CSS代码：

```css
.post {
  padding: 10px;
  border: 1px solid #ccc;
  width: 200px;
  margin: 20px auto;
}
.post p {
  margin:0 0 15px 0;
}

.post p:last-child {
  margin-bottom:0;
}
```

## 结构性伪类选择器 nth-child(n)

`:nth-child(n)`选择器用来定位某个父元素的一个或多个特定的子元素。其中`n`是其参数，而且可以是整数值(1,2,3,4)，也可以是表达式(2n+1、-n+5)和关键词(`odd`、`even`)，但参数n的起始值始终是1，而不是0。也就是说，参数n的值为0时，选择器将选择不到任何匹配的元素。

html代码：

 ```html
 <ol>
  <li>item1</li>
  <li>item2</li>
  <li>item3</li>
  <li>item4</li>
  <li>item5</li>
  <li>item6</li>
  <li>item7</li>
  <li>item8</li>
  <li>item9</li>
  <li>item10</li>
 </ol>​
 ```
 
CSS代码：

```css
ol > li:nth-child(2n){
  //将偶数行列表背景色设置为橙色
  background: orange;
}
```

## 结构性伪类选择器 nth-last-child(n)

`:nth-last-child(n)`选择器和前面的`:nth-child(n)`选择器非常的相似，只是这里多了一个`last`，所起的作用和`:nth-child(n)`选择器有所区别，从某父元素的最后一个子元素开始计算，来选择特定的元素。

html代码：

 ```
 <ol>
  <li>item1</li>
  <li>item2</li>
  <li>item3</li>
  <li>item4</li>
  <li>item5</li>
  <li>item6</li>
  <li>item7</li>
  <li>item8</li>
  <li>item9</li>
  <li>item10</li>
  <li>item11</li>
  <li>item12</li>
  <li>item13</li>
  <li>item14</li>
  <li>item15</li>
 </ol>​
 ```
 
CSS代码：

```
ol > li:nth-last-child(5){
  background: orange;
}
```

## first-of-type选择器

`:first-of-type`选择器类似于`:first-child`选择器，不同之处就是指定了元素的类型,其主要用来定位一个父元素下的某个类型的第一个子元素。

html代码：

 ```
 <div class="wrapper">
  <div>我是一个块元素，我是.wrapper的第一个子元素</div>
  <p>我是一个段落元素，我是不是.wrapper的第一个子元素，但是他的第一个段落元素</p>
  <p>我是一个段落元素</p>
  <div>我是一个块元素</div>
 </div>
 ```
 
CSS代码：

```
.wrapper {
  width: 500px;
  margin: 20px auto;
  padding: 10px;
  border: 1px solid #ccc;
  color: #fff;
}
.wrapper > div {
  background: green;
}
.wrapper > p {
  background: blue;
}
/*我要改变第一个段落的背景为橙色*/
.wrapper > p:first-of-type {
  background: orange;
}
```

## nth-of-type(n)选择器

`:nth-of-type(n)`选择器和`:nth-child(n)`选择器非常类似，不同的是它只计算父元素中指定的某种类型的子元素。当某个元素中的子元素不单单是同一种类型的子元素时，使用`:nth-of-type(n)`选择器来定位于父元素中某种类型的子元素是非常方便和有用的。在`:nth-of-type(n)`选择器中的`n`和`:nth-child(n)`选择器中的`n`参数也一样，可以是具体的整数，也可以是表达式，还可以是关键词。

html代码：

 ```
 <div class="wrapper">
  <div>我是一个Div元素</div>
  <p>我是一个段落元素</p>
  <div>我是一个Div元素</div>
  <p>我是一个段落</p>
  <div>我是一个Div元素</div>
  <p>我是一个段落</p>
  <div>我是一个Div元素</div>
  <p>我是一个段落</p>
  <div>我是一个Div元素</div>
  <p>我是一个段落</p>
  <div>我是一个Div元素</div>
  <p>我是一个段落</p>
  <div>我是一个Div元素</div>
  <p>我是一个段落</p>
  <div>我是一个Div元素</div>
  <p>我是一个段落</p>
 </div>
 ```
 
CSS代码：

```
.wrapper > p:nth-of-type(2n){
  background: orange;
}
```

## last-of-type选择器

`:last-of-type`选择器和`:first-of-type`选择器功能是一样的，不同的是他选择是父元素下的某个类型的最后一个子元素。

html代码：

 ```
 <div class="wrapper">
  <p>我是第一个段落</p>
  <p>我是第二个段落</p>
  <p>我是第三个段落</p>
  <div>我是第一个Div元素</div>
  <div>我是第二个Div元素</div>
  <div>我是第三个Div元素</div>
 </div>
 ```
 
CSS代码：

```
.wrapper > p:last-of-type{
  background: orange;
}
```

## nth-last-of-type(n)选择器

`:nth-last-of-type(n)`选择器和`:nth-of-type(n)`选择器是一样的，选择父元素中指定的某种子元素类型，但它的起始方向是从最后一个子元素开始

html代码：

 ```
 <div class="wrapper">
  <p>我是第一个段落</p>
  <p>我是第二个段落</p>
  <p>我是第三个段落</p>
  <p>我是第四个段落</p>
  <p>我是第五个段落</p>
  <div>我是一个Div元素</div>
  <p>我是第六个段落</p>
  <p>我是第七个段落</p>
 </div>
 ```
 
CSS代码：

```
.wrapper > p:nth-last-of-type(3){
  background: orange;
}
```

## only-child选择器

`:only-child`选择器选择的是父元素中只有一个子元素，而且只有唯一的一个子元素。也就是说，匹配的元素的父元素中仅有一个子元素，而且是一个唯一的子元素。

html代码：

 ```
 <div class="post">
   <p>我是一个段落</p>
   <p>我是一个段落</p>
 </div>
 <div class="post">
   <p>我是一个段落</p>
 </div>
 ```
 
CSS代码：

```
.post p {
  background: green;
  color: #fff;
  padding: 10px;
}
.post p:only-child {
  background: orange;
}
```

## only-of-type选择器

`:only-of-type`选择器用来选择一个元素是它的父元素的唯一一个相同类型的子元素。这样说或许不太好理解，换一种说法。`:only-of-type`是表示一个元素他有很多个子元素，而其中只有一种类型的子元素是唯一的，使用`:only-of-type`选择器就可以选中这个元素中的唯一一个类型子元素。

html代码：

 ```
 <div class="wrapper">
  <p>我是一个段落</p>
  <p>我是一个段落</p>
  <p>我是一个段落</p>
  <div>我是一个Div元素</div>
 </div>
 <div class="wrapper">
  <div>我是一个Div</div>
  <ul>
    <li>我是一个列表项</li>
  </ul>
  <p>我是一个段落</p>
 </div>
 ```
 
CSS代码：

```
.wrapper > div:only-of-type {
  background: orange;
}
```

## :enabled选择器

在Web的表单中，有些表单元素有可用`:enabled`和不可用`:disabled`状态，比如输入框，密码框，复选框等。在默认情况之下，这些表单元素都处在可用状态。那么我们可以通过伪选择器`:enabled`对这些表单元素设置样式。

html代码：

 ```
 <form action="#">
  <div>
    <label for="name">Text Input:</label>
    <input type="text" name="name" id="name" placeholder="可用输入框"  />
  </div>
   <div>
    <label for="name">Text Input:</label>
    <input type="text" name="name" id="name" placeholder="禁用输入框"  disabled="disabled" />
  </div>
 </form> 
 ```
 
CSS代码：

```
div{
  margin: 20px;
}
input[type="text"]:enabled {
  background: #ccc;
  border: 2px solid red;
}
```

## :disabled选择器

`:disabled`选择器刚好与`:enabled`选择器相反，用来选择不可用表单元素。要正常使用`:disabled`选择器，需要在表单元素的HTML中设置`disabled`属性。

html代码：

 ```
 <form action="#">
  <div>
    <input type="text" name="name" id="name" placeholder="我是可用输入框" />
  </div>
  <div>
    <input type="text" name="name" id="name" placeholder="我是不可用输入框" disabled />
  </div>
 </form>  
 ```
 
CSS代码：

```
form {
  margin: 50px;
}
div {
  margin-bottom: 20px;
}
input {
  background: #fff;
  padding: 10px;
  border: 1px solid orange;
  border-radius: 3px;
}
input[type="text"]:disabled {
  background: rgba(0,0,0,.15);
  border: 1px solid rgba(0,0,0,.15);
  color: rgba(0,0,0,.15);
}
```

## :checked选择器

在表单元素中，单选按钮和复选按钮都具有选中和未选中状态。（大家都知道，要覆写这两个按钮默认样式比较困难）。在CSS3中，我们可以通过状态选择器`:checked`配合其他标签实现自定义样式,而`:checked`表示的是选中状态。

html代码：

 ```
 <form action="#">
  <div class="wrapper">
    <div class="box">
      <input type="checkbox" checked="checked" id="usename" /><span>√</span>
    </div>
    <lable for="usename">我是选中状态</lable>
  </div>
  
  <div class="wrapper">
    <div class="box">
      <input type="checkbox"  id="usepwd" /><span>√</span>
    </div>
    <label for="usepwd">我是未选中状态</label>
  </div>
 </form> 
 ```
 
CSS代码：

```
form {
  border: 1px solid #ccc;
  padding: 20px;
  width: 300px;
  margin: 30px auto;
}

.wrapper {
  margin-bottom: 10px;
}

.box {
  display: inline-block;
  width: 20px;
  height: 20px;
  margin-right: 10px;
  position: relative;
  border: 2px solid orange;
  vertical-align: middle;
}

.box input {
  opacity: 0;
  position: absolute;
  top:0;
  left:0;
}

.box span {
  position: absolute;
  top: -10px;
  right: 3px;
  font-size: 30px;
  font-weight: bold;
  font-family: Arial;
  -webkit-transform: rotate(30deg);
  transform: rotate(30deg);
  color: orange;
}

input[type="checkbox"] + span {
  opacity: 0;
}

input[type="checkbox"]:checked + span {
  opacity: 1;
}
```

## ::selection选择器

`::selection`伪元素是用来匹配突出显示的文本(用鼠标选择文本时的文本)

html代码：

 ```
 <p>“::selection”伪元素是用来匹配突出显示的文本。浏览器默认情况下，选择网站文本是深蓝的背景，白色的字体，</p>
 ```
 
CSS代码：

```
::-moz-selection {
  background: red;
  color: green;
}
::selection {
  background: red;
  color: green;
}
```

## :read-only选择器

`:read-only`伪类选择器用来指定处于只读状态元素的样式。简单点理解就是，元素中设置了`readonly=’readonly’`

html代码：

 ```
 <form action="#">
  <div>
    <label for="name">姓名:</label>
    <input type="text" name="name" id="name" placeholder="大漠" />
  </div>
  <div>
    <label for="address">地址:</label>
    <input type="text" name="address" id="address" placeholder="中国上海" readonly="readonly" />
  </div>
 </form>  
 ```
 
CSS代码：

```
form {
  width: 300px;
  padding: 10px;
  border: 1px solid #ccc;
  margin: 50px auto;
}
form > div {
  margin-bottom: 10px;
}

input[type="text"]{
  border: 1px solid orange;
  padding: 5px;
  background: #fff;
  border-radius: 5px;
}

input[type="text"]:-moz-read-only{
  border-color: #ccc;
}
input[type="text"]:read-only{
  border-color: #ccc;
}
```

## :read-write选择器

`:read-write`选择器刚好与`:read-only`选择器相反，主要用来指定当元素处于非只读状态时的样式。

html代码：

 ```
 <form action="#">
  <div>
    <label for="name">姓名:</label>
    <input type="text" name="name" id="name" placeholder="大漠" />
  </div>
  <div>
    <label for="address">地址:</label>
    <input type="text" name="address" id="address" placeholder="中国上海" readonly="readonly" />
  </div>
 </form>  
 ```
 
CSS代码：

```
form {
  width: 300px;
  padding: 10px;
  border: 1px solid #ccc;
  margin: 50px auto;
}
form > div {
  margin-bottom: 10px;
}

input[type="text"]{
  border: 1px solid orange;
  padding: 5px;
  background: #fff;
  border-radius: 5px;
}

input[type="text"]:-moz-read-only{
  border-color: #ccc;
}
input[type="text"]:read-only{
  border-color: #ccc;
}

input[type="text"]:-moz-read-write{
  border-color: #f36;
}
input[type="text"]:read-write{
  border-color: #f36;
}
```

## ::before和::after

`::before`和`::after`这两个主要用来给元素的前面或后面插入内容，这两个常和`content`配合使用，使用的场景最多的就是清除浮动。

```
.clearfix::before,
.clearfix::after {
    content: ".";
    display: block;
    height: 0;
    visibility: hidden;
}
.clearfix:after {clear: both;}
.clearfix {zoom: 1;}
```

当然，我们还可以使用它们来实现阴影效果

```
.effect::before, .effect::after{
    content:"";
    position:absolute;
    z-index:-1;
    -webkit-box-shadow:0 0 20px rgba(0,0,0,0.8);
    -moz-box-shadow:0 0 20px rgba(0,0,0,0.8);
    box-shadow:0 0 20px rgba(0,0,0,0.8);
    top:50%;
    bottom:0;
    left:10px;
    right:10px;
    -moz-border-radius:100px / 10px;
    border-radius:100px / 10px;
}
```

上面代码作用在class名叫.effect上的div的前（before）后(after)都添加一个空元素，然后为这两个空元素添加阴影特效
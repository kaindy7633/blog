<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Meta标签:](#meta%E6%A0%87%E7%AD%BE)
- [获取滚动条的值：](#%E8%8E%B7%E5%8F%96%E6%BB%9A%E5%8A%A8%E6%9D%A1%E7%9A%84%E5%80%BC)
- [禁止选择文本：](#%E7%A6%81%E6%AD%A2%E9%80%89%E6%8B%A9%E6%96%87%E6%9C%AC)
- [屏蔽阴影：](#%E5%B1%8F%E8%94%BD%E9%98%B4%E5%BD%B1)
- [css之border-box：](#css%E4%B9%8Bborder-box)
- [css3多文本换行：](#css3%E5%A4%9A%E6%96%87%E6%9C%AC%E6%8D%A2%E8%A1%8C)
- [Retina屏幕高清图片：](#retina%E5%B1%8F%E5%B9%95%E9%AB%98%E6%B8%85%E5%9B%BE%E7%89%87)
- [html5重力感应事件：](#html5%E9%87%8D%E5%8A%9B%E6%84%9F%E5%BA%94%E4%BA%8B%E4%BB%B6)
- [移动端touch事件：](#%E7%A7%BB%E5%8A%A8%E7%AB%AFtouch%E4%BA%8B%E4%BB%B6)
- [单击延迟：](#%E5%8D%95%E5%87%BB%E5%BB%B6%E8%BF%9F)
- [IOS里面fixed的文本框焦点居中](#ios%E9%87%8C%E9%9D%A2fixed%E7%9A%84%E6%96%87%E6%9C%AC%E6%A1%86%E7%84%A6%E7%82%B9%E5%B1%85%E4%B8%AD)
- [position:sticky](#positionsticky)
- [移动端点透事件](#%E7%A7%BB%E5%8A%A8%E7%AB%AF%E7%82%B9%E9%80%8F%E4%BA%8B%E4%BB%B6)
- [base64编码图片替换url图片](#base64%E7%BC%96%E7%A0%81%E5%9B%BE%E7%89%87%E6%9B%BF%E6%8D%A2url%E5%9B%BE%E7%89%87)
- [手机拍照和上传图片](#%E6%89%8B%E6%9C%BA%E6%8B%8D%E7%85%A7%E5%92%8C%E4%B8%8A%E4%BC%A0%E5%9B%BE%E7%89%87)
- [动画效果时开启硬件加速](#%E5%8A%A8%E7%94%BB%E6%95%88%E6%9E%9C%E6%97%B6%E5%BC%80%E5%90%AF%E7%A1%AC%E4%BB%B6%E5%8A%A0%E9%80%9F)
- [快速回弹滚动](#%E5%BF%AB%E9%80%9F%E5%9B%9E%E5%BC%B9%E6%BB%9A%E5%8A%A8)
- [ios和android局部滚动时隐藏原生滚动条](#ios%E5%92%8Candroid%E5%B1%80%E9%83%A8%E6%BB%9A%E5%8A%A8%E6%97%B6%E9%9A%90%E8%97%8F%E5%8E%9F%E7%94%9F%E6%BB%9A%E5%8A%A8%E6%9D%A1)
- [设置placeholder时候 focus时候文字没有隐藏](#%E8%AE%BE%E7%BD%AEplaceholder%E6%97%B6%E5%80%99-focus%E6%97%B6%E5%80%99%E6%96%87%E5%AD%97%E6%B2%A1%E6%9C%89%E9%9A%90%E8%97%8F)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

> 做了多年的桌面浏览器应用开发，到了新公司后，接触到了移动web，下面把一些心得记录下来，目前还不完整，待后续完善总结一篇更完整的

## Meta标签:

```html
<meta content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=0;" name="viewport" />
```

这个想必大家都知道，当页面在手机上显示时，增加这个`meta`可以让页面强制让文档的宽度与设备的宽度保持1:1，并且文档最大的宽度比例是1.0，且不允许用户点击屏幕放大浏览。

```html
<meta content="telephone=no" name="format-detection" />
<meta content="email=no" name="format-detection" />
```

这两个属性分别对ios上自动识别电话和android上自动识别邮箱做了限制。

## 获取滚动条的值：

```javascript
window.scrollX
window.scrollY   
```

桌面浏览器中想要获取滚动条的值是通过`document.scrollTop`和`document.scrollLeft`得到的，但在iOS中你会发现这两个属性是未定义的，为什么呢？

因为在iOS中没有滚动条的概念，在Android中通过这两个属性可以正常获取到滚动条的值，那么在iOS中我们该如何获取滚动条的值呢？就是上面两个属性，但是事实证明android也支持这属性，所以索性都用`woindow.scroll`.

## 禁止选择文本：

```css
-webkit-user-select: none
```

禁止用户选择文本，ios和android都支持

## 屏蔽阴影：

```css
-webkit-appearance: none
```

亲测，可以同时屏蔽输入框怪异的内阴影，解决iOS下无法修改按钮样式，测试还发现一个小问题就是，加了上面的属性后，iOS下默认还是带有圆角的，不过可以使用`border-radius`属性修改。

## css之border-box：

```css
element {
  width: 100%;
  padding-left: 10px;
  box-sizing: border-box;
  -webkit-box-sizing: border-box;
  border: 1px solid blue;
}
```
那我想要一个元素100%显示，又必须有一个固定的padding-left／padding-right，还有1px的边框，怎么办？

这样编写代码必然导致出现横向滚动条，肿么办？

要相信问题就是用来解决的。这时候伟大的css3为我们提供了`box-sizing`属性，对于这个属性的具体解释不做赘述（想深入了解的同学可以到w3school查看，要知道自己动手会更容易记忆）

## css3多文本换行：

```css
p {
  overflow: hidden;
  text-overflow: ellipsis;
  display: - webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
}
```

Webkit支持一个名为`-webkit-line-clamp`的属性，参见链接，也就是说这个属性并不是标准的一部分，可能是Webkit内部使用的，或者被弃用的属性。需要注意的是`display`需要设置成`box`，

`-webkit-line-clamp`表示需要显示几行。

## Retina屏幕高清图片：

```css
selector {
  background-image: url(no-image-set. png );
  background: image-set(url(foo-lowres.png ) 1x, url(foo-highres.png ) 2x) center;
}
```

`image-set`的语法，类似于不同的文本，图像也会显示成不同的：

 不支持`image-set`：在不支持`image-set`的浏览器下，他会支持`background-image`图像，也就是说不支持`image-set`的浏览器下，他们解析`background-image`中的背景图像；

 支持`image-set`：如果你的浏览器支持`image-sete`，而且是普通显屏下，此时浏览器会选择`image-set`中的@1x背景图像；

 Retina屏幕下的`image-set`：如果你的浏览器支持`image-set`，而且是在Retina屏幕下，此时浏览器会选择`image-set`中的@2x背景图像。

## html5重力感应事件：

```javascript
if (window.DeviceMotionEven ) {
  window.addEventListener('devicemotion', deviceMotionHandler, false );   
}

var speed = 30; //speed
var x = y = z = lastX = lastY = lastZ = 0;

function deviceMotionHandler(eventData) {   
  var acceleration = event.accelerationIncludingGravity;
  x = acceleration.x;
  y = acceleration.y;
  z = acceleration.z;

  if (Math.abs(x - lastX) > speed || Math.abs(y - lastY) > speed || Math.abs (z - lastZ) > speed) {
    //简单的摇一摇触发代码
    alert(1);
  }

  lastX = x;
  lastY = y;
  lastZ = z;
}
```

关于`deviceMotionEvent`是HTML5新增的事件，用来检测手机重力感应效果具体可参考http://w3c.github.io/deviceorientation/spec-source-orientation.html

## 移动端touch事件：

`touchstart`       // 当手指接触屏幕时触发  
`touchmove`        // 当已经接触屏幕的手指开始移动后触发  
`touchend`         // 当手指离开屏幕时触发  
`touchcancel`      // 当某种touch事件非正常结束时触发  

这4个事件的触发顺序为：

touchstart -> touchmove ->  touchend ->touchcancel

对于某些android系统`touch`的bug:

比如手指在屏幕由上向下拖动页面时，理论上是会触发一个 `touchstart` ，很多次 `touchmove` ，和最终的 `touchend` ，可是在android 4.0上，`touchmove`只被触发一次，触发时间和`touchstart` 差不多，而 `touchend` 直接没有被触发。

这是一个非常严重的bug，在google Issue已有不少人提出 ,这个很蛋疼的bug是在模拟下拉刷新是遇到的尤其当 `touchmove` 的dom节点数量变多时比出现，当时解决办法就是用`settimeout`来稀释`touchmove`。

## 单击延迟：

`click` 事件因为要等待双击确认，会有 300ms 的延迟，体验并不是很好。

开发者大多数会使用封装的 `tap` 事件来代替 `click` 事件，所谓的 `tap` 事件由 `touchstart` 事件 + `touchmove` 判断 + `touchend` 事件封装组成。

## IOS里面fixed的文本框焦点居中

```html
<!DOCTYPE html>
<head>
  <style>
    input {
      position: fixed;
      top: 0; 
      left: 0;
    }
  </style>
</head>
<body>
  <div class="header">
    <form action="">
      <label> Testfield : 
        <input type="text" /> 
      </label>
    </form>
  </div>
</body>
</html>
```

在ios里面，当一个文本框的样式为fixed时候，如果这个文本框获得焦点，它的位置就会乱掉，由于ios里面做了自适应居中，这个fixed的文本框会跑到页面中间。类似：

![](http://static.oschina.net/uploads/img/201601/15101652_eAcL.png)

解决办法有两个：

可以在文本框获得焦点的时候将`fixed`改为`absolute`，失去焦点时在改回`fixed`，但是这样会让屏幕有上下滑动的体验不太好。

```javascript
.fixfixed {
  position: absolute;
}

$(document).on('focus', 'input', function(e) {
  $this.addClass('fixfixed');
}).on('blur', 'input', function(e) {
  $this.removeClass('fixfixed');
});
```

还有一种就是用一个假的`fixed`的文本框放在页面顶部，一个`absolute`的文本框隐藏在页面顶部，当`fixed`的文本框获得焦点时候将其隐藏，然后显示`absolute`的文本框，当失去焦点时，在把`absolute`的文本框隐藏，`fixed`的文本框显示。

```javascript
.fixfixed {
  position: absolute;
}

$(document).on('focus', 'input', function(e) {
  $absolute.show();
  $this.hide();
}).on('blur', 'input', function(e) {
  $fixed.show();
  $this.hide();
});
```

最后一种就是顶部的input不参与滚动，只让其下面滚动。

## position:sticky

`position:sticky`是一个新的css3属性，它的表现类似`position:relative`和`position:fixed`的合体，在目标区域在屏幕中可见时，它的行为就像`position:relative`; 而当页面滚动超出目标区域时，它的表现就像`position:fixed`，它会固定在目标位置。

```css
.sticky {
  position: -webkit-sticky;
  position: sticky;
  top: 15px;
}
```

浏览器兼容性：

由于这是一个全新的属性，以至于到现在都没有一个规范，W3C也刚刚开始讨论它，而现在只有webkit nightly版本和chrome 开发版(Chrome 23.0.1247.0+ Canary)才开始支持它。

另外需要注意的是，如果同时定义了left和right值，那么left生效，right会无效，同样，同时定义了top和bottom，top赢～～

## 移动端点透事件

简单的说，由于在移动端我们经常会使用`tap(touchstart)`事件来替换掉`click`事件，那么就会有一种场景是：

```html
<div i ="mengceng"></div>
<a href="www.qq.com">www.qq.com</a>
```

div是绝对定位的蒙层z-index高于a，而a标签是页面中的一个链接，我们给div绑定tap事件：

```javascript
$('#mengceng').on('tap', function() {
  $('#mengceng').hide();
});
```

我们点击蒙层时 div正常消失，但是当我们在a标签上点击蒙层时，发现a链接被触发，这就是所谓的点透事件。

原因：

`touchstart` 早于 `touchend` 早于 `click`。亦即click的触发是有延迟的，这个时间大概在300ms左右，也就是说我们`tap`触发之后蒙层隐藏，此时click还没有触发，300ms之后由于蒙层隐藏，我们的click触发到了下面的a链接上。

解决办法：

1. 尽量都使用`touch`事件来替换`click`事件。
2. 阻止a链接的`click`的`preventDefault`

## base64编码图片替换url图片

u在移动端，网络请求是很珍贵的资源，尤其在2g或者3g网络下，所以能不发请求的资源都尽量不要发，对于一些小图片icon之类的，可以将图片用base64编码，来减少网络请求。

## 手机拍照和上传图片

`<input type=”file”>`的 `accept` 属性

```html
<!-- 选择照片 -->
<input type=file accept="image/*">
<!-- 选择视频 -->
<input type=file accept="video/*">
```

## 动画效果时开启硬件加速

我们在制作动画效果时经常会想要改版元素的`top`或者`left`来让元素动起来，在pc端还好但是移动端就会有较大的卡顿感，这么我们需要使用css3的 `transform: translate3d` 来替换，

此效果可以让浏览器开启gpu加速，渲染更流畅，但是笔着实验时在ios上体验良好，但在一些低端android机型可能会出现意想不到的效果。

## 快速回弹滚动

在iOS上如果你想让一个元素拥有像 `Native` 的滚动效果，你可以这样做：

```css
.div {
  overflow: auto;
  -webkit-overflow-scrolling: touch;
}
```

经笔着测试，此效果在不同的ios系统表现不一致，

对于局部滚动，ios8以上，不加此效果，滚动的超级慢，ios8一下，不加此效果，滚动还算比较流畅
对于body滚动，ios8以上，不加此效果同样拥有弹性滚动效果。

## ios和android局部滚动时隐藏原生滚动条

android

```css
::-webkit-scrollbar {
  opacity: 0;
}
```

ios

使用一个稍微高一些div包裹住这个有滚动条的div然后设置 `overflow:hidden` 挡住之

```css
.wrap {
  height: 100px;
  overflow: hidden;
}
.box {
  width: 100 %;
  height: -webkit-calc(100 % + 5px);
  overflow-x: auto;
  overflow-y: hidden;
  - webkit-overflow-scrolling: touch;
}
```

```html
<div class="wrap" >
  <div class="box"></div>
</div>
```

## 设置placeholder时候 focus时候文字没有隐藏

```css
input: focus
::-webkit-input-placeholder {
  opacity: 0;
}
```
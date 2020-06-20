<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [检测Internet Explorer版本](#%E6%A3%80%E6%B5%8Binternet-explorer%E7%89%88%E6%9C%AC)
- [平稳滑动到页面顶部](#%E5%B9%B3%E7%A8%B3%E6%BB%91%E5%8A%A8%E5%88%B0%E9%A1%B5%E9%9D%A2%E9%A1%B6%E9%83%A8)
- [固定在顶部](#%E5%9B%BA%E5%AE%9A%E5%9C%A8%E9%A1%B6%E9%83%A8)
- [用其他内容取代html标志](#%E7%94%A8%E5%85%B6%E4%BB%96%E5%86%85%E5%AE%B9%E5%8F%96%E4%BB%A3html%E6%A0%87%E5%BF%97)
- [检测视窗宽度](#%E6%A3%80%E6%B5%8B%E8%A7%86%E7%AA%97%E5%AE%BD%E5%BA%A6)
- [自动定位并修复损坏图片](#%E8%87%AA%E5%8A%A8%E5%AE%9A%E4%BD%8D%E5%B9%B6%E4%BF%AE%E5%A4%8D%E6%8D%9F%E5%9D%8F%E5%9B%BE%E7%89%87)
- [检测复制、粘贴和剪切的操作](#%E6%A3%80%E6%B5%8B%E5%A4%8D%E5%88%B6%E7%B2%98%E8%B4%B4%E5%92%8C%E5%89%AA%E5%88%87%E7%9A%84%E6%93%8D%E4%BD%9C)
- [遇到外部链接自动添加target=”blank”的属性](#%E9%81%87%E5%88%B0%E5%A4%96%E9%83%A8%E9%93%BE%E6%8E%A5%E8%87%AA%E5%8A%A8%E6%B7%BB%E5%8A%A0targetblank%E7%9A%84%E5%B1%9E%E6%80%A7)
- [在图片上停留时逐渐增强或减弱的透明效果](#%E5%9C%A8%E5%9B%BE%E7%89%87%E4%B8%8A%E5%81%9C%E7%95%99%E6%97%B6%E9%80%90%E6%B8%90%E5%A2%9E%E5%BC%BA%E6%88%96%E5%87%8F%E5%BC%B1%E7%9A%84%E9%80%8F%E6%98%8E%E6%95%88%E6%9E%9C)
- [在文本或密码输入时禁止空格键](#%E5%9C%A8%E6%96%87%E6%9C%AC%E6%88%96%E5%AF%86%E7%A0%81%E8%BE%93%E5%85%A5%E6%97%B6%E7%A6%81%E6%AD%A2%E7%A9%BA%E6%A0%BC%E9%94%AE)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

> 在过去的几年中，jQuery一直是使用最为广泛的JavaScript脚本库。今天我们将为各位Web开发者提供10个最实用的jQuery代码片段，有需要的开发者可以保存起来。

## 检测Internet Explorer版本

当涉及到CSS设计时，对开发者和设计者而言Internet Explorer一直是个问题。尽管IE6的黑暗时代已经过去，IE也越来越不流行，它始终是一个能够容易检测的好东西。当然了，下面的代码也能用于检测别的浏览器。

```javascript
$(document).ready(function() {
  if (navigator.userAgent.match(/msie/i) ){
    alert('I am an old fashioned Internet Explorer');
  }
});
```

## 平稳滑动到页面顶部

这是一个最广泛使用的jQuery效果：对一个链接点击下会平稳地将页面移动到顶部。这里没什么新的内容，但是每个开发者必须要会偶尔编写一下类似函数

```javascript
$("a[href='#top']").click(function() {
  $("html, body").animate({ scrollTop: 0 }, "slow");
  return false;
});
```

## 固定在顶部

非常有用的代码片段，它允许一个元素固定在顶部。对导航按钮、工具栏或重要信息框是超级有用的。

```javascript
$(function(){
  var $win = $(window);
  var $nav = $('.mytoolbar');
  var navTop = $('.mytoolbar').length && $('.mytoolbar').offset().top;
  var isFixed=0;

  processScroll()

  $win.on('scroll', processScroll)

  function processScroll() {
    var i, scrollTop = $win.scrollTop();
    if (scrollTop >= navTop && !isFixed) {
        isFixed = 1
        $nav.addClass('subnav-fixed')
    } else if (scrollTop <= navTop && isFixed) {
        isFixed = 0
        $nav.removeClass('subnav-fixed')
    }
  }
```

## 用其他内容取代html标志

jQuery使得用另外一个东西取代html标志很简单。可以利用的余地无穷无尽。

```javascript
$('li').replaceWith(function(){
  return $("<div />").append($(this).contents());
});
```

## 检测视窗宽度

现在移动设备比过时的电脑更普遍，能够方便去检测一个更小的视窗宽度会很有帮助。幸运的是，用jQuery来做超级简单。

```javascript
var responsive_viewport = $(window).width();
/* if is below 481px */
if (responsive_viewport < 481) {
  alert('Viewport is smaller than 481px.');
} /* end smallest screen */
```

## 自动定位并修复损坏图片

如果你的站点比较大而且已经在线运行了好多年，你或多或少会遇到界面上某个地方有损坏的图片。这个有用的函数能够帮助检测损坏图片并用你中意的图片替换它，并会将此问题通知给访客。

```javascript
$('img').error(function(){
  $(this).attr('src', 'img/broken.png');
});
```

## 检测复制、粘贴和剪切的操作

使用jQuery可以很容易去根据你的要求去检测复制、粘贴和剪切的操作。

```javascript
$("#textA").bind('copy', function() {
  $('span').text('copy behaviour detected!')
});

$("#textA").bind('paste', function() {
  $('span').text('paste behaviour detected!')
});

$("#textA").bind('cut', function() {
  $('span').text('cut behaviour detected!')
});
```

## 遇到外部链接自动添加target=”blank”的属性

当链接到外部站点时，你可能使用`target=”blank”`的属性去在新界面中打开站点。问题在于`target=”blank”`属性并不是W3C有效的属性。让我们用jQuery来补救：下面这段代码将会检测是否链接是外链，如果是，会自动添加一个`target=”blank”`属性。

```javascript
var root = location.protocol + '//' + location.host;

$('a').not(':contains(root)').click(function(){
  this.target = "_blank";
});
```

## 在图片上停留时逐渐增强或减弱的透明效果

另一个“经典的”代码，它要放到你的工具箱里，因为你会不时地要实现它。

```javascript
$(document).ready(function(){
  $(".thumbs img").fadeTo("slow", 0.6); // This sets the opacity of the thumbs to fade down to 60% when the page loads
  $(".thumbs img").hover(function(){
    $(this).fadeTo("slow", 1.0); // This should set the opacity to 100% on hover
  },function(){
    $(this).fadeTo("slow", 0.6); // This should set the opacity back to 60% on mouseout
  });
});
```

## 在文本或密码输入时禁止空格键

在很多表格领域都不需要空格键，例如，电子邮件，用户名，密码等等等。这里是一个简单的技巧可以用于在选定输入中禁止空格键。

```javascript
$('input.nospace').keydown(function(e) {
  if (e.keyCode == 32) {
    return false;
  }
});
```

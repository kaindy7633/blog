<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [使用CSS3伪类选择器美化按钮](#%E4%BD%BF%E7%94%A8css3%E4%BC%AA%E7%B1%BB%E9%80%89%E6%8B%A9%E5%99%A8%E7%BE%8E%E5%8C%96%E6%8C%89%E9%92%AE)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# 使用CSS3伪类选择器美化按钮

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>使用CSS3美化按钮</title>
</head>
<body>
  <div class="download-info">
    [View Project On GitHub](#)
  </div>
</body>
</html>
```

CSS部分：

```css
body {
	padding-top: 50px;
}
.download-info {
	text-align: center;
}
/* 默认状态下的按钮效果 */
.btn {
        background-color: #0074cc;
        *background-color: #0055cc;  /* IE6,7 */
        /* CSS3渐变制作背景图片 */
        background-image: -webkit-gradient(linear, 0 0, 0 100%, from(#0088cc), to(#0055cc));
        background-image: -webkit-linear-gradient(top, #0088cc, #0055cc);
        background-image: -ms-linear-gradient(top, #0088cc, #0055cc);
        background-image: -o-linear-gradient(top, #0088cc, #0055cc);
        background-image: -moz-linear-gradient(top, #0088cc, #0055cc);
        background-image: linear-gradient(top, #0088cc, #0055cc);
        background-repeat: repeat-x;
        display: inline-block;
        *display: inline;  /* IE6,7 */
        border: 1px solid #ccc;
        *border: 0;  /* IE6,7 */
        border-color: #ccc;
        /* CSS3色彩模块 */
        border-color: rgba(0, 0, 0, 0.1) rgba(0, 0, 0, 0.1) rgba(0, 0, 0, 0.25);
        border-radius: 6px;
        color: #fff;
        cursor: pointer;
        font-size: 20px;
        font-weight: normal;
        filter: progid:dximagetransform.microsoft.gradient(startColorstr='#0088cc', endColorstr='#0055cc', GradientType=0);
        filter: progid:dximagetransform.microsoft.gradient(enabled=false);
        line-height: normal;
        padding: 14px 24px;
        text-align: center;
        /* CSS3文字阴影特性 */
        text-shadow: 0 -1px 0 rgba(0, 0, 0, 0.25);
        text-decoration: none;
        vertical-align: middle;
        *zoom: 1;
      }
      /* 悬浮状态下按钮效果 */
      .btn:hover {
        background-position: 0 -15px;
        background-color: #0055cc;
        *background-color: #004ab3;
        color: #fff;
        text-decoration: none;
        text-shadow: 0 -1px 0 rgba(0, 0, 0, 0.25);
        /* CSS3动画效果 */
        -webkit-transition: background-position 0.1s linear;
        -moz-transition: background-position 0.1s linear;
        -ms-transition: background-position 0.1s linear;
        -o-transition: background-position 0.1s linear;
        transition: background-position 0.1s linear;
      }
      /* 点击时按钮效果 */
      .btn:active {
        background-color: #0055cc;
        *background-color: #004ab3;
        background-color: #004099 \9;
        background-image: none;
        outline: 0;
        /* CSS3盒子阴影特性 */
        box-shadow: inset 0 2px 4px rgba(0, 0, 0, 0.15), 0 1px 2px rgba(0, 0, 0, 0.15);
        color: rgba(255, 255, 255, 0.75);
      }
      /* 获取焦点按钮效果 */
      .btn:focus {
        outline: thin dotted #333;
        outline: 5px auto -webkit-focus-ring-color;
        outline-offset: -2px;
      }
```
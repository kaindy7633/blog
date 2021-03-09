<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [写在前面](#%E5%86%99%E5%9C%A8%E5%89%8D%E9%9D%A2)
- [概览](#%E6%A6%82%E8%A7%88)
  - [开始](#%E5%BC%80%E5%A7%8B)
    - [入门](#%E5%85%A5%E9%97%A8)
    - [代码要求](#%E4%BB%A3%E7%A0%81%E8%A6%81%E6%B1%82)
    - [初始化模板](#%E5%88%9D%E5%A7%8B%E5%8C%96%E6%A8%A1%E6%9D%BF)
    - [bulma-start](#bulma-start)
  - [定制化](#%E5%AE%9A%E5%88%B6%E5%8C%96)
    - [使用Sass定制化](#%E4%BD%BF%E7%94%A8sass%E5%AE%9A%E5%88%B6%E5%8C%96)
  - [CSS类](#css%E7%B1%BB)
  - [模块化](#%E6%A8%A1%E5%9D%97%E5%8C%96)
  - [响应式](#%E5%93%8D%E5%BA%94%E5%BC%8F)
    - [元素默认垂直排列](#%E5%85%83%E7%B4%A0%E9%BB%98%E8%AE%A4%E5%9E%82%E7%9B%B4%E6%8E%92%E5%88%97)
    - [断点](#%E6%96%AD%E7%82%B9)
    - [断点变量](#%E6%96%AD%E7%82%B9%E5%8F%98%E9%87%8F)
  - [自定义变量](#%E8%87%AA%E5%AE%9A%E4%B9%89%E5%8F%98%E9%87%8F)
    - [初始变量](#%E5%88%9D%E5%A7%8B%E5%8F%98%E9%87%8F)
    - [派生变量](#%E6%B4%BE%E7%94%9F%E5%8F%98%E9%87%8F)
    - [通用变量](#%E9%80%9A%E7%94%A8%E5%8F%98%E9%87%8F)
  - [颜色值](#%E9%A2%9C%E8%89%B2%E5%80%BC)
  - [函数](#%E5%87%BD%E6%95%B0)
    - [`findColorInvert()`函数](#findcolorinvert%E5%87%BD%E6%95%B0)
  - [Mixin(混合)](#mixin%E6%B7%B7%E5%90%88)
- [修饰符](#%E4%BF%AE%E9%A5%B0%E7%AC%A6)
  - [修饰符语法](#%E4%BF%AE%E9%A5%B0%E7%AC%A6%E8%AF%AD%E6%B3%95)
  - [助手](#%E5%8A%A9%E6%89%8B)
  - [响应式助手](#%E5%93%8D%E5%BA%94%E5%BC%8F%E5%8A%A9%E6%89%8B)
    - [显示](#%E6%98%BE%E7%A4%BA)
    - [隐藏](#%E9%9A%90%E8%97%8F)
  - [排版助手](#%E6%8E%92%E7%89%88%E5%8A%A9%E6%89%8B)
    - [尺寸](#%E5%B0%BA%E5%AF%B8)
    - [响应式尺寸](#%E5%93%8D%E5%BA%94%E5%BC%8F%E5%B0%BA%E5%AF%B8)
    - [颜色](#%E9%A2%9C%E8%89%B2)
    - [对齐](#%E5%AF%B9%E9%BD%90)
    - [响应式对齐](#%E5%93%8D%E5%BA%94%E5%BC%8F%E5%AF%B9%E9%BD%90)
    - [文本转换](#%E6%96%87%E6%9C%AC%E8%BD%AC%E6%8D%A2)
    - [字体粗细](#%E5%AD%97%E4%BD%93%E7%B2%97%E7%BB%86)
- [列定义](#%E5%88%97%E5%AE%9A%E4%B9%89)
  - [基本使用](#%E5%9F%BA%E6%9C%AC%E4%BD%BF%E7%94%A8)
  - [尺寸](#%E5%B0%BA%E5%AF%B8-1)
    - [12列系统](#12%E5%88%97%E7%B3%BB%E7%BB%9F)
    - [偏移](#%E5%81%8F%E7%A7%BB)
    - [窄列](#%E7%AA%84%E5%88%97)
  - [响应列](#%E5%93%8D%E5%BA%94%E5%88%97)
    - [移动设备的列](#%E7%A7%BB%E5%8A%A8%E8%AE%BE%E5%A4%87%E7%9A%84%E5%88%97)
    - [每个断点不同的列大小](#%E6%AF%8F%E4%B8%AA%E6%96%AD%E7%82%B9%E4%B8%8D%E5%90%8C%E7%9A%84%E5%88%97%E5%A4%A7%E5%B0%8F)
  - [列嵌套](#%E5%88%97%E5%B5%8C%E5%A5%97)
  - [列间隙](#%E5%88%97%E9%97%B4%E9%9A%99)
    - [默认间距](#%E9%BB%98%E8%AE%A4%E9%97%B4%E8%B7%9D)
    - [零间距](#%E9%9B%B6%E9%97%B4%E8%B7%9D)
    - [可变间距](#%E5%8F%AF%E5%8F%98%E9%97%B4%E8%B7%9D)
  - [其他选项](#%E5%85%B6%E4%BB%96%E9%80%89%E9%A1%B9)
    - [多行](#%E5%A4%9A%E8%A1%8C)
    - [居中显示的列](#%E5%B1%85%E4%B8%AD%E6%98%BE%E7%A4%BA%E7%9A%84%E5%88%97)
- [布局](#%E5%B8%83%E5%B1%80)
  - [容器](#%E5%AE%B9%E5%99%A8)
  - [水平容器](#%E6%B0%B4%E5%B9%B3%E5%AE%B9%E5%99%A8)
    - [居中的水平容器](#%E5%B1%85%E4%B8%AD%E7%9A%84%E6%B0%B4%E5%B9%B3%E5%AE%B9%E5%99%A8)
    - [移动端水平容器](#%E7%A7%BB%E5%8A%A8%E7%AB%AF%E6%B0%B4%E5%B9%B3%E5%AE%B9%E5%99%A8)
  - [媒体对象](#%E5%AA%92%E4%BD%93%E5%AF%B9%E8%B1%A1)
    - [嵌套](#%E5%B5%8C%E5%A5%97)
  - [巨幕](#%E5%B7%A8%E5%B9%95)
    - [颜色](#%E9%A2%9C%E8%89%B2-1)
    - [渐变](#%E6%B8%90%E5%8F%98)
    - [尺寸](#%E5%B0%BA%E5%AF%B8-2)
    - [垂直高度满屏的巨幕](#%E5%9E%82%E7%9B%B4%E9%AB%98%E5%BA%A6%E6%BB%A1%E5%B1%8F%E7%9A%84%E5%B7%A8%E5%B9%95)
  - [段落](#%E6%AE%B5%E8%90%BD)
    - [变量部分](#%E5%8F%98%E9%87%8F%E9%83%A8%E5%88%86)
  - [页脚](#%E9%A1%B5%E8%84%9A)
    - [变量设置](#%E5%8F%98%E9%87%8F%E8%AE%BE%E7%BD%AE)
  - [结构平铺](#%E7%BB%93%E6%9E%84%E5%B9%B3%E9%93%BA)
    - [修饰符](#%E4%BF%AE%E9%A5%B0%E7%AC%A6-1)
    - [嵌套实现](#%E5%B5%8C%E5%A5%97%E5%AE%9E%E7%8E%B0)
    - [元素嵌套的一些要求](#%E5%85%83%E7%B4%A0%E5%B5%8C%E5%A5%97%E7%9A%84%E4%B8%80%E4%BA%9B%E8%A6%81%E6%B1%82)
    - [三列布局](#%E4%B8%89%E5%88%97%E5%B8%83%E5%B1%80)
    - [四列布局](#%E5%9B%9B%E5%88%97%E5%B8%83%E5%B1%80)
- [表单](#%E8%A1%A8%E5%8D%95)
  - [一般的](#%E4%B8%80%E8%88%AC%E7%9A%84)
    - [表单字段](#%E8%A1%A8%E5%8D%95%E5%AD%97%E6%AE%B5)
    - [表单控件](#%E8%A1%A8%E5%8D%95%E6%8E%A7%E4%BB%B6)
    - [带有图标](#%E5%B8%A6%E6%9C%89%E5%9B%BE%E6%A0%87)
    - [表单插件](#%E8%A1%A8%E5%8D%95%E6%8F%92%E4%BB%B6)
    - [表单组](#%E8%A1%A8%E5%8D%95%E7%BB%84)
    - [水平排列的表单](#%E6%B0%B4%E5%B9%B3%E6%8E%92%E5%88%97%E7%9A%84%E8%A1%A8%E5%8D%95)
    - [变量](#%E5%8F%98%E9%87%8F)
  - [输入框](#%E8%BE%93%E5%85%A5%E6%A1%86)
    - [颜色](#%E9%A2%9C%E8%89%B2-2)
    - [尺寸大小](#%E5%B0%BA%E5%AF%B8%E5%A4%A7%E5%B0%8F)
    - [样式](#%E6%A0%B7%E5%BC%8F)
    - [状态](#%E7%8A%B6%E6%80%81)
    - [添加Font Awesome图标](#%E6%B7%BB%E5%8A%A0font-awesome%E5%9B%BE%E6%A0%87)
    - [变量](#%E5%8F%98%E9%87%8F-1)
  - [多行文本框](#%E5%A4%9A%E8%A1%8C%E6%96%87%E6%9C%AC%E6%A1%86)
    - [颜色](#%E9%A2%9C%E8%89%B2-3)
    - [尺寸大小](#%E5%B0%BA%E5%AF%B8%E5%A4%A7%E5%B0%8F-1)
    - [状态](#%E7%8A%B6%E6%80%81-1)
  - [选择框](#%E9%80%89%E6%8B%A9%E6%A1%86)
    - [颜色](#%E9%A2%9C%E8%89%B2-4)
    - [样式](#%E6%A0%B7%E5%BC%8F-1)
    - [尺寸大小](#%E5%B0%BA%E5%AF%B8%E5%A4%A7%E5%B0%8F-2)
    - [状态](#%E7%8A%B6%E6%80%81-2)
    - [添加图标](#%E6%B7%BB%E5%8A%A0%E5%9B%BE%E6%A0%87)
  - [复选框](#%E5%A4%8D%E9%80%89%E6%A1%86)
  - [单选框](#%E5%8D%95%E9%80%89%E6%A1%86)
  - [文件上传](#%E6%96%87%E4%BB%B6%E4%B8%8A%E4%BC%A0)
    - [修饰符](#%E4%BF%AE%E9%A5%B0%E7%AC%A6-2)
    - [颜色](#%E9%A2%9C%E8%89%B2-5)
    - [尺寸大小](#%E5%B0%BA%E5%AF%B8%E5%A4%A7%E5%B0%8F-3)
    - [对齐](#%E5%AF%B9%E9%BD%90-1)
    - [变量](#%E5%8F%98%E9%87%8F-2)
- [元素](#%E5%85%83%E7%B4%A0)
  - [盒子](#%E7%9B%92%E5%AD%90)
    - [变量](#%E5%8F%98%E9%87%8F-3)
  - [按钮](#%E6%8C%89%E9%92%AE)
    - [颜色](#%E9%A2%9C%E8%89%B2-6)
    - [尺寸大小](#%E5%B0%BA%E5%AF%B8%E5%A4%A7%E5%B0%8F-4)
    - [样式](#%E6%A0%B7%E5%BC%8F-2)
    - [状态](#%E7%8A%B6%E6%80%81-3)
    - [按钮组](#%E6%8C%89%E9%92%AE%E7%BB%84)
    - [按钮插件](#%E6%8C%89%E9%92%AE%E6%8F%92%E4%BB%B6)
    - [按钮组插件](#%E6%8C%89%E9%92%AE%E7%BB%84%E6%8F%92%E4%BB%B6)
    - [按钮列表](#%E6%8C%89%E9%92%AE%E5%88%97%E8%A1%A8)
    - [变量](#%E5%8F%98%E9%87%8F-4)
  - [内容](#%E5%86%85%E5%AE%B9)
    - [尺寸](#%E5%B0%BA%E5%AF%B8-3)
    - [变量](#%E5%8F%98%E9%87%8F-5)
  - [删除](#%E5%88%A0%E9%99%A4)
    - [大小](#%E5%A4%A7%E5%B0%8F)
    - [组合使用](#%E7%BB%84%E5%90%88%E4%BD%BF%E7%94%A8)
  - [图标](#%E5%9B%BE%E6%A0%87)
    - [颜色](#%E9%A2%9C%E8%89%B2-7)
    - [大小](#%E5%A4%A7%E5%B0%8F-1)
    - [变量](#%E5%8F%98%E9%87%8F-6)
  - [图片](#%E5%9B%BE%E7%89%87)
    - [方形图片修正](#%E6%96%B9%E5%BD%A2%E5%9B%BE%E7%89%87%E4%BF%AE%E6%AD%A3)
    - [Retina图片](#retina%E5%9B%BE%E7%89%87)
    - [具有比例的响应式图像](#%E5%85%B7%E6%9C%89%E6%AF%94%E4%BE%8B%E7%9A%84%E5%93%8D%E5%BA%94%E5%BC%8F%E5%9B%BE%E5%83%8F)
    - [变量](#%E5%8F%98%E9%87%8F-7)
  - [通知](#%E9%80%9A%E7%9F%A5)
    - [颜色](#%E9%A2%9C%E8%89%B2-8)
    - [变量](#%E5%8F%98%E9%87%8F-8)
  - [进度条](#%E8%BF%9B%E5%BA%A6%E6%9D%A1)
    - [颜色](#%E9%A2%9C%E8%89%B2-9)
    - [尺寸大小](#%E5%B0%BA%E5%AF%B8%E5%A4%A7%E5%B0%8F-5)
    - [变量](#%E5%8F%98%E9%87%8F-9)
  - [表格](#%E8%A1%A8%E6%A0%BC)
    - [修饰符](#%E4%BF%AE%E9%A5%B0%E7%AC%A6-3)
    - [变量](#%E5%8F%98%E9%87%8F-10)
  - [标签](#%E6%A0%87%E7%AD%BE)
    - [颜色](#%E9%A2%9C%E8%89%B2-10)
    - [尺寸大小](#%E5%B0%BA%E5%AF%B8%E5%A4%A7%E5%B0%8F-6)
    - [组合使用](#%E7%BB%84%E5%90%88%E4%BD%BF%E7%94%A8-1)
    - [标签列表](#%E6%A0%87%E7%AD%BE%E5%88%97%E8%A1%A8)
    - [变量](#%E5%8F%98%E9%87%8F-11)
  - [标题](#%E6%A0%87%E9%A2%98)
    - [尺寸大小](#%E5%B0%BA%E5%AF%B8%E5%A4%A7%E5%B0%8F-7)
    - [变量](#%E5%8F%98%E9%87%8F-12)
- [组件](#%E7%BB%84%E4%BB%B6)
  - [面包屑](#%E9%9D%A2%E5%8C%85%E5%B1%91)
    - [对齐](#%E5%AF%B9%E9%BD%90-2)
    - [图标](#%E5%9B%BE%E6%A0%87-1)
    - [替换分隔符](#%E6%9B%BF%E6%8D%A2%E5%88%86%E9%9A%94%E7%AC%A6)
    - [尺寸大小](#%E5%B0%BA%E5%AF%B8%E5%A4%A7%E5%B0%8F-8)
    - [变量](#%E5%8F%98%E9%87%8F-13)
  - [卡片](#%E5%8D%A1%E7%89%87)
    - [变量](#%E5%8F%98%E9%87%8F-14)
  - [下拉](#%E4%B8%8B%E6%8B%89)
    - [下拉内容](#%E4%B8%8B%E6%8B%89%E5%86%85%E5%AE%B9)
    - [点击出现和鼠标划入切换](#%E7%82%B9%E5%87%BB%E5%87%BA%E7%8E%B0%E5%92%8C%E9%BC%A0%E6%A0%87%E5%88%92%E5%85%A5%E5%88%87%E6%8D%A2)
    - [右对齐](#%E5%8F%B3%E5%AF%B9%E9%BD%90)
    - [变量](#%E5%8F%98%E9%87%8F-15)
  - [菜单](#%E8%8F%9C%E5%8D%95)
    - [变量](#%E5%8F%98%E9%87%8F-16)
  - [消息](#%E6%B6%88%E6%81%AF)
    - [颜色](#%E9%A2%9C%E8%89%B2-11)
    - [没有头部的消息区块](#%E6%B2%A1%E6%9C%89%E5%A4%B4%E9%83%A8%E7%9A%84%E6%B6%88%E6%81%AF%E5%8C%BA%E5%9D%97)
    - [尺寸大小](#%E5%B0%BA%E5%AF%B8%E5%A4%A7%E5%B0%8F-9)
    - [变量](#%E5%8F%98%E9%87%8F-17)
  - [模态框](#%E6%A8%A1%E6%80%81%E6%A1%86)
    - [图片模态框](#%E5%9B%BE%E7%89%87%E6%A8%A1%E6%80%81%E6%A1%86)
    - [变量](#%E5%8F%98%E9%87%8F-18)
  - [导航栏](#%E5%AF%BC%E8%88%AA%E6%A0%8F)
    - [导航栏Logo标志位](#%E5%AF%BC%E8%88%AA%E6%A0%8Flogo%E6%A0%87%E5%BF%97%E4%BD%8D)
    - [汉堡菜单](#%E6%B1%89%E5%A0%A1%E8%8F%9C%E5%8D%95)
    - [导航菜单](#%E5%AF%BC%E8%88%AA%E8%8F%9C%E5%8D%95)
      - [使用JavaScript实现切换](#%E4%BD%BF%E7%94%A8javascript%E5%AE%9E%E7%8E%B0%E5%88%87%E6%8D%A2)
    - [导航菜单开始和导航菜单结束](#%E5%AF%BC%E8%88%AA%E8%8F%9C%E5%8D%95%E5%BC%80%E5%A7%8B%E5%92%8C%E5%AF%BC%E8%88%AA%E8%8F%9C%E5%8D%95%E7%BB%93%E6%9D%9F)
    - [导航栏子项目](#%E5%AF%BC%E8%88%AA%E6%A0%8F%E5%AD%90%E9%A1%B9%E7%9B%AE)
    - [透明的导航栏](#%E9%80%8F%E6%98%8E%E7%9A%84%E5%AF%BC%E8%88%AA%E6%A0%8F)
    - [固定的导航栏](#%E5%9B%BA%E5%AE%9A%E7%9A%84%E5%AF%BC%E8%88%AA%E6%A0%8F)
    - [下拉式菜单](#%E4%B8%8B%E6%8B%89%E5%BC%8F%E8%8F%9C%E5%8D%95)
      - [使用CSS或JavaScript显示/隐藏下拉菜单](#%E4%BD%BF%E7%94%A8css%E6%88%96javascript%E6%98%BE%E7%A4%BA%E9%9A%90%E8%97%8F%E4%B8%8B%E6%8B%89%E8%8F%9C%E5%8D%95)
    - [靠右显示的下拉菜单](#%E9%9D%A0%E5%8F%B3%E6%98%BE%E7%A4%BA%E7%9A%84%E4%B8%8B%E6%8B%89%E8%8F%9C%E5%8D%95)
    - [上拉菜单](#%E4%B8%8A%E6%8B%89%E8%8F%9C%E5%8D%95)
      - [下拉菜单的样式](#%E4%B8%8B%E6%8B%89%E8%8F%9C%E5%8D%95%E7%9A%84%E6%A0%B7%E5%BC%8F)
      - [激活的下拉导航菜单项](#%E6%BF%80%E6%B4%BB%E7%9A%84%E4%B8%8B%E6%8B%89%E5%AF%BC%E8%88%AA%E8%8F%9C%E5%8D%95%E9%A1%B9)
      - [下拉分组](#%E4%B8%8B%E6%8B%89%E5%88%86%E7%BB%84)
    - [颜色](#%E9%A2%9C%E8%89%B2-12)
    - [变量](#%E5%8F%98%E9%87%8F-19)
  - [分页](#%E5%88%86%E9%A1%B5)
    - [样式](#%E6%A0%B7%E5%BC%8F-3)
    - [尺寸大小](#%E5%B0%BA%E5%AF%B8%E5%A4%A7%E5%B0%8F-10)
    - [变量](#%E5%8F%98%E9%87%8F-20)
  - [面板](#%E9%9D%A2%E6%9D%BF)
    - [变量](#%E5%8F%98%E9%87%8F-21)
  - [Tabs](#tabs)
    - [对齐](#%E5%AF%B9%E9%BD%90-3)
    - [图标](#%E5%9B%BE%E6%A0%87-2)
    - [尺寸大小](#%E5%B0%BA%E5%AF%B8%E5%A4%A7%E5%B0%8F-11)
    - [样式](#%E6%A0%B7%E5%BC%8F-4)
    - [组合](#%E7%BB%84%E5%90%88)
    - [变量](#%E5%8F%98%E9%87%8F-22)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

> 此篇文档翻译自BULMA官方，因为要做公司的官方网站，在BootStrap和BULMA之间选择了很久，还是选择了BULMA。BULMA是一个轻量的、开源的CSS框架，基于Flexbox，之所以说它很轻量，是因为使用它来定义页面只需要一个CSS文件即可，对于一个官方网站来讲已经足够。翻篇了Google和百度(原谅我还在使用它)，除了阮一峰老师的关于BULMA的一篇文章，其他没有找到合适的中文文档，所以趁着空闲期，把文档翻译出来。此篇中文文档95%的内容属于官方，我会加入一些自己的理解，如有遗漏，敬请指正！ (阮一峰老师的关于BULMA的文章： http://www.ruanyifeng.com/blog/2017/10/bulma.html)

# 写在前面  

<p style="width:100%;height:25px"></p>

> BULMA的官方地址： https://bulma.io/

此篇文档完全翻译自官方，内容不算很多，因为本人E文水平有限，有些地方翻译的有瑕疵，还请指正。谢谢！

因为公司要重构官方网站，当然是三端适配，在BootStrap和BULMA之间选择了很久，最后还是选择了BULMA，为什么？轻量啊...在文档入门中的第一句就说了：`You only need 1 CSS file to use Bulma！`，使用Bulma仅仅需要一个css文件即可，对于开发一个静态的官方站点足够了。

因为找不到合适的中文指导，所以趁着空闲期，自己把它翻译了，也提供给需要的朋友在开发时作为参考。

# 概览

## 开始

### 入门

> 开始使用Bulma，你仅仅需要引入一个css文件即可

开始使用Bulma，你可以通过以下几个途径获取并引入：

1. 使用npm安装Bulma包

```bash
npm i -S bulma 
```

2. 使用CDN直接引入Bulma

https://cdnjs.com/libraries/bulma

国内可以使用bootcdn提供的地址：

https://cdn.bootcss.com/bulma/0.6.2/css/bulma.min.css

3. 直接从仓库下载

https://github.com/jgthms/bulma/tree/master/css

关于Font Awesome icons，Bluma并没有引入这个图标库(因为要控制大小嘛)，像我这个项目就不需要，所以，如果你的项目需要引入这个图标库，你需要再页面中添加：

```js
<script defer src="https://use.fontawesome.com/releases/v5.0.6/js/all.js"></script>
```

### 代码要求

为了使Bulma能正常工作，你需要做下面两件事：

1. 使用HTML5 doctype

```js
<!DOCTYPE html>
```

2. 添加viewport的meta标签

```js
<meta name="viewport" content="width=device-width， initial-scale=1">
```

### 初始化模板

官方为我们提供了一个初始化的模板，我们可以直接复制到自己的项目里使用

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width， initial-scale=1">
    <title>Hello Bulma!</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/bulma/0.6.2/css/bulma.min.css">
    <script defer src="https://use.fontawesome.com/releases/v5.0.6/js/all.js"></script>
  </head>
  <body>
  <section class="section">
    <div class="container">
      <h1 class="title">
        Hello World
      </h1>
      <p class="subtitle">
        My first website with <strong>Bulma</strong>!
      </p>
    </div>
  </section>
  </body>
</html>
```

### bulma-start

这是个什么鬼？我也不太清楚，按我的理解就是一个工具，官方的解释是一个包含了Bulma依赖的包文件，其实当我们引入其css后就能正常工作，所以这块就不过多阐述了，有兴趣的同学可以去官方看看：https://bulma.io/bulma-start/

## 定制化

### 使用Sass定制化

Bulma允许用户创建一个变量文件来定制化自己的主题。

我们可以通过npm安装Bulma，然后创建变量文件，定义自己的主题，然后再引入官方的

```bash
npm install bulma
```

或者你也可以从bulma的仓库克隆：https://github.com/jgthms/bulma

随后，你需要在根目录下创建一个自己的样式变量文件，比如：`mystyles.sass`，并在这个文件中添加自定义的颜色变量，设置新的字体等，以覆盖Bulma的默认样式

```scss
// 1. 导入初始化的变量定义文件
@import "../sass/utilities/initial-variables";
@import "../sass/utilities/functions";

// 2. 设置你需要自定义的变量
$blue: #72d0eb;
$pink: #ffb3b3;
$pink-invert: #fff;
$family-serif: "Merriweather", "Georgia", serif;

// 3. 设置你的样式中需要被派生出来的变量（也就是需要继承上面的变量值的变量）
$primary: $pink;
$primary-invert: $pink-invert;
$danger: $orange;
$family-primary: $family-serif;

// 4. 设置你自己的颜色变量
$linkedin: #0077b5;
$linkedin-invert: findColorInvert($linkedin);
$twitter: #55acee;
$twitter-invert: findColorInvert($twitter);
$github: #333;
$github-invert: findColorInvert($github);

// 5. 将新的颜色变量添加到颜色映射中
@import "../sass/utilities/derived-variables";
$addColors: (
  "twitter":($twitter, $twitter-invert),
  "linkedin": ($linkedin, $linkedin-invert),
  "github": ($github, $github-invert)
);
$colors: map-merge($colors, $addColors);

// 6. 导入原始设置
@import "./bulma";
```

最后，你需要修改下`package.json`中的配置，找到下面的这行script:

```
"build-sass": "node-sass --output-style expanded --source-map true bulma.sass css/bulma.css",
```

将`bulma.sass`修改为你创建的`mystyles.sass`,然后执行 `npm run build` 命令生成新的样式文件即可。

## CSS类

Bulma只是一个CSS类的集合。 对HTMl并没有任何要求，你可以编写任意你想要的HTML代码。

Bulma是一个CSS框架，这意味着最终编译的结果只是一个`.css`文件： https://github.com/jgthms/bulma/blob/master/css/bulma.css

由于Bulma仅包含CSS类，因此您编写的HTML代码不会影响页面的样式。这就是为什么`.input`只是一个CSS类，所以你可以选择为哪一个`<input type="text">`标签添加这个CSS类，而不会影响其他的`<input>`标签

Bulma会直接对通用标签进行两次样式设置：

- `generic.sass`会定义页面的基本样式
- `.content`类用于任何文本内容，如所见即所得

## 模块化

Bulma支持按需 (模块) 导入

Bulma由39个`.sass`文件组成，你可以单独导入。例如，假设您只需要Bulma的列定义，列定义文件位于`bulma/sass/grid`文件夹中。

在你导入你所需要的文件之前，你需要导入实用程序的依赖关系：

```scss
@import "bulma/sass/utilities/_all"  // 导入依赖关系
@import "bulma/sass/grid/columns"    // 导入列定义
```

现在，您可以直接使用类`.columns`（用于容器）和`.column`：

```html
<div class="columns">
  <div class="column">1</div>
  <div class="column">2</div>
  <div class="column">3</div>
  <div class="column">4</div>
  <div class="column">5</div>
</div>
```

如果仅仅想导入按钮的样式呢：

```scss
@import "bulma/sass/utilities/_all"
@import "bulma/sass/elements/button.sass"
```

现在你可以使用`.button`类及其所有修饰符：

- `.is-active`
- `.is-primary`, `.is-info`, `.is-success`...
- `.is-small`, `.is-medium`, `.is-large`
- `.is-outlined`, `.is-inverted`, .`is-link`
- `.is-loading`, `[disabled]`

```html
<a class="button">Button</a>
<a class="button is-primary">Primary button</a>
<a class="button is-large">Large button</a>
<a class="button is-loading">Loading button</a>
```

## 响应式

Bulma是一个移动优先的UI框架

### 元素默认垂直排列

Bulma中的每个元素都是移动优先的，并优化了垂直阅读，所以默认情况下在手机上：

- 每列都是垂直堆叠
- `level` 组件将显示其子项目，并垂直堆叠
- 导航菜单会被隐藏

例如，您可以通过附加 `is-mobile` 修饰符来强制执行水平布局或列导航。

### 断点

Bulma提供了5个断点设置：

- mobile(手机): up to 768px
- tablet(平板电脑): from 769px
- desktop(桌面): from 1024px
- widescreen(宽屏): from 1216px
- fullhd: from 1408px

Bulma使用了9个响应混合：

- `=mobile`             until 768px
- `=tablet`             from 769px
- `=tablet-only`        from 769px and until 1023px
- `=touch`              until 1023px
- `=desktop`            from 1024px
- `=desktop-only`       from 1024px and until 1215px
- `=widescreen`         from 1216px
- `=widescreen-only`    from 1216px and until 1407px
- `=fullhd`             from 1408px

### 断点变量

你可以使用断点变量来自定义响应断点。 在导入Bulma之前，只需设置一个或多个这些变量

|Name|Default value|
|---|---|
|$gap|32px|
|$tablet|769px|
|$desktop|960px + (2 * $gap)|
|$widescreen|1152px + (2 * $gap)|
|$fullhd|1344px + (2 * $gap)|

## 自定义变量

你可以很轻松的定制符合你的设计的Bulma

Bulma有两个可变文件，分为4个部分：

1. 初始变量：通过文字值定义变量的位置，如：

    - 颜色： `$blue: hsl(217, 71%, 53%)`
    - 字体大小： `$size-1: 3rem`
    - 尺寸： `$gap: 32px`
    - 其他值： `$easing: ease-out` 或 `$radius-large: 5px`

2. 派生变量，它们是根据前一个文件中设置的值计算的，例如你可以如下定义：

    - 从初始变量派生的Primary colors

        - `$primary: $turquoise`
        - `$link: $blue`
        - `$info: $cyan`
        - `$success: $green`
        - `$warning: $yellow`
        - `$danger: $red`
        - `$dark: $grey-darker`
        - `$text: $grey-dark`

    - `$background: $white-ter`: 一般背景颜色
    - `$link: $blue`: 链接使用的原色
    - `$family-primary: $family-sans-serif`: 主要字体系列是无衬线字体系列
    - 列表和地图是已定义变量的集合：

        - `$colors: ("white": ($white, $black), "black": ($black, $white), "light": ($light, $light-invert), "dark": ($dark, $dark-invert), "primary": ($primary, $primary-invert), "link": ($link, $link-invert), "info": ($info, $info-invert), "success": ($success, $success-invert), "warning": ($warning, $warning-invert), "danger": ($danger, $danger-invert))`
        - `$shades: ("black-bis": $black-bis, "black-ter": $black-ter, "grey-darker": $grey-darker, "grey-dark": $grey-dark, "grey": $grey, "grey-light": $grey-light, "grey-lighter": $grey-lighter, "white-ter": $white-ter, "white-bis": $white-bis)`
        - `$sizes: $size-1 $size-2 $size-3 $size-4 $size-5 $size-6 $size-7`

如果想要覆盖上面这些变量，只需在导入Bulma之前设置它们。

### 初始变量

下面的这些是具有字面量的变量：

|||
|---|---|
|$black|hsl(0, 0%, 4%)|
|$black-bis|hsl(0, 0%, 7%)|
|$black-ter|hsl(0, 0%, 14%)|
|$grey-darker|hsl(0, 0%, 21%)|
|$grey-dark|hsl(0, 0%, 29%)|
|$grey|hsl(0, 0%, 48%)|
|$grey-light|hsl(0, 0%, 71%)|
|$grey-lighter|hsl(0, 0%, 86%)|
|$white-ter|hsl(0, 0%, 96%)|
|$white-bis|hsl(0, 0%, 98%)|
|$white|hsl(0, 0%, 100%)|
|$orange|hsl(14, 100%, 53%)|
|$yellow|hsl(48, 100%, 67%)|
|$green|hsl(141, 71%, 48%)|
|$turquoise|hsl(171, 100%, 41%)|
|$cyan|hsl(204, 86%, 53%)|
|$blue|hsl(217, 71%, 53%)|
|$purple|hsl(271, 100%, 71%)|
|$red|hsl(348, 100%, 61%)|
|$family-sans-serif|BlinkMacSystemFont, -apple-system, "Segoe UI", "Roboto", "Oxygen", "Ubuntu", "Cantarell", "Fira Sans", "Droid Sans", "Helvetica Neue", "Helvetica", "Arial", sans-serif|
|$family-monospace|monospace|
|$render-mode|optimizeLegibility|
|$size-1|3rem|
|$size-2|2.5rem|
|$size-3|2rem|
|$size-4|1.5rem|
|$size-5|1.25rem|
|$size-6|1rem|
|$size-7|0.75rem|
|$weight-light|300|
|$weight-normal|400|
|$weight-medium|500|
|$weight-semibold|600|
|$weight-bold|700|
|$gap|32px|
|$tablet|769px|
|$desktop|960px + (2 * $gap)|
|$widescreen|1152px + (2 * $gap)|
|$fullhd|1344px + (2 * $gap)|
|$easing|ease-out|
|$radius-small|2px|
|$radius|3px|
|$radius-large|5px|
|$radius-rounded|290486px|
|$speed|86ms|
|$variable-columns|true|

### 派生变量

下面的这些变量引用了另一个变量的值(派生)

|Name|Default value|
|---|---|
|$primary|$turquoise|
|$info|$cyan|
|$success|$green|
|$warning|$yellow|
|$danger|$red|
|$light|$white-ter|
|$dark|$grey-darker|
|$orange-invert|findColorInvert($orange)|
|$yellow-invert|findColorInvert($yellow)|
|$green-invert|findColorInvert($green)|
|$turquoise-invert|findColorInvert($turquoise)|
|$cyan-invert|findColorInvert($cyan)|
|$blue-invert|findColorInvert($blue)|
|$purple-invert|findColorInvert($purple)|
|$red-invert|findColorInvert($red)|
|$primary-invert|$turquoise-invert|
|$info-invert|$cyan-invert|
|$success-invert|$green-invert|
|$warning-invert|$yellow-invert|
|$danger-invert|$red-invert|
|$light-invert|$dark|
|$dark-invert|$light|
|$background|$white-ter|
|$border|$grey-lighter|
|$border-hover|$grey-light|
|$text|$grey-dark|
|$text-invert|findColorInvert($text)|
|$text-light|$grey|
|$text-strong|$grey-darker|
|$code|$red|
|$code-background|$background|
|$pre|$text|
|$pre-background|$background|
|$link|$blue|
|$link-invert|$blue-invert|
|$link-visited|$purple|
|$link-hover|$grey-darker|
|$link-hover-border|$grey-light|
|$link-focus|$grey-darker|
|$link-focus-border|$blue|
|$link-active|$grey-darker|
|$link-active-border|$grey-dark|
|$family-primary|$family-sans-serif|
|$family-code|$family-monospace|
|$size-small|$size-7|
|$size-normal|$size-6|
|$size-medium|$size-5|
|$size-large|$size-4|
|$colors|("white": ($white, $black), "black": ($black, $white), "light": ($light, $light-invert), "dark": ($dark, $dark-invert), "primary": ($primary, $primary-invert), "link": ($link, $link-invert), "info": ($info, $info-invert), "success": ($success, $success-invert), "warning": ($warning, $warning-invert), "danger": ($danger, $danger-invert))|
|$shades|("black-bis": $black-bis, "black-ter": $black-ter, "grey-darker": $grey-darker, "grey-dark": $grey-dark, "grey": $grey, "grey-light": $grey-light, "grey-lighter": $grey-lighter, "white-ter": $white-ter, "white-bis": $white-bis)|
|$sizes|$size-1 $size-2 $size-3 $size-4 $size-5 $size-6 $size-7|

### 通用变量

您可以使用以下通用变量进行常规自定义。 在导入Bulma之前，你可以设置一个或多个这些变量

|Name|Default value|
|---|---|
|$body-background-color|#fff|
|$body-size|16px|
|$body-rendering|optimizeLegibility|
|$body-family|$family-primary|
|$body-color|$text|
|$body-weight|$weight-normal|
|$body-line-height|1.5|
|$code-family|$family-code|
|$code-padding|0.25em 0.5em 0.25em|
|$code-weight|normal|
|$code-size|0.875em|
|$hr-background-color|$border|
|$hr-height|1px|
|$hr-margin|1.5rem 0|
|$strong-color|$text-strong|
|$strong-weight|$weight-bold|

## 颜色值

设计大多数Bulma元素和组件的颜色

大多数元素和组件都具有颜色变化，这归功于修饰符的语法`.is-$color`，如`is-primary`或`is-dark`。

Bulma通过`$color` Sass map循环抓取所有颜色和它们的反转，看下表：

|颜色|变量|值|计算值|反转值|计算反转值|
|---|---|---|---|---|---|
|White|`$white`|`$white`|`hsl(0, 0%, 100%)`|`$black`|`hsl(0, 0%, 4%)`|
|Black|`$black`|`$black`|`hsl(0, 0%, 4%)`|`$white`|`hsl(0, 0%, 100%)`|
|Light|`$light`|`$white-ter`|`hsl(0, 0%, 96%)`|`$grey-darker`|`hsl(0, 0%, 21%)`|
|Dark|`$dark`|`$grey-darker`|`hsl(0, 0%, 21%)`|`$white-ter`|`hsl(0, 0%, 96%)`|
|Primary|`$primary`|`$turquoise`|`hsl(171, 100%, 41%)`|`#fff`|`#fff`|
|Link|`$link`|`$blue`|`hsl(217, 71%, 53%)`|`#fff`|`#fff`|
|Info|`$info`|`$cyan`|hsl(204, 86%, 53%)|`#fff`|`#fff`|
|Success|`$success`|`$green`|`hsl(141, 71%, 48%)`|`#fff`|`#fff`|
|Warning|`$warning`|`$yellow`|`hsl(48, 100%, 67%)`|`rgba(0, 0, 0, 0.7)`|`rgba(0, 0, 0, 0.7)`|
|Danger|`$danger`|`$red`|`hsl(348, 100%, 61%)`|`#fff`|`#fff`|

## 函数

你可以使用函数来计算颜色值和其他值

Bulma使用3个自定义函数来帮助我们动态的定义值和颜色：

- `powerNumber($number, $exp)`: 计算一个将要暴露给另外一个变量的值，它返回一个数值
- `colorLuminance($color)`: 定义颜色是深色还是浅色。 返回0到1之间的小数，其中<= 0.5是深色的，> 0.5是浅色的。
- `findColorInvert($color)`: 根据颜色的亮度返回70％透明黑色或100％不透明白色。

### `findColorInvert()`函数

`findColorInvert($color)`函数将一种颜色作为输入，并输出透明黑色`rgba（＃000,0.7）`或白色`#fff`：

- 如果 `colorLuminance($color) > 0.55`, 那么它将输出 `rgba(#000, 0.7)`
- 否则，它将输出`#fff`

使用此函数的目的是当输入颜色用作背景时，保证其文本的可读性。

|颜色|颜色亮度|findColorInvert()|输出示例|
|---|---|---|---|
|<span style="border-radius:2px;-webkit-box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1); box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1);display:inline-block;float:left;height:24px;margin-right:8px;width:24px;background:#00d1b2;"></span>`#00d1b2`|`0.52831`|<span style="border-radius:2px;-webkit-box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1); box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1);display:inline-block;float:left;height:24px;margin-right:8px;width:24px;background:#fff;"></span>`#fff`|<a class="button" style="background:#00d1b2;border-color:#00d1b2;color:#fff;height:2.25em;line-height:1.5;padding-bottom:calc(0.375em - 1px);padding-left:calc(0.625em - 1px);padding-right:calc(0.625em - 1px);padding-top:calc(0.375em - 1px);border-radius:3px;">Button</a>|
|<span style="border-radius:2px;-webkit-box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1); box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1);display:inline-block;float:left;height:24px;margin-right:8px;width:24px;background:#3273dc;"></span>`#3273dc`|`0.23119`|<span style="border-radius:2px;-webkit-box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1); box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1);display:inline-block;float:left;height:24px;margin-right:8px;width:24px;background:#fff;"></span>`#fff`|<a class="button" style="background:#3273dc;border-color:#3273dc;color:#fff;height:2.25em;line-height:1.5;padding-bottom:calc(0.375em - 1px);padding-left:calc(0.625em - 1px);padding-right:calc(0.625em - 1px);padding-top:calc(0.375em - 1px);border-radius:3px;">Button</a>|
|<span style="border-radius:2px;-webkit-box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1); box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1);display:inline-block;float:left;height:24px;margin-right:8px;width:24px;background:#23d160;"></span>`#23d160`|`0.51067`|<span style="border-radius:2px;-webkit-box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1); box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1);display:inline-block;float:left;height:24px;margin-right:8px;width:24px;background:#fff;"></span>`#fff`|<a class="button" style="background:#23d160;border-color:#23d160;color:#fff;height:2.25em;line-height:1.5;padding-bottom:calc(0.375em - 1px);padding-left:calc(0.625em - 1px);padding-right:calc(0.625em - 1px);padding-top:calc(0.375em - 1px);border-radius:3px;">Button</a>|
|<span style="border-radius:2px;-webkit-box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1); box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1);display:inline-block;float:left;height:24px;margin-right:8px;width:24px;background:#ffdd57;"></span>`#ffdd57`|`0.76863`|<span style="border-radius:2px;-webkit-box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1);box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1);display:inline-block;float:left;height:24px;margin-right:8px;width:24px;background:rgba(0, 0, 0, 0.7);"></span>`rgba(0, 0, 0, 0.7)`|<a class="button" style="background:#ffdd57;border-color:#ffdd57;color:rgba(0, 0, 0, 0.7);height:2.25em;line-height:1.5;padding-bottom:calc(0.375em - 1px);padding-left:calc(0.625em - 1px);padding-right:calc(0.625em - 1px);padding-top:calc(0.375em - 1px);border-radius:3px;">Button</a>|
|<span style="border-radius:2px;-webkit-box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1); box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1);display:inline-block;float:left;height:24px;margin-right:8px;width:24px;background:#ff3860;"></span>`#ff3860`|`0.27313`|<span style="border-radius:2px;-webkit-box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1); box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1);display:inline-block;float:left;height:24px;margin-right:8px;width:24px;background:#fff;"></span>`#fff`|<a class="button" style="background:#ff3860;border-color:#ff3860;color:#fff;height:2.25em;line-height:1.5;padding-bottom:calc(0.375em - 1px);padding-left:calc(0.625em - 1px);padding-right:calc(0.625em - 1px);padding-top:calc(0.375em - 1px);border-radius:3px;">Button</a>|
|<span style="border-radius:2px;-webkit-box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1); box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1);display:inline-block;float:left;height:24px;margin-right:8px;width:24px;background:#ffb3b3;"></span>`#ffb3b3`|`0.61796`|<span style="border-radius:2px;-webkit-box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1);box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1);display:inline-block;float:left;height:24px;margin-right:8px;width:24px;background:rgba(0, 0, 0, 0.7);"></span>`rgba(0, 0, 0, 0.7)`|<a class="button" style="background:#ffb3b3;border-color:#ffb3b3;color:rgba(0, 0, 0, 0.7);height:2.25em;line-height:1.5;padding-bottom:calc(0.375em - 1px);padding-left:calc(0.625em - 1px);padding-right:calc(0.625em - 1px);padding-top:calc(0.375em - 1px);border-radius:3px;">Button</a>|
|<span style="border-radius:2px;-webkit-box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1); box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1);display:inline-block;float:left;height:24px;margin-right:8px;width:24px;background:#ffbc6b;"></span>`#ffbc6b`|`0.63053`|<span style="border-radius:2px;-webkit-box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1);box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1);display:inline-block;float:left;height:24px;margin-right:8px;width:24px;background:rgba(0, 0, 0, 0.7);"></span>`rgba(0, 0, 0, 0.7)`|<a class="button" style="background:#ffbc6b;border-color:#ffbc6b;color:rgba(0, 0, 0, 0.7);height:2.25em;line-height:1.5;padding-bottom:calc(0.375em - 1px);padding-left:calc(0.625em - 1px);padding-right:calc(0.625em - 1px);padding-top:calc(0.375em - 1px);border-radius:3px;">Button</a>|
|<span style="border-radius:2px;-webkit-box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1); box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1);display:inline-block;float:left;height:24px;margin-right:8px;width:24px;background:hsl(294, 71%, 79%);"></span>`hsl(294, 71%, 79%)`|`0.5529`|<span style="border-radius:2px;-webkit-box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1);box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1);display:inline-block;float:left;height:24px;margin-right:8px;width:24px;background:rgba(0, 0, 0, 0.7);"></span>`rgba(0, 0, 0, 0.7)`|<a class="button" style="background:hsl(294, 71%, 79%);border-color:hsl(294, 71%, 79%);color:rgba(0, 0, 0, 0.7);height:2.25em;line-height:1.5;padding-bottom:calc(0.375em - 1px);padding-left:calc(0.625em - 1px);padding-right:calc(0.625em - 1px);padding-top:calc(0.375em - 1px);border-radius:3px;">Button</a>|

对于亮度接近0.55阈值的颜色，重写`findColorInvert()`函数并手动设置反转颜色会很有用。

例如，这种紫色 <span style="display:inline-block;background:hsl(294, 71%, 79%);float:none;height:16px;width:16px;margin-right:0;vertical-align:middle;"></span> 阴影的颜色亮度为`0.5529`。 最好设置白色而不是透明黑色的颜色反转：

|||||
|---|---|---|---|
|使用 `findColorInvert()`|`$purple-invert: findColorInvert($purple)`|<span style="border-radius:2px;-webkit-box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1);box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1);display:inline-block;float:left;height:24px;margin-right:8px;width:24px;background:rgba(0, 0, 0, 0.7);"></span>`rgba(0, 0, 0, 0.7)`|<a class="button" style="background:hsl(294, 71%, 79%);border-color:hsl(294, 71%, 79%);color:rgba(0, 0, 0, 0.7);height:2.25em;line-height:1.5;padding-bottom:calc(0.375em - 1px);padding-left:calc(0.625em - 1px);padding-right:calc(0.625em - 1px);padding-top:calc(0.375em - 1px);border-radius:3px;">Button</a>|
|手动设置|`$purple-invert: #fff`|<span style="border-radius:2px;-webkit-box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1);box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1);display:inline-block;float:left;height:24px;margin-right:8px;width:24px;background:#fff;"></span>`#fff`|<a class="button" style="background:hsl(294, 71%, 79%);border-color:hsl(294, 71%, 79%);color:#fff;height:2.25em;line-height:1.5;padding-bottom:calc(0.375em - 1px);padding-left:calc(0.625em - 1px);padding-right:calc(0.625em - 1px);padding-top:calc(0.375em - 1px);border-radius:3px;">Button</a>|

## Mixin(混合)

Bulma支持用于自定义元素和响应助手的实用程序Mixin(混合)

|||
|---|---|
|`=arrow($color)`|创建一个仅限CSS的向下箭头。 用于下拉选择。|
|`=block`|定义元素距离底部1.5rem，如果该元素是其父元素的最后一个子元素，则不应用此效果，可以用于所有块元素单元|
|`=clearfix`|在元素的末尾添加一个`clearfix`。 用于`is-clearfix`助手。|
|`=center($size)`|将元素定位在其父项的确切中心。 用于加载按钮中的微调器。|
|`=delete`|创建一个仅限CSS的交叉图标。 用于模态，消息，标签中的删除元素...|
|`=hamburger($dimensions)`|用3个小节创建一个仅限CSS的汉堡包菜单。 用于“导航切换”。|
|`=loader`|创建一个仅限CSS的加载微调器。 用于“.loader”元素，以及输入和按钮旋钮。|
|`=overflow-touch`|设置容器的样式，以便在iOS设备上滚动时保持容量。|
|`=overlay($offset: 0)`|使元素覆盖其父容器，如透明模态背景。|
|`=placeholder`|设置输入占位符的样式。|
|`=unselectable`|打开元素不可选。 用于按钮以防止点击时选择。|

上述这些Mixin已部署在整个Bulma中，可以随时使用，不过你也可以使用它们来扩展自定义的样式

# 修饰符

## 修饰符语法

在Bulma中，大多数元素都有替代样式，如果想要应用它们，你只需要附加一个修饰符类即可。这些修饰符类一般都是以 `is-` 或 `has-` 开头的。

让我们从使用“按钮”CSS类的简单按钮开始：

```html
<a class="button">
  Button
</a>
```

通过添加 `is-primary` CSS类，您可以修改背景颜色：

```html
<a class="button is-primary">
  Button
</a>
```

你还可以使用以下6种主要颜色之一：

- `is-primary`
- `is-link`
- `is-info`
- `is-success`
- `is-warning`
- `is-danger`

```html
<a class="button is-primary">
  Button
</a>
<a class="button is-link">
  Button
</a>
<a class="button is-info">
  Button
</a>
<a class="button is-success">
  Button
</a>
<a class="button is-warning">
  Button
</a>
<a class="button is-danger">
  Button
</a>
```

你也可以改变尺寸：

- `is-small`
- `is-medium`
- `is-large`

```html
<a class="button is-small">
  Button
</a>
<a class="button">
  Button
</a>
<a class="button is-medium">
  Button
</a>
<a class="button is-large">
  Button
</a>
```

或者你还可以改变样式或状态：

- `is-outlined`
- `is-loading`
- `[disabled]`

```html
<a class="button is-primary is-outlined">
  Button
</a>
<a class="button is-primary is-loading">
  Button
</a>
<a class="button is-primary" disabled>
  Button
</a>
```

## 助手

您可以将辅助类应用于几乎任何元素，以改变其风格

<table style="background-color:white;color:#363636;border-collapse:collapse;border-spacing:0;">
  <tbody>
    <tr>
      <th rowspan="3" style="border-width:1px;color:#363636;text-align:left;border:1px solid #dbdbdb;padding:0.5em 0.75em;vertical-align:top;">浮动(Float)</th>
      <td style="border-width:1px;border:1px solid #dbdbdb;padding:0.5em 0.75em;vertical-align:top;"><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding:0.25em 0.5em 0.25em;">is-clearfix</code></td>
      <td style="border-width:1px;border:1px solid #dbdbdb;border-width:0 0 1px;padding:0.5em 0.75em;vertical-align:top;">清除元素的子元素的浮动</td>
    </tr>
    <tr>
      <td style="border-width:1px;border:1px solid #dbdbdb;padding:0.5em 0.75em;vertical-align:top;"><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding:0.25em 0.5em 0.25em;">is-pulled-left</code></td>
      <td style="border-width:1px;border:1px solid #dbdbdb;border-width:0 0 1px;padding:0.5em 0.75em;vertical-align:top;">将元素移动到左侧</td>
    </tr>
    <tr>
      <td style="border-width:1px;border:1px solid #dbdbdb;padding:0.5em 0.75em;vertical-align:top;"><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding:0.25em 0.5em 0.25em;">is-pulled-right</code></td>
      <td style="border-width:1px;border:1px solid #dbdbdb;border-width:0 0 1px;padding:0.5em 0.75em;vertical-align:top;">将元素移动到右侧</td>
    </tr>
    <tr>
      <th rowspan="2" style="border-width:1px;color:#363636;text-align:left;border:1px solid #dbdbdb;padding:0.5em 0.75em;vertical-align:top;">间距(Spacing)</th>
      <td style="border-width:1px;border:1px solid #dbdbdb;padding:0.5em 0.75em;vertical-align:top;"><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding:0.25em 0.5em 0.25em;">is-marginless</code></td>
      <td style="border-width:1px;border:1px solid #dbdbdb;border-width:0 0 1px;padding:0.5em 0.75em;vertical-align:top;">移除外边距</td>
    </tr>
    <tr>
      <td style="border-width:1px;border:1px solid #dbdbdb;padding:0.5em 0.75em;vertical-align:top;"><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding:0.25em 0.5em 0.25em;">is-paddingless</code></td>
      <td style="border-width:1px;border:1px solid #dbdbdb;border-width:0 0 1px;padding:0.5em 0.75em;vertical-align:top;">移除内边距</td>
    </tr>
    <tr>
      <th rowspan="6" style="border-width:1px;color:#363636;text-align:left;border:1px solid #dbdbdb;padding:0.5em 0.75em;vertical-align:top;">其他</th>
      <td style="border-width:1px;border:1px solid #dbdbdb;padding:0.5em 0.75em;vertical-align:top;"><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding:0.25em 0.5em 0.25em;">is-overlay</code></td>
      <td style="border-width:1px;border:1px solid #dbdbdb;border-width:0 0 1px;padding:0.5em 0.75em;vertical-align:top;">覆盖第一个定位的父元素</td>
    </tr>
      <tr><td style="border-width:1px;border:1px solid #dbdbdb;padding:0.5em 0.75em;vertical-align:top;"><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding:0.25em 0.5em 0.25em;">is-clipped</code></td>
      <td style="border-width:1px;border:1px solid #dbdbdb;border-width:0 0 1px;padding:0.5em 0.75em;vertical-align:top;">添加隐藏的溢出</td>
    </tr>
    <tr>
      <td style="border-width:1px;border:1px solid #dbdbdb;padding:0.5em 0.75em;vertical-align:top;"><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding:0.25em 0.5em 0.25em;">is-radiusless</code></td>
      <td style="border-width:1px;border:1px solid #dbdbdb;border-width:0 0 1px;padding:0.5em 0.75em;vertical-align:top;">移除所有的半径</td>
    </tr>
    <tr>
      <td style="border-width:1px;border:1px solid #dbdbdb;padding:0.5em 0.75em;vertical-align:top;"><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding:0.25em 0.5em 0.25em;">is-shadowless</code></td>
      <td style="border-width:1px;border:1px solid #dbdbdb;border-width:0 0 1px;padding:0.5em 0.75em;vertical-align:top;">移除所有的阴影</td>
    </tr>
    <tr>
      <td style="border-width:1px;border:1px solid #dbdbdb;padding:0.5em 0.75em;vertical-align:top;"><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding:0.25em 0.5em 0.25em;">is-unselectable</code></td>
      <td style="border-width:1px;border:1px solid #dbdbdb;border-width:0 0 1px;padding:0.5em 0.75em;vertical-align:top;">禁止选择文本</td>
    </tr>
    <tr>
      <td style="border-width:1px;border:1px solid #dbdbdb;padding:0.5em 0.75em;vertical-align:top;"><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding:0.25em 0.5em 0.25em;">is-invisible</code></td>
      <td style="border-width:1px;border:1px solid #dbdbdb;border-width:0 0 1px;padding:0.5em 0.75em;vertical-align:top;">增加隐藏的可见性</td>
    </tr>
  </tbody>
</table>

## 响应式助手

根据视口宽度的变化显示或隐藏内容

### 显示

你可以使用以下其中之一的显示类：

- `block`
- `flex`
- `inline`
- `inline-block`
- `inline-flex`

| Class | Mobile Up to 768px | Tablet Between 769px and 1023px | Desktop Between 1024px and 1215px | Widescreen Between 1216px and 1407px | FullHD 1408px and above |
| --- | --- | --- | --- | --- | --- |
| `is-flex-mobile` | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">flex</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> |
| `is-flex-tablet-only` | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">flex</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> |
| `is-flex-desktop-only` | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">flex</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> |
| `is-flex-desktop-only` | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">flex</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> |

可以显示特定断点或从特定断点显示的类

| Class | Mobile Up to 768px | Tablet Between 769px and 1023px | Desktop Between 1024px and 1215px | Widescreen Between 1216px and 1407px | FullHD 1408px and above |
| --- | --- | --- | --- | --- | --- |
| `is-flex-touch` | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">flex</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">flex</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> |
| `is-flex-tablet` | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">flex</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">flex</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">flex</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">flex</p> |
| `is-flex-desktop` | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">flex</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">flex</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">flex</p> |
| `is-flex-widescreen` | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">flex</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">flex</p> |
| `is-flex-fullhd` | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">flex</p> |

对于其他显示选项，只需将`is-flex`替换为`is-block`、 `is-inline`、 `is-inline-block`或`is-inline-flex`

### 隐藏

| Class | Mobile Up to 768px | Tablet Between 769px and 1023px | Desktop Between 1024px and 1215px | Widescreen Between 1216px and 1407px | FullHD 1408px and above |
| --- | --- | --- | --- | --- | --- |
| `is-hidden-mobile` | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">hidden</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">visible</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">visible</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">visible</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">visible</p> |
| `is-hidden-tablet-only` | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">visible</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">hidden</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">visible</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">visible</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">visible</p> |
| `is-hidden-desktop-only` | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">visible</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">visible</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">hidden</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">visible</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">visible</p> |
| `is-hidden-widescreen-only` | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">visible</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">visible</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">visible</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">hidden</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">visible</p> |

隐藏到特定断点或从特定断点隐藏的类

| Class | Mobile Up to 768px | Tablet Between 769px and 1023px | Desktop Between 1024px and 1215px | Widescreen Between 1216px and 1407px | FullHD 1408px and above |
| --- | --- | --- | --- | --- | --- |
| `is-hidden-touch` | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">hidden</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">hidden</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">visible</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">visible</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">visible</p> |
| `is-hidden-tablet` | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">visible</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">hidden</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">hidden</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">hidden</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">hidden</p> |
| `is-hidden-desktop` | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">visible</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">visible</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">hidden</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">hidden</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">hidden</p> |
| `is-hidden-widescreen` | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">visible</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">visible</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">visible</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">hidden</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">hidden</p> |
| `is-hidden-fullhd` | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">visible</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">visible</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">visible</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">visible</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">hidden</p> |

## 排版助手

排版助手帮助我们更改一个或多个视口宽度的文本的大小和颜色

### 尺寸

在Bulma中有7个尺寸供选择：

| Class |	Font-size |
| ----- | --------- |
| `is-size-1` |	3rem |
| `is-size-2` |	2.5rem |
| `is-size-3` |	2rem |
| `is-size-4` |	1.5rem |
| `is-size-5` |	1.25rem |
| `is-size-6` |	1rem |
| `is-size-7` |	0.75rem |

### 响应式尺寸

你可以为每个视口宽度选择一个特定的大小，只需将视口宽度附加到大小修改器上，例如，以下是 `$size-1` 的修饰符：

| Class | Mobile Up to 768px | Tablet Between 769px and 1023px | Desktop Between 1024px and 1215px | Widescreen Between 1216px and 1407px | FullHD 1408px and above |
| --- | --- | --- | --- | --- | --- |
| `is-size-1-mobile` | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">3rem</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> |
| `is-size-1-tablet` | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">3rem</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> |
| `is-size-1-touch` | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">3rem</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">3rem</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> |
| `is-size-1-desktop` | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">3rem</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">3rem</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">3rem</p> |
| `is-size-1-widescreen` | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">3rem</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">3rem</p> |
| `is-size-1-fullhd` | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">3rem</p> |

您可以对7种尺寸中的每种尺寸使用相同的逻辑。

### 颜色

您可以将任何元素设置为9种颜色或9种灰色之一：

| Class | Color |
| ----- | ----- |
| `has-text-white` | <span style="border-radius:2px;-webkit-box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1); box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1);display:inline-block;float:left;height:24px;margin-right:8px;width:24px;background:hsl(0, 0%, 100%);"></span>`hsl(0, 0%, 100%)` |
| `has-text-black` | <span style="border-radius:2px;-webkit-box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1); box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1);display:inline-block;float:left;height:24px;margin-right:8px;width:24px;background:hsl(0, 0%, 4%);"></span>`hsl(0, 0%, 4%)` |
| `has-text-light` | <span style="border-radius:2px;-webkit-box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1); box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1);display:inline-block;float:left;height:24px;margin-right:8px;width:24px;background:hsl(0, 0%, 96%);"></span>`hsl(0, 0%, 96%)` |
| `has-text-dark` | <span style="border-radius:2px;-webkit-box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1); box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1);display:inline-block;float:left;height:24px;margin-right:8px;width:24px;background:hsl(0, 0%, 21%);"></span>`hsl(0, 0%, 21%)` |
| `has-text-primary` | <span style="border-radius:2px;-webkit-box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1); box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1);display:inline-block;float:left;height:24px;margin-right:8px;width:24px;background:hsl(171, 100%, 41%);"></span>`hsl(171, 100%, 41%)` |
| `has-text-info` | <span style="border-radius:2px;-webkit-box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1); box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1);display:inline-block;float:left;height:24px;margin-right:8px;width:24px;background:hsl(204, 86%, 53%);"></span>`hsl(204, 86%, 53%)` |
| `has-text-link` | <span style="border-radius:2px;-webkit-box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1); box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1);display:inline-block;float:left;height:24px;margin-right:8px;width:24px;background:hsl(217, 71%, 53%);"></span>`hsl(217, 71%, 53%)` |
| `has-text-success` | <span style="border-radius:2px;-webkit-box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1); box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1);display:inline-block;float:left;height:24px;margin-right:8px;width:24px;background:hsl(141, 71%, 48%);"></span>`hsl(141, 71%, 48%)` |
| `has-text-warning` | <span style="border-radius:2px;-webkit-box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1); box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1);display:inline-block;float:left;height:24px;margin-right:8px;width:24px;background:hsl(48, 100%, 67%);"></span>`hsl(48, 100%, 67%)` |
| `has-text-danger` | <span style="border-radius:2px;-webkit-box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1); box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1);display:inline-block;float:left;height:24px;margin-right:8px;width:24px;background:hsl(348, 100%, 61%);"></span>`hsl(348, 100%, 61%)` |
| `has-text-black-bis` | <span style="border-radius:2px;-webkit-box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1); box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1);display:inline-block;float:left;height:24px;margin-right:8px;width:24px;background:hsl(0, 0%, 7%);"></span>`hsl(0, 0%, 7%)` |
| `has-text-black-ter` | <span style="border-radius:2px;-webkit-box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1); box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1);display:inline-block;float:left;height:24px;margin-right:8px;width:24px;background:hsl(0, 0%, 14%);"></span>`hsl(0, 0%, 14%)` |
| `has-text-grey-darker` | <span style="border-radius:2px;-webkit-box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1); box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1);display:inline-block;float:left;height:24px;margin-right:8px;width:24px;background:hsl(0, 0%, 21%);"></span>`hsl(0, 0%, 21%)` |
| `has-text-grey-dark` | <span style="border-radius:2px;-webkit-box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1); box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1);display:inline-block;float:left;height:24px;margin-right:8px;width:24px;background:hsl(0, 0%, 29%);"></span>`hsl(0, 0%, 29%)` |
| `has-text-grey` | <span style="border-radius:2px;-webkit-box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1); box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1);display:inline-block;float:left;height:24px;margin-right:8px;width:24px;background:hsl(0, 0%, 48%);"></span>`hsl(0, 0%, 48%)` |
| `has-text-grey-light` | <span style="border-radius:2px;-webkit-box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1); box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1);display:inline-block;float:left;height:24px;margin-right:8px;width:24px;background:hsl(0, 0%, 71%);"></span>`hsl(0, 0%, 71%)` |
| `has-text-grey-lighter` | <span style="border-radius:2px;-webkit-box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1); box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1);display:inline-block;float:left;height:24px;margin-right:8px;width:24px;background:hsl(0, 0%, 86%);"></span>`hsl(0, 0%, 86%)` |
| `has-text-white-ter` | <span style="border-radius:2px;-webkit-box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1); box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1);display:inline-block;float:left;height:24px;margin-right:8px;width:24px;background:hsl(0, 0%, 96%);"></span>`hsl(0, 0%, 96%)` |
| `has-text-white-bis` | <span style="border-radius:2px;-webkit-box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1); box-shadow:0 2px 3px 0 rgba(0, 0, 0, 0.1),inset 0 0 0 1px rgba(0, 0, 0, 0.1);display:inline-block;float:left;height:24px;margin-right:8px;width:24px;background:hsl(0, 0%, 98%);"></span>`hsl(0, 0%, 98%)` |

### 对齐

你可以使用以下的4个对齐助手来处理文本位置

| Class | Alignment |
| ----- | --------- |
| `has-text-centered` | 使文本居中对齐 |
| `has-text-justified` | 使文本处于合理的位置 |
| `has-text-left` | 将文本对齐到左侧 |
| `has-text-right` | 将文本对齐到右侧 |

### 响应式对齐

现在您可以为每个视口宽度对齐文本。 您只需将视口宽度附加到对齐修改器即可。例如，以下是`has-text-left`的修饰符：

| Class | Mobile Up to 768px | Tablet Between 769px and 1023px | Desktop Between 1024px and 1215px | Widescreen Between 1216px and 1407px | FullHD 1408px and above |
| --- | --- | --- | --- | --- | --- |
| `has-text-left-mobile` | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">left-aligned</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> |
| `has-text-left-tablet` | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">left-aligned</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">left-aligned</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">left-aligned</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">left-aligned</p> |
| `has-text-left-tablet-only` | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">left-aligned</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> |
| `has-text-left-touch` | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">left-aligned</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">left-aligned</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> |
| `has-text-left-desktop` | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">left-aligned</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">left-aligned</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">left-aligned</p> |
| `has-text-left-desktop-only` | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">left-aligned</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> |
| `has-text-left-widescreen` | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">left-aligned</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">left-aligned</p> |
| `has-text-left-widescreen-only` | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">left-aligned</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> |
| `has-text-left-fullhd` | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:whitesmoke;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;color:#363636;">unchanged</p> | <p style="background-color:#23d160;color:#fff;border-radius:3px;padding:1.25rem 2.5rem 1.25rem 1.5rem;position:relative;">left-aligned</p> |

### 文本转换

您可以使用下列4个文本转换助手之一来转换文本：

| Class |	Transformation |
| ----- | -------------- |
| `is-capitalized` | 将每个单词的第一个字符转换为大写 |
| `is-lowercase` | 将所有字符转换为小写 |
| `is-uppercase` | 将所有字符转换为大写 |
| `is-italic` |	将所有字符转换为斜体 |

### 字体粗细

您可以使用4个文本加权助手之一来转换文本权重：

| Class | Weight |
| ----- | ------ |
| `has-text-weight-light` |	将文本转换为清细字体 |
| `has-text-weight-normal` | 将文本转换为正常 |
| `has-text-weight-semibold` | 将文字权重转换为半粗体 |
| `has-text-weight-bold` | 将文本权重转换为粗体 |

# 列定义

## 基本使用

构建响应式列的简单方法:

使用Bulma构建列布局非常简单：

1. 添加一个列容器
2. 根据需要添加尽可能多的列元素

无论列的数量如何，每列的宽度都是相等的。

![](https://todever-images.oss-cn-beijing.aliyuncs.com/201803291122.png)

```html
<div class="columns">
  <div class="column">
    First column
  </div>
  <div class="column">
    Second column
  </div>
  <div class="column">
    Third column
  </div>
  <div class="column">
    Fourth column
  </div>
</div>
```

## 尺寸

Bulma允许你分别定义每个列的大小，你可以使用以下CSS类来修改单列的大小:

- `is-three-quarters`
- `is-two-thirds`
- `is-half`
- `is-one-third`
- `is-one-quarter`

其他列将自动填充剩余空间。

在v0.6.1版本中，你也可以使用以下20％的倍数：

- `is-four-fifths`
- `is-three-fifths`
- `is-two-fifths`
- `is-one-fifth`

![](https://todever-images.oss-cn-beijing.aliyuncs.com/201803291123.png)

```html
<div class="columns">
  <div class="column is-four-fifths">is-four-fifths</div>
  <div class="column">Auto</div>
  <div class="column">Auto</div>
</div>

<div class="columns">
  <div class="column is-three-quarters">is-three-quarters</div>
  <div class="column">Auto</div>
  <div class="column">Auto</div>
</div>

<div class="columns">
  <div class="column is-two-thirds">is-two-thirds</div>
  <div class="column">Auto</div>
  <div class="column">Auto</div>
</div>

<div class="columns">
  <div class="column is-three-fifths">is-three-fifths</div>
  <div class="column">Auto</div>
  <div class="column">Auto</div>
</div>

<div class="columns">
  <div class="column is-half">is-half</div>
  <div class="column">Auto</div>
  <div class="column">Auto</div>
</div>

<div class="columns">
  <div class="column is-two-fifths">is-two-fifths</div>
  <div class="column">Auto</div>
  <div class="column">Auto</div>
</div>

<div class="columns">
  <div class="column is-one-third">is-one-third</div>
  <div class="column">Auto</div>
  <div class="column">Auto</div>
</div>

<div class="columns">
  <div class="column is-one-quarter">is-one-quarter</div>
  <div class="column">Auto</div>
</div>

<div class="columns">
  <div class="column is-one-fifth">is-one-fifth</div>
  <div class="column">Auto</div>
  <div class="column">Auto</div>
</div>
```

### 12列系统

由于网格可以分成12列，每个分区都有尺寸等级：

- `is-2`
- `is-3`
- `is-4`
- `is-5`
- `is-6`
- `is-7`
- `is-8`
- `is-9`
- `is-10`
- `is-11`

命名约定：每个修饰符类都以12个列中您想要的列数来命名。所以，如果您需要12列中的7列，请使用`is-7`。

![](https://todever-images.oss-cn-beijing.aliyuncs.com/201803291128.png)

### 偏移

你可以使用空列（如`<div class =“column”> </ div>`）来创建`.column`元素周围的空白的空间，但Bulma推荐使用偏移量修饰符，如`.is-offset-x`：

![](https://todever-images.oss-cn-beijing.aliyuncs.com/201803291131.png)

```html
<div class="columns is-mobile">
  <div class="column is-half is-offset-one-quarter"></div>
</div>

<div class="columns is-mobile">
  <div class="column is-three-fifths is-offset-one-fifth"></div>
</div>

<div class="columns is-mobile">
  <div class="column is-4 is-offset-8"></div>
</div>

<div class="columns is-mobile">
  <div class="column is-11 is-offset-1"></div>
</div>
```

### 窄列

如果你想要创建一个仅仅占用它所需的空间的列，请使用`is-narrow`修饰符。 另一列将填满剩余的空间。

![](https://todever-images.oss-cn-beijing.aliyuncs.com/201803291134.png)

```html
<div class="columns">
  <div class="column is-narrow">
    <div class="box" style="width: 200px;">
      <p class="title is-5">Narrow column</p>
      <p class="subtitle">This column is only 200px wide.</p>
    </div>
  </div>
  <div class="column">
    <div class="box">
      <p class="title is-5">Flexible column</p>
      <p class="subtitle">This column will take up the remaining space available.</p>
    </div>
  </div>
</div>
```

至于大小修饰符，您可以针对不同的断点使用较窄的列：

- `is-narrow-mobile`
- `is-narrow-tablet`
- `is-narrow-desktop`

## 响应列

为每个断点处理不同的列布局

### 移动设备的列

默认情况下，列仅在平板电脑之后被激活， 这意味着列在移动设备上是堆叠在一起的。如果您希望列也可以在移动设备上工作，只需在列容器中添加`is-mobile`修改器即可：

```html
<div class="columns is-mobile">
  <div class="column">1</div>
  <div class="column">2</div>
  <div class="column">3</div>
  <div class="column">4</div>
</div>
```

如果您想查看其中的差异，请调整浏览器大小并查看列的堆叠时间和水平分布时间。

如果您只希望桌面上的列向上移动，只需在列容器上使用`is-desktop`修饰符即可：

```html
<div class="columns is-desktop">
  <div class="column">1</div>
  <div class="column">2</div>
  <div class="column">3</div>
  <div class="column">4</div>
</div>
```

### 每个断点不同的列大小

您可以为每个视口大小定义列大小：移动设备，平板电脑和桌面。

![](https://todever-images.oss-cn-beijing.aliyuncs.com/201803291503.png)

如果您想要查看这些类，请调整浏览器窗口大小，并查看每个断点处同一列的宽度是如何变化的。

```html
<div class="columns is-mobile">
  <div class="column is-three-quarters-mobile is-two-thirds-tablet is-half-desktop is-one-third-widescreen is-one-quarter-fullhd">
    <code>is-three-quarters-mobile</code><br>
    <code>is-two-thirds-tablet</code><br>
    <code>is-half-desktop</code>
    <code>is-one-third-widescreen</code>
    <code>is-one-quarter-fullhd</code>
  </div>
  <div class="column">1</div>
  <div class="column">1</div>
</div>
```

## 列嵌套

构建响应式列的简单方法

您可以嵌套列以在设计中拥有更大的灵活性。 你只需要遵循这个结构：

<ul><li><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding:0.25em 0.5em 0.25em;-webkit-font-smoothing:auto;font-family:monospace;">columns</code>: 顶级列容器<ul style="list-style-type:circle;list-style:disc outside;"><li><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding:0.25em 0.5em 0.25em;-webkit-font-smoothing:auto;font-family: monospace;">column</code><ul style="list-style-type:square;list-style:disc outside;"><li><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding:0.25em 0.5em 0.25em;-webkit-font-smoothing:auto;font-family:monospace;">columns</code>:  嵌套列<ul style="list-style-type:square;list-style:disc outside;"><li><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding:0.25em 0.5em 0.25em;-webkit-font-smoothing:auto;font-family:monospace;">column</code>  等等…</li></ul></li></ul></li></ul></li></ul>

与多行列的区别在于HTML代码中的顺序：所有蓝色列出现在红色列之前。 调整到较窄的视口以查看结果。

![](https://todever-images.oss-cn-beijing.aliyuncs.com/201803291508.png)

多行列也将在每行之间存在差距。

## 列间隙

Bulma支持自定义列之间的差距

### 默认间距

每列都有一个等于变量`$column-gap`的间距，其缺省值为`0.75rem`。

由于间隔位于列的每一侧，因此两个相邻列之间的间隔将是`$column-gap`的两倍，或者默认为`1.5rem`。

### 零间距

如果要删除列之间的空间，请在列容器上添加`is-gapless`修饰符：

![](https://todever-images.oss-cn-beijing.aliyuncs.com/201803291515.png)

```html
<div class="columns is-gapless">
  <div class="column">
    No gap
  </div>
  <div class="column">
    No gap
  </div>
  <div class="column">
    No gap
  </div>
  <div class="column">
    No gap
  </div>
</div>
```

您也可以将它与`is-multiline`修饰符结合使用：

![](https://todever-images.oss-cn-beijing.aliyuncs.com/201803291516.png)

```html
<div class="columns is-gapless is-multiline is-mobile">
  <div class="column is-one-quarter">
    is-one-quarter
  </div>
  <div class="column is-one-quarter">
    is-one-quarter
  </div>
  <div class="column is-one-quarter">
    is-one-quarter
  </div>
  <div class="column is-one-quarter">
    is-one-quarter
  </div>
  <div class="column is-half">
    is-half
  </div>
  <div class="column is-one-quarter">
    is-one-quarter
  </div>
  <div class="column is-one-quarter">
    is-one-quarter
  </div>
  <div class="column is-one-quarter">
    is-one-quarter
  </div>
  <div class="column">
    Auto
  </div>
</div>
```

### 可变间距

您可以通过在`.columns`容器上附加9个修饰符之一来指定自定义列间隔。

- `is-0` 移除所有间距(类似于`is-gapless`)
- `is-3` 默认值，相当于`0.75rem`
- `is-8` 最大间距，相当于`2rem`

另外，应该在`.columns`容器上添加`.is`变量。

![](https://todever-images.oss-cn-beijing.aliyuncs.com/201803291535.png)

此功能仅在支持CSS变量的浏览器中可用：

如果您的Sass安装程序不支持CSS变量，则可以通过将`$variable-columns`设置为`false`来禁用此功能。

## 其他选项

设计不同类型的列布局

### 多行

无论何时想要开始一个新行，您都可以关闭一个列容器并开始一个新的行。 但是，您也可以添加`is-multiline`修改器，并添加更多适合单行的列元素。

![](https://todever-images.oss-cn-beijing.aliyuncs.com/201803291541.png)

```html
<div class="columns is-multiline is-mobile">
  <div class="column is-one-quarter">
    <code>is-one-quarter</code>
  </div>
  <div class="column is-one-quarter">
    <code>is-one-quarter</code>
  </div>
  <div class="column is-one-quarter">
    <code>is-one-quarter</code>
  </div>
  <div class="column is-one-quarter">
    <code>is-one-quarter</code>
  </div>
  <div class="column is-half">
    <code>is-half</code>
  </div>
  <div class="column is-one-quarter">
    <code>is-one-quarter</code>
  </div>
  <div class="column is-one-quarter">
    <code>is-one-quarter</code>
  </div>
  <div class="column is-one-quarter">
    <code>is-one-quarter</code>
  </div>
  <div class="column">
    Auto
  </div>
</div>
```

### 居中显示的列

尽管您可以使用空列（如`<div class =“column”> </ div>`）来创建`.column`元素周围的水平空间，但您也可以在父`.columns`元素上使用`.is`居中。

![](https://todever-images.oss-cn-beijing.aliyuncs.com/201803291544.png)

```html
<div class="columns is-mobile is-centered">
  <div class="column is-half is-narrow">
    <p class="bd-notification is-info">
      <code class="html">is-half</code><br>
      <code class="html">is-narrow</code>
    </p>
  </div>
</div>
```

你还可以使用`.is-multiline`创建一个灵活的居中列表（尝试调整大小以在不同的视口大小中进行居中）：

![](https://todever-images.oss-cn-beijing.aliyuncs.com/201803291545.png)

```html
<div class="columns is-mobile is-multiline is-centered">
  <div class="column is-narrow">
    <p class="bd-notification is-info">
      <code class="html">is-narrow</code><br>
      First Column
    </p>
  </div>
  <div class="column is-narrow">
    <p class="bd-notification is-success">
      <code class="html">is-narrow</code><br>
      Our Second Column
    </p>
  </div>
  <div class="column is-narrow">
    <p class="bd-notification is-danger">
      <code class="html">is-narrow</code><br>
      Third Column
    </p>
  </div>
  <div class="column is-narrow">
    <p class="bd-notification is-info">
      <code class="html">is-narrow</code><br>
      The Fourth Column
    </p>
  </div>
  <div class="column is-narrow">
    <p class="bd-notification is-success">
      <code class="html">is-narrow</code><br>
      Fifth Column
    </p>
  </div>
</div>
```

# 布局

## 容器

在Bulma中，你可以创建一个简单的容器，用于水平放置您的内容

`.container`类可以在任何情况下使用，但主要作为以下任一情况的直接子项：

- `.navbar`
- `.hero`
- `.section`
- `.footer`

每个断点的容器宽度是：`$device - （2 * $gap）`。 `$gap`变量的默认值是32px，并且可以修改。

在不同的断点下，容器有不同的表现：

- 在`$desktop`上， 它将拥有一个960px的最大宽度
- 在`$widescreen`上， 它将拥有一个1152px的最大宽度
- 在`$fullhd`上， 它将拥有一个1344px的最大宽度

下面来看一些样例：

在桌面环境中居中显示的容器：

```html
<div class="container">
  <div class="notification">
    This container is <strong>centered</strong> on desktop.
  </div>
</div>
```

一个流式的容器，在任何一个视口尺寸上，它都会有32px的间隙。如果你始终想让容器的左右两边保留32px的边距，就使用`is-fluid`类

```html
<div class="container is-fluid">
  <div class="notification">
    This container is <strong>fluid</strong>: it will have a 32px gap on either side, on any
    viewport size.
  </div>
</div>
```

使用`.is-widescreen`和`.is-fullhd`这两个修饰符，您可以拥有一个全宽容器，直到这些特定的断点。

```html
<div class="container is-widescreen">
  <div class="notification">
    This container is <strong>fullwidth</strong> <em>until</em> the <code>$widescreen</code> breakpoint.
  </div>
</div>
```

```html
<div class="container is-fullhd">
  <div class="notification">
    This container is <strong>fullwidth</strong> <em>until</em> the <code>$fullhd</code> breakpoint.
  </div>
</div>
```

## 水平容器

在Bulma中，水平容器可以包含几乎任何其他元素，容器的结构如下：

<ul>
  <li><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding:0.25em 0.5em 0.25em;-webkit-font-smoothing:auto;font-family:monospace;">level</code>: 主容器
    <ul style="list-style-type:circle;list-style:disc outside;">
      <li><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding:0.25em 0.5em 0.25em;-webkit-font-smoothing:auto;font-family: monospace;">level-left</code>：左侧部分</li>
      <li><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding:0.25em 0.5em 0.25em;-webkit-font-smoothing:auto;font-family: monospace;">level-right</code>：右侧部分
        <ul style="list-style-type:circle;list-style:disc outside;">
          <li><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding:0.25em 0.5em 0.25em;-webkit-font-smoothing:auto;font-family: monospace;">level-item</code>：每一个单独的元素</li>
        </ul>
      </li>
    </ul>
  </li>
</ul>

在一个`level-item`中，您可以插入几乎任何您想要的内容：标题，按钮，文本输入或简单文本。 无论您将什么元素放入Bulma的`level`中，它们都将始终处于垂直居中位置。

```html
<!-- Main container -->
<nav class="level">
  <!-- Left side -->
  <div class="level-left">
    <div class="level-item">
      <p class="subtitle is-5">
        <strong>123</strong> posts
      </p>
    </div>
    <div class="level-item">
      <div class="field has-addons">
        <p class="control">
          <input class="input" type="text" placeholder="Find a post">
        </p>
        <p class="control">
          <button class="button">
            Search
          </button>
        </p>
      </div>
    </div>
  </div>

  <!-- Right side -->
  <div class="level-right">
    <p class="level-item"><strong>All</strong></p>
    <p class="level-item"><a>Published</a></p>
    <p class="level-item"><a>Drafts</a></p>
    <p class="level-item"><a>Deleted</a></p>
    <p class="level-item"><a class="button is-success">New</a></p>
  </div>
</nav>
```

### 居中的水平容器

如果你有一个居中的水平容器，那么你可以为它添加任意多的子容器

```html
<nav class="level">
  <div class="level-item has-text-centered">
    <div>
      <p class="heading">Tweets</p>
      <p class="title">3,456</p>
    </div>
  </div>
  <div class="level-item has-text-centered">
    <div>
      <p class="heading">Following</p>
      <p class="title">123</p>
    </div>
  </div>
  <div class="level-item has-text-centered">
    <div>
      <p class="heading">Followers</p>
      <p class="title">456K</p>
    </div>
  </div>
  <div class="level-item has-text-centered">
    <div>
      <p class="heading">Likes</p>
      <p class="title">789</p>
    </div>
  </div>
</nav>
```

```html
<nav class="level">
  <p class="level-item has-text-centered">
    <a class="link is-info">Home</a>
  </p>
  <p class="level-item has-text-centered">
    <a class="link is-info">Menu</a>
  </p>
  <p class="level-item has-text-centered">
    <img src="https://bulma.io/images/bulma-type.png" alt="" style="height: 30px;">
  </p>
  <p class="level-item has-text-centered">
    <a class="link is-info">Reservations</a>
  </p>
  <p class="level-item has-text-centered">
    <a class="link is-info">Contact</a>
  </p>
</nav>
```

### 移动端水平容器

默认情况下，水平容器在移动设备上是垂直的。 如果您希望它在移动设备上保持水平，请在容器上添加`is-mobile`修改器。

```html
<nav class="level is-mobile">
  <div class="level-item has-text-centered">
    <div>
      <p class="heading">Tweets</p>
      <p class="title">3,456</p>
    </div>
  </div>
  <div class="level-item has-text-centered">
    <div>
      <p class="heading">Following</p>
      <p class="title">123</p>
    </div>
  </div>
  <div class="level-item has-text-centered">
    <div>
      <p class="heading">Followers</p>
      <p class="title">456K</p>
    </div>
  </div>
  <div class="level-item has-text-centered">
    <div>
      <p class="heading">Likes</p>
      <p class="title">789</p>
    </div>
  </div>
</nav>
```

## 媒体对象

媒体对象在社交类应用的界面设计中非常常见，也广泛的使用在任何场景下。媒体对象很适合重复和嵌套内容的UI元素

```html
<article class="media">
  <figure class="media-left">
    <p class="image is-64x64">
      <img src="https://bulma.io/images/placeholders/128x128.png">
    </p>
  </figure>
  <div class="media-content">
    <div class="content">
      <p>
        <strong>John Smith</strong> <small>@johnsmith</small> <small>31m</small>
        <br>
        Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin ornare magna eros, eu pellentesque tortor vestibulum ut. Maecenas non massa sem. Etiam finibus odio quis feugiat facilisis.
      </p>
    </div>
    <nav class="level is-mobile">
      <div class="level-left">
        <a class="level-item">
          <span class="icon is-small"><i class="fas fa-reply"></i></span>
        </a>
        <a class="level-item">
          <span class="icon is-small"><i class="fas fa-retweet"></i></span>
        </a>
        <a class="level-item">
          <span class="icon is-small"><i class="fas fa-heart"></i></span>
        </a>
      </div>
    </nav>
  </div>
  <div class="media-right">
    <button class="delete"></button>
  </div>
</article>
```

你可以在其中包含任何其他的Bulma的元素，比如：`input`、`textarea`、`icons`、`buttons`，甚至是导航栏

```html
<article class="media">
  <figure class="media-left">
    <p class="image is-64x64">
      <img src="https://bulma.io/images/placeholders/128x128.png">
    </p>
  </figure>
  <div class="media-content">
    <div class="field">
      <p class="control">
        <textarea class="textarea" placeholder="Add a comment..."></textarea>
      </p>
    </div>
    <nav class="level">
      <div class="level-left">
        <div class="level-item">
          <a class="button is-info">Submit</a>
        </div>
      </div>
      <div class="level-right">
        <div class="level-item">
          <label class="checkbox">
            <input type="checkbox"> Press enter to submit
          </label>
        </div>
      </div>
    </nav>
  </div>
</article>
```

### 嵌套

您可以将媒体对象嵌套深达3层。

```html
<article class="media">
  <figure class="media-left">
    <p class="image is-64x64">
      <img src="https://bulma.io/images/placeholders/128x128.png">
    </p>
  </figure>
  <div class="media-content">
    <div class="content">
      <p>
        <strong>Barbara Middleton</strong>
        <br>
        Lorem ipsum dolor sit amet, consectetur adipiscing elit. Duis porta eros lacus, nec ultricies elit blandit non. Suspendisse pellentesque mauris sit amet dolor blandit rutrum. Nunc in tempus turpis.
        <br>
        <small><a>Like</a> · <a>Reply</a> · 3 hrs</small>
      </p>
    </div>

    <article class="media">
      <figure class="media-left">
        <p class="image is-48x48">
          <img src="https://bulma.io/images/placeholders/96x96.png">
        </p>
      </figure>
      <div class="media-content">
        <div class="content">
          <p>
            <strong>Sean Brown</strong>
            <br>
            Donec sollicitudin urna eget eros malesuada sagittis. Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Aliquam blandit nisl a nulla sagittis, a lobortis leo feugiat.
            <br>
            <small><a>Like</a> · <a>Reply</a> · 2 hrs</small>
          </p>
        </div>

        <article class="media">
          Vivamus quis semper metus, non tincidunt dolor. Vivamus in mi eu lorem cursus ullamcorper sit amet nec massa.
        </article>

        <article class="media">
          Morbi vitae diam et purus tincidunt porttitor vel vitae augue. Praesent malesuada metus sed pharetra euismod. Cras tellus odio, tincidunt iaculis diam non, porta aliquet tortor.
        </article>
      </div>
    </article>

    <article class="media">
      <figure class="media-left">
        <p class="image is-48x48">
          <img src="https://bulma.io/images/placeholders/96x96.png">
        </p>
      </figure>
      <div class="media-content">
        <div class="content">
          <p>
            <strong>Kayli Eunice </strong>
            <br>
            Sed convallis scelerisque mauris, non pulvinar nunc mattis vel. Maecenas varius felis sit amet magna vestibulum euismod malesuada cursus libero. Vestibulum ante ipsum primis in faucibus orci luctus et ultrices posuere cubilia Curae; Phasellus lacinia non nisl id feugiat.
            <br>
            <small><a>Like</a> · <a>Reply</a> · 2 hrs</small>
          </p>
        </div>
      </div>
    </article>
  </div>
</article>
<article class="media">
  <figure class="media-left">
    <p class="image is-64x64">
      <img src="https://bulma.io/images/placeholders/128x128.png">
    </p>
  </figure>
  <div class="media-content">
    <div class="field">
      <p class="control">
        <textarea class="textarea" placeholder="Add a comment..."></textarea>
      </p>
    </div>
    <div class="field">
      <p class="control">
        <button class="button">Post comment</button>
      </p>
    </div>
  </div>
</article>
```

## 巨幕

下面的代码展示了一个基本的巨幕，它包含一个`hero-body`

```html
<section class="hero">
  <div class="hero-body">
    <div class="container">
      <h1 class="title">
        Hero title
      </h1>
      <h2 class="subtitle">
        Hero subtitle
      </h2>
    </div>
  </div>
</section>
```

### 颜色

与按钮组件一样，您可以选择7种不同颜色之一：

```html
<section class="hero is-primary">
  <div class="hero-body">
    <div class="container">
      <h1 class="title">
        Primary title
      </h1>
      <h2 class="subtitle">
        Primary subtitle
      </h2>
    </div>
  </div>
</section>
```

```html
<section class="hero is-info">
  <div class="hero-body">
    <div class="container">
      <h1 class="title">
        Info title
      </h1>
      <h2 class="subtitle">
        Info subtitle
      </h2>
    </div>
  </div>
</section>
```

```html
<section class="hero is-success">
  <div class="hero-body">
    <div class="container">
      <h1 class="title">
        Success title
      </h1>
      <h2 class="subtitle">
        Success subtitle
      </h2>
    </div>
  </div>
</section>
```

```html
<section class="hero is-warning">
  <div class="hero-body">
    <div class="container">
      <h1 class="title">
        Warning title
      </h1>
      <h2 class="subtitle">
        Warning subtitle
      </h2>
    </div>
  </div>
</section>
```

```html
<section class="hero is-danger">
  <div class="hero-body">
    <div class="container">
      <h1 class="title">
        Danger title
      </h1>
      <h2 class="subtitle">
        Danger subtitle
      </h2>
    </div>
  </div>
</section>
```

```html
<section class="hero is-light">
  <div class="hero-body">
    <div class="container">
      <h1 class="title">
        Light title
      </h1>
      <h2 class="subtitle">
        Light subtitle
      </h2>
    </div>
  </div>
</section>
```

```html
<section class="hero is-dark">
  <div class="hero-body">
    <div class="container">
      <h1 class="title">
        Dark title
      </h1>
      <h2 class="subtitle">
        Dark subtitle
      </h2>
    </div>
  </div>
</section>
```

### 渐变

通过添加`is-bold`修饰符，可以为巨幕生成细微的渐变效果

```html
<section class="hero is-medium is-primary is-bold">
  <div class="hero-body">
    <div class="container">
      <h1 class="title">
        Primary bold title
      </h1>
      <h2 class="subtitle">
        Primary bold subtitle
      </h2>
    </div>
  </div>
</section>
```

```html
<section class="hero is-medium is-info is-bold">
  <div class="hero-body">
    <div class="container">
      <h1 class="title">
        Info bold title
      </h1>
      <h2 class="subtitle">
        Info bold subtitle
      </h2>
    </div>
  </div>
</section>
```

```html
<section class="hero is-medium is-warning is-bold">
  <div class="hero-body">
    <div class="container">
      <h1 class="title">
        Warning bold title
      </h1>
      <h2 class="subtitle">
        Warning bold subtitle
      </h2>
    </div>
  </div>
</section>
```

```html
<section class="hero is-medium is-danger is-bold">
  <div class="hero-body">
    <div class="container">
      <h1 class="title">
        Danger bold title
      </h1>
      <h2 class="subtitle">
        Danger bold subtitle
      </h2>
    </div>
  </div>
</section>
```

```html
<section class="hero is-medium is-light is-bold">
  <div class="hero-body">
    <div class="container">
      <h1 class="title">
        Light bold title
      </h1>
      <h2 class="subtitle">
        Light bold subtitle
      </h2>
    </div>
  </div>
</section>
```

```html
<section class="hero is-medium is-dark is-bold">
  <div class="hero-body">
    <div class="container">
      <h1 class="title">
        Dark bold title
      </h1>
      <h2 class="subtitle">
        Dark bold subtitle
      </h2>
    </div>
  </div>
</section>
```

### 尺寸

在Bulma中，有三种不同尺寸的巨幕供你选择：

1. `Medium`

```html
<section class="hero is-primary is-medium">
  <div class="hero-body">
    <div class="container">
      <h1 class="title">
        Medium title
      </h1>
      <h2 class="subtitle">
        Medium subtitle
      </h2>
    </div>
  </div>
</section>
```

2. `Large`

```html
<section class="hero is-info is-large">
  <div class="hero-body">
    <div class="container">
      <h1 class="title">
        Large title
      </h1>
      <h2 class="subtitle">
        Large subtitle
      </h2>
    </div>
  </div>
</section>
```

3. `Full Height`

```html
<section class="hero is-success is-fullheight">
  <div class="hero-body">
    <div class="container">
      <h1 class="title">
        Full Height title
      </h1>
      <h2 class="subtitle">
        Full Height subtitle
      </h2>
    </div>
  </div>
</section>
```

### 垂直高度满屏的巨幕

在垂直高度上满屏的巨幕，并且内容是水平、垂直居中的。你可以将它分为3个垂直部分：

- `hero`
    - `hero-head` (始终在顶部的部分)
    - `hero-body` (在中间且水平、垂直居中的部分)
    - `hero-foot` (始终在底部的部分)

```html
<section class="hero is-primary is-medium">
  <!-- Hero head: will stick at the top -->
  <div class="hero-head">
    <nav class="navbar">
      <div class="container">
        <div class="navbar-brand">
          <a class="navbar-item">
            <img src="https://bulma.io/images/bulma-type-white.png" alt="Logo">
          </a>
          <span class="navbar-burger burger" data-target="navbarMenuHeroA">
            <span></span>
            <span></span>
            <span></span>
          </span>
        </div>
        <div id="navbarMenuHeroA" class="navbar-menu">
          <div class="navbar-end">
            <a class="navbar-item is-active">
              Home
            </a>
            <a class="navbar-item">
              Examples
            </a>
            <a class="navbar-item">
              Documentation
            </a>
            <span class="navbar-item">
              <a class="button is-primary is-inverted">
                <span class="icon">
                  <i class="fab fa-github"></i>
                </span>
                <span>Download</span>
              </a>
            </span>
          </div>
        </div>
      </div>
    </nav>
  </div>

  <!-- Hero content: will be in the middle -->
  <div class="hero-body">
    <div class="container has-text-centered">
      <h1 class="title">
        Title
      </h1>
      <h2 class="subtitle">
        Subtitle
      </h2>
    </div>
  </div>

  <!-- Hero footer: will stick at the bottom -->
  <div class="hero-foot">
    <nav class="tabs">
      <div class="container">
        <ul>
          <li class="is-active"><a>Overview</a></li>
          <li><a>Modifiers</a></li>
          <li><a>Grid</a></li>
          <li><a>Elements</a></li>
          <li><a>Components</a></li>
          <li><a>Layout</a></li>
        </ul>
      </div>
    </nav>
  </div>
</section>
```

```html
<section class="hero is-info is-large">
  <div class="hero-head">
    <nav class="navbar">
      <div class="container">
        <div class="navbar-brand">
          <a class="navbar-item">
            <img src="https://bulma.io/images/bulma-type-white.png" alt="Logo">
          </a>
          <span class="navbar-burger burger" data-target="navbarMenuHeroB">
            <span></span>
            <span></span>
            <span></span>
          </span>
        </div>
        <div id="navbarMenuHeroB" class="navbar-menu">
          <div class="navbar-end">
            <a class="navbar-item is-active">
              Home
            </a>
            <a class="navbar-item">
              Examples
            </a>
            <a class="navbar-item">
              Documentation
            </a>
            <span class="navbar-item">
              <a class="button is-info is-inverted">
                <span class="icon">
                  <i class="fab fa-github"></i>
                </span>
                <span>Download</span>
              </a>
            </span>
          </div>
        </div>
      </div>
    </nav>
  </div>

  <div class="hero-body">
    <div class="container has-text-centered">
      <p class="title">
        Title
      </p>
      <p class="subtitle">
        Subtitle
      </p>
    </div>
  </div>

  <div class="hero-foot">
    <nav class="tabs is-boxed is-fullwidth">
      <div class="container">
        <ul>
          <li class="is-active">
            <a>Overview</a>
          </li>
          <li>
            <a>Modifiers</a>
          </li>
          <li>
            <a>Grid</a>
          </li>
          <li>
            <a>Elements</a>
          </li>
          <li>
            <a>Components</a>
          </li>
          <li>
            <a>Layout</a>
          </li>
        </ul>
      </div>
    </nav>
  </div>
</section>
```

```html
<section class="hero is-success is-fullheight">
  <!-- Hero head: will stick at the top -->
  <div class="hero-head">
    <header class="navbar">
      <div class="container">
        <div class="navbar-brand">
          <a class="navbar-item">
            <img src="https://bulma.io/images/bulma-type-white.png" alt="Logo">
          </a>
          <span class="navbar-burger burger" data-target="navbarMenuHeroC">
            <span></span>
            <span></span>
            <span></span>
          </span>
        </div>
        <div id="navbarMenuHeroC" class="navbar-menu">
          <div class="navbar-end">
            <a class="navbar-item is-active">
              Home
            </a>
            <a class="navbar-item">
              Examples
            </a>
            <a class="navbar-item">
              Documentation
            </a>
            <span class="navbar-item">
              <a class="button is-success is-inverted">
                <span class="icon">
                  <i class="fab fa-github"></i>
                </span>
                <span>Download</span>
              </a>
            </span>
          </div>
        </div>
      </div>
    </header>
  </div>

  <!-- Hero content: will be in the middle -->
  <div class="hero-body">
    <div class="container has-text-centered">
      <h1 class="title">
        Title
      </h1>
      <h2 class="subtitle">
        Subtitle
      </h2>
    </div>
  </div>

  <!-- Hero footer: will stick at the bottom -->
  <div class="hero-foot">
    <nav class="tabs is-boxed is-fullwidth">
      <div class="container">
        <ul>
          <li class="is-active"><a>Overview</a></li>
          <li><a>Modifiers</a></li>
          <li><a>Grid</a></li>
          <li><a>Elements</a></li>
          <li><a>Components</a></li>
          <li><a>Layout</a></li>
        </ul>
      </div>
    </nav>
  </div>
</section>
```

## 段落

一个简单的容器可以将您的页面分成不同的部分，例如您正在阅读的部分。你可以将`sections`作为`body`的直接子元素

```html
<body>
  <section class="section">
    <div class="container">
      <h1 class="title">Section</h1>
      <h2 class="subtitle">
        A simple container to divide your page into <strong>sections</strong>, like the one you're currently reading
      </h2>
    </div>
  </section>
</body>
```

您可以使用修饰符`is-medium`和`is-large`来更改间距。

### 变量部分

你可以使用下面的这些变量来自定义布局。在导入Bulma之前，你需要设置一个或多个这样的变量

| Name | Default value |
| ---- | ------------- |
| `$section-padding` | `3rem 1.5rem` |
| `$section-padding-medium` | `9rem 1.5rem` |
| `$section-padding-large` | `18rem 1.5rem` |

## 页脚

一个简单的响应式页脚，可以包含任何内容：列表，标题，列，图标，按钮等。

```html
<footer class="footer">
  <div class="container">
    <div class="content has-text-centered">
      <p>
        <strong>Bulma</strong> by <a href="https://jgthms.com">Jeremy Thomas</a>. The source code is licensed
        <a href="http://opensource.org/licenses/mit-license.php">MIT</a>. The website content
        is licensed <a href="http://creativecommons.org/licenses/by-nc-sa/4.0/">CC BY NC SA 4.0</a>.
      </p>
    </div>
  </div>
</footer>
```

### 变量设置

你可以使用下面的这些变量来自定义布局。在导入Bulma之前，你需要设置一个或多个这样的变量

| Name | Default value |
| ---- | ------------- |
| `$footer-background-color` | `$background` |

## 结构平铺

结构元素平铺可以构建二维的`Metro-like`, `Pinterest-like`,或任何你喜欢的布局样式

要构建复杂的二维布局，您只需要一个元素: `tile`:

```html
<div class="tile">
  <!-- The magical tile element! -->
</div>
```

样例：

![](https://todever-images.oss-cn-beijing.aliyuncs.com/201803301500.png)

```html
<div class="tile is-ancestor">
  <div class="tile is-vertical is-8">
    <div class="tile">
      <div class="tile is-parent is-vertical">
        <article class="tile is-child notification is-primary">
          <p class="title">Vertical...</p>
          <p class="subtitle">Top tile</p>
        </article>
        <article class="tile is-child notification is-warning">
          <p class="title">...tiles</p>
          <p class="subtitle">Bottom tile</p>
        </article>
      </div>
      <div class="tile is-parent">
        <article class="tile is-child notification is-info">
          <p class="title">Middle tile</p>
          <p class="subtitle">With an image</p>
          <figure class="image is-4by3">
            <img src="https://bulma.io/images/placeholders/640x480.png">
          </figure>
        </article>
      </div>
    </div>
    <div class="tile is-parent">
      <article class="tile is-child notification is-danger">
        <p class="title">Wide tile</p>
        <p class="subtitle">Aligned with the right tile</p>
        <div class="content">
          <!-- Content -->
        </div>
      </article>
    </div>
  </div>
  <div class="tile is-parent">
    <article class="tile is-child notification is-success">
      <div class="content">
        <p class="title">Tall tile</p>
        <p class="subtitle">With even more content</p>
        <div class="content">
          <!-- Content -->
        </div>
      </div>
    </article>
  </div>
</div>
```

### 修饰符

`Tile`拥有16个修饰符：

- 3个上下文修饰符
    - `is-ancestor`
    - `is-parent`
    - `is-child`
- 1个定向修饰符
    - `is-vertical`
- 12个水平尺寸修饰符
    - from `is-1`
    - to `is-12`

### 嵌套实现

所有的元素都是平铺的。要创建一个平铺的拼贴网格，你只需要拼贴`tile`元素

我们从一个包含了所有其他`tile`的祖先`tile`开始吧：

```html
<div class="tile is-ancestor">
  <!-- All other tile elemnts -->
</div>
```

添加将自动水平分布的元素：

```html
<div class="tile is-ancestor">
  <div class="tile">
    <!-- Add content or other tiles -->
  </div>
  <div class="tile">
    <!-- Add content or other tiles -->
  </div>
</div>
```

您可以根据12列网格调整任何`tile`的大小。例如，`is-4`将占据水平空间的三分之一：

```html
<div class="tile is-ancestor">
  <div class="tile is-4">
    <!-- 1/3 -->
  </div>
  <div class="tile">
    <!-- This tile will take the rest: 2/3 -->
  </div>
</div>
```

如果你想要垂直叠加这些`tile`，请在它们的父元素`tile`上添加修饰符`is-vertical`

```html
<div class="tile is-ancestor">
  <div class="tile is-4 is-vertical">
    <div class="tile">
      <!-- Top tile -->
    </div>
    <div class="tile">
      <!-- Bottom tile -->
    </div>
  </div>
  <div class="tile">
    <!-- This tile will take up the whole vertical space -->
  </div>
</div>
```

如果你想要添加内容到`tile`里，你可以这样做：

- 添加你想要的任何类样式，比如：`box`
- 添加修饰符 `is-child` 到这个`tile`上
- 添加修饰符 `is-parent`到这个`tile`的父级元素上

```html
<div class="tile is-ancestor">
  <div class="tile is-4 is-vertical is-parent">
    <div class="tile is-child box">
      <p class="title">One</p>
    </div>
    <div class="tile is-child box">
      <p class="title">Two</p>
    </div>
  </div>
  <div class="tile is-parent">
    <div class="tile is-child box">
      <p class="title">Three</p>
    </div>
  </div>
</div>
```

![](https://todever-images.oss-cn-beijing.aliyuncs.com/201803301518.png)

```html
<div class="tile is-ancestor">
  <div class="tile is-4 is-vertical is-parent">
    <div class="tile is-child box">
      <p class="title">One</p>
      <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin ornare magna eros, eu pellentesque tortor vestibulum ut. Maecenas non massa sem. Etiam finibus odio quis feugiat facilisis.</p>
    </div>
    <div class="tile is-child box">
      <p class="title">Two</p>
      <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin ornare magna eros, eu pellentesque tortor vestibulum ut. Maecenas non massa sem. Etiam finibus odio quis feugiat facilisis.</p>
    </div>
  </div>
  <div class="tile is-parent">
    <div class="tile is-child box">
      <p class="title">Three</p>
      <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Etiam semper diam at erat pulvinar, at pulvinar felis blandit. Vestibulum volutpat tellus diam, consequat gravida libero rhoncus ut. Morbi maximus, leo sit amet vehicula eleifend, nunc dui porta orci, quis semper odio felis ut quam.</p>
      <p>Suspendisse varius ligula in molestie lacinia. Maecenas varius eget ligula a sagittis. Pellentesque interdum, nisl nec interdum maximus, augue diam porttitor lorem, et sollicitudin felis neque sit amet erat. Maecenas imperdiet felis nisi, fringilla luctus felis hendrerit sit amet. Aenean vitae gravida diam, finibus dignissim turpis. Sed eget varius ligula, at volutpat tortor.</p>
      <p>Integer sollicitudin, tortor a mattis commodo, velit urna rhoncus erat, vitae congue lectus dolor consequat libero. Donec leo ligula, maximus et pellentesque sed, gravida a metus. Cras ullamcorper a nunc ac porta. Aliquam ut aliquet lacus, quis faucibus libero. Quisque non semper leo.</p>
    </div>
  </div>
</div>
```

### 元素嵌套的一些要求

<article style="background-color:#fff5f7;margin-bottom:1.5rem;border-radius:3px;font-size:1rem;font-weight:400;line-height: 1.5;"><div style="background-color:#ff3860;color:#fff;-webkit-box-align:center;-ms-flex-align:center;align-items:center;border-radius:3px 3px 0 0;color:#fff;display:-webkit-box;display:-ms-flexbox;display:flex;-webkit-box-pack:justify;-ms-flex-pack:justify;justify-content:space-between;line-height:1.25;padding:0.5em 0.75em;position:relative;">至少需要3个层次...</div><div style="border-color:#ff3860;color:#cd0930;border-top-left-radius:0;border-top-right-radius:0;border-top:none;border:1px solid #dbdbdb;border-radius:3px;color:#4a4a4a;padding:1em 1.25em;"><div class="content"><p>您至少需要3级层次结构：:</p><figure style="margin-left:0;margin-right:0;text-align:left;background-color:#f5f5f5;color:#586e75;font-weight:400;max-width: 100%;overflow:hidden;padding:0;"><pre><code class="language-markdown" data-lang="markdown">tile is-ancestor
|
└───tile is-parent
    |
    └───tile is-child</code></pre></figure></div></div></article>

<article style="background-color:#fff5f7;margin-bottom:1.5rem;border-radius:3px;font-size:1rem;font-weight:400;line-height: 1.5;"><div style="background-color:#23d160;color:#fff;-webkit-box-align:center;-ms-flex-align:center;align-items:center;border-radius:3px 3px 0 0;color:#fff;display:-webkit-box;display:-ms-flexbox;display:flex;-webkit-box-pack:justify;-ms-flex-pack:justify;justify-content:space-between;line-height:1.25;padding:0.5em 0.75em;position:relative;">如果你想要，可以添加更多的...</div><div style="border-color:#ff3860;color:#cd0930;border-top-left-radius:0;border-top-right-radius:0;border-top:none;border:1px solid #dbdbdb;border-radius:3px;color:#4a4a4a;padding:1em 1.25em;"><div class="content"><p>你也可以<code>tile</code>嵌入到更深的地方，并将其混合起来</p><figure style="margin-left:0;margin-right:0;text-align:left;background-color:#f5f5f5;color:#586e75;font-weight:400;max-width: 100%;overflow:hidden;padding:0;"><pre><code class="language-markdown" data-lang="markdown">tile is-ancestor
|
├───tile is-vertical is-8
|   |
|   ├───tile
|   |   |
|   |   ├───tile is-parent is-vertical
|   |   |   ├───tile is-child
|   |   |   └───tile is-child
|   |   |
|   |   └───tile is-parent
|   |       └───tile is-child
|   |
|   └───tile is-parent
|       └───tile is-child
|
└───tile is-parent
    └───tile is-child</code></pre></figure></div></div></article>

![](https://todever-images.oss-cn-beijing.aliyuncs.com/201803301533.png)

```html
<div class="tile is-ancestor">
  <div class="tile is-vertical is-8">
    <div class="tile">
      <div class="tile is-parent is-vertical">
        <article class="tile is-child box">
          <!-- Put any content you want -->
        </article>
        <article class="tile is-child box">
          <!-- Put any content you want -->
        </article>
      </div>
      <div class="tile is-parent">
        <article class="tile is-child box">
          <!-- Put any content you want -->
        </article>
      </div>
    </div>
    <div class="tile is-parent">
      <article class="tile is-child box">
        <!-- Put any content you want -->
      </article>
    </div>
  </div>
  <div class="tile is-parent">
    <article class="tile is-child box">
      <!-- Put any content you want -->
    </article>
  </div>
</div>
```

### 三列布局

```html
<div class="tile is-ancestor">
  <div class="tile is-parent">
    <article class="tile is-child box">
      <p class="title">Hello World</p>
      <p class="subtitle">What is up?</p>
    </article>
  </div>
  <div class="tile is-parent">
    <article class="tile is-child box">
      <p class="title">Foo</p>
      <p class="subtitle">Bar</p>
    </article>
  </div>
  <div class="tile is-parent">
    <article class="tile is-child box">
      <p class="title">Third column</p>
      <p class="subtitle">With some content</p>
      <div class="content">
        <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin ornare magna eros, eu pellentesque tortor vestibulum ut. Maecenas non massa sem. Etiam finibus odio quis feugiat facilisis.</p>
      </div>
    </article>
  </div>
</div>

<div class="tile is-ancestor">
  <div class="tile is-vertical is-8">
    <div class="tile">
      <div class="tile is-parent is-vertical">
        <article class="tile is-child box">
          <p class="title">Vertical tiles</p>
          <p class="subtitle">Top box</p>
        </article>
        <article class="tile is-child box">
          <p class="title">Vertical tiles</p>
          <p class="subtitle">Bottom box</p>
        </article>
      </div>
      <div class="tile is-parent">
        <article class="tile is-child box">
          <p class="title">Middle box</p>
          <p class="subtitle">With an image</p>
          <figure class="image is-4by3">
            <img src="https://bulma.io/images/placeholders/640x480.png">
          </figure>
        </article>
      </div>
    </div>
    <div class="tile is-parent">
      <article class="tile is-child box">
        <p class="title">Wide column</p>
        <p class="subtitle">Aligned with the right column</p>
        <div class="content">
          <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin ornare magna eros, eu pellentesque tortor vestibulum ut. Maecenas non massa sem. Etiam finibus odio quis feugiat facilisis.</p>
        </div>
      </article>
    </div>
  </div>
  <div class="tile is-parent">
    <article class="tile is-child box">
      <div class="content">
        <p class="title">Tall column</p>
        <p class="subtitle">With even more content</p>
        <div class="content">
          <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Etiam semper diam at erat pulvinar, at pulvinar felis blandit. Vestibulum volutpat tellus diam, consequat gravida libero rhoncus ut. Morbi maximus, leo sit amet vehicula eleifend, nunc dui porta orci, quis semper odio felis ut quam.</p>
          <p>Suspendisse varius ligula in molestie lacinia. Maecenas varius eget ligula a sagittis. Pellentesque interdum, nisl nec interdum maximus, augue diam porttitor lorem, et sollicitudin felis neque sit amet erat. Maecenas imperdiet felis nisi, fringilla luctus felis hendrerit sit amet. Aenean vitae gravida diam, finibus dignissim turpis. Sed eget varius ligula, at volutpat tortor.</p>
          <p>Integer sollicitudin, tortor a mattis commodo, velit urna rhoncus erat, vitae congue lectus dolor consequat libero. Donec leo ligula, maximus et pellentesque sed, gravida a metus. Cras ullamcorper a nunc ac porta. Aliquam ut aliquet lacus, quis faucibus libero. Quisque non semper leo.</p>
        </div>
      </div>
    </article>
  </div>
</div>

<div class="tile is-ancestor">
  <div class="tile is-parent">
    <article class="tile is-child box">
      <p class="title">Side column</p>
      <p class="subtitle">With some content</p>
      <div class="content">
        <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin ornare magna eros, eu pellentesque tortor vestibulum ut. Maecenas non massa sem. Etiam finibus odio quis feugiat facilisis.</p>
      </div>
    </article>
  </div>
  <div class="tile is-parent is-8">
    <article class="tile is-child box">
      <p class="title">Main column</p>
      <p class="subtitle">With some content</p>
      <div class="content">
        <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin ornare magna eros, eu pellentesque tortor vestibulum ut. Maecenas non massa sem. Etiam finibus odio quis feugiat facilisis.</p>
      </div>
    </article>
  </div>
</div>
```

### 四列布局

```html
<div class="tile is-ancestor">
  <div class="tile is-parent">
    <article class="tile is-child box">
      <p class="title">One</p>
      <p class="subtitle">Subtitle</p>
    </article>
  </div>
  <div class="tile is-parent">
    <article class="tile is-child box">
      <p class="title">Two</p>
      <p class="subtitle">Subtitle</p>
    </article>
  </div>
  <div class="tile is-parent">
    <article class="tile is-child box">
      <p class="title">Three</p>
      <p class="subtitle">Subtitle</p>
    </article>
  </div>
  <div class="tile is-parent">
    <article class="tile is-child box">
      <p class="title">Four</p>
      <p class="subtitle">Subtitle</p>
    </article>
  </div>
</div>

<div class="tile is-ancestor">
  <div class="tile is-vertical is-9">
    <div class="tile">
      <div class="tile is-parent">
        <article class="tile is-child box">
          <p class="title">Five</p>
          <p class="subtitle">Subtitle</p>
          <div class="content">
            <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Etiam semper diam at erat pulvinar, at pulvinar felis blandit. Vestibulum volutpat tellus diam, consequat gravida libero rhoncus ut. Morbi maximus, leo sit amet vehicula eleifend, nunc dui porta orci, quis semper odio felis ut quam.</p>
          </div>
        </article>
      </div>
      <div class="tile is-8 is-vertical">
        <div class="tile">
          <div class="tile is-parent">
            <article class="tile is-child box">
              <p class="title">Six</p>
              <p class="subtitle">Subtitle</p>
            </article>
          </div>
          <div class="tile is-parent">
            <article class="tile is-child box">
              <p class="title">Seven</p>
              <p class="subtitle">Subtitle</p>
            </article>
          </div>
        </div>
        <div class="tile is-parent">
          <article class="tile is-child box">
            <p class="title">Eight</p>
            <p class="subtitle">Subtitle</p>
          </article>
        </div>
      </div>
    </div>
    <div class="tile">
      <div class="tile is-8 is-parent">
        <article class="tile is-child box">
          <p class="title">Nine</p>
          <p class="subtitle">Subtitle</p>
          <div class="content">
            <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin ornare magna eros, eu pellentesque tortor vestibulum ut. Maecenas non massa sem. Etiam finibus odio quis feugiat facilisis.</p>
          </div>
        </article>
      </div>
      <div class="tile is-parent">
        <article class="tile is-child box">
          <p class="title">Ten</p>
          <p class="subtitle">Subtitle</p>
          <div class="content">
            <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin ornare magna eros, eu pellentesque tortor vestibulum ut. Maecenas non massa sem. Etiam finibus odio quis feugiat facilisis.</p>
          </div>
        </article>
      </div>
    </div>
  </div>
  <div class="tile is-parent">
    <article class="tile is-child box">
      <div class="content">
        <p class="title">Eleven</p>
        <p class="subtitle">Subtitle</p>
        <div class="content">
          <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Etiam semper diam at erat pulvinar, at pulvinar felis blandit. Vestibulum volutpat tellus diam, consequat gravida libero rhoncus ut. Morbi maximus, leo sit amet vehicula eleifend, nunc dui porta orci, quis semper odio felis ut quam.</p>
          <p>Integer sollicitudin, tortor a mattis commodo, velit urna rhoncus erat, vitae congue lectus dolor consequat libero. Donec leo ligula, maximus et pellentesque sed, gravida a metus. Cras ullamcorper a nunc ac porta. Aliquam ut aliquet lacus, quis faucibus libero. Quisque non semper leo.</p>
        </div>
      </div>
    </article>
  </div>
</div>

<div class="tile is-ancestor">
  <div class="tile is-parent">
    <article class="tile is-child box">
      <p class="title">Twelve</p>
      <p class="subtitle">Subtitle</p>
      <div class="content">
        <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin ornare magna eros, eu pellentesque tortor vestibulum ut.</p>
      </div>
    </article>
  </div>
  <div class="tile is-parent is-6">
    <article class="tile is-child box">
      <p class="title">Thirteen</p>
      <p class="subtitle">Subtitle</p>
      <div class="content">
        <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin ornare magna eros, eu pellentesque tortor vestibulum ut. Maecenas non massa sem. Etiam finibus odio quis feugiat facilisis.</p>
      </div>
    </article>
  </div>
  <div class="tile is-parent">
    <article class="tile is-child box">
      <p class="title">Fourteen</p>
      <p class="subtitle">Subtitle</p>
      <div class="content">
        <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin ornare magna eros, eu pellentesque tortor vestibulum ut.</p>
      </div>
    </article>
  </div>
</div>
```

# 表单

## 一般的

在Bulma中，所有的表单控件都会保持一致性，Bulma支持以下表单控件类：

- `.label`
- `.input`
- `.textarea`
- `.select`
- `.checkbox`
- `.radio`
- `.button`
- `.help`

它们中的每一个都应该被包含在一个`.container`容器中。

在窗体中组合多个控件时，请使用`.field`类作为容器，以保持间距一致。

![](https://todever-images.oss-cn-beijing.aliyuncs.com/201804021029.png)

```html
<div class="field">
  <label class="label">Name</label>
  <div class="control">
    <input class="input" type="text" placeholder="Text input">
  </div>
</div>

<div class="field">
  <label class="label">Username</label>
  <div class="control has-icons-left has-icons-right">
    <input class="input is-success" type="text" placeholder="Text input" value="bulma">
    <span class="icon is-small is-left">
      <i class="fas fa-user"></i>
    </span>
    <span class="icon is-small is-right">
      <i class="fas fa-check"></i>
    </span>
  </div>
  <p class="help is-success">This username is available</p>
</div>

<div class="field">
  <label class="label">Email</label>
  <div class="control has-icons-left has-icons-right">
    <input class="input is-danger" type="email" placeholder="Email input" value="hello@">
    <span class="icon is-small is-left">
      <i class="fas fa-envelope"></i>
    </span>
    <span class="icon is-small is-right">
      <i class="fas fa-exclamation-triangle"></i>
    </span>
  </div>
  <p class="help is-danger">This email is invalid</p>
</div>

<div class="field">
  <label class="label">Subject</label>
  <div class="control">
    <div class="select">
      <select>
        <option>Select dropdown</option>
        <option>With options</option>
      </select>
    </div>
  </div>
</div>

<div class="field">
  <label class="label">Message</label>
  <div class="control">
    <textarea class="textarea" placeholder="Textarea"></textarea>
  </div>
</div>

<div class="field">
  <div class="control">
    <label class="checkbox">
      <input type="checkbox">
      I agree to the <a href="#">terms and conditions</a>
    </label>
  </div>
</div>

<div class="field">
  <div class="control">
    <label class="radio">
      <input type="radio" name="question">
      Yes
    </label>
    <label class="radio">
      <input type="radio" name="question">
      No
    </label>
  </div>
</div>

<div class="field is-grouped">
  <div class="control">
    <button class="button is-link">Submit</button>
  </div>
  <div class="control">
    <button class="button is-text">Cancel</button>
  </div>
</div>
```

### 表单字段

字段容器`.field`非常的简单，一般它用于以下场景：

- 一个文本标签 `label`
- 一个表单控件 `control`
- 一个可选的帮助文件 `help`

```html
<div class="field">
  <label class="label">Label</label>
  <div class="control">
    <input class="input" type="text" placeholder="Text input">
  </div>
  <p class="help">This is a help text</p>
</div>
```

这个容器允许表单域保持一致：

```html
<div class="field">
  <label class="label">Name</label>
  <div class="control">
    <input class="input" type="text" placeholder="e.g Alex Smith">
  </div>
</div>

<div class="field">
  <label class="label">Email</label>
  <div class="control">
    <input class="input" type="email" placeholder="e.g. alexsmith@gmail.com">
  </div>
</div>
```

### 表单控件

该控件是一个多功能容器，它旨在增强单一窗体控件。 由于它与控制元素具有相同的高度，因此它只能包含以下元素：

- `input`
- `select`
- `button`
- `icon`

```html
<div class="control">
  <input class="input" type="text" placeholder="Text input">
</div>
```

```html
<div class="control">
  <div class="select">
    <select>
      <option>Select dropdown</option>
      <option>With options</option>
    </select>
  </div>
</div>
```

```html
<div class="control">
  <button class="button is-primary">Submit</button>
</div>
```

### 带有图标

你可以在控件上追加下面的2个修饰符中的一个：

- `has-icons-left`
- `has-icons-right`

您还需要在图标上添加修饰符：

- 如果使用了`has-icons-left`修饰符，则添加`icon is-left`
- 如果使用了`has-icons-right`修饰符，则添加`icon is-right`

输入的大小将定义图标容器的大小。

```html
<div class="field">
  <p class="control has-icons-left has-icons-right">
    <input class="input" type="email" placeholder="Email">
    <span class="icon is-small is-left">
      <i class="fas fa-envelope"></i>
    </span>
    <span class="icon is-small is-right">
      <i class="fas fa-check"></i>
    </span>
  </p>
</div>
<div class="field">
  <p class="control has-icons-left">
    <input class="input" type="password" placeholder="Password">
    <span class="icon is-small is-left">
      <i class="fas fa-lock"></i>
    </span>
  </p>
</div>
<div class="field">
  <p class="control">
    <button class="button is-success">
      Login
    </button>
  </p>
</div>
```

你也可以在选择下拉菜单中添加图标

```html
<div class="field">
  <p class="control has-icons-left">
    <span class="select">
      <select>
        <option selected>Country</option>
        <option>Select dropdown</option>
        <option>With options</option>
      </select>
    </span>
    <span class="icon is-small is-left">
      <i class="fas fa-globe"></i>
    </span>
  </p>
</div>
```

如果控件包含图标，Bulma将确保图标保持居中，而不管输入或图标的大小。

```html
<div class="field">
  <label class="label is-small">Small input</label>
  <div class="control has-icons-left has-icons-right">
    <input class="input is-small" type="email" placeholder="Normal">
    <span class="icon is-small is-left">
      <i class="fas fa-envelope"></i>
    </span>
    <span class="icon is-small is-right">
      <i class="fas fa-check"></i>
    </span>
  </div>
</div>
```

```html
<div class="field">
  <label class="label">Normal input</label>
  <div class="control has-icons-left has-icons-right">
    <input class="input" type="email" placeholder="Extra small">
    <span class="icon is-small is-left">
      <i class="fas fa-envelope fa-xs"></i>
    </span>
    <span class="icon is-small is-right">
      <i class="fas fa-check fa-xs"></i>
    </span>
  </div>
</div>

<div class="field">
  <div class="control has-icons-left has-icons-right">
    <input class="input" type="email" placeholder="Normal">
    <span class="icon is-left">
      <i class="fas fa-envelope"></i>
    </span>
    <span class="icon is-right">
      <i class="fas fa-check"></i>
    </span>
  </div>
</div>
```

```html
<div class="field">
  <label class="label is-medium">Medium input</label>
  <div class="control has-icons-left has-icons-right">
    <input class="input is-medium" type="email" placeholder="Extra small">
    <span class="icon is-small is-left">
      <i class="fas fa-envelope fa-xs"></i>
    </span>
    <span class="icon is-small is-right">
      <i class="fas fa-check fa-xs"></i>
    </span>
  </div>
</div>

<div class="field">
  <div class="control has-icons-left has-icons-right">
    <input class="input is-medium" type="email" placeholder="Small">
    <span class="icon is-left">
      <i class="fas fa-envelope fa-sm"></i>
    </span>
    <span class="icon is-right">
      <i class="fas fa-check fa-sm"></i>
    </span>
  </div>
</div>

<div class="field">
  <div class="control has-icons-left has-icons-right">
    <input class="input is-medium" type="email" placeholder="Normal">
    <span class="icon is-medium is-left">
      <i class="fas fa-envelope"></i>
    </span>
    <span class="icon is-medium is-right">
      <i class="fas fa-check"></i>
    </span>
  </div>
</div>
```

```html
<div class="field">
  <label class="label is-large">Large input</label>
  <div class="control has-icons-left has-icons-right">
    <input class="input is-large" type="email" placeholder="Extra small">
    <span class="icon is-small is-left">
      <i class="fas fa-envelope fa-xs"></i>
    </span>
    <span class="icon is-small is-right">
      <i class="fas fa-check fa-xs"></i>
    </span>
  </div>
</div>

<div class="field">
  <div class="control has-icons-left has-icons-right">
    <input class="input is-large" type="email" placeholder="Small">
    <span class="icon is-left">
      <i class="fas fa-envelope fa-sm"></i>
    </span>
    <span class="icon is-right">
      <i class="fas fa-check fa-sm"></i>
    </span>
  </div>
</div>

<div class="field">
  <div class="control has-icons-left has-icons-right">
    <input class="input is-large" type="email" placeholder="Normal">
    <span class="icon is-large is-left">
      <i class="fas fa-envelope"></i>
    </span>
    <span class="icon is-large is-right">
      <i class="fas fa-check"></i>
    </span>
  </div>
</div>

<div class="field">
  <div class="control has-icons-left has-icons-right">
    <input class="input is-large" type="email" placeholder="Large">
    <span class="icon is-medium is-left">
      <i class="fas fa-envelope fa-lg"></i>
    </span>
    <span class="icon is-medium is-right">
      <i class="fas fa-check fa-lg"></i>
    </span>
  </div>
</div>
```

### 表单插件

如果你想附加一个控件，可以在`field`容器上添加`has-addons`修饰符

```html
<div class="field has-addons">
  <div class="control">
    <input class="input" type="text" placeholder="Find a repository">
  </div>
  <div class="control">
    <a class="button is-info">
      Search
    </a>
  </div>
</div>
```

但你只能附加输入、按钮和下拉菜单。

你也可以追加静态按钮：

```html
<div class="field has-addons">
  <p class="control">
    <input class="input" type="text" placeholder="Your email">
  </p>
  <p class="control">
    <a class="button is-static">
      @gmail.com
    </a>
  </p>
</div>
```

在要填充剩余空间的元素（在本例中为输入）上使用`is-expanded`修饰符：

```html
<div class="field has-addons">
  <p class="control">
    <span class="select">
      <select>
        <option>$</option>
        <option>£</option>
        <option>€</option>
      </select>
    </span>
  </p>
  <p class="control">
    <input class="input" type="text" placeholder="Amount of money">
  </p>
  <p class="control">
    <a class="button">
      Transfer
    </a>
  </p>
</div>

<div class="field has-addons">
  <p class="control">
    <span class="select">
      <select>
        <option>$</option>
        <option>£</option>
        <option>€</option>
      </select>
    </span>
  </p>
  <p class="control is-expanded">
    <input class="input" type="text" placeholder="Amount of money">
  </p>
  <p class="control">
    <a class="button">
      Transfer
    </a>
  </p>
</div>
```

如果你想要一个100%宽度的选择下拉菜单，在带有`control is-expanded`修饰符的元素中添加带有select is-fullwidt`修饰符的元素

```html
<div class="field has-addons">
  <div class="control is-expanded">
    <div class="select is-fullwidth">
      <select name="country">
        <option value="Argentina">Argentina</option>
        <option value="Bolivia">Bolivia</option>
        <option value="Brazil">Brazil</option>
        <option value="Chile">Chile</option>
        <option value="Colombia">Colombia</option>
        <option value="Ecuador">Ecuador</option>
        <option value="Guyana">Guyana</option>
        <option value="Paraguay">Paraguay</option>
        <option value="Peru">Peru</option>
        <option value="Suriname">Suriname</option>
        <option value="Uruguay">Uruguay</option>
        <option value="Venezuela">Venezuela</option>
      </select>
    </div>
  </div>
  <div class="control">
    <button type="submit" class="button is-primary">Choose</button>
  </div>
</div>
```

你可以使用`has-addons-centered`修饰符或`has-addons-right`修饰符来改变对齐

```html
<div class="field has-addons has-addons-centered">
  <p class="control">
    <span class="select">
      <select>
        <option>$</option>
        <option>£</option>
        <option>€</option>
      </select>
    </span>
  </p>
  <p class="control">
    <input class="input" type="text" placeholder="Amount of money">
  </p>
  <p class="control">
    <a class="button is-primary">
      Transfer
    </a>
  </p>
</div>
```

```html
<div class="field has-addons has-addons-right">
  <p class="control">
    <span class="select">
      <select>
        <option>$</option>
        <option>£</option>
        <option>€</option>
      </select>
    </span>
  </p>
  <p class="control">
    <input class="input" type="text" placeholder="Amount of money">
  </p>
  <p class="control">
    <a class="button is-primary">
      Transfer
    </a>
  </p>
</div>
```

### 表单组

如果你想添加组控制器，可以在`field`容器上使用`is-grouped`修饰符

```html
<div class="field is-grouped">
  <p class="control">
    <a class="button is-primary">
      Submit
    </a>
  </p>
  <p class="control">
    <a class="button is-light">
      Cancel
    </a>
  </p>
</div>
```

你可以使用`is-grouped-centered`修饰符和`is-grouped-right`修饰符来改变对齐

```html
<div class="field is-grouped is-grouped-centered">
  <p class="control">
    <a class="button is-primary">
      Submit
    </a>
  </p>
  <p class="control">
    <a class="button is-light">
      Cancel
    </a>
  </p>
</div>
```

```html
<div class="field is-grouped is-grouped-right">
  <p class="control">
    <a class="button is-primary">
      Submit
    </a>
  </p>
  <p class="control">
    <a class="button is-light">
      Cancel
    </a>
  </p>
</div>
```

在你想要填充其剩余空间的元素上使用`is-expanded`修饰符

```html
<div class="field is-grouped">
  <p class="control is-expanded">
    <input class="input" type="text" placeholder="Find a repository">
  </p>
  <p class="control">
    <a class="button is-info">
      Search
    </a>
  </p>
</div>
```

如果你想要一个可换行的控件列表，你可以添加`is-grouped-multiline`修饰符以允许控件填充多行

```html
<div class="field is-grouped is-grouped-multiline">
  <p class="control">
    <a class="button">
      One
    </a>
  </p>
  <p class="control">
    <a class="button">
      Two
    </a>
  </p>
  <p class="control">
    <a class="button">
      Three
    </a>
  </p>
  <p class="control">
    <a class="button">
      Four
    </a>
  </p>
  <p class="control">
    <a class="button">
      Five
    </a>
  </p>
  <p class="control">
    <a class="button">
      Size
    </a>
  </p>
  <p class="control">
    <a class="button">
      Seven
    </a>
  </p>
  <p class="control">
    <a class="button">
      Eight
    </a>
  </p>
  <p class="control">
    <a class="button">
      Nine
    </a>
  </p>
  <p class="control">
    <a class="button">
      Ten
    </a>
  </p>
  <p class="control">
    <a class="button">
      Eleven
    </a>
  </p>
  <p class="control">
    <a class="button">
      Twelve
    </a>
  </p>
  <p class="control">
    <a class="button">
      Thirteen
    </a>
  </p>
</div>
```

如果您只需要按钮列表，请尝试使用新的`buttons`类创建多行按钮列表。

### 水平排列的表单

如果你想要一个水平排列的表单控件，你可以在`field`容器上使用`is-horizontal`修饰符，其中包括：

- 在侧边标签中，使用`field-label`
- 在`input`/`select`/`textarea`容器中，使用`field-body`

你还可以为子元素使用`is-grouped`或`has-addons`修饰符

![](https://todever-images.oss-cn-beijing.aliyuncs.com/201804021424.png)

```html
<div class="field is-horizontal">
  <div class="field-label is-normal">
    <label class="label">From</label>
  </div>
  <div class="field-body">
    <div class="field">
      <p class="control is-expanded has-icons-left">
        <input class="input" type="text" placeholder="Name">
        <span class="icon is-small is-left">
          <i class="fas fa-user"></i>
        </span>
      </p>
    </div>
    <div class="field">
      <p class="control is-expanded has-icons-left has-icons-right">
        <input class="input is-success" type="email" placeholder="Email" value="alex@smith.com">
        <span class="icon is-small is-left">
          <i class="fas fa-envelope"></i>
        </span>
        <span class="icon is-small is-right">
          <i class="fas fa-check"></i>
        </span>
      </p>
    </div>
  </div>
</div>

<div class="field is-horizontal">
  <div class="field-label"></div>
  <div class="field-body">
    <div class="field is-expanded">
      <div class="field has-addons">
        <p class="control">
          <a class="button is-static">
            +44
          </a>
        </p>
        <p class="control is-expanded">
          <input class="input" type="tel" placeholder="Your phone number">
        </p>
      </div>
      <p class="help">Do not enter the first zero</p>
    </div>
  </div>
</div>

<div class="field is-horizontal">
  <div class="field-label is-normal">
    <label class="label">Department</label>
  </div>
  <div class="field-body">
    <div class="field is-narrow">
      <div class="control">
        <div class="select is-fullwidth">
          <select>
            <option>Business development</option>
            <option>Marketing</option>
            <option>Sales</option>
          </select>
        </div>
      </div>
    </div>
  </div>
</div>

<div class="field is-horizontal">
  <div class="field-label">
    <label class="label">Already a member?</label>
  </div>
  <div class="field-body">
    <div class="field is-narrow">
      <div class="control">
        <label class="radio">
          <input type="radio" name="member">
          Yes
        </label>
        <label class="radio">
          <input type="radio" name="member">
          No
        </label>
      </div>
    </div>
  </div>
</div>

<div class="field is-horizontal">
  <div class="field-label is-normal">
    <label class="label">Subject</label>
  </div>
  <div class="field-body">
    <div class="field">
      <div class="control">
        <input class="input is-danger" type="text" placeholder="e.g. Partnership opportunity">
      </div>
      <p class="help is-danger">
        This field is required
      </p>
    </div>
  </div>
</div>

<div class="field is-horizontal">
  <div class="field-label is-normal">
    <label class="label">Question</label>
  </div>
  <div class="field-body">
    <div class="field">
      <div class="control">
        <textarea class="textarea" placeholder="Explain how we can help you"></textarea>
      </div>
    </div>
  </div>
</div>

<div class="field is-horizontal">
  <div class="field-label">
    <!-- Left empty for spacing -->
  </div>
  <div class="field-body">
    <div class="field">
      <div class="control">
        <button class="button is-primary">
          Send message
        </button>
      </div>
    </div>
  </div>
</div>
```

为了保持标签与每种控件类型和尺寸的垂直对齐，`.field`标签带有4种尺寸修改器：

- `.is-small`
- `.is-normal` for any `.input` or `.button`
- `.is-medium`
- `.is-large`

![](https://todever-images.oss-cn-beijing.aliyuncs.com/201804021427.png)

```html
<div class="field is-horizontal">
  <div class="field-label">
    <label class="label">No padding</label>
  </div>
  <div class="field-body">
    <div class="field">
      <div class="control">
        <label class="checkbox">
          <input type="checkbox">
          Checkbox
        </label>
      </div>
    </div>
  </div>
</div>

<div class="field is-horizontal">
  <div class="field-label is-small">
    <label class="label">Small padding</label>
  </div>
  <div class="field-body">
    <div class="field">
      <div class="control">
        <input class="input is-small" type="text" placeholder="Small sized input">
      </div>
    </div>
  </div>
</div>

<div class="field is-horizontal">
  <div class="field-label is-normal">
    <label class="label">Normal label</label>
  </div>
  <div class="field-body">
    <div class="field">
      <div class="control">
        <input class="input" type="text" placeholder="Normal sized input">
      </div>
    </div>
  </div>
</div>

<div class="field is-horizontal">
  <div class="field-label is-medium">
    <label class="label">Medium label</label>
  </div>
  <div class="field-body">
    <div class="field">
      <div class="control">
        <input class="input is-medium" type="text" placeholder="Medium sized input">
      </div>
    </div>
  </div>
</div>

<div class="field is-horizontal">
  <div class="field-label is-large">
    <label class="label">Large label</label>
  </div>
  <div class="field-body">
    <div class="field">
      <div class="control">
        <input class="input is-large" type="text" placeholder="Large sized input">
      </div>
    </div>
  </div>
</div>
```

### 变量

表单元素可以使用以下通用变量进行自定义。

| Name | Default value |
| ---- | ------------- |
| `$control-radius` |	`$radius` |
| `$control-radius-small` |	`$radius-small` |
| `$control-padding-vertical` |	`calc(0.375em - 1px)` |
| `$control-padding-horizontal` |	`calc(0.625em - 1px)` |
| `$label-color` |	`$grey-darker` |
| `$label-weight` |	`$weight-bold` |
| `$help-size` |	`$size-small` |

## 输入框

文本输入框支持一下修饰符：

- `color`
- `size`
- `state`

支持以下类型属性：

- `type="text"`
- `type="password"`
- `type="email"`
- `type="tel"`

```html
<input class="input" type="text" placeholder="Text input">
```

### 颜色

```html
<div class="field">
  <div class="control">
    <input class="input is-primary" type="text" placeholder="Primary input">
  </div>
</div>
<div class="field">
  <div class="control">
    <input class="input is-info" type="text" placeholder="Info input">
  </div>
</div>
<div class="field">
  <div class="control">
    <input class="input is-success" type="text" placeholder="Success input">
  </div>
</div>
<div class="field">
  <div class="control">
    <input class="input is-warning" type="text" placeholder="Warning input">
  </div>
</div>
<div class="field">
  <div class="control">
    <input class="input is-danger" type="text" placeholder="Danger input">
  </div>
</div>
```

### 尺寸大小

```html
<div class="field">
  <div class="control">
    <input class="input is-small" type="text" placeholder="Small input">
  </div>
</div>
<div class="field">
  <div class="control">
    <input class="input" type="text" placeholder="Normal input">
  </div>
</div>
<div class="field">
  <div class="control">
    <input class="input is-medium" type="text" placeholder="Medium input">
  </div>
</div>
<div class="field">
  <div class="control">
    <input class="input is-large" type="text" placeholder="Large input">
  </div>
</div>
```

### 样式

在0.6.2版本中，支持新的圆角input

```html
<input class="input is-rounded" type="text" placeholder="Rounded input">
```

### 状态

Normal：

```html
<div class="control">
  <input class="input" type="text" placeholder="Normal input">
</div>
```

Hover:

```html
<div class="control">
  <input class="input is-hovered" type="text" placeholder="Hovered input">
</div>
```

Focus:

```html
<div class="control">
  <input class="input is-focused" type="text" placeholder="Focused input">
</div>
```

Loading:

```html
<div class="control is-loading">
  <input class="input" type="text" placeholder="Loading input">
</div>
```

您可以通过在控制容器中添加`is-small`，`is-medium`或`is-large`来调整加载微调器的大小。

```html
<div class="field">
  <div class="control is-small is-loading">
    <input class="input is-small" type="text" placeholder="Small loading input">
  </div>
</div>
<div class="field">
  <div class="control is-loading">
    <input class="input" type="text" placeholder="Normal loading input">
  </div>
</div>
<div class="field">
  <div class="control is-medium is-loading">
    <input class="input is-medium" type="text" placeholder="Medium loading input">
  </div>
</div>
<div class="field">
  <div class="control is-large is-loading">
    <input class="input is-large" type="text" placeholder="Large loading input">
  </div>
</div>
```

Disabled:

```html
<div class="control">
  <input class="input" type="text" placeholder="Disabled input" disabled>
</div>
```

如果你使用`onlyread`属性，输入框看起来类似于正常的输入，但不可编辑且没有阴影

```html
<div class="control">
  <input class="input" type="text" value="This text is readonly" readonly>
</div>
```

如果您还附加了`is-static`修饰符，它将移除背景，边框，阴影和水平填充，同时保持垂直间距，以便您可以在任何上下文中轻松对齐输入，如水平表单。

```html
<div class="field is-horizontal">
  <div class="field-label is-normal">
    <label class="label">From</label>
  </div>
  <div class="field-body">
    <div class="field">
      <p class="control">
        <input class="input is-static" type="email" value="me@example.com" readonly>
      </p>
    </div>
  </div>
</div>

<div class="field is-horizontal">
  <div class="field-label is-normal">
    <label class="label">To</label>
  </div>
  <div class="field-body">
    <div class="field">
      <p class="control">
        <input class="input" type="email" placeholder="Recipient email">
      </p>
    </div>
  </div>
</div>
```

### 添加Font Awesome图标

你可以在控件上追加下面2个修饰符中的一个：

- `has-icons-left`
- `has-icons-right`

同时你还需要在图标上添加修饰符：

- 如果上面添加的是`has-icons-left`,则添加`icon is-left`
- 如果上面添加的是`has-icons-right`,则添加`icon is-right`

输入框的大小将决定图标容器的大小。

```html
<div class="field">
  <p class="control has-icons-left has-icons-right">
    <input class="input" type="email" placeholder="Email">
    <span class="icon is-small is-left">
      <i class="fas fa-envelope"></i>
    </span>
    <span class="icon is-small is-right">
      <i class="fas fa-check"></i>
    </span>
  </p>
</div>
<div class="field">
  <p class="control has-icons-left">
    <input class="input" type="password" placeholder="Password">
    <span class="icon is-small is-left">
      <i class="fas fa-lock"></i>
    </span>
  </p>
</div>
```

如果控件中包含图标，Bulma将确保图标是居中的，而不管输入框或图标的大小

```html
<div class="control has-icons-left has-icons-right">
  <input class="input is-small" type="email" placeholder="Email">
  <span class="icon is-small is-left">
    <i class="fas fa-envelope"></i>
  </span>
  <span class="icon is-small is-right">
    <i class="fas fa-check"></i>
  </span>
</div>
```

```html
<div class="control has-icons-left has-icons-right">
  <input class="input" type="email" placeholder="Email">
  <span class="icon is-small is-left">
    <i class="fas fa-envelope"></i>
  </span>
  <span class="icon is-small is-right">
    <i class="fas fa-check"></i>
  </span>
</div>
```

```html
<div class="control has-icons-left has-icons-right">
  <input class="input is-medium" type="email" placeholder="Email">
  <span class="icon is-left">
    <i class="fas fa-envelope"></i>
  </span>
  <span class="icon is-right">
    <i class="fas fa-check"></i>
  </span>
</div>
```

```html
<div class="control has-icons-left has-icons-right">
  <input class="input is-large" type="email" placeholder="Email">
  <span class="icon is-medium is-left">
    <i class="fas fa-envelope"></i>
  </span>
  <span class="icon is-medium is-right">
    <i class="fas fa-check"></i>
  </span>
</div>
```

### 变量

你可以使用下面的变量来自定义元素样式

| Name | Default value |
| ---- | ------------- |
| `$input-color` |	`$grey-darker` |
| `$input-background-color` |	`$white` |
| `$input-border-color` |	`$grey-lighter` |
| `$input-shadow` |	`inset 0 1px 2px rgba($black, 0.1)` |
| `$input-hover-color` |	`$grey-darker` |
| `$input-hover-border-color` |	`$grey-light` |
| `$input-focus-color` |	`$grey-darker` |
| `$input-focus-border-color` |	`$link` |
| `$input-focus-box-shadow-size` |	`0 0 0 0.125em` |
| `$input-focus-box-shadow-color` |	`rgba($link, 0.25)` |
| `$input-disabled-color` |	`$text-light` |
| `$input-disabled-background-color` |	`$background` |
| `$input-disabled-border-color` |	`$background` |
| `$input-arrow` |	`$link` |
| `$input-icon-color` |	`$grey-lighter` |
| `$input-icon-active-color` |	`$grey` |
| `$input-radius` |	`$radius` |

## 多行文本框

多行文本框有颜色和尺寸大小的属性，但没有变量控制

```html
<textarea class="textarea" placeholder="e.g. Hello world"></textarea>
```

你可以使用`rows`属性来设置textarea的高度

```html
<textarea class="textarea" placeholder="10 lines of textarea" rows="10"></textarea>
```

### 颜色

```html
<div class="field">
  <div class="control">
    <textarea class="textarea is-primary" type="text" placeholder="Primary textarea"></textarea>
  </div>
</div>
<div class="field">
  <div class="control">
    <textarea class="textarea is-info" type="text" placeholder="Info textarea"></textarea>
  </div>
</div>
<div class="field">
  <div class="control">
    <textarea class="textarea is-success" type="text" placeholder="Success textarea"></textarea>
  </div>
</div>
<div class="field">
  <div class="control">
    <textarea class="textarea is-warning" type="text" placeholder="Warning textarea"></textarea>
  </div>
</div>
<div class="field">
  <div class="control">
    <textarea class="textarea is-danger" type="text" placeholder="Danger textarea"></textarea>
  </div>
</div>
```

### 尺寸大小

```html
<div class="field">
  <div class="control">
    <textarea class="textarea is-small" type="text" placeholder="Small textarea"></textarea>
  </div>
</div>
<div class="field">
  <div class="control">
    <textarea class="textarea" type="text" placeholder="Normal textarea"></textarea>
  </div>
</div>
<div class="field">
  <div class="control">
    <textarea class="textarea is-medium" type="text" placeholder="Medium textarea"></textarea>
  </div>
</div>
<div class="field">
  <div class="control">
    <textarea class="textarea is-large" type="text" placeholder="Large textarea"></textarea>
  </div>
</div>
```

### 状态

Normal：

```html
<div class="control">
  <textarea class="textarea" type="text" placeholder="Normal textarea"></textarea>
</div>
```

Hover:

```html
<div class="control">
  <textarea class="textarea is-hovered" type="text" placeholder="Hovered textarea"></textarea>
</div>
```

Focus：

```html
<div class="control">
  <textarea class="textarea is-focused" type="text" placeholder="Focused textarea"></textarea>
</div>
```

Loading:

```html
<div class="control is-loading">
  <textarea class="textarea" type="text" placeholder="Loading textarea"></textarea>
</div>
```

您可以通过在控制容器中添加`is-small`，`is-medium`或`is-large`来调整加载微调器的大小。

```html
<div class="field">
  <div class="control is-small is-loading">
    <textarea class="textarea is-small" type="text" placeholder="Small loading textarea"></textarea>
  </div>
</div>
<div class="field">
  <div class="control is-loading">
    <textarea class="textarea" type="text" placeholder="Normal loading textarea"></textarea>
  </div>
</div>
<div class="field">
  <div class="control is-medium is-loading">
    <textarea class="textarea is-medium" type="text" placeholder="Medium loading textarea"></textarea>
  </div>
</div>
<div class="field">
  <div class="control is-large is-loading">
    <textarea class="textarea is-large" type="text" placeholder="Large loading textarea"></textarea>
  </div>
</div>
```

Disabled:

```html
<div class="control">
  <textarea class="textarea" type="text" placeholder="Disabled textarea" disabled></textarea>
</div>
```

Readonly:

如果你使用了`readonly`只读属性，textarea看起来跟正常的类似，但不可编辑且没有阴影

```html
<div class="control">
  <textarea class="textarea" type="text" readonly>This content is readonly</textarea>
</div>
```

## 选择框

下拉选择框是浏览器内置的功能，它支持以下修饰符：

- color
- size
- state

```html
<div class="select">
  <select>
    <option>Select dropdown</option>
    <option>With options</option>
  </select>
</div>
```

您可以通过使用`is-multiple`修饰符以及使用多个HTML属性来设置多选下拉列表的样式。

```html
<div class="select is-multiple">
  <select multiple size="8">
    <option value="Argentina">Argentina</option>
    <option value="Bolivia">Bolivia</option>
    <option value="Brazil">Brazil</option>
    <option value="Chile">Chile</option>
    <option value="Colombia">Colombia</option>
    <option value="Ecuador">Ecuador</option>
    <option value="Guyana">Guyana</option>
    <option value="Paraguay">Paraguay</option>
    <option value="Peru">Peru</option>
    <option value="Suriname">Suriname</option>
    <option value="Uruguay">Uruguay</option>
    <option value="Venezuela">Venezuela</option>
  </select>
</div>
```

### 颜色

```html
<div class="field">
  <div class="control">
    <div class="select is-primary">
      <select>
        <option>Select dropdown</option>
        <option>With options</option>
      </select>
    </div>
  </div>
</div>
<div class="field">
  <div class="control">
    <div class="select is-info">
      <select>
        <option>Select dropdown</option>
        <option>With options</option>
      </select>
    </div>
  </div>
</div>
<div class="field">
  <div class="control">
    <div class="select is-success">
      <select>
        <option>Select dropdown</option>
        <option>With options</option>
      </select>
    </div>
  </div>
</div>
<div class="field">
  <div class="control">
    <div class="select is-warning">
      <select>
        <option>Select dropdown</option>
        <option>With options</option>
      </select>
    </div>
  </div>
</div>
<div class="field">
  <div class="control">
    <div class="select is-danger">
      <select>
        <option>Select dropdown</option>
        <option>With options</option>
      </select>
    </div>
  </div>
</div>
```

### 样式

在0.6.2版本中，支持圆角下拉框

```html
<div class="select is-rounded">
  <select>
    <option>Rounded dropdown</option>
    <option>With options</option>
  </select>
</div>
```

### 尺寸大小

```html
<div class="field">
  <div class="control">
    <div class="select is-small">
      <select>
        <option>Select dropdown</option>
        <option>With options</option>
      </select>
    </div>
  </div>
</div>
<div class="field">
  <div class="control">
    <div class="select">
      <select>
        <option>Select dropdown</option>
        <option>With options</option>
      </select>
    </div>
  </div>
</div>
<div class="field">
  <div class="control">
    <div class="select is-medium">
      <select>
        <option>Select dropdown</option>
        <option>With options</option>
      </select>
    </div>
  </div>
</div>
<div class="field">
  <div class="control">
    <div class="select is-large">
      <select>
        <option>Select dropdown</option>
        <option>With options</option>
      </select>
    </div>
  </div>
</div>
```

### 状态

States:

```html
<div class="control">
  <div class="select">
    <select>
      <option>Select dropdown</option>
      <option>With options</option>
    </select>
  </div>
</div>
```

Hover:

```html
<div class="control">
  <div class="select">
    <select class="is-hovered">
      <option>Select dropdown</option>
      <option>With options</option>
    </select>
  </div>
</div>
```

Focus:

```html
<div class="control">
  <div class="select">
    <select class="is-focused">
      <option>Select dropdown</option>
      <option>With options</option>
    </select>
  </div>
</div>
```

Loading:

```html
<div class="control">
  <div class="select is-loading">
    <select>
      <option>Select dropdown</option>
      <option>With options</option>
    </select>
  </div>
</div>
```

### 添加图标

你可以在控件上添加下面的修饰符：

- `has-icons-left`

你还需要再图标上添加修饰符：

- `icon is-left`

下拉选择框的大小决定图标的大小

```html
<div class="field">
  <div class="control has-icons-left">
    <div class="select">
      <select>
        <option selected>Country</option>
        <option>Select dropdown</option>
        <option>With options</option>
      </select>
    </div>
    <div class="icon is-small is-left">
      <i class="fas fa-globe"></i>
    </div>
  </div>
</div>
```

如果控件中包含图标，Bulma将确保图标是居中显示的，而不管下拉框或图标的大小

```html
<div class="control has-icons-left">
  <div class="select is-small">
    <select>
      <option selected>Country</option>
      <option>Select dropdown</option>
      <option>With options</option>
    </select>
  </div>
  <span class="icon is-small is-left">
    <i class="fas fa-globe"></i>
  </span>
</div>
```

```html
<div class="control has-icons-left">
  <div class="select">
    <select>
      <option selected>Country</option>
      <option>Select dropdown</option>
      <option>With options</option>
    </select>
  </div>
  <span class="icon is-left">
    <i class="fas fa-globe"></i>
  </span>
</div>
```

```html
<div class="control has-icons-left">
  <div class="select is-medium">
    <select>
      <option selected>Country</option>
      <option>Select dropdown</option>
      <option>With options</option>
    </select>
  </div>
  <span class="icon is-medium is-left">
    <i class="fas fa-globe"></i>
  </span>
</div>
```

```html
<div class="control has-icons-left">
  <div class="select is-large">
    <select>
      <option selected>Country</option>
      <option>Select dropdown</option>
      <option>With options</option>
    </select>
  </div>
  <span class="icon is-large is-left">
    <i class="fas fa-globe"></i>
  </span>
</div>
```

## 复选框

Bulma中的复选框类是：`<input type="checkbox">`，它没有风格，以保持跨浏览器兼容性和用户体验.

```html
<label class="checkbox">
  <input type="checkbox">
  Remember me
</label>
```

您可以添加链接到您的复选框，甚至禁用它。

```html
<label class="checkbox">
  <input type="checkbox">
  I agree to the <a href="#">terms and conditions</a>
</label>

<label class="checkbox" disabled>
  <input type="checkbox" disabled>
  Save my preferences
</label>
```

## 单选框

Bulma中的单选框类是：`<input type="radio">`，它没有风格，以保持跨浏览器兼容性和用户体验。确保链接单选按钮的名称HTML属性具有相同的值。

```html
<div class="control">
  <label class="radio">
    <input type="radio" name="answer">
    Yes
  </label>
  <label class="radio">
    <input type="radio" name="answer">
    No
  </label>
</div>
```

默认情况下，您可以通过`checked`属性来确定那一个是你需要的默认值

```html
<div class="control">
  <label class="radio">
    <input type="radio" name="foobar">
    Foo
  </label>
  <label class="radio">
    <input type="radio" name="foobar" checked>
    Bar
  </label>
</div>
```

您可以通过将禁用的HTML属性添加到`<label>`和`<input>`来添加禁用单选按钮。

```html
<div class="control">
  <label class="radio">
    <input type="radio" name="rsvp">
    Going
  </label>
  <label class="radio">
    <input type="radio" name="rsvp">
    Not going
  </label>
  <label class="radio" disabled>
    <input type="radio" name="rsvp" disabled>
    Maybe
  </label>
</div>
```

## 文件上传

在Bulma中，你可以自定义文件上传，无需JavaScript

`.file`元素是一个包装`<input type =“file”>`的简单交互式标签。 它包含几个子元素：

<ul>
  <li>
    <code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding:0.25em 0.5em 0.25em;-webkit-font-smoothing:auto;font-family:monospace;">.file</code><span style="margin-left:10px">主容器</span>
      <ul style="list-style-type:circle;list-style:disc outside;">
        <li>
          <code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding:0.25em 0.5em 0.25em;-webkit-font-smoothing:auto;font-family:monospace;">.file-label
          </code><span style="margin-left:10px">元素的实际交互式和可点击部分</span>
            <ul style="list-style-type:square;list-style:disc outside;">
              <li>
                <code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding:0.25em 0.5em 0.25em;-webkit-font-smoothing:auto;font-family:monospace;">.file-input
                </code><span style="margin-left:10px">原生文件输入，隐藏用于样式目的</span>
              </li>
              <li>
                <code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding:0.25em 0.5em 0.25em;-webkit-font-smoothing:auto;font-family:monospace;">.file-cta
                </code><span style="margin-left:10px">点击触发文件上传区域</span>
                <ul style="list-style-type:square;list-style:disc outside;">
                  <li>
                    <code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding:0.25em 0.5em 0.25em;-webkit-font-smoothing:auto;font-family:monospace;">.file-icon
                    </code><span style="margin-left:10px">一个可选的上传图标</span>
                  </li>
                  <li>
                    <code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding:0.25em 0.5em 0.25em;-webkit-font-smoothing:auto;font-family:monospace;">.file-label
                    </code><span style="margin-left:10px">显示上传的文本</span>
                  </li>
                </ul>
              </li>
              <li>
                <code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding:0.25em 0.5em 0.25em;-webkit-font-smoothing:auto;font-family:monospace;">.file-name
                </code><span style="margin-left:10px">容器的文件名</span>
              </li>
            </ul>
        </li>
      </ul>
  </li>
</ul>

```html
<div class="file">
  <label class="file-label">
    <input class="file-input" type="file" name="resume">
    <span class="file-cta">
      <span class="file-icon">
        <i class="fas fa-upload"></i>
      </span>
      <span class="file-label">
        Choose a file…
      </span>
    </span>
  </label>
</div>
```

### 修饰符

通过将`.has-name`修饰符与`.file-name`元素结合使用，可以为选定的文件名添加占位符。

```html
<div class="file has-name">
  <label class="file-label">
    <input class="file-input" type="file" name="resume">
    <span class="file-cta">
      <span class="file-icon">
        <i class="fas fa-upload"></i>
      </span>
      <span class="file-label">
        Choose a file…
      </span>
    </span>
    <span class="file-name">
      Screen Shot 2017-07-29 at 15.54.25.png
    </span>
  </label>
</div>
```

您可以使用`.is-right`修改符将上传窗体移动到右侧。

```html
<div class="file has-name is-right">
  <label class="file-label">
    <input class="file-input" type="file" name="resume">
    <span class="file-cta">
      <span class="file-icon">
        <i class="fas fa-upload"></i>
      </span>
      <span class="file-label">
        Choose a file…
      </span>
    </span>
    <span class="file-name">
      Screen Shot 2017-07-29 at 15.54.25.png
    </span>
  </label>
</div>
```

您还可以使用`.is-fullwidth`修改器扩展名称以填充空间

```html
<div class="file has-name is-fullwidth">
  <label class="file-label">
    <input class="file-input" type="file" name="resume">
    <span class="file-cta">
      <span class="file-icon">
        <i class="fas fa-upload"></i>
      </span>
      <span class="file-label">
        Choose a file…
      </span>
    </span>
    <span class="file-name">
      Screen Shot 2017-07-29 at 15.54.25.png
    </span>
  </label>
</div>
```

您可以使用`.is-boxed`修饰符来装入一个块状的上传区域

```html
<div class="file is-boxed">
  <label class="file-label">
    <input class="file-input" type="file" name="resume">
    <span class="file-cta">
      <span class="file-icon">
        <i class="fas fa-upload"></i>
      </span>
      <span class="file-label">
        Choose a file…
      </span>
    </span>
  </label>
</div>
```

你可以结合`.has-name`和`.is-boxed`。

```html
<div class="file has-name is-boxed">
  <label class="file-label">
    <input class="file-input" type="file" name="resume">
    <span class="file-cta">
      <span class="file-icon">
        <i class="fas fa-upload"></i>
      </span>
      <span class="file-label">
        Choose a file…
      </span>
    </span>
    <span class="file-name">
      Screen Shot 2017-07-29 at 15.54.25.png
    </span>
  </label>
</div>`
```

### 颜色

您可以通过追加10个颜色修改器中的一个来设置文件元素的样式：

- `is-white`
- `is-black`
- `is-light`
- `is-dark`
- `is-primary`
- `is-link`
- `is-info`
- `is-success`
- `is-warning`
- `is-danger`

```html
<div class="field">
  <div class="file is-primary">
    <label class="file-label">
      <input class="file-input" type="file" name="resume">
      <span class="file-cta">
        <span class="file-icon">
          <i class="fas fa-upload"></i>
        </span>
        <span class="file-label">
          Primary file…
        </span>
      </span>
    </label>
  </div>
</div>

<div class="field">
  <div class="file is-info has-name">
    <label class="file-label">
      <input class="file-input" type="file" name="resume">
      <span class="file-cta">
        <span class="file-icon">
          <i class="fas fa-upload"></i>
        </span>
        <span class="file-label">
          Info file…
        </span>
      </span>
      <span class="file-name">
        Screen Shot 2017-07-29 at 15.54.25.png
      </span>
    </label>
  </div>
</div>

<div class="field">
  <div class="file is-warning is-boxed">
    <label class="file-label">
      <input class="file-input" type="file" name="resume">
      <span class="file-cta">
        <span class="file-icon">
          <i class="fas fa-cloud-upload-alt"></i>
        </span>
        <span class="file-label">
          Warning file…
        </span>
      </span>
    </label>
  </div>
</div>

<div class="field">
  <div class="file is-danger has-name is-boxed">
    <label class="file-label">
      <input class="file-input" type="file" name="resume">
      <span class="file-cta">
        <span class="file-icon">
          <i class="fas fa-cloud-upload-alt"></i>
        </span>
        <span class="file-label">
          Danger file…
        </span>
      </span>
      <span class="file-name">
        Screen Shot 2017-07-29 at 15.54.25.png
      </span>
    </label>
  </div>
</div>
```

### 尺寸大小

你可以添加以下三种尺寸：

- `.is-small`
- `.is-medium`
- `.is-large`

```html
<div class="field">
  <div class="file is-small">
    <label class="file-label">
      <input class="file-input" type="file" name="resume">
      <span class="file-cta">
        <span class="file-icon">
          <i class="fas fa-upload"></i>
        </span>
        <span class="file-label">
          Small file…
        </span>
      </span>
    </label>
  </div>
</div>

<div class="field">
  <div class="file">
    <label class="file-label">
      <input class="file-input" type="file" name="resume">
      <span class="file-cta">
        <span class="file-icon">
          <i class="fas fa-upload"></i>
        </span>
        <span class="file-label">
          Normal file…
        </span>
      </span>
    </label>
  </div>
</div>

<div class="field">
  <div class="file is-medium">
    <label class="file-label">
      <input class="file-input" type="file" name="resume">
      <span class="file-cta">
        <span class="file-icon">
          <i class="fas fa-upload"></i>
        </span>
        <span class="file-label">
          Medium file…
        </span>
      </span>
    </label>
  </div>
</div>

<div class="field">
  <div class="file is-large">
    <label class="file-label">
      <input class="file-input" type="file" name="resume">
      <span class="file-cta">
        <span class="file-icon">
          <i class="fas fa-upload"></i>
        </span>
        <span class="file-label">
          Large file…
        </span>
      </span>
    </label>
  </div>
</div>
```

```html
<div class="field">
  <div class="file is-small has-name">
    <label class="file-label">
      <input class="file-input" type="file" name="resume">
      <span class="file-cta">
        <span class="file-icon">
          <i class="fas fa-upload"></i>
        </span>
        <span class="file-label">
          Small file…
        </span>
      </span>
      <span class="file-name">
        Screen Shot 2017-07-29 at 15.54.25.png
      </span>
    </label>
  </div>
</div>

<div class="field">
  <div class="file has-name">
    <label class="file-label">
      <input class="file-input" type="file" name="resume">
      <span class="file-cta">
        <span class="file-icon">
          <i class="fas fa-upload"></i>
        </span>
        <span class="file-label">
          Normal file…
        </span>
      </span>
      <span class="file-name">
        Screen Shot 2017-07-29 at 15.54.25.png
      </span>
    </label>
  </div>
</div>

<div class="field">
  <div class="file is-medium has-name">
    <label class="file-label">
      <input class="file-input" type="file" name="resume">
      <span class="file-cta">
        <span class="file-icon">
          <i class="fas fa-upload"></i>
        </span>
        <span class="file-label">
          Medium file…
        </span>
      </span>
      <span class="file-name">
        Screen Shot 2017-07-29 at 15.54.25.png
      </span>
    </label>
  </div>
</div>

<div class="field">
  <div class="file is-large has-name">
    <label class="file-label">
      <input class="file-input" type="file" name="resume">
      <span class="file-cta">
        <span class="file-icon">
          <i class="fas fa-upload"></i>
        </span>
        <span class="file-label">
          Large file…
        </span>
      </span>
      <span class="file-name">
        Screen Shot 2017-07-29 at 15.54.25.png
      </span>
    </label>
  </div>
</div>
```

```html
<div class="field">
  <div class="file is-small is-boxed">
    <label class="file-label">
      <input class="file-input" type="file" name="resume">
      <span class="file-cta">
        <span class="file-icon">
          <i class="fas fa-upload"></i>
        </span>
        <span class="file-label">
          Small file…
        </span>
      </span>
    </label>
  </div>
</div>

<div class="field">
  <div class="file is-boxed">
    <label class="file-label">
      <input class="file-input" type="file" name="resume">
      <span class="file-cta">
        <span class="file-icon">
          <i class="fas fa-upload"></i>
        </span>
        <span class="file-label">
          Normal file…
        </span>
      </span>
    </label>
  </div>
</div>

<div class="field">
  <div class="file is-medium is-boxed">
    <label class="file-label">
      <input class="file-input" type="file" name="resume">
      <span class="file-cta">
        <span class="file-icon">
          <i class="fas fa-upload"></i>
        </span>
        <span class="file-label">
          Medium file…
        </span>
      </span>
    </label>
  </div>
</div>

<div class="field">
  <div class="file is-large is-boxed">
    <label class="file-label">
      <input class="file-input" type="file" name="resume">
      <span class="file-cta">
        <span class="file-icon">
          <i class="fas fa-upload"></i>
        </span>
        <span class="file-label">
          Large file…
        </span>
      </span>
    </label>
  </div>
</div>
```

```html
<div class="field">
  <div class="file is-small is-boxed has-name">
    <label class="file-label">
      <input class="file-input" type="file" name="resume">
      <span class="file-cta">
        <span class="file-icon">
          <i class="fas fa-upload"></i>
        </span>
        <span class="file-label">
          Small file…
        </span>
      </span>
      <span class="file-name">
        Screen Shot 2017-07-29 at 15.54.25.png
      </span>
    </label>
  </div>
</div>

<div class="field">
  <div class="file is-boxed has-name">
    <label class="file-label">
      <input class="file-input" type="file" name="resume">
      <span class="file-cta">
        <span class="file-icon">
          <i class="fas fa-upload"></i>
        </span>
        <span class="file-label">
          Normal file…
        </span>
      </span>
      <span class="file-name">
        Screen Shot 2017-07-29 at 15.54.25.png
      </span>
    </label>
  </div>
</div>

<div class="field">
  <div class="file is-medium is-boxed has-name">
    <label class="file-label">
      <input class="file-input" type="file" name="resume">
      <span class="file-cta">
        <span class="file-icon">
          <i class="fas fa-upload"></i>
        </span>
        <span class="file-label">
          Medium file…
        </span>
      </span>
      <span class="file-name">
        Screen Shot 2017-07-29 at 15.54.25.png
      </span>
    </label>
  </div>
</div>

<div class="field">
  <div class="file is-large is-boxed has-name">
    <label class="file-label">
      <input class="file-input" type="file" name="resume">
      <span class="file-cta">
        <span class="file-icon">
          <i class="fas fa-upload"></i>
        </span>
        <span class="file-label">
          Large file…
        </span>
      </span>
      <span class="file-name">
        Screen Shot 2017-07-29 at 15.54.25.png
      </span>
    </label>
  </div>
</div>
```

### 对齐

你可以调整上传区域的对齐效果

- 使用`is-centered`修饰符使上传居中
- 使用`is-right`修饰符的上传具右

```html
<div class="field">
  <div class="file is-centered is-boxed is-success has-name">
    <label class="file-label">
      <input class="file-input" type="file" name="resume">
      <span class="file-cta">
        <span class="file-icon">
          <i class="fas fa-upload"></i>
        </span>
        <span class="file-label">
          Centered file…
        </span>
      </span>
      <span class="file-name">
        Screen Shot 2017-07-29 at 15.54.25.png
      </span>
    </label>
  </div>
</div>
```

```html
<div class="field">
  <div class="file is-right is-info">
    <label class="file-label">
      <input class="file-input" type="file" name="resume">
      <span class="file-cta">
        <span class="file-icon">
          <i class="fas fa-upload"></i>
        </span>
        <span class="file-label">
          Right file…
        </span>
      </span>
      <span class="file-name">
        Screen Shot 2017-07-29 at 15.54.25.png
      </span>
    </label>
  </div>
</div>
```

### 变量

你可以使用下面的变量来自定义上传

| Name | Default value |
| ---- | ------------- |
| `$file-border-color` |	`$border` |
| `$file-radius` |	`$radius` |
| `$file-cta-background-color` |	`$white-ter` |
| `$file-cta-color` |	`$grey-dark` |
| `$file-cta-hover-color` |	`$grey-darker` |
| `$file-cta-active-color` |	`$grey-darker` |
| `$file-name-border-color` |	`$border` |
| `$file-name-border-style` |	`solid` |
| `$file-name-border-width` |	`1px 1px 1px 0` |
| `$file-name-max-width` |	`16em` |

# 元素

## 盒子

Box是一个可以包含其他元素的白色区块。

带有`.box`类的元素是一个带有阴影、边框、半径和一些填充的容器，例如，你可以在里面包含媒体对象：

```html
<div class="box">
  <article class="media">
    <div class="media-left">
      <figure class="image is-64x64">
        <img src="https://bulma.io/images/placeholders/128x128.png" alt="Image">
      </figure>
    </div>
    <div class="media-content">
      <div class="content">
        <p>
          <strong>John Smith</strong> <small>@johnsmith</small> <small>31m</small>
          <br>
          Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aenean efficitur sit amet massa fringilla egestas. Nullam condimentum luctus turpis.
        </p>
      </div>
      <nav class="level is-mobile">
        <div class="level-left">
          <a class="level-item">
            <span class="icon is-small"><i class="fas fa-reply"></i></span>
          </a>
          <a class="level-item">
            <span class="icon is-small"><i class="fas fa-retweet"></i></span>
          </a>
          <a class="level-item">
            <span class="icon is-small"><i class="fas fa-heart"></i></span>
          </a>
        </div>
      </nav>
    </div>
  </article>
</div>
```

### 变量

你可以使用下面这些变量来自定义此元素，在导入Bulma之前，你只需设置一个或多个这些变量的值

| Name | Default value |
| ---- | ------------- |
| `$box-color` | `$text` |
| `$box-background-color` | `$white` |
| `$box-radius` | `$radius-large` |
| `$box-shadow` | `0 2px 3px rgba($black, 0.1), 0 0 0 1px rgba($black, 0.1)` |
| `$box-padding` | `1.25rem` |
| `$box-link-hover-shadow` | `0 2px 3px rgba($black, 0.1), 0 0 0 1px $link` |
| `$box-link-active-shadow` | `inset 0 1px 2px rgba($black, 0.2), 0 0 0 1px $link` |

## 按钮

在Bulma中，按钮元素可以设置不同的颜色、尺寸和状态

按钮在所有的UI设计中都是非常重要的元素，它提供了用户与网页之间的互动

```html
<a class="button">Button</a>
```

`.button`类可用于下面的元素中：

- `<a>` 锚链接
- `<button>` 表单按钮
- `<input type="submit">` 提交输入
- `<input type="reset">` 重置输入

```html
<a class="button">Anchor</a>
<button class="button">Button</button>
<input class="button" type="submit" value="Submit input">
<input class="button" type="reset" value="Reset input">
```

### 颜色

```html
<a class="button is-white">White</a>
<a class="button is-light">Light</a>
<a class="button is-dark">Dark</a>
<a class="button is-black">Black</a>
<a class="button is-text">Text</a>
```

```html
<a class="button is-primary">Primary</a>
<a class="button is-link">Link</a>
<a class="button is-info">Info</a>
<a class="button is-success">Success</a>
<a class="button is-warning">Warning</a>
<a class="button is-danger">Danger</a>
```

### 尺寸大小

```html
<a class="button is-small">Small</a>
<a class="button">Normal</a>
<a class="button is-medium">Medium</a>
<a class="button is-large">Large</a>
```

### 样式

Outlined:

```html
<a class="button is-outlined">Outlined</a>
<a class="button is-primary is-outlined">Outlined</a>
<a class="button is-link is-outlined">Outlined</a>
<a class="button is-info is-outlined">Outlined</a>
<a class="button is-success is-outlined">Outlined</a>
<a class="button is-danger is-outlined">Outlined</a>
```

Inverted:

```html
<a class="button is-primary is-inverted">Inverted</a>
<a class="button is-link is-inverted">Inverted</a>
<a class="button is-info is-inverted">Inverted</a>
<a class="button is-success is-inverted">Inverted</a>
<a class="button is-danger is-inverted">Inverted</a>
```

Invert Outlined:

```html
<a class="button is-primary is-inverted is-outlined">Invert Outlined</a>
<a class="button is-link is-inverted is-outlined">Invert Outlined</a>
<a class="button is-info is-inverted is-outlined">Invert Outlined</a>
<a class="button is-success is-inverted is-outlined">Invert Outlined</a>
<a class="button is-danger is-inverted is-outlined">Invert Outlined</a>
```

Rounded buttons:

```html
<a class="button is-rounded">Rounded</a>
<a class="button is-primary is-rounded">Rounded</a>
<a class="button is-link is-rounded">Rounded</a>
<a class="button is-info is-rounded">Rounded</a>
<a class="button is-success is-rounded">Rounded</a>
<a class="button is-danger is-rounded">Rounded</a>
```

### 状态

Normal:

```html
<a class="button">Normal</a>
<a class="button is-primary">Normal</a>
<a class="button is-link">Normal</a>
<a class="button is-info">Normal</a>
<a class="button is-success">Normal</a>
<a class="button is-warning">Normal</a>
<a class="button is-danger">Normal</a>
```

Hover:

```html
<a class="button is-hovered">Hover</a>
<a class="button is-primary is-hovered">Hover</a>
<a class="button is-link is-hovered">Hover</a>
<a class="button is-info is-hovered">Hover</a>
<a class="button is-success is-hovered">Hover</a>
<a class="button is-warning is-hovered">Hover</a>
<a class="button is-danger is-hovered">Hover</a>
```

Focus:

```html
<a class="button is-focused">Focus</a>
<a class="button is-primary is-focused">Focus</a>
<a class="button is-link is-focused">Focus</a>
<a class="button is-info is-focused">Focus</a>
<a class="button is-success is-focused">Focus</a>
<a class="button is-warning is-focused">Focus</a>
<a class="button is-danger is-focused">Focus</a>
```

Active:

```html
<a class="button is-active">Active</a>
<a class="button is-primary is-active">Active</a>
<a class="button is-link is-active">Active</a>
<a class="button is-info is-active">Active</a>
<a class="button is-success is-active">Active</a>
<a class="button is-warning is-active">Active</a>
<a class="button is-danger is-active">Active</a>
```

Loading:

```html
<a class="button is-loading">Loading</a>
<a class="button is-primary is-loading">Loading</a>
<a class="button is-link is-loading">Loading</a>
<a class="button is-info is-loading">Loading</a>
<a class="button is-success is-loading">Loading</a>
<a class="button is-warning is-loading">Loading</a>
<a class="button is-danger is-loading">Loading</a>
```

Static:

```html
<span class="button is-static">Static</span>
```

Disabled:

```html
<a class="button" title="Disabled button" disabled>Disabled</a>
<a class="button is-primary" title="Disabled button" disabled>Disabled</a>
<a class="button is-link" title="Disabled button" disabled>Disabled</a>
<a class="button is-info" title="Disabled button" disabled>Disabled</a>
<a class="button is-success" title="Disabled button" disabled>Disabled</a>
<a class="button is-warning" title="Disabled button" disabled>Disabled</a>
<a class="button is-danger" title="Disabled button" disabled>Disabled</a>
```

With Font Awesome icons:

```html
<p class="field">
  <a class="button">
    <span class="icon is-small">
      <i class="fas fa-bold"></i>
    </span>
  </a>
  <a class="button">
    <span class="icon is-small">
      <i class="fas fa-italic"></i>
    </span>
  </a>
  <a class="button">
    <span class="icon is-small">
      <i class="fas fa-underline"></i>
    </span>
  </a>
</p>
<p class="field">
  <a class="button">
    <span class="icon">
      <i class="fab fa-github"></i>
    </span>
    <span>GitHub</span>
  </a>
  <a class="button is-primary">
    <span class="icon">
      <i class="fab fa-twitter"></i>
    </span>
    <span>Twitter</span>
  </a>
  <a class="button is-success">
    <span class="icon is-small">
      <i class="fas fa-check"></i>
    </span>
    <span>Save</span>
  </a>
  <a class="button is-danger is-outlined">
    <span>Delete</span>
    <span class="icon is-small">
      <i class="fas fa-times"></i>
    </span>
  </a>
</p>
<p class="field">
  <a class="button is-small">
    <span class="icon is-small">
      <i class="fab fa-github"></i>
    </span>
    <span>GitHub</span>
  </a>
  <a class="button">
    <span class="icon">
      <i class="fab fa-github"></i>
    </span>
    <span>GitHub</span>
  </a>
  <a class="button is-medium">
    <span class="icon">
      <i class="fab fa-github"></i>
    </span>
    <span>GitHub</span>
  </a>
  <a class="button is-large">
    <span class="icon is-medium">
      <i class="fab fa-github"></i>
    </span>
    <span>GitHub</span>
  </a>
</p>
```

如果按钮只包含一个图标，Bulma将确保该按钮保持正方形，不管按钮或图标的大小

```html
<p class="field">
  <a class="button is-small">
    <span class="icon is-small">
      <i class="fas fa-heading"></i>
    </span>
  </a>
</p>
<p class="field">
  <a class="button">
    <span class="icon is-small">
      <i class="fas fa-heading"></i>
    </span>
  </a>
  <a class="button">
  <span class="icon">
    <i class="fas fa-heading fa-lg"></i>
  </span>
  </a>
</p>
<p class="field">
  <a class="button is-medium">
    <span class="icon is-small">
      <i class="fas fa-heading"></i>
    </span>
  </a>
  <a class="button is-medium">
  <span class="icon">
    <i class="fas fa-heading fa-lg"></i>
  </span>
  </a>
  <a class="button is-medium">
    <span class="icon is-medium">
      <i class="fas fa-heading fa-2x"></i>
    </span>
  </a>
</p>
<p class="field">
  <a class="button is-large">
    <span class="icon is-small">
      <i class="fas fa-heading"></i>
    </span>
  </a>
  <a class="button is-large">
  <span class="icon">
    <i class="fas fa-heading fa-lg"></i>
  </span>
  </a>
  <a class="button is-large">
    <span class="icon is-medium">
      <i class="fas fa-heading fa-2x"></i>
    </span>
  </a>
</p>
```

### 按钮组

如果你想在一行上组合创建按钮组，请在带有`.field`修饰符的容器上使用`is-grouped`修饰符

```html
<div class="field is-grouped">
  <p class="control">
    <a class="button is-link">
      Save changes
    </a>
  </p>
  <p class="control">
    <a class="button">
      Cancel
    </a>
  </p>
  <p class="control">
    <a class="button is-danger">
      Delete post
    </a>
  </p>
</div>
```

### 按钮插件

如果你想讲按钮用作插件，请在`.field`容器上使用`has-addons`修饰符

```html
<div class="field has-addons">
  <p class="control">
    <a class="button">
      <span class="icon is-small">
        <i class="fas fa-align-left"></i>
      </span>
      <span>Left</span>
    </a>
  </p>
  <p class="control">
    <a class="button">
      <span class="icon is-small">
        <i class="fas fa-align-center"></i>
      </span>
      <span>Center</span>
    </a>
  </p>
  <p class="control">
    <a class="button">
      <span class="icon is-small">
        <i class="fas fa-align-right"></i>
      </span>
      <span>Right</span>
    </a>
  </p>
</div>
```

### 按钮组插件

你也可以将按钮组和插件组合在一起：

```html
<div class="field has-addons">
  <p class="control">
    <a class="button">
      <span class="icon is-small">
        <i class="fas fa-bold"></i>
      </span>
      <span>Bold</span>
    </a>
  </p>
  <p class="control">
    <a class="button">
      <span class="icon is-small">
        <i class="fas fa-italic"></i>
      </span>
      <span>Italic</span>
    </a>
  </p>
  <p class="control">
    <a class="button">
      <span class="icon is-small">
        <i class="fas fa-underline"></i>
      </span>
      <span>Underline</span>
    </a>
  </p>
</div>

<div class="field has-addons">
  <p class="control">
    <a class="button">
      <span class="icon is-small">
        <i class="fas fa-align-left"></i>
      </span>
      <span>Left</span>
    </a>
  </p>
  <p class="control">
    <a class="button">
      <span class="icon is-small">
        <i class="fas fa-align-center"></i>
      </span>
      <span>Center</span>
    </a>
  </p>
  <p class="control">
    <a class="button">
      <span class="icon is-small">
        <i class="fas fa-align-right"></i>
      </span>
      <span>Right</span>
    </a>
  </p>
</div>
```

### 按钮列表

你现在可以在使用`.buttons`的容器里创建一个按钮列表

```html
<div class="buttons">
  <span class="button is-success">Save changes</span>
  <span class="button is-info">Save and continue</span>
  <span class="button is-danger">Cancel</span>
</div>
```

如果列表很长，它将自动换行多行，同时保持所有按钮间隔均匀。

```html
<div class="buttons">
  <span class="button">One</span>
  <span class="button">Two</span>
  <span class="button">Three</span>
  <span class="button">Four</span>
  <span class="button">Five</span>
  <span class="button">Six</span>
  <span class="button">Seven</span>
  <span class="button">Eight</span>
  <span class="button">Nine</span>
  <span class="button">Ten</span>
  <span class="button">Eleven</span>
  <span class="button">Twelve</span>
  <span class="button">Thirteen</span>
  <span class="button">Fourteen</span>
  <span class="button">Fifteen</span>
  <span class="button">Sixteen</span>
  <span class="button">Seventeen</span>
  <span class="button">Eighteen</span>
  <span class="button">Nineteen</span>
  <span class="button">Twenty</span>
</div>
```

您可以使用`.has-addons`修饰符将按钮连接在一起。

```html
<div class="buttons has-addons">
  <span class="button">Yes</span>
  <span class="button">Maybe</span>
  <span class="button">No</span>
</div>
```

使用`is-centered`或`is-right`修饰符来改变对齐方式。

```html
<div class="buttons has-addons is-centered">
  <span class="button">Yes</span>
  <span class="button">Maybe</span>
  <span class="button">No</span>
</div>

<div class="buttons has-addons is-right">
  <span class="button">Yes</span>
  <span class="button">Maybe</span>
  <span class="button">No</span>
</div>
```

您可以在每个按钮上使用任何修饰符类来区分它们。 添加`is-selected`修饰符，以确保选定的按钮位于其兄弟之上。

```html
<div class="buttons has-addons">
  <span class="button is-success is-selected">Yes</span>
  <span class="button">Maybe</span>
  <span class="button">No</span>
</div>

<div class="buttons has-addons">
  <span class="button">Yes</span>
  <span class="button is-info is-selected">Maybe</span>
  <span class="button">No</span>
</div>

<div class="buttons has-addons">
  <span class="button">Yes</span>
  <span class="button">Maybe</span>
  <span class="button is-danger is-selected">No</span>
</div>
```

<div style="background-color:#f6fbfe;border-radius:3px;font-size:1rem;"><div style="background-color:#209cee;color:#fff;-webkit-box-align:center;-ms-flex-align:center;align-items: center;border-radius:3px 3px 0 0;display:flex;-webkit-box-pack:justify;justify-content:space-between;line-height:1.25;padding:0.5em 0.75em;position: relative;">表单组和按钮列表之间的区别</div><div style="border-color:#209cee;color:#12537e;border-top-left-radius:0;border-top-right-radius:0;border-top: none;border:1px solid #dbdbdb;border-radius:3px;padding:1em 1.25em;"><p style="">虽然按钮样式列表可以通过<code>field is-grouped</code>或新的<code>buttons</code>按钮类来实现，但他们是有一些区别的：</p><ul><li><code>buttons</code>有一个更简单的标记</li><li><code>buttons</code>只能包含<code>button</code>元素</li><li><code>field is-grouped</code>可以包含任何类型的<code>control</code>输入</li><li><code>field is-grouped</code>可以强制所有控件在一行上显示</li><li><code>field is-grouped</code>你可以扩展其中的任意一个控件</li></ul><p style="">基本上，如果你只需要一个按钮列表，建议使用<code>buttons</code>, 如果您需要对样式和元素进行更多控制，请使用<code>form group</code></p></div></div>

### 变量

您可以使用下列变量来自定义这些元素。 在导入Bulma之前，只需设置一个或多个这些变量

| Name | Default value |
| ---- | ------------- |
| `$button-color` | `$grey-darker` |
| `$button-background-color` | `$white` |
| `$button-border-color` | `$grey-lighter` |
| `$button-hover-color` | `$link-hover` |
| `$button-hover-border-color` | `$link-hover-border` |
| `$button-focus-color` | `$link-focus` |
| `$button-focus-border-color` | `$link-focus-border` |
| `$button-focus-box-shadow-size` | `0 0 0 0.125em` |
| `$button-focus-box-shadow-color` | `rgba($link, 0.25)` |
| `$button-active-color` | `$link-active` |
| `$button-active-border-color` | `$link-active-border` |
| `$button-text-color` | `$text` |
| `$button-text-hover-background-color` | `$background` |
| `$button-text-hover-color` | `$text-strong` |
| `$button-disabled-background-color` | `$white` |
| `$button-disabled-border-color` | `$grey-lighter` |
| `$button-disabled-shadow` | `none` |
| `$button-disabled-opacity` | `0.5` |
| `$button-static-color` | `$grey` |
| `$button-static-background-color` | `$white-ter` |
| `$button-static-border-color` | `$grey-lighter` |

## 内容

当你不能使用你想要的CSS类，或者当你只想直接使用HTML标签时，使用内容作为容器。 它几乎可以处理任何HTML标签：

- `<p>` 段落
- `<ul>` `<ol>` `<dl>` 列表
- `<h1>` to `<h6>` 头部
- `<blockquote>` 引用
- `<em>` 和 `<strong>`
- `<table>` `<tr>` `<th>` `<td>` 表格

这个`.content`类可以用于你只想写（或只能）写一些文本的任何场合。 例如，它用于您正在阅读的段落。

```html
<div class="content">
  <h1>Hello World</h1>
  <p>Lorem ipsum<sup><a>[1]</a></sup> dolor sit amet, consectetur adipiscing elit. Nulla accumsan, metus ultrices eleifend gravida, nulla nunc varius lectus, nec rutrum justo nibh eu lectus. Ut vulputate semper dui. Fusce erat odio, sollicitudin vel erat vel, interdum mattis neque. Sub<sub>script</sub> works as well!</p>
  <h2>Second level</h2>
  <p>Curabitur accumsan turpis pharetra <strong>augue tincidunt</strong> blandit. Quisque condimentum maximus mi, sit amet commodo arcu rutrum id. Proin pretium urna vel cursus venenatis. Suspendisse potenti. Etiam mattis sem rhoncus lacus dapibus facilisis. Donec at dignissim dui. Ut et neque nisl.</p>
  <ul>
    <li>In fermentum leo eu lectus mollis, quis dictum mi aliquet.</li>
    <li>Morbi eu nulla lobortis, lobortis est in, fringilla felis.</li>
    <li>Aliquam nec felis in sapien venenatis viverra fermentum nec lectus.</li>
    <li>Ut non enim metus.</li>
  </ul>
  <h3>Third level</h3>
  <p>Quisque ante lacus, malesuada ac auctor vitae, congue <a href="#">non ante</a>. Phasellus lacus ex, semper ac tortor nec, fringilla condimentum orci. Fusce eu rutrum tellus.</p>
  <ol>
    <li>Donec blandit a lorem id convallis.</li>
    <li>Cras gravida arcu at diam gravida gravida.</li>
    <li>Integer in volutpat libero.</li>
    <li>Donec a diam tellus.</li>
    <li>Aenean nec tortor orci.</li>
    <li>Quisque aliquam cursus urna, non bibendum massa viverra eget.</li>
    <li>Vivamus maximus ultricies pulvinar.</li>
  </ol>
  <blockquote>Ut venenatis, nisl scelerisque sollicitudin fermentum, quam libero hendrerit ipsum, ut blandit est tellus sit amet turpis.</blockquote>
  <p>Quisque at semper enim, eu hendrerit odio. Etiam auctor nisl et <em>justo sodales</em> elementum. Maecenas ultrices lacus quis neque consectetur, et lobortis nisi molestie.</p>
  <p>Sed sagittis enim ac tortor maximus rutrum. Nulla facilisi. Donec mattis vulputate risus in luctus. Maecenas vestibulum interdum commodo.</p>
  <dl>
    <dt>Web</dt>
    <dd>The part of the Internet that contains websites and web pages</dd>
    <dt>HTML</dt>
    <dd>A markup language for creating web pages</dd>
    <dt>CSS</dt>
    <dd>A technology to make HTML look better</dd>
  </dl>
  <p>Suspendisse egestas sapien non felis placerat elementum. Morbi tortor nisl, suscipit sed mi sit amet, mollis malesuada nulla. Nulla facilisi. Nullam ac erat ante.</p>
  <h4>Fourth level</h4>
  <p>Nulla efficitur eleifend nisi, sit amet bibendum sapien fringilla ac. Mauris euismod metus a tellus laoreet, at elementum ex efficitur.</p>
  <pre>
<!DOCTYPE html>
<html>
  <head>
    <title>Hello World</title>
  </head>
  <body>
    <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec viverra nec nulla vitae mollis.</p>
  </body>
</html>
</pre>
  <p>Maecenas eleifend sollicitudin dui, faucibus sollicitudin augue cursus non. Ut finibus eleifend arcu ut vehicula. Mauris eu est maximus est porta condimentum in eu justo. Nulla id iaculis sapien.</p>
  <table>
    <thead>
      <tr>
        <th>One</th>
        <th>Two</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>Three</td>
        <td>Four</td>
      </tr>
      <tr>
        <td>Five</td>
        <td>Six</td>
      </tr>
      <tr>
        <td>Seven</td>
        <td>Eight</td>
      </tr>
      <tr>
        <td>Nine</td>
        <td>Ten</td>
      </tr>
      <tr>
        <td>Eleven</td>
        <td>Twelve</td>
      </tr>
    </tbody>
  </table>
  <p>Phasellus porttitor enim id metus volutpat ultricies. Ut nisi nunc, blandit sed dapibus at, vestibulum in felis. Etiam iaculis lorem ac nibh bibendum rhoncus. Nam interdum efficitur ligula sit amet ullamcorper. Etiam tristique, leo vitae porta faucibus, mi lacus laoreet metus, at cursus leo est vel tellus. Sed ac posuere est. Nunc ultricies nunc neque, vitae ultricies ex sodales quis. Aliquam eu nibh in libero accumsan pulvinar. Nullam nec nisl placerat, pretium metus vel, euismod ipsum. Proin tempor cursus nisl vel condimentum. Nam pharetra varius metus non pellentesque.</p>
  <h5>Fifth level</h5>
  <p>Aliquam sagittis rhoncus vulputate. Cras non luctus sem, sed tincidunt ligula. Vestibulum at nunc elit. Praesent aliquet ligula mi, in luctus elit volutpat porta. Phasellus molestie diam vel nisi sodales, a eleifend augue laoreet. Sed nec eleifend justo. Nam et sollicitudin odio.</p>
  <figure>
    <img src="https://bulma.io/images/placeholders/256x256.png">
    <img src="https://bulma.io/images/placeholders/256x256.png">
    <figcaption>
      Figure 1: Some beautiful placeholders
    </figcaption>
  </figure>
  <h6>Sixth level</h6>
  <p>Cras in nibh lacinia, venenatis nisi et, auctor urna. Donec pulvinar lacus sed diam dignissim, ut eleifend eros accumsan. Phasellus non tortor eros. Ut sed rutrum lacus. Etiam purus nunc, scelerisque quis enim vitae, malesuada ultrices turpis. Nunc vitae maximus purus, nec consectetur dui. Suspendisse euismod, elit vel rutrum commodo, ipsum tortor maximus dui, sed varius sapien odio vitae est. Etiam at cursus metus.</p>
</div>
```

### 尺寸

您可以使用`is-small`，`is-medium`和`is-large`修饰符来更改字体大小。

### 变量

| Name | Default value |
| ---- | ------------- |
| `$content-heading-color` | `$text-strong` |
| `$content-heading-weight` | `$weight-normal` |
| `$content-heading-line-height` | `1.125` |
| `$content-blockquote-background-color` | `$background` |
| `$content-blockquote-border-left` | `5px solid $border` |
| `$content-blockquote-padding` | `1.25em 1.5em` |
| `$content-pre-padding` | `1.25em 1.5em` |
| `$content-table-cell-border` | `1px solid $border` |
| `$content-table-cell-border-width` | `0 0 1px` |
| `$content-table-cell-padding` | `0.5em 0.75em` |
| `$content-table-cell-heading-color` | `$text-strong` |
| `$content-table-row-hover-background-color` | `$background` |
| `$content-table-head-cell-border-width` | `0 0 2px` |
| `$content-table-head-cell-color` | `$text-strong` |
| `$content-table-foot-cell-border-width` | `2px 0 0` |
| `$content-table-foot-cell-color` | `$text-strong` |

## 删除

`.delete`元素是一个独立的元素，可以在不同的上下文中使用。

```html
<a class="delete"></a>
```

### 大小

```html
<a class="delete is-small"></a>
<a class="delete"></a>
<a class="delete is-medium"></a>
<a class="delete is-large"></a>
```

### 组合使用

Bulma将它用于标签、通知和消息：

```html
<div class="block">
  <span class="tag is-success">
    Hello World
    <button class="delete is-small"></button>
  </span>
</div>

<div class="notification is-danger">
  <button class="delete"></button>
  Lorem ipsum dolor sit amet, consectetur adipiscing elit lorem ipsum dolor sit amet, consectetur adipiscing elit
</div>

<article class="message is-info">
  <div class="message-header">
    Info
    <button class="delete"></button>
  </div>
  <div class="message-body">
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Pellentesque risus mi, tempus quis placerat ut, porta nec nulla. Vestibulum rhoncus ac ex sit amet fringilla. Nullam gravida purus diam, et dictum felis venenatis efficitur. Aenean ac eleifend lacus, in mollis lectus. Donec sodales, arcu et sollicitudin porttitor, tortor urna tempor ligula, id porttitor mi magna a neque. Donec dui urna, vehicula et sem eget, facilisis sodales sem.
  </div>
</article>
```

## 图标

Bulma兼容所有的图标字体库，包括`Font Awesome 5`, `Font Awesome 4`, `Material Design Icons`, `Open Iconic`, `Ionicons etc`

图标元素是任何类型图标字体的容器。 由于这些图标可能需要几秒钟才能加载，并且因为您想要控制图标将要占用的空间，所以可以使用图标类作为可靠的方形容器，以防止页面在加载页面时“跳跃”。

```html
<span class="icon">
  <i class="fas fa-home"></i>
</span>
```

默认情况下，图标容器将占用`1.5rem x 1.5rem`的空间大小。 图标本身的大小相应于您正在使用的图标库。 例如，`Font Awesome 5`图标将继承字体大小。

### 颜色

由于图标字体只是文本，因此可以使用文本颜色修改器来更改图标的颜色。

```html
<span class="icon has-text-info">
  <i class="fas fa-info-circle"></i>
</span>
<span class="icon has-text-success">
  <i class="fas fa-check-square"></i>
</span>
<span class="icon has-text-warning">
  <i class="fas fa-exclamation-triangle"></i>
</span>
<span class="icon has-text-danger">
  <i class="fas fa-ban"></i>
</span>
```

### 大小

Bulma图标容器有4种尺寸。 它应该总是比它包含的图标稍大。 例如，`Font Awesome 5`图标默认使用`1em`的字体大小（因为它继承了字体大小），但提供了更多大小。

### 变量

| Name | Default value |
| ---- | ------------- |
| `$icon-dimensions` | `1.5rem` |
| `$icon-dimensions-small` | `1rem` |
| `$icon-dimensions-medium` | `2rem` |
| `$icon-dimensions-large` | `3rem` |

## 图片

由于图像可能需要几秒钟才能加载（或根本不需要），因此使用`.image`容器可以指定尺寸精确的容器，以便布局不会因图像加载或图像错误而中断。

```html
<figure class="image is-128x128">
  <img src="https://bulma.io/images/placeholders/128x128.png">
</figure>
```

### 方形图片修正

我们有7个大小可以选择：

<table style="background-color:white;color:#363636;margin-bottom:1.5rem;border-collapse:collapse;border-spacing:0;"><tbody style="display:table-row-group;vertical-align: middle;"><tr style="display:table-row;"><td style="border-width:1px;border:1px solid #dbdbdb;padding:0.5em 0.75em;vertical-align:top;text-align:left;"><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight: normal;padding:0.25em 0.5em 0.25em;">image is-16x16</code></td><td style="border-width:1px;border:1px solid #dbdbdb;padding:0.5em 0.75em;vertical-align:top;text-align:left;"><figure class="image is-16x16"><img src="https://bulma.io/images/placeholders/16x16.png"></figure></td><td style="border-width:1px;border:1px solid #dbdbdb;padding:0.5em 0.75em;vertical-align:top;text-align:left;">16x16px</td></tr><tr style="display:table-row;"><td style="border-width:1px;border:1px solid #dbdbdb;padding:0.5em 0.75em;vertical-align:top;text-align:left;"><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight: normal;padding:0.25em 0.5em 0.25em;">image is-24x24</code></td><td style="border-width:1px;border:1px solid #dbdbdb;padding:0.5em 0.75em;vertical-align:top;text-align:left;"><figure class="image is-24x24"><img src="https://bulma.io/images/placeholders/24x24.png"></figure></td><td style="border-width:1px;border:1px solid #dbdbdb;padding:0.5em 0.75em;vertical-align:top;text-align:left;">24x24px</td></tr><tr style="display:table-row;">
<td style="border-width:1px;border:1px solid #dbdbdb;padding:0.5em 0.75em;vertical-align:top;text-align:left;"><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight: normal;padding:0.25em 0.5em 0.25em;">image is-32x32</code></td><td style="border-width:1px;border:1px solid #dbdbdb;padding:0.5em 0.75em;vertical-align:top;text-align:left;"><figure class="image is-32x32"><img src="https://bulma.io/images/placeholders/32x32.png"></figure></td><td style="border-width:1px;border:1px solid #dbdbdb;padding:0.5em 0.75em;vertical-align:top;text-align:left;">32x32px</td></tr><tr style="display:table-row;">
<td style="border-width:1px;border:1px solid #dbdbdb;padding:0.5em 0.75em;vertical-align:top;text-align:left;"><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight: normal;padding:0.25em 0.5em 0.25em;">image is-48x48</code></td><td style="border-width:1px;border:1px solid #dbdbdb;padding:0.5em 0.75em;vertical-align:top;text-align:left;"><figure class="image is-48x48"><img src="https://bulma.io/images/placeholders/48x48.png"></figure></td><td style="border-width:1px;border:1px solid #dbdbdb;padding:0.5em 0.75em;vertical-align:top;text-align:left;">48x48px</td></tr><tr style="display:table-row;">
<td style="border-width:1px;border:1px solid #dbdbdb;padding:0.5em 0.75em;vertical-align:top;text-align:left;"><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight: normal;padding:0.25em 0.5em 0.25em;">image is-64x64</code></td><td style="border-width:1px;border:1px solid #dbdbdb;padding:0.5em 0.75em;vertical-align:top;text-align:left;"><figure class="image is-64x64"><img src="https://bulma.io/images/placeholders/64x64.png"></figure></td><td style="border-width:1px;border:1px solid #dbdbdb;padding:0.5em 0.75em;vertical-align:top;text-align:left;">64x64px</td></tr><tr style="display:table-row;">
<td style="border-width:1px;border:1px solid #dbdbdb;padding:0.5em 0.75em;vertical-align:top;text-align:left;"><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight: normal;padding:0.25em 0.5em 0.25em;">image is-96x96</code></td><td style="border-width:1px;border:1px solid #dbdbdb;padding:0.5em 0.75em;vertical-align:top;text-align:left;"><figure class="image is-96x96"><img src="https://bulma.io/images/placeholders/96x96.png"></figure></td><td style="border-width:1px;border:1px solid #dbdbdb;padding:0.5em 0.75em;vertical-align:top;text-align:left;">96x96px</td></tr><tr style="display:table-row;">
<td style="border-width:1px;border:1px solid #dbdbdb;padding:0.5em 0.75em;vertical-align:top;text-align:left;"><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight: normal;padding:0.25em 0.5em 0.25em;">image is-128x128</code></td><td style="border-width:1px;border:1px solid #dbdbdb;padding:0.5em 0.75em;vertical-align:top;text-align:left;"><figure class="image is-128x128"><img src="https://bulma.io/images/placeholders/128x128.png"></figure></td><td style="border-width:1px;border:1px solid #dbdbdb;padding:0.5em 0.75em;vertical-align:top;text-align:left;">128x128px</td></tr></tbody></table>

### Retina图片

由于图像的大小是固定的，因此可以使用两倍大的图像。 例如，在一个128x128的容器中，您可以使用256x256图像，但调整为128x128像素。

```html
<figure class="image is-128x128">
  <img src="https://bulma.io/images/placeholders/256x256.png">
</figure>
```

### 具有比例的响应式图像

如果您不知道确切的尺寸，但知道比例，则可以使用5个比率修饰符中的一个：

<table style="background-color:white;color:#363636;margin-bottom:1.5rem;border-collapse:collapse;border-spacing:0;"><tbody style="display:table-row-group;vertical-align: middle;"><tr style="display:table-row;"><td style="border-width:1px;border:1px solid #dbdbdb;padding:0.5em 0.75em;vertical-align:top;text-align:left;"><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight: normal;padding:0.25em 0.5em 0.25em;">image is-square</code></td><td style="border-width:1px;border:1px solid #dbdbdb;padding:0.5em 0.75em;vertical-align:top;text-align:left;"><figure class="image is-square"><img src="https://bulma.io/images/placeholders/480x480.png"></figure></td><td style="border-width:1px;border:1px solid #dbdbdb;padding:0.5em 0.75em;vertical-align:top;text-align:left;">Square (or 1by1)</td></tr><tr style="display:table-row;"><td style="border-width:1px;border:1px solid #dbdbdb;padding:0.5em 0.75em;vertical-align:top;text-align:left;"><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight: normal;padding:0.25em 0.5em 0.25em;">image is-1by1</code></td><td style="border-width:1px;border:1px solid #dbdbdb;padding:0.5em 0.75em;vertical-align:top;text-align:left;"><figure class="image is-1by1"><img src="https://bulma.io/images/placeholders/480x480.png"></figure></td><td style="border-width:1px;border:1px solid #dbdbdb;padding:0.5em 0.75em;vertical-align:top;text-align:left;">1 by 1</td></tr><tr style="display:table-row;">
<td style="border-width:1px;border:1px solid #dbdbdb;padding:0.5em 0.75em;vertical-align:top;text-align:left;"><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight: normal;padding:0.25em 0.5em 0.25em;">image is-4by3</code></td><td style="border-width:1px;border:1px solid #dbdbdb;padding:0.5em 0.75em;vertical-align:top;text-align:left;"><figure class="image is-4by3"><img src="https://bulma.io/images/placeholders/640x480.png"></figure></td><td style="border-width:1px;border:1px solid #dbdbdb;padding:0.5em 0.75em;vertical-align:top;text-align:left;">4 by 3</td></tr><tr style="display:table-row;">
<td style="border-width:1px;border:1px solid #dbdbdb;padding:0.5em 0.75em;vertical-align:top;text-align:left;"><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight: normal;padding:0.25em 0.5em 0.25em;">image is-3by2</code></td><td style="border-width:1px;border:1px solid #dbdbdb;padding:0.5em 0.75em;vertical-align:top;text-align:left;"><figure class="image is-3by2"><img src="https://bulma.io/images/placeholders/480x320.png"></figure></td><td style="border-width:1px;border:1px solid #dbdbdb;padding:0.5em 0.75em;vertical-align:top;text-align:left;">3 by 2</td></tr><tr style="display:table-row;">
<td style="border-width:1px;border:1px solid #dbdbdb;padding:0.5em 0.75em;vertical-align:top;text-align:left;"><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight: normal;padding:0.25em 0.5em 0.25em;">image is-16by9</code></td><td style="border-width:1px;border:1px solid #dbdbdb;padding:0.5em 0.75em;vertical-align:top;text-align:left;"><figure class="image is-16by9"><img src="https://bulma.io/images/placeholders/640x360.png"></figure></td><td style="border-width:1px;border:1px solid #dbdbdb;padding:0.5em 0.75em;vertical-align:top;text-align:left;">16 by 9</td></tr><tr style="display:table-row;">
<td style="border-width:1px;border:1px solid #dbdbdb;padding:0.5em 0.75em;vertical-align:top;text-align:left;"><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight: normal;padding:0.25em 0.5em 0.25em;">image is-2by1</code></td><td style="border-width:1px;border:1px solid #dbdbdb;padding:0.5em 0.75em;vertical-align:top;text-align:left;"><figure class="image is-2by1"><img src="https://bulma.io/images/placeholders/640x320.png"></figure></td><td style="border-width:1px;border:1px solid #dbdbdb;padding:0.5em 0.75em;vertical-align:top;text-align:left;">2 by 1</td></tr></tbody></table>

`.image`容器将占用整个宽度，同时保持完美的比例。

### 变量

| Name | Default value |
| ---- | ------------- |
| `$dimensions` | `16 24 32 48 64 96 128` |

## 通知

在Bulma中，通知是一个粗体的通知块，提醒用户注意事项

```html
<div class="notification">
  <button class="delete"></button>
  Lorem ipsum dolor sit amet, consectetur
  adipiscing elit lorem ipsum dolor. <strong>Pellentesque risus mi</strong>, tempus quis placerat ut, porta nec nulla. Vestibulum rhoncus ac ex sit amet fringilla. Nullam gravida purus diam, et dictum <a>felis venenatis</a> efficitur. Sit amet,
  consectetur adipiscing elit
</div>
```

### 颜色

```html
<div class="notification is-primary">
  <button class="delete"></button>
  Primar lorem ipsum dolor sit amet, consectetur
  adipiscing elit lorem ipsum dolor. <strong>Pellentesque risus mi</strong>, tempus quis placerat ut, porta nec nulla. Vestibulum rhoncus ac ex sit amet fringilla. Nullam gravida purus diam, et dictum <a>felis venenatis</a> efficitur. Sit amet,
  consectetur adipiscing elit
</div>

<div class="notification is-link">
  <button class="delete"></button>
  Primar lorem ipsum dolor sit amet, consectetur
  adipiscing elit lorem ipsum dolor. <strong>Pellentesque risus mi</strong>, tempus quis placerat ut, porta nec nulla. Vestibulum rhoncus ac ex sit amet fringilla. Nullam gravida purus diam, et dictum <a>felis venenatis</a> efficitur. Sit amet,
  consectetur adipiscing elit
</div>

<div class="notification is-info">
  <button class="delete"></button>
  Primar lorem ipsum dolor sit amet, consectetur
  adipiscing elit lorem ipsum dolor. <strong>Pellentesque risus mi</strong>, tempus quis placerat ut, porta nec nulla. Vestibulum rhoncus ac ex sit amet fringilla. Nullam gravida purus diam, et dictum <a>felis venenatis</a> efficitur. Sit amet,
  consectetur adipiscing elit
</div>

<div class="notification is-success">
  <button class="delete"></button>
  Primar lorem ipsum dolor sit amet, consectetur
  adipiscing elit lorem ipsum dolor. <strong>Pellentesque risus mi</strong>, tempus quis placerat ut, porta nec nulla. Vestibulum rhoncus ac ex sit amet fringilla. Nullam gravida purus diam, et dictum <a>felis venenatis</a> efficitur. Sit amet,
  consectetur adipiscing elit
</div>

<div class="notification is-warning">
  <button class="delete"></button>
  Primar lorem ipsum dolor sit amet, consectetur
  adipiscing elit lorem ipsum dolor. <strong>Pellentesque risus mi</strong>, tempus quis placerat ut, porta nec nulla. Vestibulum rhoncus ac ex sit amet fringilla. Nullam gravida purus diam, et dictum <a>felis venenatis</a> efficitur. Sit amet,
  consectetur adipiscing elit
</div>

<div class="notification is-danger">
  <button class="delete"></button>
  Primar lorem ipsum dolor sit amet, consectetur
  adipiscing elit lorem ipsum dolor. <strong>Pellentesque risus mi</strong>, tempus quis placerat ut, porta nec nulla. Vestibulum rhoncus ac ex sit amet fringilla. Nullam gravida purus diam, et dictum <a>felis venenatis</a> efficitur. Sit amet,
  consectetur adipiscing elit
</div>
```

### 变量

| Name | Default value |
| ---- | ------------- |
| `$notification-background-color` | `$background` |
| `$notification-radius` | `$radius` |
| `$notification-padding` | `1.25rem 2.5rem 1.25rem 1.5rem` |

## 进度条

Bulma中的进度条是原生HTML进度条

```html
<progress class="progress" value="15" max="100">15%</progress>
```

### 颜色

```html
<progress class="progress is-primary" value="15" max="100">30%</progress>
<progress class="progress is-link" value="30" max="100">30%</progress>
<progress class="progress is-info" value="45" max="100">45%</progress>
<progress class="progress is-success" value="60" max="100">60%</progress>
<progress class="progress is-warning" value="75" max="100">75%</progress>
<progress class="progress is-danger" value="90" max="100">90%</progress>
```

### 尺寸大小

```html
<progress class="progress is-small" value="15" max="100">15%</progress>
<progress class="progress" value="30" max="100">30%</progress>
<progress class="progress is-medium" value="45" max="100">45%</progress>
<progress class="progress is-large" value="60" max="100">60%</progress>
```

### 变量

| Name | Default value |
| ---- | ------------- |
| `$progress-bar-background-color` | `$border` |
| `$progress-value-background-color` | `$text` |

## 表格

在Bulma中，创建表格很简单，你只需在一个`<table>`标签上添加`.table`CSS类即可，结构如下：

<ul style="list-style:disc outside;margin-top:1em;"><li><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding: 0.25em 0.5em 0.25em;">table</code> 主容器<ul style="list-style:disc outside;"><li><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding: 0.25em 0.5em 0.25em;">thead</code> 表格的可选顶部部分</li><li><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding: 0.25em 0.5em 0.25em;">tfoot</code> 表格的可选底部</li><li><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding: 0.25em 0.5em 0.25em;">tbody</code> 表格的主要内容<ul style="list-style:disc outside;"><li><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding: 0.25em 0.5em 0.25em;">tr</code> 表格每一行<ul style="list-style:disc outside;"><li><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding: 0.25em 0.5em 0.25em;">th</code> 表格的单元格标题</li><li><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding: 0.25em 0.5em 0.25em;">td</code> 一个表格的单元格</li></ul></li></ul></li></ul></li></ul>

您可以通过在`<tr>`上附加`is-selected`修饰符来设置表格行

```html
<table class="table">
  <thead>
    <tr>
      <th><abbr title="Position">Pos</abbr></th>
      <th>Team</th>
      <th><abbr title="Played">Pld</abbr></th>
      <th><abbr title="Won">W</abbr></th>
      <th><abbr title="Drawn">D</abbr></th>
      <th><abbr title="Lost">L</abbr></th>
      <th><abbr title="Goals for">GF</abbr></th>
      <th><abbr title="Goals against">GA</abbr></th>
      <th><abbr title="Goal difference">GD</abbr></th>
      <th><abbr title="Points">Pts</abbr></th>
      <th>Qualification or relegation</th>
    </tr>
  </thead>
  <tfoot>
    <tr>
      <th><abbr title="Position">Pos</abbr></th>
      <th>Team</th>
      <th><abbr title="Played">Pld</abbr></th>
      <th><abbr title="Won">W</abbr></th>
      <th><abbr title="Drawn">D</abbr></th>
      <th><abbr title="Lost">L</abbr></th>
      <th><abbr title="Goals for">GF</abbr></th>
      <th><abbr title="Goals against">GA</abbr></th>
      <th><abbr title="Goal difference">GD</abbr></th>
      <th><abbr title="Points">Pts</abbr></th>
      <th>Qualification or relegation</th>
    </tr>
  </tfoot>
  <tbody>
    <tr>
      <th>1</th>
      <td><a href="https://en.wikipedia.org/wiki/Leicester_City_F.C." title="Leicester City F.C.">Leicester City</a> <strong>(C)</strong>
      </td>
      <td>38</td>
      <td>23</td>
      <td>12</td>
      <td>3</td>
      <td>68</td>
      <td>36</td>
      <td>+32</td>
      <td>81</td>
      <td>Qualification for the <a href="https://en.wikipedia.org/wiki/2016%E2%80%9317_UEFA_Champions_League#Group_stage" title="2016–17 UEFA Champions League">Champions League group stage</a></td>
    </tr>
    <tr>
      <th>2</th>
      <td><a href="https://en.wikipedia.org/wiki/Arsenal_F.C." title="Arsenal F.C.">Arsenal</a></td>
      <td>38</td>
      <td>20</td>
      <td>11</td>
      <td>7</td>
      <td>65</td>
      <td>36</td>
      <td>+29</td>
      <td>71</td>
      <td>Qualification for the <a href="https://en.wikipedia.org/wiki/2016%E2%80%9317_UEFA_Champions_League#Group_stage" title="2016–17 UEFA Champions League">Champions League group stage</a></td>
    </tr>
    <tr>
      <th>3</th>
      <td><a href="https://en.wikipedia.org/wiki/Tottenham_Hotspur_F.C." title="Tottenham Hotspur F.C.">Tottenham Hotspur</a></td>
      <td>38</td>
      <td>19</td>
      <td>13</td>
      <td>6</td>
      <td>69</td>
      <td>35</td>
      <td>+34</td>
      <td>70</td>
      <td>Qualification for the <a href="https://en.wikipedia.org/wiki/2016%E2%80%9317_UEFA_Champions_League#Group_stage" title="2016–17 UEFA Champions League">Champions League group stage</a></td>
    </tr>
    <tr class="is-selected">
      <th>4</th>
      <td><a href="https://en.wikipedia.org/wiki/Manchester_City_F.C." title="Manchester City F.C.">Manchester City</a></td>
      <td>38</td>
      <td>19</td>
      <td>9</td>
      <td>10</td>
      <td>71</td>
      <td>41</td>
      <td>+30</td>
      <td>66</td>
      <td>Qualification for the <a href="https://en.wikipedia.org/wiki/2016%E2%80%9317_UEFA_Champions_League#Play-off_round" title="2016–17 UEFA Champions League">Champions League play-off round</a></td>
    </tr>
    <tr>
      <th>5</th>
      <td><a href="https://en.wikipedia.org/wiki/Manchester_United_F.C." title="Manchester United F.C.">Manchester United</a></td>
      <td>38</td>
      <td>19</td>
      <td>9</td>
      <td>10</td>
      <td>49</td>
      <td>35</td>
      <td>+14</td>
      <td>66</td>
      <td>Qualification for the <a href="https://en.wikipedia.org/wiki/2016%E2%80%9317_UEFA_Europa_League#Group_stage" title="2016–17 UEFA Europa League">Europa League group stage</a></td>
    </tr>
    <tr>
      <th>6</th>
      <td><a href="https://en.wikipedia.org/wiki/Southampton_F.C." title="Southampton F.C.">Southampton</a></td>
      <td>38</td>
      <td>18</td>
      <td>9</td>
      <td>11</td>
      <td>59</td>
      <td>41</td>
      <td>+18</td>
      <td>63</td>
      <td>Qualification for the <a href="https://en.wikipedia.org/wiki/2016%E2%80%9317_UEFA_Europa_League#Group_stage" title="2016–17 UEFA Europa League">Europa League group stage</a></td>
    </tr>
    <tr>
      <th>7</th>
      <td><a href="https://en.wikipedia.org/wiki/West_Ham_United_F.C." title="West Ham United F.C.">West Ham United</a></td>
      <td>38</td>
      <td>16</td>
      <td>14</td>
      <td>8</td>
      <td>65</td>
      <td>51</td>
      <td>+14</td>
      <td>62</td>
      <td>Qualification for the <a href="https://en.wikipedia.org/wiki/2016%E2%80%9317_UEFA_Europa_League#Third_qualifying_round" title="2016–17 UEFA Europa League">Europa League third qualifying round</a></td>
    </tr>
    <tr>
      <th>8</th>
      <td><a href="https://en.wikipedia.org/wiki/Liverpool_F.C." title="Liverpool F.C.">Liverpool</a></td>
      <td>38</td>
      <td>16</td>
      <td>12</td>
      <td>10</td>
      <td>63</td>
      <td>50</td>
      <td>+13</td>
      <td>60</td>
      <td></td>
    </tr>
    <tr>
      <th>9</th>
      <td><a href="https://en.wikipedia.org/wiki/Stoke_City_F.C." title="Stoke City F.C.">Stoke City</a></td>
      <td>38</td>
      <td>14</td>
      <td>9</td>
      <td>15</td>
      <td>41</td>
      <td>55</td>
      <td>−14</td>
      <td>51</td>
      <td></td>
    </tr>
    <tr>
      <th>10</th>
      <td><a href="https://en.wikipedia.org/wiki/Chelsea_F.C." title="Chelsea F.C.">Chelsea</a></td>
      <td>38</td>
      <td>12</td>
      <td>14</td>
      <td>12</td>
      <td>59</td>
      <td>53</td>
      <td>+6</td>
      <td>50</td>
      <td></td>
    </tr>
    <tr>
      <th>11</th>
      <td><a href="https://en.wikipedia.org/wiki/Everton_F.C." title="Everton F.C.">Everton</a></td>
      <td>38</td>
      <td>11</td>
      <td>14</td>
      <td>13</td>
      <td>59</td>
      <td>55</td>
      <td>+4</td>
      <td>47</td>
      <td></td>
    </tr>
    <tr>
      <th>12</th>
      <td><a href="https://en.wikipedia.org/wiki/Swansea_City_A.F.C." title="Swansea City A.F.C.">Swansea City</a></td>
      <td>38</td>
      <td>12</td>
      <td>11</td>
      <td>15</td>
      <td>42</td>
      <td>52</td>
      <td>−10</td>
      <td>47</td>
      <td></td>
    </tr>
    <tr>
      <th>13</th>
      <td><a href="https://en.wikipedia.org/wiki/Watford_F.C." title="Watford F.C.">Watford</a></td>
      <td>38</td>
      <td>12</td>
      <td>9</td>
      <td>17</td>
      <td>40</td>
      <td>50</td>
      <td>−10</td>
      <td>45</td>
      <td></td>
    </tr>
    <tr>
      <th>14</th>
      <td><a href="https://en.wikipedia.org/wiki/West_Bromwich_Albion_F.C." title="West Bromwich Albion F.C.">West Bromwich Albion</a></td>
      <td>38</td>
      <td>10</td>
      <td>13</td>
      <td>15</td>
      <td>34</td>
      <td>48</td>
      <td>−14</td>
      <td>43</td>
      <td></td>
    </tr>
    <tr>
      <th>15</th>
      <td><a href="https://en.wikipedia.org/wiki/Crystal_Palace_F.C." title="Crystal Palace F.C.">Crystal Palace</a></td>
      <td>38</td>
      <td>11</td>
      <td>9</td>
      <td>18</td>
      <td>39</td>
      <td>51</td>
      <td>−12</td>
      <td>42</td>
      <td></td>
    </tr>
    <tr>
      <th>16</th>
      <td><a href="https://en.wikipedia.org/wiki/A.F.C._Bournemouth" title="A.F.C. Bournemouth">AFC Bournemouth</a></td>
      <td>38</td>
      <td>11</td>
      <td>9</td>
      <td>18</td>
      <td>45</td>
      <td>67</td>
      <td>−22</td>
      <td>42</td>
      <td></td>
    </tr>
    <tr>
      <th>17</th>
      <td><a href="https://en.wikipedia.org/wiki/Sunderland_A.F.C." title="Sunderland A.F.C.">Sunderland</a></td>
      <td>38</td>
      <td>9</td>
      <td>12</td>
      <td>17</td>
      <td>48</td>
      <td>62</td>
      <td>−14</td>
      <td>39</td>
      <td></td>
    </tr>
    <tr>
      <th>18</th>
      <td><a href="https://en.wikipedia.org/wiki/Newcastle_United_F.C." title="Newcastle United F.C.">Newcastle United</a> <strong>(R)</strong>
      </td>
      <td>38</td>
      <td>9</td>
      <td>10</td>
      <td>19</td>
      <td>44</td>
      <td>65</td>
      <td>−21</td>
      <td>37</td>
      <td>Relegation to the <a href="https://en.wikipedia.org/wiki/2016%E2%80%9317_Football_League_Championship" title="2016–17 Football League Championship">Football League Championship</a></td>
    </tr>
    <tr>
      <th>19</th>
      <td><a href="https://en.wikipedia.org/wiki/Norwich_City_F.C." title="Norwich City F.C.">Norwich City</a> <strong>(R)</strong>
      </td>
      <td>38</td>
      <td>9</td>
      <td>7</td>
      <td>22</td>
      <td>39</td>
      <td>67</td>
      <td>−28</td>
      <td>34</td>
      <td>Relegation to the <a href="https://en.wikipedia.org/wiki/2016%E2%80%9317_Football_League_Championship" title="2016–17 Football League Championship">Football League Championship</a></td>    </tr>
    <tr>
      <th>20</th>
      <td><a href="https://en.wikipedia.org/wiki/Aston_Villa_F.C." title="Aston Villa F.C.">Aston Villa</a> <strong>(R)</strong>
      </td>
      <td>38</td>
      <td>3</td>
      <td>8</td>
      <td>27</td>
      <td>27</td>
      <td>76</td>
      <td>−49</td>
      <td>17</td>
      <td>Relegation to the <a href="https://en.wikipedia.org/wiki/2016%E2%80%9317_Football_League_Championship" title="2016–17 Football League Championship">Football League Championship</a></td>
    </tr>
  </tbody>
</table>
```

### 修饰符

你可以使用`table is-bordered`修饰符为所有的单元格添加边框

```html
<table class="table is-bordered">
  <thead>
    <tr>
      <th>One</th>
      <th>Two</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Three</td>
      <td>Four</td>
    </tr>
  </tbody>
</table>
```

你可以使用`table is-striped`修饰符为表格添加条纹

```html
<table class="table is-striped">
  <thead>
    <tr>
      <th>One</th>
      <th>Two</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Three</td>
      <td>Four</td>
    </tr>
    <tr>
      <td>Five</td>
      <td>Six</td>
    </tr>
    <tr>
      <td>Seven</td>
      <td>Eight</td>
    </tr>
    <tr>
      <td>Nine</td>
      <td>Ten</td>
    </tr>
    <tr>
      <td>Eleven</td>
      <td>Twelve</td>
    </tr>
  </tbody>
</table>
```

你可以使用`table is-narrow`来使得表格表现的很紧凑

```html
<table class="table is-narrow">
  <thead>
    <tr>
      <th>One</th>
      <th>Two</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Three</td>
      <td>Four</td>
    </tr>
    <tr>
      <td>Five</td>
      <td>Six</td>
    </tr>
    <tr>
      <td>Seven</td>
      <td>Eight</td>
    </tr>
    <tr>
      <td>Nine</td>
      <td>Ten</td>
    </tr>
    <tr>
      <td>Eleven</td>
      <td>Twelve</td>
    </tr>
  </tbody>
</table>
```

您可以使用`table is-hoverable`在每一行上添加悬停效果

```html

<table class="table is-hoverable">
  <thead>
    <tr>
      <th>One</th>
      <th>Two</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Three</td>
      <td>Four</td>
    </tr>
    <tr>
      <td>Five</td>
      <td>Six</td>
    </tr>
    <tr>
      <td>Seven</td>
      <td>Eight</td>
    </tr>
    <tr>
      <td>Nine</td>
      <td>Ten</td>
    </tr>
    <tr>
      <td>Eleven</td>
      <td>Twelve</td>
    </tr>
  </tbody>
</table>
```

你可以使用`table is-fullwidth`来添加一个100%宽度的表格

```html
<table class="table is-fullwidth">
  <thead>
    <tr>
      <th>One</th>
      <th>Two</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Three</td>
      <td>Four</td>
    </tr>
    <tr>
      <td>Five</td>
      <td>Six</td>
    </tr>
    <tr>
      <td>Seven</td>
      <td>Eight</td>
    </tr>
    <tr>
      <td>Nine</td>
      <td>Ten</td>
    </tr>
    <tr>
      <td>Eleven</td>
      <td>Twelve</td>
    </tr>
  </tbody>
</table>
```

你也可以组合使用上面的5个修饰符

```html
<table class="table is-bordered is-striped is-narrow is-hoverable is-fullwidth">
  <thead>
    <tr>
      <th>One</th>
      <th>Two</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Three</td>
      <td>Four</td>
    </tr>
    <tr>
      <td>Five</td>
      <td>Six</td>
    </tr>
    <tr>
      <td>Seven</td>
      <td>Eight</td>
    </tr>
    <tr>
      <td>Nine</td>
      <td>Ten</td>
    </tr>
    <tr>
      <td>Eleven</td>
      <td>Twelve</td>
    </tr>
  </tbody>
</table>
```

### 变量

| Name | Default value |
| ---- | ------------- |
| `$table-color` | `$grey-darker` |
| `$table-background-color` | `$white` |
| `$table-cell-border` | `1px solid $grey-lighter` |
| `$table-cell-border-width` | `0 0 1px` |
| `$table-cell-padding` | `0.5em 0.75em` |
| `$table-cell-heading-color` | `$text-strong` |
| `$table-head-cell-border-width` | `0 0 2px` |
| `$table-head-cell-color` | `$text-strong` |
| `$table-foot-cell-border-width` | `2px 0 0` |
| `$table-foot-cell-color` | `$text-strong` |
| `$table-row-hover-background-color` | `$white-bis` |
| `$table-row-active-background-color` | `$primary` |
| `$table-row-active-color` | `$primary-invert` |
| `$table-striped-row-even-background-color` | `$white-bis` |
| `$table-striped-row-even-hover-background-color` | `$white-ter` |

## 标签

默认情况下，标签是1.5英寸高的`label`。

```html
<span class="tag">
  Tag label
</span>
```

### 颜色

就像`button`一样，它也有10种不同的颜色可供选择。

```html
<span class="tag is-black">Black</span>
<span class="tag is-dark">Dark</span>
<span class="tag is-light">Light</span>
<span class="tag is-white">White</span>
<span class="tag is-primary">Primary</span>
<span class="tag is-link">Link</span>
<span class="tag is-info">Info</span>
<span class="tag is-success">Success</span>
<span class="tag is-warning">Warning</span>
<span class="tag is-danger">Danger</span>
```

### 尺寸大小

它有2个额外的尺寸设置：

```html
<span class="tag is-primary is-medium">Medium</span>
<span class="tag is-info is-large">Large</span>
```

你可以添加`is-rounded`修饰符来制作一个大圆角标签

```html
<span class="tag is-rounded">Rounded</span>
```

您可以添加`is-delete`修饰符来将标签转换为删除按钮。

```html
<a class="tag is-delete"></a>
```

### 组合使用

你可以在标签上附加一个删除按钮

```html
<span class="tag is-success">
  Bar
  <button class="delete is-small"></button>
</span>
<span class="tag is-warning is-medium">
  Hello
  <button class="delete is-small"></button>
</span>
<span class="tag is-danger is-large">
  World
  <button class="delete"></button>
</span>
```

### 标签列表

你可以使用`.tags`容器创建一个标签列表

```html
<div class="tags">
  <span class="tag">One</span>
  <span class="tag">Two</span>
  <span class="tag">Three</span>
</div>
```

如果列表很长，它会自动换行多行，同时保持所有标签间隔均匀。

```html
<div class="tags">
  <span class="tag">One</span>
  <span class="tag">Two</span>
  <span class="tag">Three</span>
  <span class="tag">Four</span>
  <span class="tag">Five</span>
  <span class="tag">Six</span>
  <span class="tag">Seven</span>
  <span class="tag">Eight</span>
  <span class="tag">Nine</span>
  <span class="tag">Ten</span>
  <span class="tag">Eleven</span>
  <span class="tag">Twelve</span>
  <span class="tag">Thirteen</span>
  <span class="tag">Fourteen</span>
  <span class="tag">Fifteen</span>
  <span class="tag">Sixteen</span>
  <span class="tag">Seventeen</span>
  <span class="tag">Eighteen</span>
  <span class="tag">Nineteen</span>
  <span class="tag">Twenty</span>
</div>
```

您可以使用`.has-addons`修饰符将标签附加在一起。(没有间距)

```html
<div class="tags has-addons">
  <span class="tag">Package</span>
  <span class="tag is-primary">Bulma</span>
</div>
```

您也可以将带有删除的标签和带有文本的标签附加在一起。

```html
<div class="tags has-addons">
  <span class="tag is-danger">Alex Smith</span>
  <a class="tag is-delete"></a>
</div>
```

如果要将`.tags`容器附加在一起，只需使用`.field`元素，以及`.is-grouped`和`.is-grouped-multiline`修饰符。

```html
<div class="field is-grouped is-grouped-multiline">
  <div class="control">
    <div class="tags has-addons">
      <span class="tag is-dark">npm</span>
      <span class="tag is-info">0.5.0</span>
    </div>
  </div>

  <div class="control">
    <div class="tags has-addons">
      <span class="tag is-dark">build</span>
      <span class="tag is-success">passing</span>
    </div>
  </div>

  <div class="control">
    <div class="tags has-addons">
      <span class="tag is-dark">chat</span>
      <span class="tag is-primary">on gitter</span>
    </div>
  </div>
</div>
```

这种场景很适合博客站点的标签列表

```html
<div class="field is-grouped is-grouped-multiline">
  <div class="control">
    <div class="tags has-addons">
      <a class="tag is-link">Technology</a>
      <a class="tag is-delete"></a>
    </div>
  </div>

  <div class="control">
    <div class="tags has-addons">
      <a class="tag is-link">CSS</a>
      <a class="tag is-delete"></a>
    </div>
  </div>

  <div class="control">
    <div class="tags has-addons">
      <a class="tag is-link">Flexbox</a>
      <a class="tag is-delete"></a>
    </div>
  </div>

  <div class="control">
    <div class="tags has-addons">
      <a class="tag is-link">Web Design</a>
      <a class="tag is-delete"></a>
    </div>
  </div>

  <div class="control">
    <div class="tags has-addons">
      <a class="tag is-link">Open Source</a>
      <a class="tag is-delete"></a>
    </div>
  </div>

  <div class="control">
    <div class="tags has-addons">
      <a class="tag is-link">Community</a>
      <a class="tag is-delete"></a>
    </div>
  </div>

  <div class="control">
    <div class="tags has-addons">
      <a class="tag is-link">Documentation</a>
      <a class="tag is-delete"></a>
    </div>
  </div>
</div>
```

### 变量

| Name | Default value |
| ---- | ------------- |
| `$tag-background-color` | `$background` |
| `$tag-color` | `$text` |
| `$tag-radius` | `$radius` |
| `$tag-delete-margin` | `1px` |

## 标题

在Bulma中，有两种不同类型的标题：

- `.title`
- `.subtitle`

```html
<h1 class="title">Title</h1>
<h2 class="subtitle">Subtitle</h2>
```

### 尺寸大小

有6种尺寸可供选择：

```html
<h1 class="title is-1">Title 1</h1>
<h2 class="title is-2">Title 2</h2>
<h3 class="title is-3">Title 3</h3>
<h4 class="title is-4">Title 4</h4>
<h5 class="title is-5">Title 5</h5>
<h6 class="title is-6">Title 6</h6>
```

```html
<h1 class="subtitle is-1">Subtitle 1</h1>
<h2 class="subtitle is-2">Subtitle 2</h2>
<h3 class="subtitle is-3">Subtitle 3</h3>
<h4 class="subtitle is-4">Subtitle 4</h4>
<h5 class="subtitle is-5">Subtitle 5</h5>
<h6 class="subtitle is-6">Subtitle 6</h6>
```

当你将标题和副标题结合在一起时，它们会靠得更近。

所以，作为一条经验，建议标题和副标题使用两个不同的尺寸。 如果您使用标题`is-1`，请将其与小标题`is-3`结合使用。

```html
<p class="title is-1">Title 1</p>
<p class="subtitle is-3">Subtitle 3</p>

<p class="title is-2">Title 2</p>
<p class="subtitle is-4">Subtitle 4</p>

<p class="title is-3">Title 3</p>
<p class="subtitle is-5">Subtitle 5</p>
```

如果在第一个元素上使用` is-spaced`修饰符，则可以保持标题和副标题之间的正常间距。

```html
<p class="title is-1 is-spaced">Title 1</p>
<p class="subtitle is-3">Subtitle 3</p>

<p class="title is-2 is-spaced">Title 2</p>
<p class="subtitle is-4">Subtitle 4</p>

<p class="title is-3 is-spaced">Title 3</p>
<p class="subtitle is-5">Subtitle 5</p>
```

### 变量

| Name | Default value |
| ---- | ------------- |
| `$title-color` | `$grey-darker` |
| `$title-size` | `$size-3` |
| `$title-weight` | `$weight-semibold` |
| `$title-strong-color` | `inherit` |
| `$title-strong-weight` | `inherit` |
| `$subtitle-color` | `$grey-dark` |
| `$subtitle-size` | `$size-5` |
| `$subtitle-weight` | `$weight-normal` |
| `$subtitle-strong-color` | `$grey-darker` |
| `$subtitle-strong-weight` | `$weight-semibold` |

# 组件

## 面包屑

你可以在Bulma中创建一个简单的面包屑组件来改善你的导航体验

面包屑组件只需要一个`.breadcrumb`容器标签和一个`ul`列表。分隔符是在`li`标签的`::before`伪元素的内容中自动创建的。您可以使用`li`标签中的`is-active`修饰符通知当前页面。 它将禁用内部链接的导航。

```html
<nav class="breadcrumb" aria-label="breadcrumbs">
  <ul>
    <li><a href="#">Bulma</a></li>
    <li><a href="#">Documentation</a></li>
    <li><a href="#">Components</a></li>
    <li class="is-active"><a href="#" aria-current="page">Breadcrumb</a></li>
  </ul>
</nav>
```

### 对齐

你可以在`.breadcrumb`容器上使用`is-centered`修饰符或`is-right`修饰符来选择面包屑如何对齐

```html
<!-- 居中对齐 -->
<nav class="breadcrumb is-centered" aria-label="breadcrumbs">
  <ul>
    <li><a href="#">Bulma</a></li>
    <li><a href="#">Documentation</a></li>
    <li><a href="#">Components</a></li>
    <li class="is-active"><a href="#" aria-current="page">Breadcrumb</a></li>
  </ul>
</nav>
```

```html
<!-- 向右对齐 -->
<nav class="breadcrumb is-right" aria-label="breadcrumbs">
  <ul>
    <li><a href="#">Bulma</a></li>
    <li><a href="#">Documentation</a></li>
    <li><a href="#">Components</a></li>
    <li class="is-active"><a href="#" aria-current="page">Breadcrumb</a></li>
  </ul>
</nav>
```

### 图标

您可以在面包屑上使用任何`Font Awesome`的图标。

```html
<nav class="breadcrumb" aria-label="breadcrumbs">
  <ul>
    <li><a href="#"><span class="icon is-small"><i class="fas fa-home"></i></span><span>Bulma</span></a></li>
    <li><a href="#"><span class="icon is-small"><i class="fas fa-book"></i></span><span>Documentation</span></a></li>
    <li><a href="#"><span class="icon is-small"><i class="fas fa-puzzle-piece"></i></span><span>Components</span></a></li>
    <li class="is-active"><a href="#" aria-current="page"><span class="icon is-small"><i class="fas fa-thumbs-up" aria-hidden="true"></i></span><span>Breadcrumb</span></a></li>
  </ul>
</nav>
```

### 替换分隔符

您可以选择4个附加分隔符：

- `has-arrow-separator`
- `has-bullet-separator`
- `has-dot-separator`
- `has-succeeds-separator`

```html
<nav class="breadcrumb has-arrow-separator" aria-label="breadcrumbs">
  <ul>
    <li><a href="#">Bulma</a></li>
    <li><a href="#">Documentation</a></li>
    <li><a href="#">Components</a></li>
    <li class="is-active"><a href="#" aria-current="page">Breadcrumb</a></li>
  </ul>
</nav>
```

```html
<nav class="breadcrumb has-bullet-separator" aria-label="breadcrumbs">
  <ul>
    <li><a href="#">Bulma</a></li>
    <li><a href="#">Documentation</a></li>
    <li><a href="#">Components</a></li>
    <li class="is-active"><a href="#" aria-current="page">Breadcrumb</a></li>
  </ul>
</nav>
```

```html
<nav class="breadcrumb has-dot-separator" aria-label="breadcrumbs">
  <ul>
    <li><a href="#">Bulma</a></li>
    <li><a href="#">Documentation</a></li>
    <li><a href="#">Components</a></li>
    <li class="is-active"><a href="#" aria-current="page">Breadcrumb</a></li>
  </ul>
</nav>
```

```html
<nav class="breadcrumb has-succeeds-separator" aria-label="breadcrumbs">
  <ul>
    <li><a href="#">Bulma</a></li>
    <li><a href="#">Documentation</a></li>
    <li><a href="#">Components</a></li>
    <li class="is-active"><a href="#" aria-current="page">Breadcrumb</a></li>
  </ul>
</nav>
```

### 尺寸大小

你可以选择3种尺寸：`is-small`、`is-medium`和`is=large`

```html
<nav class="breadcrumb is-small" aria-label="breadcrumbs">
  <ul>
    <li><a href="#">Bulma</a></li>
    <li><a href="#">Documentation</a></li>
    <li><a href="#">Components</a></li>
    <li class="is-active"><a href="#" aria-current="page">Breadcrumb</a></li>
  </ul>
</nav>
```

```html
<nav class="breadcrumb is-medium" aria-label="breadcrumbs">
  <ul>
    <li><a href="#">Bulma</a></li>
    <li><a href="#">Documentation</a></li>
    <li><a href="#">Components</a></li>
    <li class="is-active"><a href="#" aria-current="page">Breadcrumb</a></li>
  </ul>
</nav>
```

```html
<nav class="breadcrumb is-large" aria-label="breadcrumbs">
  <ul>
    <li><a href="#">Bulma</a></li>
    <li><a href="#">Documentation</a></li>
    <li><a href="#">Components</a></li>
    <li class="is-active"><a href="#" aria-current="page">Breadcrumb</a></li>
  </ul>
</nav>
```

### 变量

| Name | Default value |
| ---- | ------------- |
| `$breadcrumb-item-color` | `$link` |
| `$breadcrumb-item-hover-color` | `$link-hover` |
| `$breadcrumb-item-active-color` | `$text-strong` |
| `$breadcrumb-item-separator-color` | `$text` |

## 卡片

卡片是一个全能且灵活的可组合组件，卡组件包含多个可混合搭配的元素：

<ul style="list-style:disc outside;margin-top:1em;"><li><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding: 0.25em 0.5em 0.25em;">card</code> 主容器<ul style="list-style:disc outside;"><li><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding: 0.25em 0.5em 0.25em;">card-header</code> 一个带阴影效果的横向排列的bar<ul style="list-style:disc outside;"><li><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding: 0.25em 0.5em 0.25em;">card-header-title</code> 一个靠左排列的粗体文本</li><li><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding: 0.25em 0.5em 0.25em;">card-header-icon</code> 一个图标的占位符</li></ul></li><li><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding: 0.25em 0.5em 0.25em;">card-image</code> 一个100%宽度的响应式图片</li><li><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding: 0.25em 0.5em 0.25em;">card-content</code> 一个用于任何其他元素的多用途容器</li><li><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding: 0.25em 0.5em 0.25em;">card-footer</code> 一个水平排列的控件列表<ul style="list-style:disc outside;"><li><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding: 0.25em 0.5em 0.25em;">card-footer-item</code> 一个可重复的清单项目</li></ul></li></ul></li></ul>

你可以通过添加`is0centered`修饰符来让带有`card-header-title`的标题居中显示

```html
<div class="card">
  <div class="card-image">
    <figure class="image is-4by3">
      <img src="https://bulma.io/images/placeholders/1280x960.png" alt="Placeholder image">
    </figure>
  </div>
  <div class="card-content">
    <div class="media">
      <div class="media-left">
        <figure class="image is-48x48">
          <img src="https://bulma.io/images/placeholders/96x96.png" alt="Placeholder image">
        </figure>
      </div>
      <div class="media-content">
        <p class="title is-4">John Smith</p>
        <p class="subtitle is-6">@johnsmith</p>
      </div>
    </div>

    <div class="content">
      Lorem ipsum dolor sit amet, consectetur adipiscing elit.
      Phasellus nec iaculis mauris. <a>@bulmaio</a>.
      <a href="#">#css</a> <a href="#">#responsive</a>
      <br>
      <time datetime="2016-1-1">11:09 PM - 1 Jan 2016</time>
    </div>
  </div>
</div>
```

```html
<div class="card">
  <header class="card-header">
    <p class="card-header-title">
      Component
    </p>
    <a href="#" class="card-header-icon" aria-label="more options">
      <span class="icon">
        <i class="fas fa-angle-down" aria-hidden="true"></i>
      </span>
    </a>
  </header>
  <div class="card-content">
    <div class="content">
      Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus nec iaculis mauris.
      <a href="#">@bulmaio</a>. <a href="#">#css</a> <a href="#">#responsive</a>
      <br>
      <time datetime="2016-1-1">11:09 PM - 1 Jan 2016</time>
    </div>
  </div>
  <footer class="card-footer">
    <a href="#" class="card-footer-item">Save</a>
    <a href="#" class="card-footer-item">Edit</a>
    <a href="#" class="card-footer-item">Delete</a>
  </footer>
</div>
```

```html
<div class="card">
  <div class="card-content">
    <p class="title">
      “There are two hard things in computer science: cache invalidation, naming things, and off-by-one errors.”
    </p>
    <p class="subtitle">
      Jeff Atwood
    </p>
  </div>
  <footer class="card-footer">
    <p class="card-footer-item">
      <span>
        View on <a href="https://twitter.com/codinghorror/status/506010907021828096">Twitter</a>
      </span>
    </p>
    <p class="card-footer-item">
      <span>
        Share on <a href="#">Facebook</a>
      </span>
    </p>
  </footer>
</div>
```

### 变量

| Name | Default value |
| ---- | ------------- |
| `$card-color` | `$text` |
| `$card-background-color` | `$white` |
| `$card-shadow` | `0 2px 3px rgba($black, 0.1), 0 0 0 1px rgba($black, 0.1)` |
| `$card-header-color` | `$text-strong` |
| `$card-header-shadow` | `0 1px 2px rgba($black, 0.1)` |
| `$card-header-weight` | `$weight-bold` |
| `$card-footer-border-top` | `1px solid $border` |

## 下拉

下拉组件是下拉按钮和下拉菜单的容器。

<ul style="list-style:disc outside;margin-top:1em;"><li><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding:0.25em 0.5em 0.25em;">dropdown</code> 主容器<ul style="list-style:disc outside;"><li><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding:0.25em 0.5em 0.25em;">dropdown-trigger</code> 一个带`button`的容器</li><li><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding:0.25em 0.5em 0.25em;">dropdown-menu</code> 可切换菜单，默认隐藏<ul style="list-style:disc outside;"><li><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding:0.25em 0.5em 0.25em;">dropdown-content</code> 带有白色背景和阴影的下拉框<ul style="list-style:disc outside;"><li><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding:0.25em 0.5em 0.25em;">dropdown-item</code> 下拉菜单中的每个项目，可以是`a`标签或`div`标签</li><li><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding:0.25em 0.5em 0.25em;">dropdown-divider</code> 用于分隔下拉项目的水平线</li></ul></li></ul></li></ul></li></ul>

```html
<div class="dropdown is-active">
  <div class="dropdown-trigger">
    <button class="button" aria-haspopup="true" aria-controls="dropdown-menu">
      <span>Dropdown button</span>
      <span class="icon is-small">
        <i class="fas fa-angle-down" aria-hidden="true"></i>
      </span>
    </button>
  </div>
  <div class="dropdown-menu" id="dropdown-menu" role="menu">
    <div class="dropdown-content">
      <a href="#" class="dropdown-item">
        Dropdown item
      </a>
      <a class="dropdown-item">
        Other dropdown item
      </a>
      <a href="#" class="dropdown-item is-active">
        Active dropdown item
      </a>
      <a href="#" class="dropdown-item">
        Other dropdown item
      </a>
      <hr class="dropdown-divider">
      <a href="#" class="dropdown-item">
        With a divider
      </a>
    </div>
  </div>
</div>
```

### 下拉内容

虽然下拉菜单项可以用作锚链接`<a>`，但您也可以使用`<div>`并插入几乎任何类型的内容。

```html
<div class="dropdown is-active">
  <div class="dropdown-trigger">
    <button class="button" aria-haspopup="true" aria-controls="dropdown-menu2">
      <span>Content</span>
      <span class="icon is-small">
        <i class="fas fa-angle-down" aria-hidden="true"></i>
      </span>
    </button>
  </div>
  <div class="dropdown-menu" id="dropdown-menu2" role="menu">
    <div class="dropdown-content">
      <div class="dropdown-item">
        <p>You can insert <strong>any type of content</strong> within the dropdown menu.</p>
      </div>
      <hr class="dropdown-divider">
      <div class="dropdown-item">
        <p>You simply need to use a <code><div></code> instead.</p>
      </div>
      <hr class="dropdown-divider">
      <a href="#" class="dropdown-item">
        This is a link
      </a>
    </div>
  </div>
</div>
```

### 点击出现和鼠标划入切换

下拉组件有两个额外的修饰符：

- `is-hoverable`: 当悬停下拉触发器时，下拉菜单会显示出来
- `is-active`: 下拉菜单会一直显示

```html
<div class="dropdown">
  <div class="dropdown-trigger">
    <button class="button" aria-haspopup="true" aria-controls="dropdown-menu3">
      <span>Click me</span>
      <span class="icon is-small">
        <i class="fas fa-angle-down" aria-hidden="true"></i>
      </span>
    </button>
  </div>
  <div class="dropdown-menu" id="dropdown-menu3" role="menu">
    <div class="dropdown-content">
      <a href="#" class="dropdown-item">
        Overview
      </a>
      <a href="#" class="dropdown-item">
        Modifiers
      </a>
      <a href="#" class="dropdown-item">
        Grid
      </a>
      <a href="#" class="dropdown-item">
        Form
      </a>
      <a href="#" class="dropdown-item">
        Elements
      </a>
      <a href="#" class="dropdown-item">
        Components
      </a>
      <a href="#" class="dropdown-item">
        Layout
      </a>
      <hr class="dropdown-divider">
      <a href="#" class="dropdown-item">
        More
      </a>
    </div>
  </div>
</div>

<div class="dropdown is-hoverable">
  <div class="dropdown-trigger">
    <button class="button" aria-haspopup="true" aria-controls="dropdown-menu4">
      <span>Hover me</span>
      <span class="icon is-small">
        <i class="fas fa-angle-down" aria-hidden="true"></i>
      </span>
    </button>
  </div>
  <div class="dropdown-menu" id="dropdown-menu4" role="menu">
    <div class="dropdown-content">
      <div class="dropdown-item">
        <p>You can insert <strong>any type of content</strong> within the dropdown menu.</p>
      </div>
    </div>
  </div>
</div>
```

### 右对齐

默认情况下，下拉是左对齐的，你可以添加`is-right`修饰符来将下拉右对齐

```html
<div class="dropdown is-right is-active">
  <div class="dropdown-trigger">
    <button class="button" aria-haspopup="true" aria-controls="dropdown-menu6">
      <span>Right aligned</span>
      <span class="icon is-small">
        <i class="fas fa-angle-down" aria-hidden="true"></i>
      </span>
    </button>
  </div>
  <div class="dropdown-menu" id="dropdown-menu6" role="menu">
    <div class="dropdown-content">
      <div class="dropdown-item">
        <p>Add the <code>is-right</code> modifier for a <strong>right-aligned</strong> dropdown.</p>
      </div>
    </div>
  </div>
</div>
```

您可以添加`is-up`修饰符,以在下拉按钮上方显示下拉菜单。

```html
<div class="dropdown is-up">
  <div class="dropdown-trigger">
    <button class="button" aria-haspopup="true" aria-controls="dropdown-menu7">
      <span>Dropup button</span>
      <span class="icon is-small">
        <i class="fas fa-angle-up" aria-hidden="true"></i>
      </span>
    </button>
  </div>
  <div class="dropdown-menu" id="dropdown-menu7" role="menu">
    <div class="dropdown-content">
      <div class="dropdown-item">
        <p>You can add the <code>is-up</code> modifier to have a dropdown menu that appears above the dropdown button.</p>
      </div>
    </div>
  </div>
</div>
```

### 变量

| Name | Default value |
| ---- | ------------- |
| `$dropdown-content-background-color` | `$white` |
| `$dropdown-content-arrow` | `$link` |
| `$dropdown-content-offset` | `4px` |
| `$dropdown-content-radius` | `$radius` |
| `$dropdown-content-shadow` | `0 2px 3px rgba($black, 0.1), 0 0 0 1px rgba($black, 0.1)` |
| `$dropdown-content-z` | `20` |
| `$dropdown-item-color` | `$grey-dark` |
| `$dropdown-item-hover-color` | `$black` |
| `$dropdown-item-hover-background-color` | `$background` |
| `$dropdown-item-active-color` | `$link-invert` |
| `$dropdown-item-active-background-color` | `$link` |
| `$dropdown-divider-background-color` | `$border` |

## 菜单

Bulma中的菜单，适用于任何类型的垂直导航

```html
<aside class="menu">
  <p class="menu-label">
    General
  </p>
  <ul class="menu-list">
    <li><a>Dashboard</a></li>
    <li><a>Customers</a></li>
  </ul>
  <p class="menu-label">
    Administration
  </p>
  <ul class="menu-list">
    <li><a>Team Settings</a></li>
    <li>
      <a class="is-active">Manage Your Team</a>
      <ul>
        <li><a>Members</a></li>
        <li><a>Plugins</a></li>
        <li><a>Add a member</a></li>
      </ul>
    </li>
    <li><a>Invitations</a></li>
    <li><a>Cloud Storage Environment Settings</a></li>
    <li><a>Authentication</a></li>
  </ul>
  <p class="menu-label">
    Transactions
  </p>
  <ul class="menu-list">
    <li><a>Payments</a></li>
    <li><a>Transfers</a></li>
    <li><a>Balance</a></li>
  </ul>
</aside>
```

### 变量

| Name | Default value |
| ---- | ------------- |
| `$menu-item-color` | `$text` |
| `$menu-item-radius` | `$radius-small` |
| `$menu-item-hover-color` | `$text-strong` |
| `$menu-item-hover-background-color` | `$background` |
| `$menu-item-active-color` | `$link-invert` |
| `$menu-item-active-background-color` | `$link` |
| `$menu-list-border-left` | `1px solid $border` |
| `$menu-label-color` | `$text-light` |

## 消息

你可以在Bulma中创建彩色的消息区块，以强调这块区域的重要性

```html
<article class="message">
  <div class="message-header">
    <p>Hello World</p>
    <button class="delete" aria-label="delete"></button>
  </div>
  <div class="message-body">
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. <strong>Pellentesque risus mi</strong>, tempus quis placerat ut, porta nec nulla. Vestibulum rhoncus ac ex sit amet fringilla. Nullam gravida purus diam, et dictum <a>felis venenatis</a> efficitur. Aenean ac <em>eleifend lacus</em>, in mollis lectus. Donec sodales, arcu et sollicitudin porttitor, tortor urna tempor ligula, id porttitor mi magna a neque. Donec dui urna, vehicula et sem eget, facilisis sodales sem.
  </div>
</article>
```

### 颜色

```html
<article class="message is-dark">
  <div class="message-header">
    <p>Dark</p>
    <button class="delete" aria-label="delete"></button>
  </div>
  <div class="message-body">
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. <strong>Pellentesque risus mi</strong>, tempus quis placerat ut, porta nec nulla. Vestibulum rhoncus ac ex sit amet fringilla. Nullam gravida purus diam, et dictum <a>felis venenatis</a> efficitur. Aenean ac <em>eleifend lacus</em>, in mollis lectus. Donec sodales, arcu et sollicitudin porttitor, tortor urna tempor ligula, id porttitor mi magna a neque. Donec dui urna, vehicula et sem eget, facilisis sodales sem.
  </div>
</article>

<article class="message is-primary">
  <div class="message-header">
    <p>Primary</p>
    <button class="delete" aria-label="delete"></button>
  </div>
  <div class="message-body">
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. <strong>Pellentesque risus mi</strong>, tempus quis placerat ut, porta nec nulla. Vestibulum rhoncus ac ex sit amet fringilla. Nullam gravida purus diam, et dictum <a>felis venenatis</a> efficitur. Aenean ac <em>eleifend lacus</em>, in mollis lectus. Donec sodales, arcu et sollicitudin porttitor, tortor urna tempor ligula, id porttitor mi magna a neque. Donec dui urna, vehicula et sem eget, facilisis sodales sem.
  </div>
</article>

<article class="message is-link">
  <div class="message-header">
    <p>Link</p>
    <button class="delete" aria-label="delete"></button>
  </div>
  <div class="message-body">
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. <strong>Pellentesque risus mi</strong>, tempus quis placerat ut, porta nec nulla. Vestibulum rhoncus ac ex sit amet fringilla. Nullam gravida purus diam, et dictum <a>felis venenatis</a> efficitur. Aenean ac <em>eleifend lacus</em>, in mollis lectus. Donec sodales, arcu et sollicitudin porttitor, tortor urna tempor ligula, id porttitor mi magna a neque. Donec dui urna, vehicula et sem eget, facilisis sodales sem.
  </div>
</article>

<article class="message is-info">
  <div class="message-header">
    <p>Info</p>
    <button class="delete" aria-label="delete"></button>
  </div>
  <div class="message-body">
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. <strong>Pellentesque risus mi</strong>, tempus quis placerat ut, porta nec nulla. Vestibulum rhoncus ac ex sit amet fringilla. Nullam gravida purus diam, et dictum <a>felis venenatis</a> efficitur. Aenean ac <em>eleifend lacus</em>, in mollis lectus. Donec sodales, arcu et sollicitudin porttitor, tortor urna tempor ligula, id porttitor mi magna a neque. Donec dui urna, vehicula et sem eget, facilisis sodales sem.
  </div>
</article>

<article class="message is-success">
  <div class="message-header">
    <p>Success</p>
    <button class="delete" aria-label="delete"></button>
  </div>
  <div class="message-body">
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. <strong>Pellentesque risus mi</strong>, tempus quis placerat ut, porta nec nulla. Vestibulum rhoncus ac ex sit amet fringilla. Nullam gravida purus diam, et dictum <a>felis venenatis</a> efficitur. Aenean ac <em>eleifend lacus</em>, in mollis lectus. Donec sodales, arcu et sollicitudin porttitor, tortor urna tempor ligula, id porttitor mi magna a neque. Donec dui urna, vehicula et sem eget, facilisis sodales sem.
  </div>
</article>

<article class="message is-warning">
  <div class="message-header">
    <p>Warning</p>
    <button class="delete" aria-label="delete"></button>
  </div>
  <div class="message-body">
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. <strong>Pellentesque risus mi</strong>, tempus quis placerat ut, porta nec nulla. Vestibulum rhoncus ac ex sit amet fringilla. Nullam gravida purus diam, et dictum <a>felis venenatis</a> efficitur. Aenean ac <em>eleifend lacus</em>, in mollis lectus. Donec sodales, arcu et sollicitudin porttitor, tortor urna tempor ligula, id porttitor mi magna a neque. Donec dui urna, vehicula et sem eget, facilisis sodales sem.
  </div>
</article>

<article class="message is-danger">
  <div class="message-header">
    <p>Danger</p>
    <button class="delete" aria-label="delete"></button>
  </div>
  <div class="message-body">
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. <strong>Pellentesque risus mi</strong>, tempus quis placerat ut, porta nec nulla. Vestibulum rhoncus ac ex sit amet fringilla. Nullam gravida purus diam, et dictum <a>felis venenatis</a> efficitur. Aenean ac <em>eleifend lacus</em>, in mollis lectus. Donec sodales, arcu et sollicitudin porttitor, tortor urna tempor ligula, id porttitor mi magna a neque. Donec dui urna, vehicula et sem eget, facilisis sodales sem.
  </div>
</article>
```

### 没有头部的消息区块

在制作消息区块时，你可以省略消息的标题：

```html
<article class="message">
  <div class="message-body">
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. <strong>Pellentesque risus mi</strong>, tempus quis placerat ut, porta nec nulla. Vestibulum rhoncus ac ex sit amet fringilla. Nullam gravida purus diam, et dictum <a>felis venenatis</a> efficitur. Aenean ac <em>eleifend lacus</em>, in mollis lectus. Donec sodales, arcu et sollicitudin porttitor, tortor urna tempor ligula, id porttitor mi magna a neque. Donec dui urna, vehicula et sem eget, facilisis sodales sem.
  </div>
</article>
<article class="message is-dark">
  <div class="message-body">
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. <strong>Pellentesque risus mi</strong>, tempus quis placerat ut, porta nec nulla. Vestibulum rhoncus ac ex sit amet fringilla. Nullam gravida purus diam, et dictum <a>felis venenatis</a> efficitur. Aenean ac <em>eleifend lacus</em>, in mollis lectus. Donec sodales, arcu et sollicitudin porttitor, tortor urna tempor ligula, id porttitor mi magna a neque. Donec dui urna, vehicula et sem eget, facilisis sodales sem.
  </div>
</article>

<article class="message is-primary">
  <div class="message-body">
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. <strong>Pellentesque risus mi</strong>, tempus quis placerat ut, porta nec nulla. Vestibulum rhoncus ac ex sit amet fringilla. Nullam gravida purus diam, et dictum <a>felis venenatis</a> efficitur. Aenean ac <em>eleifend lacus</em>, in mollis lectus. Donec sodales, arcu et sollicitudin porttitor, tortor urna tempor ligula, id porttitor mi magna a neque. Donec dui urna, vehicula et sem eget, facilisis sodales sem.
  </div>
</article>

<article class="message is-link">
  <div class="message-body">
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. <strong>Pellentesque risus mi</strong>, tempus quis placerat ut, porta nec nulla. Vestibulum rhoncus ac ex sit amet fringilla. Nullam gravida purus diam, et dictum <a>felis venenatis</a> efficitur. Aenean ac <em>eleifend lacus</em>, in mollis lectus. Donec sodales, arcu et sollicitudin porttitor, tortor urna tempor ligula, id porttitor mi magna a neque. Donec dui urna, vehicula et sem eget, facilisis sodales sem.
  </div>
</article>

<article class="message is-info">
  <div class="message-body">
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. <strong>Pellentesque risus mi</strong>, tempus quis placerat ut, porta nec nulla. Vestibulum rhoncus ac ex sit amet fringilla. Nullam gravida purus diam, et dictum <a>felis venenatis</a> efficitur. Aenean ac <em>eleifend lacus</em>, in mollis lectus. Donec sodales, arcu et sollicitudin porttitor, tortor urna tempor ligula, id porttitor mi magna a neque. Donec dui urna, vehicula et sem eget, facilisis sodales sem.
  </div>
</article>

<article class="message is-success">
  <div class="message-body">
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. <strong>Pellentesque risus mi</strong>, tempus quis placerat ut, porta nec nulla. Vestibulum rhoncus ac ex sit amet fringilla. Nullam gravida purus diam, et dictum <a>felis venenatis</a> efficitur. Aenean ac <em>eleifend lacus</em>, in mollis lectus. Donec sodales, arcu et sollicitudin porttitor, tortor urna tempor ligula, id porttitor mi magna a neque. Donec dui urna, vehicula et sem eget, facilisis sodales sem.
  </div>
</article>

<article class="message is-warning">
  <div class="message-body">
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. <strong>Pellentesque risus mi</strong>, tempus quis placerat ut, porta nec nulla. Vestibulum rhoncus ac ex sit amet fringilla. Nullam gravida purus diam, et dictum <a>felis venenatis</a> efficitur. Aenean ac <em>eleifend lacus</em>, in mollis lectus. Donec sodales, arcu et sollicitudin porttitor, tortor urna tempor ligula, id porttitor mi magna a neque. Donec dui urna, vehicula et sem eget, facilisis sodales sem.
  </div>
</article>

<article class="message is-danger">
  <div class="message-body">
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. <strong>Pellentesque risus mi</strong>, tempus quis placerat ut, porta nec nulla. Vestibulum rhoncus ac ex sit amet fringilla. Nullam gravida purus diam, et dictum <a>felis venenatis</a> efficitur. Aenean ac <em>eleifend lacus</em>, in mollis lectus. Donec sodales, arcu et sollicitudin porttitor, tortor urna tempor ligula, id porttitor mi magna a neque. Donec dui urna, vehicula et sem eget, facilisis sodales sem.
  </div>
</article>
```

### 尺寸大小

```html
<article class="message is-small">
  <div class="message-header">
    <p>Small message</p>
    <button class="delete is-small" aria-label="delete"></button>
  </div>
  <div class="message-body">
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. <strong>Pellentesque risus mi</strong>, tempus quis placerat ut, porta nec nulla.Nullam gravida purus diam, et dictum <a>felis venenatis</a> efficitur. Aenean ac <em>eleifend lacus</em>, in mollis lectus.
  </div>
</article>
```

```html
<article class="message">
  <div class="message-header">
    <p>Normal message</p>
    <button class="delete" aria-label="delete"></button>
  </div>
  <div class="message-body">
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. <strong>Pellentesque risus mi</strong>, tempus quis placerat ut, porta nec nulla.Nullam gravida purus diam, et dictum <a>felis venenatis</a> efficitur. Aenean ac <em>eleifend lacus</em>, in mollis lectus.
  </div>
</article>
```

```html
<article class="message is-medium">
  <div class="message-header">
    <p>Medium message</p>
    <button class="delete is-medium" aria-label="delete"></button>
  </div>
  <div class="message-body">
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. <strong>Pellentesque risus mi</strong>, tempus quis placerat ut, porta nec nulla.Nullam gravida purus diam, et dictum <a>felis venenatis</a> efficitur. Aenean ac <em>eleifend lacus</em>, in mollis lectus.
  </div>
</article>
```

```html
<article class="message is-large">
  <div class="message-header">
    <p>Large message</p>
    <button class="delete is-large" aria-label="delete"></button>
  </div>
  <div class="message-body">
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. <strong>Pellentesque risus mi</strong>, tempus quis placerat ut, porta nec nulla.Nullam gravida purus diam, et dictum <a>felis venenatis</a> efficitur. Aenean ac <em>eleifend lacus</em>, in mollis lectus.
  </div>
</article>
```

### 变量

| Name | Default value |
| ---- | ------------- |
| `$message-background-color` | `$background` |
| `$message-radius` | `$radius` |
| `$message-header-background-color` | `$text` |
| `$message-header-color` | `$text-invert` |
| `$message-header-padding` | `0.5em 0.75em` |
| `$message-header-radius` | `$radius` |
| `$message-body-border` | `1px solid $border` |
| `$message-body-color` | `$text` |
| `$message-body-padding` | `1em 1.25em` |
| `$message-body-radius` | `$radius` |
| `$message-body-pre-background-color` | `$white` |
| `$message-body-pre-code-background-color` | `transparent` |

## 模态框

你可以在Bulma中创建经典的模态框，其中可以包含任何你想要的内容

模态框的结构如下：

<ul style="list-style:disc outside;margin-top:1em;"><li><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding:0.25em 0.5em 0.25em;">modal</code> 主容器<ul style="list-style:disc outside;"><li><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding:0.25em 0.5em 0.25em;">modal-background</code> 一个透明的覆盖层，可以当做一个关闭按钮来关闭模态框</li><li><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding:0.25em 0.5em 0.25em;">modal-content</code> 一个水平和垂直居中的容器，最大宽度为640px，其中可以包含任何内容</li><li><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding:0.25em 0.5em 0.25em;">modal-close</code> 一个简单的位于右上角的关闭按钮</li></ul></li></ul>

```html
<div class="modal">
  <div class="modal-background"></div>
  <div class="modal-content">
    <!-- Any other Bulma elements you want -->
  </div>
  <button class="modal-close is-large" aria-label="close"></button>
</div>
```

如果想要一开始就激活模态框，只需在`.modal`容器上添加`is-active`修饰符即可

<div style="background-color:#fff5f7;border-radius:3px;font-size:1rem;font-weight:400;line-height:1.5;"><div style="background-color:#ff3860;color:#fff;-webkit-box-align:center;align-items:center;border-radius:3px 3px 0 0;display:flex;-webkit-box-pack:justify;justify-content:space-between;line-height:1.25;padding:0.5em 0.75em;position: relative;">不包含JavaScript</div><div style="border-color:#ff3860;color:#cd0930;border-top-left-radius:0;border-top-right-radius:0;border-top:none;border: 1px solid #dbdbdb;border-radius:3px;padding:1em 1.25em;">Bulma不包括任何JavaScript交互， 你必须自己使用JavaScript来实现这些类的切换。</div></div>

### 图片模态框

因为模态框可以包含任何你想要的东西，所以你可以非常简单的构建一个图片模态框

```html
<div class="modal">
  <div class="modal-background"></div>
  <div class="modal-content">
    <p class="image is-4by3">
      <img src="https://bulma.io/images/placeholders/1280x960.png" alt="">
    </p>
  </div>
  <button class="modal-close is-large" aria-label="close"></button>
</div>
```

如果你想要创建一个完整的经典的模态框，包含头部、内容和脚部，那就使用`modal-card`

```html
<div class="modal">
  <div class="modal-background"></div>
  <div class="modal-card">
    <header class="modal-card-head">
      <p class="modal-card-title">Modal title</p>
      <button class="delete" aria-label="close"></button>
    </header>
    <section class="modal-card-body">
      <!-- Content ... -->
    </section>
    <footer class="modal-card-foot">
      <button class="button is-success">Save changes</button>
      <button class="button">Cancel</button>
    </footer>
  </div>
</div>`
```

### 变量

| Name | Default value |
| ---- | ------------- |
| `$modal-z` | `20` |
| `$modal-background-background-color` | `rgba($black, 0.86)` |
| `$modal-content-width` | `640px` |
| `$modal-content-margin-mobile` | `20px` |
| `$modal-content-spacing-mobile` | `160px` |
| `$modal-content-spacing-tablet` | `40px` |
| `$modal-close-dimensions` | `40px` |
| `$modal-close-right` | `20px` |
| `$modal-close-top` | `20px` |
| `$modal-card-spacing` | `40px` |
| `$modal-card-head-background-color` | `$background` |
| `$modal-card-head-border-bottom` | `1px solid $border` |
| `$modal-card-head-padding` | `20px` |
| `$modal-card-head-radius` | `$radius-large` |
| `$modal-card-title-color` | `$text-strong` |
| `$modal-card-title-line-height` | `1` |
| `$modal-card-title-size` | `$size-4` |
| `$modal-card-foot-radius` | `$radius-large` |
| `$modal-card-foot-border-top` | `1px solid $border` |
| `$modal-card-body-background-color` | `$white` |
| `$modal-card-body-padding` | `20px` |

## 导航栏

你可以在Bulma中创建响应式水平导航栏，可以支持图片，链接，按钮和下拉菜单。

导航栏组件是响应式和多功能水平导航栏，它具有以下结构：

<ul style="list-style:disc outside;margin-top:1em;"><li><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding:0.25em 0.5em 0.25em;">navbar</code> 主容器<ul style="list-style:disc outside;"><li><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding:0.25em 0.5em 0.25em;">navbar-brand</code> 左侧部分，始终可见，通常包含徽标和可选的链接或图标<ul style="list-style:disc outside;"><li><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding:0.25em 0.5em 0.25em;">navbar-burger</code> 汉堡图标，用于在触摸设备上切换导航栏菜单</li></ul></li><li><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding:0.25em 0.5em 0.25em;">navbar-menu</code> 右侧部分，在触摸设备上隐藏，在桌面环境始终可见<ul style="list-style:disc outside;"><li><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding:0.25em 0.5em 0.25em;">navbar-start</code> 菜单的左侧部</li><li><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding:0.25em 0.5em 0.25em;">navbar-end</code> 菜单的右侧部分，它出现在导航栏的末尾<ul style="list-style:disc outside;"><li><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding:0.25em 0.5em 0.25em;">navbar-item</code> 导航栏的每个项目，可以是<code>a</code>标签或<code>div</code>标签<ul style="list-style:disc outside;"><li><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding:0.25em 0.5em 0.25em;">navbar-link</code> 导航的下拉菜单项，带有箭头指示</li><li><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding:0.25em 0.5em 0.25em;">navbar-dropdown</code> 下拉菜单，其中可以包含导航栏项目和分隔符<ul style="list-style:disc outside;"><li><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding:0.25em 0.5em 0.25em;">navbar-divider</code> 用于分隔导航栏项目的水平线</li></ul></li></ul></li></ul></li></ul></li></ul></li></ul>

### 导航栏Logo标志位

导航栏Logo标志位位于其左侧，它可以包含：

- 一些`navbar-item`
- `navbar-burger`作为其最后一个子元素

```html
<nav class="navbar" role="navigation" aria-label="main navigation">
  <div class="navbar-brand">
    <!-- navbar items, navbar burger... -->
  </div>
</nav>
```

在触摸设备上(width <1024)和桌面(width > 1024)上，导航栏的Logo标志位是始终可见的，因此建议只使用少数导航栏项目，以避免在小设备上水平溢出。

```html
<nav class="navbar" role="navigation" aria-label="main navigation">
  <div class="navbar-brand">
    <a class="navbar-item" href="https://bulma.io">
      <img src="https://bulma.io/images/bulma-logo.png" alt="Bulma: a modern CSS framework based on Flexbox" width="112" height="28">
    </a>

    <div class="navbar-burger">
      <span></span>
      <span></span>
      <span></span>
    </div>
  </div>
</nav>
```

### 汉堡菜单

汉堡菜单进会出现在手机上，它必须作为导航栏Logo标志位的最后一个子元素出现

```html
<div class="navbar-burger">
  <span></span>
  <span></span>
  <span></span>
</div>
```

您可以添加修饰符类`is-active`将其变为可点击的关闭十字按钮

### 导航菜单

导航栏菜单是导航栏Logo标志位的对应部分。 因此，它必须以导航Logo标志位的兄弟元素的身份出现在导航栏中

```html
<nav class="navbar" role="navigation" aria-label="main navigation">
  <div class="navbar-brand">
    <!-- navbar items, navbar burger... -->
  </div>
  <div class="navbar-menu">
    <!-- navbar start, navbar end -->
  </div>
</nav>
```

在宽度小于1024像素的触控设备上，导航栏菜单是隐藏的， 如果你需要显示它，你需要添加`is-active`修饰符类。

```html
<div class="navbar-menu">
  <!-- hidden on mobile -->
</div>

<div class="navbar-menu is-active">
  <!-- shown on mobile -->
</div>
```

在宽度大于1024像素的桌面设备上，导航栏菜单将填充导航栏中所有可用的空间，导航栏Logo标志位只需要它所需的空间。 但是，它需要两个直接的子元素：

- `navbar-start`
- `navbar-end`

<div style="background-color:#f6fbfe;border-radius:3px;font-size:1rem;"><h4 style="background-color:#209cee;color:#fff;-webkit-box-align:center;align-items:center;border-radius:3px 3px 0 0;display:flex;-webkit-box-pack:justify;justify-content:space-between;line-height:1.25;padding:0.5em 0.75em;position:relative;">使用JavaScript实现切换</h4><div style="border-color:#209cee;color:#12537e;border:1px solid #dbdbdb;border-radius:3px;padding:1em 1.25em;"><div class="content"><p>在Bulma中不包含任何JavaScript代码<br>下面是一个示例，演示如何使用`is-active`修饰符来切换导航栏Logo标志位和导航菜单。</p><figure style="background-color:#f5f5f5;color:#586e75;position:relative;"><pre style="white-space:pre-wrap;background-color:white;overflow:auto;max-width:100%;padding:1.25em 1.5em;word-wrap:normal;color:#4a4a4a;font-size: 0.875em;"><code style="background-color:transparent;color:currentColor;font-size:1em;padding:0;font-weight:normal;" data-lang="html"><span class="nt"><div</span> <span class="na">class=</span><span class="s">"navbar-burger"</span> <span class="na">data-target=</span><span class="s">"navMenu"</span><span class="nt">></span>
  <span class="nt"><span></span></span>
  <span class="nt"><span></span></span>
  <span class="nt"><span></span></span>
<span class="nt"></div></span>

<span class="nt"><div</span> <span class="na">class=</span><span class="s">"navbar-menu"</span> <span class="na">id=</span><span class="s">"navMenu"</span><span class="nt">></span>
  <span class="c"><!-- navbar-start, navbar-end... --></span>
<span class="nt"></div></span></code></pre></figure>
          <figure style="background-color:#f5f5f5;color:#586e75;position:relative;"><pre style="white-space:pre-wrap;background-color:white;overflow:auto;max-width:100%;padding:1.25em 1.5em;word-wrap:normal;color:#4a4a4a;font-size: 0.875em;"><code style="background-color:transparent;color:currentColor;font-size:1em;padding:0;font-weight:normal;" data-lang="javascript"><span class="nb">document</span><span class="p">.</span><span class="nx">addEventListener</span><span class="p">(</span><span class="s1">'DOMContentLoaded'</span><span class="p">,</span> <span class="kd">function</span> <span class="p">()</span> <span class="p">{</span>

  <span class="c1">// Get all "navbar-burger" elements</span>
  <span class="kd">var</span> <span class="nx">$navbarBurgers</span> <span class="o">=</span> <span class="nb">Array</span><span class="p">.</span><span class="nx">prototype</span><span class="p">.</span><span class="nx">slice</span><span class="p">.</span><span class="nx">call</span><span class="p">(</span><span class="nb">document</span><span class="p">.</span><span class="nx">querySelectorAll</span><span class="p">(</span><span class="s1">'.navbar-burger'</span><span class="p">),</span> <span class="mi">0</span><span class="p">);</span>

  <span class="c1">// Check if there are any navbar burgers</span>
  <span class="k">if</span> <span class="p">(</span><span class="nx">$navbarBurgers</span><span class="p">.</span><span class="nx">length</span> <span class="o">></span> <span class="mi">0</span><span class="p">)</span> <span class="p">{</span>
    <span class="c1">// Add a click event on each of them</span>
    <span class="nx">$navbarBurgers</span><span class="p">.</span><span class="nx">forEach</span><span class="p">(</span><span class="kd">function</span> <span class="p">(</span><span class="nx">$el</span><span class="p">)</span> <span class="p">{</span>
      <span class="nx">$el</span><span class="p">.</span><span class="nx">addEventListener</span><span class="p">(</span><span class="s1">'click'</span><span class="p">,</span> <span class="kd">function</span> <span class="p">()</span> <span class="p">{</span>
        <span class="c1">// Get the target from the "data-target" attribute</span>
        <span class="kd">var</span> <span class="nx">target</span> <span class="o">=</span> <span class="nx">$el</span><span class="p">.</span><span class="nx">dataset</span><span class="p">.</span><span class="nx">target</span><span class="p">;</span>
        <span class="kd">var</span> <span class="nx">$target</span> <span class="o">=</span> <span class="nb">document</span><span class="p">.</span><span class="nx">getElementById</span><span class="p">(</span><span class="nx">target</span><span class="p">);</span>
        <span class="c1">// Toggle the class on both the "navbar-burger" and the "navbar-menu"</span>
        <span class="nx">$el</span><span class="p">.</span><span class="nx">classList</span><span class="p">.</span><span class="nx">toggle</span><span class="p">(</span><span class="s1">'is-active'</span><span class="p">);</span>
        <span class="nx">$target</span><span class="p">.</span><span class="nx">classList</span><span class="p">.</span><span class="nx">toggle</span><span class="p">(</span><span class="s1">'is-active'</span><span class="p">);</span>
      <span class="p">});</span>
    <span class="p">});</span>
  <span class="p">}</span>
<span class="p">});</span></code></pre></figure>
        </div>
      </div>
    </div>

### 导航菜单开始和导航菜单结束

`navbar-start`和`navbar-end`是`navbar-menu`的两个直接和唯一的子节点。

在大于等于2014的桌面设备上：

- `navbar-start` 将出现在左侧
- `navbar-end` 将显示在右侧

它们每个都可以包含任意数量的`navbar-item`。

```html
<div class="navbar-menu">
  <div class="navbar-start">
    <!-- navbar items -->
  </div>

  <div class="navbar-end">
    <!-- navbar items -->
  </div>
</div>
```

### 导航栏子项目

`navbar-item`是一个可重复的元素，它可以是：

- 一个导航链接

```html
<a class="navbar-item">
  Home
</a>
```

- 品牌Logo标识位的容器

```html
<a class="navbar-item">
  <img src="https://bulma.io/images/bulma-logo.png" width="112" height="28" alt="Bulma">
</a>
```

- 下拉菜单的父级容器

```html
<div class="navbar-item has-dropdown">
  <a class="navbar-link">
    Docs
  </a>

  <div class="navbar-dropdown">
    <!-- Other navbar items -->
  </div>
</div>
```

- 导航栏下拉菜单的一个子菜单

```html
<div class="navbar-dropdown">
  <a class="navbar-item">
    Overview
  </a>
</div>
```

- 任何你想要的容器，比如一个字段容器

```html
<div class="navbar-item">
  <div class="field is-grouped">
    <p class="control">
      <a class="button">
        <span class="icon">
          <i class="fab fa-twitter" aria-hidden="true"></i>
        </span>
        <span>Tweet</span>
      </a>
    </p>
    <p class="control">
      <a class="button is-primary">
        <span class="icon">
          <i class="fas fa-download" aria-hidden="true"></i>
        </span>
        <span>Download</span>
      </a>
    </p>
  </div>
</div>
```

它也可以是锚标签`<a>`或`<div>`,可以作为以下任一项的直接子项：

- `navbar`
- `navbar-brand`
- `navbar-start`
- `navbar-end`
- `navbar-dropdown`

您可以添加修饰符类`is-expanded`以将其变成100%宽度的元素

### 透明的导航栏

要在任何可视上下文中无缝集成导航栏，您可以在导航栏组件上添加`is-transparent`修饰符。 这将从导航栏中删除任何悬停或活动背景。

```html
<nav class="navbar is-transparent">
  <div class="navbar-brand">
    <a class="navbar-item" href="https://bulma.io">
      <img src="https://bulma.io/images/bulma-logo.png" alt="Bulma: a modern CSS framework based on Flexbox" width="112" height="28">
    </a>
    <div class="navbar-burger burger" data-target="navbarExampleTransparentExample">
      <span></span>
      <span></span>
      <span></span>
    </div>
  </div>

  <div id="navbarExampleTransparentExample" class="navbar-menu">
    <div class="navbar-start">
      <a class="navbar-item" href="https://bulma.io/">
        Home
      </a>
      <div class="navbar-item has-dropdown is-hoverable">
        <a class="navbar-link" href="/documentation/overview/start/">
          Docs
        </a>
        <div class="navbar-dropdown is-boxed">
          <a class="navbar-item" href="/documentation/overview/start/">
            Overview
          </a>
          <a class="navbar-item" href="https://bulma.io/documentation/modifiers/syntax/">
            Modifiers
          </a>
          <a class="navbar-item" href="https://bulma.io/documentation/columns/basics/">
            Columns
          </a>
          <a class="navbar-item" href="https://bulma.io/documentation/layout/container/">
            Layout
          </a>
          <a class="navbar-item" href="https://bulma.io/documentation/form/general/">
            Form
          </a>
          <hr class="navbar-divider">
          <a class="navbar-item" href="https://bulma.io/documentation/elements/box/">
            Elements
          </a>
          <a class="navbar-item is-active" href="https://bulma.io/documentation/components/breadcrumb/">
            Components
          </a>
        </div>
      </div>
    </div>

    <div class="navbar-end">
      <div class="navbar-item">
        <div class="field is-grouped">
          <p class="control">
            <a class="bd-tw-button button" data-social-network="Twitter" data-social-action="tweet" data-social-target="http://localhost:4000" target="_blank" href="https://twitter.com/intent/tweet?text=Bulma: a modern CSS framework based on Flexbox&hashtags=bulmaio&url=http://localhost:4000&via=jgthms">
              <span class="icon">
                <i class="fab fa-twitter"></i>
              </span>
              <span>
                Tweet
              </span>
            </a>
          </p>
          <p class="control">
            <a class="button is-primary" href="https://github.com/jgthms/bulma/archive/0.5.1.zip">
              <span class="icon">
                <i class="fas fa-download"></i>
              </span>
              <span>Download</span>
            </a>
          </p>
        </div>
      </div>
    </div>
  </div>
</nav>
```

### 固定的导航栏

您现在可以将导航栏修改为页面的顶部或底部, 要实现固定导航栏需要进行下面的两步操作：

- 向导航栏组件添加`is-fixed-top`或者`is-fixed-bottom`

```html
<nav class="navbar is-fixed-top">
```

- 将相应的`has-navbar-fixed-top`或`has-navbar-fixed-bottom`修饰符添加到`<html>`或`<body>`元素以向页面提供适当的填充

```html
<html class="has-navbar-fixed-top">
```

### 下拉式菜单

要创建下拉菜单，您需要4个元素：

- 带有下拉修饰符`has-dropdown`的`navbar-item`元素
- 包含下拉箭头的`navbar-link`
- `navbar-dropdown`可以包含`navbar-item`和`navbar-divider`的实例

```html
<nav class="navbar" role="navigation" aria-label="dropdown navigation">
  <div class="navbar-item has-dropdown">
    <a class="navbar-link">
      Docs
    </a>

    <div class="navbar-dropdown">
      <a class="navbar-item">
        Overview
      </a>
      <a class="navbar-item">
        Elements
      </a>
      <a class="navbar-item">
        Components
      </a>
      <hr class="navbar-divider">
      <div class="navbar-item">
        Version 0.6.2
      </div>
    </div>
  </div>
</nav>
```

#### 使用CSS或JavaScript显示/隐藏下拉菜单

导航栏下拉菜单在宽度小于1024的触控设备上是可见的，但在宽度大于等于1024像素的左面设备上是隐藏的。如何在桌面设备上显示下拉菜单取决于父级元素的类别。

带有`has-dropdown`修饰符的`navbar-item`是含有2个额外的修饰符的：

- `is-hoverable`：当鼠标悬停在父`navbar-item`上时，会显示下拉菜单
- `is-active`: 下拉菜单会一直显示

尽管CSS的`hover`实现可以完美工作，但`is-active`类适用于想要使用JavaScript控制下拉菜单显示的用户。

```html
<div class="navbar-item has-dropdown is-hoverable">
  <!-- navbar-link, navbar-dropdown etc. -->
</div>
```

```html
<nav class="navbar" role="navigation" aria-label="dropdown navigation">
  <div class="navbar-item has-dropdown is-hoverable">
    <a class="navbar-link">
      Docs
    </a>

    <div class="navbar-dropdown">
      <a class="navbar-item">
        Overview
      </a>
      <a class="navbar-item">
        Elements
      </a>
      <a class="navbar-item">
        Components
      </a>
      <hr class="navbar-divider">
      <div class="navbar-item">
        Version 0.6.2
      </div>
    </div>
  </div>
</nav>
```

```html
<div class="navbar-item has-dropdown is-active">
  <!-- navbar-link, navbar-dropdown etc. -->
</div>
```

```html
<nav class="navbar" role="navigation" aria-label="dropdown navigation">
  <div class="navbar-item has-dropdown is-active">
    <a class="navbar-link">
      Docs
    </a>

    <div class="navbar-dropdown">
      <a class="navbar-item">
        Overview
      </a>
      <a class="navbar-item">
        Elements
      </a>
      <a class="navbar-item">
        Components
      </a>
      <hr class="navbar-divider">
      <div class="navbar-item">
        Version 0.6.2
      </div>
    </div>
  </div>
</nav>
```

### 靠右显示的下拉菜单

如果您的父`navbar-item`位于右侧，则可以使用`is-right`修饰符将下拉列表显示在右侧。

```html
<div class="navbar-dropdown is-right">
  <!-- navbar-item, navbar-divider etc. -->
</div>
```

```html
<nav class="navbar" role="navigation" aria-label="dropdown navigation">
  <div class="navbar-menu">
    <div class="navbar-start">
      <div class="navbar-item has-dropdown is-active">
        <a class="navbar-link">
          Left
        </a>

        <div class="navbar-dropdown">
          <a class="navbar-item">
            Overview
          </a>
          <a class="navbar-item">
            Elements
          </a>
          <a class="navbar-item">
            Components
          </a>
          <hr class="navbar-divider">
          <div class="navbar-item">
            Version 0.6.2
          </div>
        </div>
      </div>
    </div>

    <div class="navbar-end">
      <div class="navbar-item has-dropdown is-active">
        <a class="navbar-link">
          Right
        </a>

        <div class="navbar-dropdown is-right">
          <a class="navbar-item">
            Overview
          </a>
          <a class="navbar-item">
            Elements
          </a>
          <a class="navbar-item">
            Components
          </a>
          <hr class="navbar-divider">
          <div class="navbar-item">
            Version 0.6.2
          </div>
        </div>
      </div>
    </div>
  </div>
</nav>

<section class="hero is-primary">
  <div class="hero-body">
    <p class="title">
      Documentation
    </p>
    <p class="subtitle">
      Everything you need to <strong>create a website</strong> with Bulma
    </p>
  </div>
</section>
```

### 上拉菜单

如果您在底部使用导航栏（如固定底部导航栏），则可能需要使用一个上拉菜单。 只需将`has-dropdown`和`has-dropdown-up`修饰符添加到父`navbar-item`元素上。

```html
<div class="navbar-item has-dropdown has-dropdown-up is-hoverable">
  <a class="navbar-link" href="/documentation/overview/start/">
    Docs
  </a>
  <div class="navbar-dropdown">
    <a class="navbar-item" href="/documentation/overview/start/">
      Overview
    </a>
  </div>
</div>
```

```html
<section class="hero is-primary">
  <div class="hero-body">
    <p class="title">
      Documentation
    </p>
    <p class="subtitle">
      Everything you need to <strong>create a website</strong> with Bulma
    </p>
  </div>
</section>

<nav class="navbar" role="navigation" aria-label="dropdown navigation">
  <div class="navbar-menu">
    <div class="navbar-start">
      <div class="navbar-item has-dropdown has-dropdown-up is-active">
        <a class="navbar-link">
          Dropup
        </a>

        <div class="navbar-dropdown">
          <a class="navbar-item">
            Overview
          </a>
          <a class="navbar-item">
            Elements
          </a>
          <a class="navbar-item">
            Components
          </a>
          <hr class="navbar-divider">
          <div class="navbar-item">
            Version 0.6.2
          </div>
        </div>
      </div>
    </div>
  </div>
</nav>
```

#### 下拉菜单的样式

一般情况下，下拉菜单`navbar-dropdown`有如下默认样式：

- 一个灰色的边框
- 左下角和右下角都是圆角样式

```html
<nav class="navbar" role="navigation" aria-label="dropdown navigation">
  <a class="navbar-item">
    <img src="https://bulma.io/images/bulma-logo.png" alt="Bulma: a modern CSS framework based on Flexbox" width="112" height="28">
  </a>

  <div class="navbar-item has-dropdown is-active">
    <a class="navbar-link">
      Docs
    </a>

    <div class="navbar-dropdown">
      <a class="navbar-item">
        Overview
      </a>
      <a class="navbar-item">
        Elements
      </a>
      <a class="navbar-item">
        Components
      </a>
      <hr class="navbar-divider">
      <div class="navbar-item">
        Version 0.6.2
      </div>
    </div>
  </div>
</nav>

<section class="hero is-primary">
  <div class="hero-body">
    <p class="title">
      Documentation
    </p>
    <p class="subtitle">
      Everything you need to <strong>create a website</strong> with Bulma
    </p>
  </div>
</section>
```

当使用透明导航栏时，最好使用`is-boxed`修饰符来使用下拉框的盒装版本，它具有以下特征：

- 灰色边框被删除
- 会添加一个浅色的内阴影
- 都是圆角
- 悬停或被激活状态是带有动画效果的。

```html
<nav class="navbar is-transparent" role="navigation" aria-label="dropdown navigation">
  <a class="navbar-item">
    <img src="https://bulma.io/images/bulma-logo.png" alt="Bulma: a modern CSS framework based on Flexbox" width="112" height="28">
  </a>

  <div class="navbar-item has-dropdown is-active">
    <a class="navbar-link">
      Docs
    </a>

    <div class="navbar-dropdown is-boxed">
      <a class="navbar-item">
        Overview
      </a>
      <a class="navbar-item">
        Elements
      </a>
      <a class="navbar-item">
        Components
      </a>
      <hr class="navbar-divider">
      <div class="navbar-item">
        Version 0.6.2
      </div>
    </div>
  </div>
</nav>

<section class="hero">
  <div class="hero-body">
    <p class="title">
      Documentation
    </p>
    <p class="subtitle">
      Everything you need to <strong>create a website</strong> with Bulma
    </p>
  </div>
</section>
```

#### 激活的下拉导航菜单项

```html
<nav class="navbar" role="navigation" aria-label="dropdown navigation">
  <a class="navbar-item">
    <img src="https://bulma.io/images/bulma-logo.png" alt="Bulma: a modern CSS framework based on Flexbox" width="112" height="28">
  </a>

  <div class="navbar-item has-dropdown is-active">
    <a class="navbar-link">
      Docs
    </a>

    <div class="navbar-dropdown">
      <a class="navbar-item">
        Overview
      </a>
      <a class="navbar-item is-active">
        Elements
      </a>
      <a class="navbar-item">
        Components
      </a>
      <hr class="navbar-divider">
      <div class="navbar-item">
        Version 0.6.2
      </div>
    </div>
  </div>
</nav>

<section class="hero is-primary">
  <div class="hero-body">
    <p class="title">
      Documentation
    </p>
    <p class="subtitle">
      Everything you need to <strong>create a website</strong> with Bulma
    </p>
  </div>
</section>
```

#### 下拉分组

您可以添加一个导航栏分隔线，以在导航栏下拉菜单中显示水平线。

```html
<hr class="navbar-divider">
```

### 颜色

您可以使用下面9种颜色修饰符之一来更改导航栏的背景颜色：

- `is-primary`
- `is-link`
- `is-info`
- `is-success`
- `is-warning`
- `is-danger`
- `is-black`
- `is-dark`
- `is-light`
- `is-white`

```html
<nav class="navbar is-primary">
  <!-- navbar brand, navbar menu... -->
</nav>
```

### 变量

| Name | Default value |
| ---- | ------------- |
| `$navbar-background-color` | `$white` |
| `$navbar-height` | `3.25rem` |
| `$navbar-item-color` | `$grey-dark` |
| `$navbar-item-hover-color` | `$link` |
| `$navbar-item-hover-background-color` | `$background` |
| `$navbar-item-active-color` | `$black` |
| `$navbar-item-active-background-color` | `transparent` |
| `$navbar-item-img-max-height` | `1.75rem` |
| `$navbar-tab-hover-background-color` | `transparent` |
| `$navbar-tab-hover-border-bottom-color` | `$link` |
| `$navbar-tab-active-color` | `$link` |
| `$navbar-tab-active-background-color` | `transparent` |
| `$navbar-tab-active-border-bottom-color` | `$link` |
| `$navbar-tab-active-border-bottom-style` | `solid` |
| `$navbar-tab-active-border-bottom-width` | `3px` |
| `$navbar-dropdown-background-color` | `$white` |
| `$navbar-dropdown-border-top` | `1px solid $border` |
| `$navbar-dropdown-offset` | `-4px` |
| `$navbar-dropdown-arrow` | `$link` |
| `$navbar-dropdown-radius` | `$radius-large` |
| `$navbar-dropdown-z` | `20` |
| `$navbar-dropdown-boxed-radius` | `$radius-large` |
| `$navbar-dropdown-boxed-shadow` | `0 8px 8px rgba($black, 0.1), 0 0 0 1px rgba($black, 0.1)` |
| `$navbar-dropdown-item-hover-color` | `$black` |
| `$navbar-dropdown-item-hover-background-color` | `$background` |
| `$navbar-dropdown-item-active-color` | `$link` |
| `$navbar-dropdown-item-active-background-color` | `$background` |
| `$navbar-divider-background-color` | `$border` |

## 分页

你可以在Bulma中创建一个响应式的、可用的、灵活的分页组件

分页组件由以下几个元素组成：

<ul style="list-style:disc outside;margin-top:1em;"><li><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding:0.25em 0.5em 0.25em;">pagination-previous</code>和<code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding:0.25em 0.5em 0.25em;">pagination-next</code> 构成整个导航</li><li><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding:0.25em 0.5em 0.25em;">pagination-list</code> 显示页面项目<ul style="list-style:disc outside;"><li><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding:0.25em 0.5em 0.25em;">pagination-link</code> 构成页码</li><li><code style="background-color:whitesmoke;color:#ff3860;font-size:0.875em;font-weight:normal;padding:0.25em 0.5em 0.25em;">pagination-ellipsis</code> 构成范围分隔符</li></ul></li></ul>

所有元素都是可选的，因此您可以根据需要编写分页。

```html
<nav class="pagination" role="navigation" aria-label="pagination">
  <a class="pagination-previous">Previous</a>
  <a class="pagination-next">Next page</a>
  <ul class="pagination-list">
    <li>
      <a class="pagination-link" aria-label="Goto page 1">1</a>
    </li>
    <li>
      <span class="pagination-ellipsis">…</span>
    </li>
    <li>
      <a class="pagination-link" aria-label="Goto page 45">45</a>
    </li>
    <li>
      <a class="pagination-link is-current" aria-label="Page 46" aria-current="page">46</a>
    </li>
    <li>
      <a class="pagination-link" aria-label="Goto page 47">47</a>
    </li>
    <li>
      <span class="pagination-ellipsis">…</span>
    </li>
    <li>
      <a class="pagination-link" aria-label="Goto page 86">86</a>
    </li>
  </ul>
</nav>
```

您可以禁用某些链接（如果它们未处于活动状态），或更改可用的页码数量。

```html
<nav class="pagination" role="navigation" aria-label="pagination">
  <a class="pagination-previous" title="This is the first page" disabled>Previous</a>
  <a class="pagination-next">Next page</a>
  <ul class="pagination-list">
    <li>
      <a class="pagination-link is-current" aria-label="Page 1" aria-current="page">1</a>
    </li>
    <li>
      <a class="pagination-link" aria-label="Goto page 2">2</a>
    </li>
    <li>
      <a class="pagination-link" aria-label="Goto page 3">3</a>
    </li>
  </ul>
</nav>
```

如果用户使用平板电脑，默认情况下，列表位于左侧，右侧为上一个/下一个按钮。 但是你可以通过使用`is-centered`和`is-right`修饰符来改变这些元素的顺序。

```html
<nav class="pagination is-centered" role="navigation" aria-label="pagination">
  <a class="pagination-previous">Previous</a>
  <a class="pagination-next">Next page</a>
  <ul class="pagination-list">
    <li><a class="pagination-link" aria-label="Goto page 1">1</a></li>
    <li><span class="pagination-ellipsis">…</span></li>
    <li><a class="pagination-link" aria-label="Goto page 45">45</a></li>
    <li><a class="pagination-link is-current" aria-label="Page 46" aria-current="page">46</a></li>
    <li><a class="pagination-link" aria-label="Goto page 47">47</a></li>
    <li><span class="pagination-ellipsis">…</span></li>
    <li><a class="pagination-link" aria-label="Goto page 86">86</a></li>
  </ul>
</nav>
```

修改之后：

```html
<nav class="pagination is-right" role="navigation" aria-label="pagination">
  <a class="pagination-previous">Previous</a>
  <a class="pagination-next">Next page</a>
  <ul class="pagination-list">
    <li><a class="pagination-link" aria-label="Goto page 1">1</a></li>
    <li><span class="pagination-ellipsis">…</span></li>
    <li><a class="pagination-link" aria-label="Goto page 45">45</a></li>
    <li><a class="pagination-link is-current" aria-label="Page 46" aria-current="page">46</a></li>
    <li><a class="pagination-link" aria-label="Goto page 47">47</a></li>
    <li><span class="pagination-ellipsis">…</span></li>
    <li><a class="pagination-link" aria-label="Goto page 86">86</a></li>
  </ul>
</nav>
```

### 样式

添加`is-rounded`修饰符来让分页按钮显示为圆形

```html
<nav class="pagination is-rounded" role="navigation" aria-label="pagination">
  <a class="pagination-previous">Previous</a>
  <a class="pagination-next">Next page</a>
  <ul class="pagination-list">
    <li><a class="pagination-link" aria-label="Goto page 1">1</a></li>
    <li><span class="pagination-ellipsis">…</span></li>
    <li><a class="pagination-link" aria-label="Goto page 45">45</a></li>
    <li><a class="pagination-link is-current" aria-label="Page 46" aria-current="page">46</a></li>
    <li><a class="pagination-link" aria-label="Goto page 47">47</a></li>
    <li><span class="pagination-ellipsis">…</span></li>
    <li><a class="pagination-link" aria-label="Goto page 86">86</a></li>
  </ul>
</nav>
```

### 尺寸大小

分页有3种尺寸。您只需要将修饰符添加到分页组件中，即`is-small`，`is-medium`或`is-large`。

```html
<nav class="pagination is-small" role="navigation" aria-label="pagination">
  <a class="pagination-previous">Previous</a>
  <a class="pagination-next">Next page</a>
  <ul class="pagination-list">
    <li><a class="pagination-link" aria-label="Goto page 1">1</a></li>
    <li><span class="pagination-ellipsis">…</span></li>
    <li><a class="pagination-link" aria-label="Goto page 45">45</a></li>
    <li><a class="pagination-link is-current" aria-label="Page 46" aria-current="page">46</a></li>
    <li><a class="pagination-link" aria-label="Goto page 47">47</a></li>
    <li><span class="pagination-ellipsis">…</span></li>
    <li><a class="pagination-link" aria-label="Goto page 86">86</a></li>
  </ul>
</nav>
```

```html
<nav class="pagination is-medium" role="navigation" aria-label="pagination">
  <a class="pagination-previous">Previous</a>
  <a class="pagination-next">Next page</a>
  <ul class="pagination-list">
    <li><a class="pagination-link" aria-label="Goto page 1">1</a></li>
    <li><span class="pagination-ellipsis">…</span></li>
    <li><a class="pagination-link" aria-label="Goto page 45">45</a></li>
    <li><a class="pagination-link is-current" aria-label="Page 46" aria-current="page">46</a></li>
    <li><a class="pagination-link" aria-label="Goto page 47">47</a></li>
    <li><span class="pagination-ellipsis">…</span></li>
    <li><a class="pagination-link" aria-label="Goto page 86">86</a></li>
  </ul>
</nav>
```

```html
<nav class="pagination is-large" role="navigation" aria-label="pagination">
  <a class="pagination-previous">Previous</a>
  <a class="pagination-next">Next page</a>
  <ul class="pagination-list">
    <li><a class="pagination-link" aria-label="Goto page 1">1</a></li>
    <li><span class="pagination-ellipsis">…</span></li>
    <li><a class="pagination-link" aria-label="Goto page 45">45</a></li>
    <li><a class="pagination-link is-current" aria-label="Page 46" aria-current="page">46</a></li>
    <li><a class="pagination-link" aria-label="Goto page 47">47</a></li>
    <li><span class="pagination-ellipsis">…</span></li>
    <li><a class="pagination-link" aria-label="Goto page 86">86</a></li>
  </ul>
</nav>
```

### 变量

| Name | Default value |
| ---- | ------------- |
| `$pagination-color` | `$grey-darker` |
| `$pagination-border-color` | `$grey-lighter` |
| `$pagination-margin` | `-0.25rem` |
| `$pagination-hover-color` | `$link-hover` |
| `$pagination-hover-border-color` | `$link-hover-border` |
| `$pagination-focus-color` | `$link-focus` |
| `$pagination-focus-border-color` | `$link-focus-border` |
| `$pagination-active-color` | `$link-active` |
| `$pagination-active-border-color` | `$link-active-border` |
| `$pagination-disabled-color` | `$grey` |
| `$pagination-disabled-background-color` | `$grey-lighter` |
| `$pagination-disabled-border-color` | `$grey-lighter` |
| `$pagination-current-color` | `$link-invert` |
| `$pagination-current-background-color` | `$link` |
| `$pagination-current-border-color` | `$link` |
| `$pagination-ellipsis-color` | `$grey-light` |

## 面板

面板是几种类型组件的一个容器

- `panel-heading` 容器的第一个子元素
- `panel-tabs` 导航
- `panel-block` 一个区块容器，可以包含以下元素：
    - `control`
    - `input`
    - `button`
    - `panel-icon`

`panel-block`可以是锚标签`<a>`或带有复选框的标签`<label>`。

```html
<nav class="panel">
  <p class="panel-heading">
    repositories
  </p>
  <div class="panel-block">
    <p class="control has-icons-left">
      <input class="input is-small" type="text" placeholder="search">
      <span class="icon is-small is-left">
        <i class="fas fa-search"></i>
      </span>
    </p>
  </div>
  <p class="panel-tabs">
    <a class="is-active">all</a>
    <a>public</a>
    <a>private</a>
    <a>sources</a>
    <a>forks</a>
  </p>
  <a class="panel-block is-active">
    <span class="panel-icon">
      <i class="fas fa-book"></i>
    </span>
    bulma
  </a>
  <a class="panel-block">
    <span class="panel-icon">
      <i class="fas fa-book"></i>
    </span>
    marksheet
  </a>
  <a class="panel-block">
    <span class="panel-icon">
      <i class="fas fa-book"></i>
    </span>
    minireset.css
  </a>
  <a class="panel-block">
    <span class="panel-icon">
      <i class="fas fa-book"></i>
    </span>
    jgthms.github.io
  </a>
  <a class="panel-block">
    <span class="panel-icon">
      <i class="fas fa-code-branch"></i>
    </span>
    daniellowtw/infboard
  </a>
  <a class="panel-block">
    <span class="panel-icon">
      <i class="fas fa-code-branch"></i>
    </span>
    mojs
  </a>
  <label class="panel-block">
    <input type="checkbox">
    remember me
  </label>
  <div class="panel-block">
    <button class="button is-link is-outlined is-fullwidth">
      reset all filters
    </button>
  </div>
</nav>
```

### 变量

| Name | Default value |
| ---- | ------------- |
| `$panel-item-border` | `1px solid $border` |
| `$panel-heading-background-color` | `$background` |
| `$panel-heading-color` | `$text-strong` |
| `$panel-heading-line-height` | `1.25` |
| `$panel-heading-padding` | `0.5em 0.75em` |
| `$panel-heading-radius` | `$radius` |
| `$panel-heading-size` | `1.25em` |
| `$panel-heading-weight` | `$weight-light` |
| `$panel-tab-border-bottom` | `1px solid $border` |
| `$panel-tab-active-border-bottom-color` | `$link-active-border` |
| `$panel-tab-active-color` | `$link-active` |
| `$panel-list-item-color` | `$text` |
| `$panel-list-item-hover-color` | `$link` |
| `$panel-block-color` | `$text-strong` |
| `$panel-block-hover-background-color` | `$background` |
| `$panel-block-active-border-left-color` | `$link` |
| `$panel-block-active-color` | `$link-active` |
| `$panel-block-active-icon-color` | `$link` |
| `$panel-icon-color` | `$text-light` |

## Tabs

在Bulma中，可以非常简单的构建响应式的水平导航标签。

构建`Tabs`只需要一个`tabs`容器和一个`ul`列表。默认的标签样式在底部有一个单独的边框。

```html
<div class="tabs">
  <ul>
    <li class="is-active"><a>Pictures</a></li>
    <li><a>Music</a></li>
    <li><a>Videos</a></li>
    <li><a>Documents</a></li>
  </ul>
</div>
```

```html
<div class="tabs">
  <ul>
    <li class="is-active"><a>Pictures</a></li>
    <li><a>Music</a></li>
    <li><a>Videos</a></li>
    <li><a>Documents</a></li>
  </ul>
</div>
```

### 对齐

要对齐选项卡列表，请在`.tabs`容器上使用以`is-centered`或`is-right`修饰符：

```html
<div class="tabs is-centered">
  <ul>
    <li class="is-active"><a>Pictures</a></li>
    <li><a>Music</a></li>
    <li><a>Videos</a></li>
    <li><a>Documents</a></li>
  </ul>
</div>
```

```html
<div class="tabs is-right">
  <ul>
    <li class="is-active"><a>Pictures</a></li>
    <li><a>Music</a></li>
    <li><a>Videos</a></li>
    <li><a>Documents</a></li>
  </ul>
</div>
```

### 图标

您可以使用任何`Font Awesome`图标。

```html
<div class="tabs is-centered">
  <ul>
    <li class="is-active">
      <a>
        <span class="icon is-small"><i class="fas fa-image"></i></span>
        <span>Pictures</span>
      </a>
    </li>
    <li>
      <a>
        <span class="icon is-small"><i class="fas fa-music"></i></span>
        <span>Music</span>
      </a>
    </li>
    <li>
      <a>
        <span class="icon is-small"><i class="fas fa-film"></i></span>
        <span>Videos</span>
      </a>
    </li>
    <li>
      <a>
        <span class="icon is-small"><i class="fas fa-file-alt"></i></span>
        <span>Documents</span>
      </a>
    </li>
  </ul>
</div>
```

```html
<div class="tabs is-centered">
  <ul>
    <li class="is-active">
      <a>
        <span class="icon is-small"><i class="fas fa-image"></i></span>
        <span>Pictures</span>
      </a>
    </li>
    <li>
      <a>
        <span class="icon is-small"><i class="fas fa-music"></i></span>
        <span>Music</span>
      </a>
    </li>
    <li>
      <a>
        <span class="icon is-small"><i class="fas fa-film"></i></span>
        <span>Videos</span>
      </a>
    </li>
    <li>
      <a>
        <span class="icon is-small"><i class="fas fa-file-alt"></i></span>
        <span>Documents</span>
      </a>
    </li>
  </ul>
</div>
```

### 尺寸大小

您可以选择3种尺寸：`is-small`、`is-medium`和`is-large`.

```html
<div class="tabs is-small">
  <ul>
    <li class="is-active"><a>Pictures</a></li>
    <li><a>Music</a></li>
    <li><a>Videos</a></li>
    <li><a>Documents</a></li>
  </ul>
</div>
```

```html
<div class="tabs is-medium">
  <ul>
    <li class="is-active"><a>Pictures</a></li>
    <li><a>Music</a></li>
    <li><a>Videos</a></li>
    <li><a>Documents</a></li>
  </ul>
</div>
```

```html
<div class="tabs is-large">
  <ul>
    <li class="is-active"><a>Pictures</a></li>
    <li><a>Music</a></li>
    <li><a>Videos</a></li>
    <li><a>Documents</a></li>
  </ul>
</div>
```

### 样式

如果你想要带有边框的经典风格，只需附加`is-boxed`修饰符。

```html
<div class="tabs is-boxed">
  <ul>
    <li class="is-active">
      <a>
        <span class="icon is-small"><i class="fas fa-image"></i></span>
        <span>Pictures</span>
      </a>
    </li>
    <li>
      <a>
        <span class="icon is-small"><i class="fas fa-music"></i></span>
        <span>Music</span>
      </a>
    </li>
    <li>
      <a>
        <span class="icon is-small"><i class="fas fa-film"></i></span>
        <span>Videos</span>
      </a>
    </li>
    <li>
      <a>
        <span class="icon is-small"><i class="fas fa-file-alt"></i></span>
        <span>Documents</span>
      </a>
    </li>
  </ul>
</div>
```

如果您想要互斥选项卡（如单选按钮取消选择所有其他选项），请使用`is-toggle`修饰符。

```html
<div class="tabs is-toggle">
  <ul>
    <li class="is-active">
      <a>
        <span class="icon is-small"><i class="fas fa-image"></i></span>
        <span>Pictures</span>
      </a>
    </li>
    <li>
      <a>
        <span class="icon is-small"><i class="fas fa-music"></i></span>
        <span>Music</span>
      </a>
    </li>
    <li>
      <a>
        <span class="icon is-small"><i class="fas fa-film"></i></span>
        <span>Videos</span>
      </a>
    </li>
    <li>
      <a>
        <span class="icon is-small"><i class="fas fa-file-alt"></i></span>
        <span>Documents</span>
      </a>
    </li>
  </ul>
</div>
```

如果您同时使用`is-toggle`和`is-toggle-rounded`，则第一项和最后一项将会呈现最大圆角的样式。

```html
<div class="tabs is-toggle is-toggle-rounded">
  <ul>
    <li class="is-active">
      <a>
        <span class="icon is-small"><i class="fas fa-image"></i></span>
        <span>Pictures</span>
      </a>
    </li>
    <li>
      <a>
        <span class="icon is-small"><i class="fas fa-music"></i></span>
        <span>Music</span>
      </a>
    </li>
    <li>
      <a>
        <span class="icon is-small"><i class="fas fa-film"></i></span>
        <span>Videos</span>
      </a>
    </li>
    <li>
      <a>
        <span class="icon is-small"><i class="fas fa-file-alt"></i></span>
        <span>Documents</span>
      </a>
    </li>
  </ul>
</div>
```

如果您希望选项卡占用整个可用宽度，请使用`is-fullwidth`。

```html
<div class="tabs is-fullwidth">
  <ul>
    <li>
      <a>
        <span class="icon"><i class="fas fa-angle-left"></i></span>
        <span>Left</span>
      </a>
    </li>
    <li>
      <a>
        <span class="icon"><i class="fas fa-angle-up"></i></span>
        <span>Up</span>
      </a>
    </li>
    <li>
      <a>
        <span>Right</span>
        <span class="icon"><i class="fas fa-angle-right"></i></span>
      </a>
    </li>
  </ul>
</div>
```

### 组合

你可以组合不同的修饰符。 例如，您可以拥有居中的方格标签或全宽切换标签。

```html
<div class="tabs is-centered is-boxed">
  <ul>
    <li class="is-active">
      <a>
        <span class="icon is-small"><i class="fas fa-image"></i></span>
        <span>Pictures</span>
      </a>
    </li>
    <li>
      <a>
        <span class="icon is-small"><i class="fas fa-music"></i></span>
        <span>Music</span>
      </a>
    </li>
    <li>
      <a>
        <span class="icon is-small"><i class="fas fa-film"></i></span>
        <span>Videos</span>
      </a>
    </li>
    <li>
      <a>
        <span class="icon is-small"><i class="fas fa-file-alt"></i></span>
        <span>Documents</span>
      </a>
    </li>
  </ul>
</div>
```

```html
<div class="tabs is-toggle is-fullwidth">
  <ul>
    <li class="is-active">
      <a>
        <span class="icon is-small"><i class="fas fa-image"></i></span>
        <span>Pictures</span>
      </a>
    </li>
    <li>
      <a>
        <span class="icon is-small"><i class="fas fa-music"></i></span>
        <span>Music</span>
      </a>
    </li>
    <li>
      <a>
        <span class="icon is-small"><i class="fas fa-film"></i></span>
        <span>Videos</span>
      </a>
    </li>
    <li>
      <a>
        <span class="icon is-small"><i class="fas fa-file-alt"></i></span>
        <span>Documents</span>
      </a>
    </li>
  </ul>
</div>
```

```html
<div class="tabs is-centered is-boxed is-medium">
  <ul>
    <li class="is-active">
      <a>
        <span class="icon is-small"><i class="fas fa-image"></i></span>
        <span>Pictures</span>
      </a>
    </li>
    <li>
      <a>
        <span class="icon is-small"><i class="fas fa-music"></i></span>
        <span>Music</span>
      </a>
    </li>
    <li>
      <a>
        <span class="icon is-small"><i class="fas fa-film"></i></span>
        <span>Videos</span>
      </a>
    </li>
    <li>
      <a>
        <span class="icon is-small"><i class="fas fa-file-alt"></i></span>
        <span>Documents</span>
      </a>
    </li>
  </ul>
</div>
```

```html
<div class="tabs is-toggle is-fullwidth is-large">
  <ul>
    <li class="is-active">
      <a>
        <span class="icon"><i class="fas fa-image"></i></span>
        <span>Pictures</span>
      </a>
    </li>
    <li>
      <a>
        <span class="icon"><i class="fas fa-music"></i></span>
        <span>Music</span>
      </a>
    </li>
    <li>
      <a>
        <span class="icon"><i class="fas fa-film"></i></span>
        <span>Videos</span>
      </a>
    </li>
    <li>
      <a>
        <span class="icon"><i class="fas fa-file-alt"></i></span>
        <span>Documents</span>
      </a>
    </li>
  </ul>
</div>
```

### 变量

| Name | Default value |
| ---- | ------------- |
| `$tabs-border-bottom-color` | `$border` |
| `$tabs-border-bottom-style` | `solid` |
| `$tabs-border-bottom-width` | `1px` |
| `$tabs-link-color` | `$text` |
| `$tabs-link-hover-border-bottom-color` | `$text-strong` |
| `$tabs-link-hover-color` | `$text-strong` |
| `$tabs-link-active-border-bottom-color` | `$link` |
| `$tabs-link-active-color` | `$link` |
| `$tabs-link-padding	0.5em` | `1em` |
| `$tabs-boxed-link-radius` | `$radius` |
| `$tabs-boxed-link-hover-background-color` | `$background` |
| `$tabs-boxed-link-hover-border-bottom-color` | `$border` |
| `$tabs-boxed-link-active-background-color` | `$white` |
| `$tabs-boxed-link-active-border-color` | `$border` |
| `$tabs-boxed-link-active-border-bottom-color` | `transparent` |
| `$tabs-toggle-link-border-color` | `$border` |
| `$tabs-toggle-link-border-style` | `solid` |
| `$tabs-toggle-link-border-width` | `1px` |
| `$tabs-toggle-link-hover-background-color` | `$background` |
| `$tabs-toggle-link-hover-border-color` | `$border-hover` |
| `$tabs-toggle-link-radius` | `$radius` |
| `$tabs-toggle-link-active-background-color` | `$link` |
| `$tabs-toggle-link-active-border-color` | `$link` |
| `$tabs-toggle-link-active-color` | `$link-invert` |

全文翻译完成.
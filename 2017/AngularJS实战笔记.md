<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [初识Angular](#%E5%88%9D%E8%AF%86angular)
  - [Angular简介](#angular%E7%AE%80%E4%BB%8B)
    - [特点](#%E7%89%B9%E7%82%B9)
  - [几个Angular的示例](#%E5%87%A0%E4%B8%AAangular%E7%9A%84%E7%A4%BA%E4%BE%8B)
- [Angular基础](#angular%E5%9F%BA%E7%A1%80)
  - [表达式](#%E8%A1%A8%E8%BE%BE%E5%BC%8F)
  - [控制器](#%E6%8E%A7%E5%88%B6%E5%99%A8)
    - [初始化`$scope`对象](#%E5%88%9D%E5%A7%8B%E5%8C%96scope%E5%AF%B9%E8%B1%A1)
    - [添加`$scope`对象方法](#%E6%B7%BB%E5%8A%A0scope%E5%AF%B9%E8%B1%A1%E6%96%B9%E6%B3%95)
    - [在事件中为`$scope`对象绑定方法](#%E5%9C%A8%E4%BA%8B%E4%BB%B6%E4%B8%AD%E4%B8%BAscope%E5%AF%B9%E8%B1%A1%E7%BB%91%E5%AE%9A%E6%96%B9%E6%B3%95)
    - [`$scope`对象属性和方法的继承](#scope%E5%AF%B9%E8%B1%A1%E5%B1%9E%E6%80%A7%E5%92%8C%E6%96%B9%E6%B3%95%E7%9A%84%E7%BB%A7%E6%89%BF)
  - [模板](#%E6%A8%A1%E6%9D%BF)
    - [构建模板内容](#%E6%9E%84%E5%BB%BA%E6%A8%A1%E6%9D%BF%E5%86%85%E5%AE%B9)
    - [使用指令复制元素](#%E4%BD%BF%E7%94%A8%E6%8C%87%E4%BB%A4%E5%A4%8D%E5%88%B6%E5%85%83%E7%B4%A0)
    - [添加元素样式](#%E6%B7%BB%E5%8A%A0%E5%85%83%E7%B4%A0%E6%A0%B7%E5%BC%8F)
    - [控制元素的隐藏与显示状态](#%E6%8E%A7%E5%88%B6%E5%85%83%E7%B4%A0%E7%9A%84%E9%9A%90%E8%97%8F%E4%B8%8E%E6%98%BE%E7%A4%BA%E7%8A%B6%E6%80%81)
  - [表单控件](#%E8%A1%A8%E5%8D%95%E6%8E%A7%E4%BB%B6)
    - [表单基本验证功能](#%E8%A1%A8%E5%8D%95%E5%9F%BA%E6%9C%AC%E9%AA%8C%E8%AF%81%E5%8A%9F%E8%83%BD)
    - [表单中的checkbox和radio控件](#%E8%A1%A8%E5%8D%95%E4%B8%AD%E7%9A%84checkbox%E5%92%8Cradio%E6%8E%A7%E4%BB%B6)
    - [表单中的select控件](#%E8%A1%A8%E5%8D%95%E4%B8%AD%E7%9A%84select%E6%8E%A7%E4%BB%B6)
- [Angular的过滤器和作用域](#angular%E7%9A%84%E8%BF%87%E6%BB%A4%E5%99%A8%E5%92%8C%E4%BD%9C%E7%94%A8%E5%9F%9F)
  - [过滤器](#%E8%BF%87%E6%BB%A4%E5%99%A8)
    - [排序方式过滤](#%E6%8E%92%E5%BA%8F%E6%96%B9%E5%BC%8F%E8%BF%87%E6%BB%A4)
    - [匹配方式过滤](#%E5%8C%B9%E9%85%8D%E6%96%B9%E5%BC%8F%E8%BF%87%E6%BB%A4)
    - [自定义过滤器](#%E8%87%AA%E5%AE%9A%E4%B9%89%E8%BF%87%E6%BB%A4%E5%99%A8)
  - [过滤器的应用](#%E8%BF%87%E6%BB%A4%E5%99%A8%E7%9A%84%E5%BA%94%E7%94%A8)
    - [表头排序](#%E8%A1%A8%E5%A4%B4%E6%8E%92%E5%BA%8F)
    - [字符查找](#%E5%AD%97%E7%AC%A6%E6%9F%A5%E6%89%BE)
  - [作用域概述](#%E4%BD%9C%E7%94%A8%E5%9F%9F%E6%A6%82%E8%BF%B0)
    - [作用域特点](#%E4%BD%9C%E7%94%A8%E5%9F%9F%E7%89%B9%E7%82%B9)
    - [作为数据模型的作用域](#%E4%BD%9C%E4%B8%BA%E6%95%B0%E6%8D%AE%E6%A8%A1%E5%9E%8B%E7%9A%84%E4%BD%9C%E7%94%A8%E5%9F%9F)
  - [作用域的层级和事件](#%E4%BD%9C%E7%94%A8%E5%9F%9F%E7%9A%84%E5%B1%82%E7%BA%A7%E5%92%8C%E4%BA%8B%E4%BB%B6)
    - [作用域的层级](#%E4%BD%9C%E7%94%A8%E5%9F%9F%E7%9A%84%E5%B1%82%E7%BA%A7)
    - [作用域事件的传播](#%E4%BD%9C%E7%94%A8%E5%9F%9F%E4%BA%8B%E4%BB%B6%E7%9A%84%E4%BC%A0%E6%92%AD)
- [Angular的依赖注入](#angular%E7%9A%84%E4%BE%9D%E8%B5%96%E6%B3%A8%E5%85%A5)
  - [依赖注入介绍](#%E4%BE%9D%E8%B5%96%E6%B3%A8%E5%85%A5%E4%BB%8B%E7%BB%8D)
    - [依赖注入的原理](#%E4%BE%9D%E8%B5%96%E6%B3%A8%E5%85%A5%E7%9A%84%E5%8E%9F%E7%90%86)
    - [简单依赖注入的示例](#%E7%AE%80%E5%8D%95%E4%BE%9D%E8%B5%96%E6%B3%A8%E5%85%A5%E7%9A%84%E7%A4%BA%E4%BE%8B)
  - [依赖注入标记](#%E4%BE%9D%E8%B5%96%E6%B3%A8%E5%85%A5%E6%A0%87%E8%AE%B0)
    - [推断式注入](#%E6%8E%A8%E6%96%AD%E5%BC%8F%E6%B3%A8%E5%85%A5)
    - [标记式注入](#%E6%A0%87%E8%AE%B0%E5%BC%8F%E6%B3%A8%E5%85%A5)
    - [行内式注入](#%E8%A1%8C%E5%86%85%E5%BC%8F%E6%B3%A8%E5%85%A5)
  - [$injector常用API](#injector%E5%B8%B8%E7%94%A8api)
    - [has和get方法](#has%E5%92%8Cget%E6%96%B9%E6%B3%95)
    - [invoke方法](#invoke%E6%96%B9%E6%B3%95)
    - [依赖注入的应用场景](#%E4%BE%9D%E8%B5%96%E6%B3%A8%E5%85%A5%E7%9A%84%E5%BA%94%E7%94%A8%E5%9C%BA%E6%99%AF)
- [Angular中的MVC模式](#angular%E4%B8%AD%E7%9A%84mvc%E6%A8%A1%E5%BC%8F)
  - [MVC模式概述](#mvc%E6%A8%A1%E5%BC%8F%E6%A6%82%E8%BF%B0)
    - [MVC简介](#mvc%E7%AE%80%E4%BB%8B)
    - [使用Angular中MVC的优势和缺点](#%E4%BD%BF%E7%94%A8angular%E4%B8%ADmvc%E7%9A%84%E4%BC%98%E5%8A%BF%E5%92%8C%E7%BC%BA%E7%82%B9)
  - [Model组件](#model%E7%BB%84%E4%BB%B6)
    - [Model组件的基本概念](#model%E7%BB%84%E4%BB%B6%E7%9A%84%E5%9F%BA%E6%9C%AC%E6%A6%82%E5%BF%B5)
    - [使用ngRepeater方式遍历Model对象](#%E4%BD%BF%E7%94%A8ngrepeater%E6%96%B9%E5%BC%8F%E9%81%8D%E5%8E%86model%E5%AF%B9%E8%B1%A1)
  - [Controller组件](#controller%E7%BB%84%E4%BB%B6)
    - [控制器的属性和方法](#%E6%8E%A7%E5%88%B6%E5%99%A8%E7%9A%84%E5%B1%9E%E6%80%A7%E5%92%8C%E6%96%B9%E6%B3%95)
    - [控制器方法中的参数](#%E6%8E%A7%E5%88%B6%E5%99%A8%E6%96%B9%E6%B3%95%E4%B8%AD%E7%9A%84%E5%8F%82%E6%95%B0)
    - [控制器中属性和方法的继承](#%E6%8E%A7%E5%88%B6%E5%99%A8%E4%B8%AD%E5%B1%9E%E6%80%A7%E5%92%8C%E6%96%B9%E6%B3%95%E7%9A%84%E7%BB%A7%E6%89%BF)
  - [View组件](#view%E7%BB%84%E4%BB%B6)
    - [View组件中的模板切换](#view%E7%BB%84%E4%BB%B6%E4%B8%AD%E7%9A%84%E6%A8%A1%E6%9D%BF%E5%88%87%E6%8D%A2)
    - [在切换视图模板时传递参数](#%E5%9C%A8%E5%88%87%E6%8D%A2%E8%A7%86%E5%9B%BE%E6%A8%A1%E6%9D%BF%E6%97%B6%E4%BC%A0%E9%80%92%E5%8F%82%E6%95%B0)
- [Angular中的服务](#angular%E4%B8%AD%E7%9A%84%E6%9C%8D%E5%8A%A1)
  - [Angular服务介绍](#angular%E6%9C%8D%E5%8A%A1%E4%BB%8B%E7%BB%8D)
    - [内置服务](#%E5%86%85%E7%BD%AE%E6%9C%8D%E5%8A%A1)
    - [自定义服务](#%E8%87%AA%E5%AE%9A%E4%B9%89%E6%9C%8D%E5%8A%A1)
  - [创建Angular服务](#%E5%88%9B%E5%BB%BAangular%E6%9C%8D%E5%8A%A1)
    - [使用`factory`方法自定义服务](#%E4%BD%BF%E7%94%A8factory%E6%96%B9%E6%B3%95%E8%87%AA%E5%AE%9A%E4%B9%89%E6%9C%8D%E5%8A%A1)
    - [使用`service`方法自定义服务](#%E4%BD%BF%E7%94%A8service%E6%96%B9%E6%B3%95%E8%87%AA%E5%AE%9A%E4%B9%89%E6%9C%8D%E5%8A%A1)
    - [使用constant和value方法自定义服务](#%E4%BD%BF%E7%94%A8constant%E5%92%8Cvalue%E6%96%B9%E6%B3%95%E8%87%AA%E5%AE%9A%E4%B9%89%E6%9C%8D%E5%8A%A1)
  - [管理服务的依赖](#%E7%AE%A1%E7%90%86%E6%9C%8D%E5%8A%A1%E7%9A%84%E4%BE%9D%E8%B5%96)
    - [添加自定义服务依赖项方法](#%E6%B7%BB%E5%8A%A0%E8%87%AA%E5%AE%9A%E4%B9%89%E6%9C%8D%E5%8A%A1%E4%BE%9D%E8%B5%96%E9%A1%B9%E6%96%B9%E6%B3%95)
    - [嵌套注入服务](#%E5%B5%8C%E5%A5%97%E6%B3%A8%E5%85%A5%E6%9C%8D%E5%8A%A1)
  - [添加服务的其他设置](#%E6%B7%BB%E5%8A%A0%E6%9C%8D%E5%8A%A1%E7%9A%84%E5%85%B6%E4%BB%96%E8%AE%BE%E7%BD%AE)
    - [服务的装饰器](#%E6%9C%8D%E5%8A%A1%E7%9A%84%E8%A3%85%E9%A5%B0%E5%99%A8)
- [Angular与服务端交互](#angular%E4%B8%8E%E6%9C%8D%E5%8A%A1%E7%AB%AF%E4%BA%A4%E4%BA%92)
  - [与服务端交互简介](#%E4%B8%8E%E6%9C%8D%E5%8A%A1%E7%AB%AF%E4%BA%A4%E4%BA%92%E7%AE%80%E4%BB%8B)
    - [传统的Ajax方式与服务端交互](#%E4%BC%A0%E7%BB%9F%E7%9A%84ajax%E6%96%B9%E5%BC%8F%E4%B8%8E%E6%9C%8D%E5%8A%A1%E7%AB%AF%E4%BA%A4%E4%BA%92)
    - [使用`$http`服务与服务端交互](#%E4%BD%BF%E7%94%A8http%E6%9C%8D%E5%8A%A1%E4%B8%8E%E6%9C%8D%E5%8A%A1%E7%AB%AF%E4%BA%A4%E4%BA%92)
    - [使用`$http`配置对象方式与服务端交互](#%E4%BD%BF%E7%94%A8http%E9%85%8D%E7%BD%AE%E5%AF%B9%E8%B1%A1%E6%96%B9%E5%BC%8F%E4%B8%8E%E6%9C%8D%E5%8A%A1%E7%AB%AF%E4%BA%A4%E4%BA%92)
  - [Angular中的缓存](#angular%E4%B8%AD%E7%9A%84%E7%BC%93%E5%AD%98)
    - [`$cacheFactory`服务创建缓存对象](#cachefactory%E6%9C%8D%E5%8A%A1%E5%88%9B%E5%BB%BA%E7%BC%93%E5%AD%98%E5%AF%B9%E8%B1%A1)
    - [`$http`服务中的缓存](#http%E6%9C%8D%E5%8A%A1%E4%B8%AD%E7%9A%84%E7%BC%93%E5%AD%98)
    - [自定义`$http`服务中的缓存](#%E8%87%AA%E5%AE%9A%E4%B9%89http%E6%9C%8D%E5%8A%A1%E4%B8%AD%E7%9A%84%E7%BC%93%E5%AD%98)
  - [`$resource`服务](#resource%E6%9C%8D%E5%8A%A1)
    - [`$resource`服务的使用和对象中的方法](#resource%E6%9C%8D%E5%8A%A1%E7%9A%84%E4%BD%BF%E7%94%A8%E5%92%8C%E5%AF%B9%E8%B1%A1%E4%B8%AD%E7%9A%84%E6%96%B9%E6%B3%95)
    - [在`$resource`服务中自定义请求方法](#%E5%9C%A8resource%E6%9C%8D%E5%8A%A1%E4%B8%AD%E8%87%AA%E5%AE%9A%E4%B9%89%E8%AF%B7%E6%B1%82%E6%96%B9%E6%B3%95)
  - [promise对象](#promise%E5%AF%B9%E8%B1%A1)
    - [promise对象在$http中的应用](#promise%E5%AF%B9%E8%B1%A1%E5%9C%A8http%E4%B8%AD%E7%9A%84%E5%BA%94%E7%94%A8)
- [Angular指令](#angular%E6%8C%87%E4%BB%A4)
  - [Angular指令概述](#angular%E6%8C%87%E4%BB%A4%E6%A6%82%E8%BF%B0)
    - [指令定义的基础](#%E6%8C%87%E4%BB%A4%E5%AE%9A%E4%B9%89%E7%9A%84%E5%9F%BA%E7%A1%80)
    - [设置指令对象的基础属性](#%E8%AE%BE%E7%BD%AE%E6%8C%87%E4%BB%A4%E5%AF%B9%E8%B1%A1%E7%9A%84%E5%9F%BA%E7%A1%80%E5%B1%9E%E6%80%A7)
  - [Angular指令对象的重要属性](#angular%E6%8C%87%E4%BB%A4%E5%AF%B9%E8%B1%A1%E7%9A%84%E9%87%8D%E8%A6%81%E5%B1%9E%E6%80%A7)
    - [指令对象中的transclude属性](#%E6%8C%87%E4%BB%A4%E5%AF%B9%E8%B1%A1%E4%B8%AD%E7%9A%84transclude%E5%B1%9E%E6%80%A7)
    - [指令对象中的link属性](#%E6%8C%87%E4%BB%A4%E5%AF%B9%E8%B1%A1%E4%B8%AD%E7%9A%84link%E5%B1%9E%E6%80%A7)
    - [指令对象中的compile属性](#%E6%8C%87%E4%BB%A4%E5%AF%B9%E8%B1%A1%E4%B8%AD%E7%9A%84compile%E5%B1%9E%E6%80%A7)
  - [Angular指令对象的scope属性](#angular%E6%8C%87%E4%BB%A4%E5%AF%B9%E8%B1%A1%E7%9A%84scope%E5%B1%9E%E6%80%A7)
    - [scope属性是布尔值](#scope%E5%B1%9E%E6%80%A7%E6%98%AF%E5%B8%83%E5%B0%94%E5%80%BC)
    - [scope属性是对象](#scope%E5%B1%9E%E6%80%A7%E6%98%AF%E5%AF%B9%E8%B1%A1)
  - [Angular指令对象的require和controller属性](#angular%E6%8C%87%E4%BB%A4%E5%AF%B9%E8%B1%A1%E7%9A%84require%E5%92%8Ccontroller%E5%B1%9E%E6%80%A7)
    - [require和controller属性的概念](#require%E5%92%8Ccontroller%E5%B1%9E%E6%80%A7%E7%9A%84%E6%A6%82%E5%BF%B5)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# 初识Angular

> Angular是Google公司提供的一套开源免费的项目框架，它是一套基于MVC结构的JavaScript开发工具

## Angular简介

Angular是基于HTML基础进行扩展的开发工具，它希望能通过HTML标签构建动态的Web应用，它的特点有数据的双向绑定、依赖注入等。

### 特点

- 使用双大括号语法对动态获取的数据进行绑定
- 能将HTML元素代码通过分合的方式组成可重用的组件
- 支持表单和表单验证
- 能使用逻辑代码与DOM元素相关联

**注意：Angular只适合构建一个CRUD的应用，不适合图形或游戏的应用开发**

## 几个Angular的示例

```javascript
<!DOCTYPE html>
<html lang="zh-CN" ng-app>
<head>
  <meta charset="UTF-8">
  <title>第一个简单的Angular示例</title>
</head>
<body>

  {{'Hello, Angular!'}}

<script src="http://cdn.bootcss.com/angular.js/1.5.6/angular.min.js"></script>
</body>
</html>
```

```javascript
<!DOCTYPE html>
<html lang="zh-CN" ng-app>
<head>
  <meta charset="UTF-8">
  <title>数值计算表达式</title>
</head>
<body>

  1.98 + 2.98 = {{1.98 + 2.98 | number : 0}}

<script src="http://cdn.bootcss.com/angular.js/1.5.6/angular.min.js"></script>
</body>
</html>
```

```javascript
<!DOCTYPE html>
<html lang="zh-CN" ng-app>
<head>
  <meta charset="UTF-8">
  <title>数据双向绑定</title>
</head>
<body>

  <input type="text" ng-model="user.name">
  <p>{{user.name}}</p>

<script src="http://cdn.bootcss.com/angular.js/1.5.6/angular.min.js"></script>
<script>
  function userController ($scope) {
    $scope.user = {
      name : ''
    }
  }
</script>
</body>
</html>
```

```javascript
<!DOCTYPE html>
<html lang="zh-CN" ng-app="MyApp">
<head>
  <meta charset="UTF-8">
  <title>在页面中绑定并显示多项数据</title>
</head>
<body>

  <ul ng-controller="stuController">
    <li ng-repeat="stu in stuList">
      <span>{{stu.name}}</span>
      <span>{{stu.sex}}</span>
      <span>{{stu.age}}</span>
      <span>{{stu.score}}</span>
    </li>
  </ul>

<script src="http://cdn.bootcss.com/angular.js/1.5.6/angular.min.js"></script>
<script>
  angular.module('MyApp', [])
  .controller('stuController', function($scope){
    $scope.stuList = [
      {name: '张明明', sex: '女', age: 24, score: 95},
      {name: '沥青死', sex: '女', age: 27, score: 87},
      {name: '刘晓华', sex: '男', age: 28, score: 86},
      {name: '陈种种', sex: '男', age: 24, score: 95}
    ];
  })
</script>
</body>
</html>
```

# Angular基础

## 表达式

在Angular中表达式是运用在视图中的一段代码，如：

```javascript
{{ 1.98 + 2.98 | number : 0 }}
```

## 控制器

在Angular中，控制器(controller)的功能是管理页面的逻辑代码，当控制器通过`ng-controller`指令被添加到DOM页面时，Angular将会通过控制器构造函数生成一个实体对象，在这个过程中，`$scope`对象作为参数注入其中，并允许用户访问`$scope`对象

### 初始化`$scope`对象

```javascript
<!DOCTYPE html>
<html ng-app="MyApp">
<head>
  <meta charset="UTF-8">
  <title></title>
</head>
<body ng-controller="MyController">

  {{text}}

<script src="./angular.min.js"></script>
<script>
  angular.module('MyApp', [])
  .controller('MyController', function($scope){
    $scope.text = 'Hello, World!';
  })
</script>
</body>
</html>
```

### 添加`$scope`对象方法

除了可以通过初始化的方式为`$scope`对象添加属性之外，还可以为`$scope`对象添加方法，并依靠这些定义的方法来满足视图层中逻辑处理和事件执行的需要

```javascript
<!DOCTYPE html>
<html ng-app="MyApp">
<head>
  <meta charset="UTF-8">
  <title></title>
</head>
<body ng-controller="MyController">

  {{text_show()}}

<script src="./angular.min.js"></script>
<script>
  angular.module('MyApp', [])
  .controller('MyController', function($scope){
    $scope.text_show = function () {
      return 'Hello, Angular!';
    }
  })
</script>
</body>
</html>
```

### 在事件中为`$scope`对象绑定方法

```javascript
<!DOCTYPE html>
<html ng-app="MyApp">
<head>
  <meta charset="UTF-8">
  <title></title>
</head>
<body ng-controller="MyController">

  <p>{{text}}</p>
  <button ng-click="click_show()">点击</button>

<script src="./angular.min.js"></script>
<script>
  angular.module('MyApp', [])
  .controller('MyController', function($scope){
    $scope.text = 'Hello, World!';
    $scope.click_show = function() {
      $scope.text = '这是点击后显示的内容';
    }
  })
</script>
</body>
</html>
```

除了可以向`$scope`对象添加方法外，还可以在方法中添加参数，多个参数通过口号隔开

```javascript
<!DOCTYPE html>
<html ng-app="MyApp">
<head>
  <meta charset="UTF-8">
  <title></title>
</head>
<body ng-controller="MyController">

  <p>{{text}}</p>
  <button ng-click="click_show()">点击显示</button>
  <button ng-click="click_params('我是带参数的')">带参数的点击</button>

<script src="./angular.min.js"></script>
<script>
  angular.module('MyApp', [])
  .controller('MyController', function($scope){
    $scope.text = '';
    $scope.click_show = function() {
      $scope.text = 'Hello, World!';
    }
    $scope.click_params = function(param) {
      $scope.text = param;
    }
  })
</script>
</body>
</html>
```

### `$scope`对象属性和方法的继承

在Angular中，`ng-controller`指令允许在不同的层次元素中指定控制器，处于子层控制器中的`$scope`对象将会自动继承父层控制器中`$scope`对象的属性和方法

```javascript
<!DOCTYPE html>
<html ng-app="MyApp">
<head>
  <meta charset="UTF-8">
  <title></title>
</head>
<body>

  <div ng-controller="parentController">
    <div ng-controller="childController">
      <span>{{text}}</span><br>
      <span>{{child_text}}</span><br>
      <button ng-click="click_show()">继承</button>
    </div>
  </div>

<script src="./angular.min.js"></script>
<script>
  angular.module('MyApp', [])
  .controller('parentController', function($scope){
    $scope.text = 'Hello, Angular!';
    $scope.click_show = function() {
      $scope.text = '单击后显示的内容';
    }
  })
  .controller('childController', function($scope){
    $scope.child_text = '欢迎来到AngularJS的世界！';
  })
</script>
</body>
</html>
```

## 模板

Angular提供一套完善的模板系统，配合`$scope`对象和数据双向绑定机制，将页面纯静态元素经过行为、属性的添加和格式的转换，最终变成在浏览器中显示的动态页

### 构建模板内容

构建的方式一般通过下面三种方式：

- 直接在页面中添加元素和Angular指令，依赖控制器中构建的属性和方式绑定模板中的元素内容和事件，实现应用需求
- 通过`type`类型为`text/ng-template`的`<script>`元素来构建一个用于绑定数据的模板
- 通过添加元素的`src`属性，导入一个外部文件作为绑定数据的模板，除了`src`属性外，还需要使用`ng-include`指令

```javascript
<!DOCTYPE html>
<html ng-app="MyApp">
<head>
  <meta charset="UTF-8">
  <title></title>
</head>
<body>

<script type="text/ng-template" id="tplbase">
  姓名: {{name}} <br>
  邮箱: {{email}}
</script>
<div ng-include="'tplbase'" ng-controller="MyController"></div>

<script src="./angular.min.js"></script>
<script>
  angular.module('MyApp', [])
          .controller('MyController', function($scope){
            $scope.name = 'Kaindy7633';
            $scope.email = 'kaindy7633@gmail.com';
          })
</script>
</body>
</html>
```

### 使用指令复制元素

在Angular中，使用`ng-repeat`指令来复制元素，也可以叫循环输入元素

在使用`ng-repeat`中，Angular还提供了几个专有变量，通过它们可以处理显示数据时的各种状态

- `$first`：标记记录是否是首条，如果是返回true，否则返回false
- `$last`：标记记录是否是尾条，如果是返回true，否则返回false
- `$middle`：标记记录是否是中间条，如果是返回true，否则返回false
- `$index`：标记记录的索引号，其对应的值从0开始

```javascript
<!DOCTYPE html>
<html ng-app="MyApp">
<head>
  <meta charset="UTF-8">
  <title></title>
</head>
<body>

  <div ng-controller="MyController">
    <ul>
      <li>
        <span>序号</span>
        <span>姓名</span>
        <span>性别</span>
        <span>是否首条</span>
        <span>是否尾条</span>
      </li>
      <li ng-repeat="stu in data">
        <span>{{$index+1}}</span>
        <span>{{stu.name}}</span>
        <span>{{stu.sex}}</span>
        <span>{{$first?'是':'否'}}</span>
        <span>{{$last?'是':'否'}}</span>
      </li>
    </ul>
  </div>

<script src="./angular.min.js"></script>
<script>
  angular.module('MyApp', [])
          .controller('MyController', function($scope){
            $scope.data = [
              {name: '张明明', sex: '女'},
              {name: '李青思', sex: '女'},
              {name: '刘晓华', sex: '男'},
              {name: '陈忠忠', sex: '男'}
            ];
          })
</script>
</body>
</html>
```

### 添加元素样式

在Angular中，添加元素样式分为以下几种方式：

**(1)** 直接绑定值为CSS类别名称的`$scope`对象属性，如：

在Angular中定义：

```javascript
$scope.red = 'red';
```

在HTML中定义：

```javascript
<div ng-class="{{red}}"></div>
```

或者

```javascript
<div class="{{red}}"></div>
```

上面的这种方式简单，但不提倡，在开发Angular应用时，尽量保证控制器代码是处理业务逻辑，而不涉及页面元素

**(2)** 以字符串数组方式选择性添加CSS类别名称

这种方式根据控制器中一个布尔类型的属性值来决定页面元素添加那种CSS样式

在Angular中定义：

```javascript
$scope.blnfocus = true;
```

在html中定义：

```javascript
<div ng-class="{true: 'red', false: 'green'}[blnfocus]"><div>
```

**(3)** 通过定义key/value对象的方式来添加多个CSS样式名称

这种方式根据控制显示样式的属性值添加多个样式名

在Angular中定义：

```javascript
$scope.a = false;
$scope.b = true;
```

在html中定义：

```javascript
<div ng-class="{'red': a, 'green': b}"></div>
```

另外，在Angular中，还有两个与定义样式相关的指令，分别是`ng-class-odd`和`ng-class-even`，它们专用于以列表方式显示数据，对应奇数行与偶数行的样式

```javascript
<!doctype html>
<html ng-app="MyApp">
<head>    
  <meta charset="UTF-8">    
  <title>Document</title>    
    <style>        
        body {font-size: 12px;}        
        ul {list-style-type: none; width: 408px; margin: 0; padding: 0;}        
        ul li {float: left; padding: 5px 0;}        
        ul .odd {color: #0026ff;}        
        ul .even {color: #ff0000;}        
        ul .bold {font-weight: bold;}        
        ul li span {width: 52px; float: left; padding: 0px 10px;}                        ul .focus {background-color: #ccc;}    
    </style>  
  </head>
    <body>    
    <div ng-controller="MyController">        
        <ul>            
          <li ng-class="{{bold}}">                
              <span>序号</span>                
              <span>姓名</span>                
              <span>性别</span>                
              <span>是否首条</span>                
              <span>是否尾条</span>            
          </li>            
          <li ng-repeat="stu in data"                
               ng-class-odd="'odd'"                
               ng-class-even="'even'"                
               ng-click="li_click($index)"                
               ng-class="{focus: $index==focus}">                          
              <span>{{$index+1}}</span>                
              <span>{{stu.name}}</span>                
              <span>{{stu.sex}}</span>                
              <span>{{$first?'是':'否'}}</span>                
              <span>{{$last?'是':'否'}}</span>            
          </li>        
      </ul>    
    </div>
<script src="./angular.min.js"></script>
<script>
  angular.module('MyApp', [])
  .controller('MyController', function($scope){
    $scope.bold = 'bold';
    $scope.li_click = function() {
      $scope.focus = i;
    };
    $scope.data = [
      {name: '张明明', sex: '女'},                    
      {name: '李青思', sex: '女'},                   
      {name: '刘晓华', sex: '男'},                   
      {name: '陈忠忠', sex: '男'}  
    ];
  })
</script>
</body>
</html>
```

### 控制元素的隐藏与显示状态

在Angular中，可以通过`ng-show`、`ng-hide`和`ng-switch`指令来控制元素的隐藏与显示

而`ng-switch`指令的功能是显示匹配成功的元素，它要与`ng-switch-when`和`ng-switch-default`指令配合使用

```javascript
<!doctype html>
<html ng-app="MyApp">
  <head>  
    <meta charset="UTF-8">  
    <title>Document</title>
  </head>
  <body>  
    <div ng-controller="MyController">    
      <div ng-show="{{isshow}}">Kaindy7633</div>    
      <div ng-hide="{{isHide}}">kaindy7633@gmail.com</div>      
      <ul ng-switch on={{switch}}>      
        <li ng-switch-when="1">Kaindy7633</li>      
        <li ng-switch-when="2">Kaindy7633@gmail.com</li>  
        <li ng-switch-default>更多...</li>    
      </ul>  
    </div>  
    <script src="./angular.min.js"></script>  
    <script>    
      angular.module('MyApp', [])    
      .controller('MyController', function($scope){       
        $scope.isshow = true;      
        $scope.isHide = false;      
        $scope.switch = 3;    
      })  
    </script>
  </body>
</html>
```

## 表单控件

### 表单基本验证功能

在Angular中，针对表单和表单控件提供了如下属性，用于验证控件交互值的状态

- `$prisine`表示表单或控件内容是否未输入过
- `$dirty`表示表单或控件内容是否已输入过
- `$valid`表单或控件内容是否已验证通过
- `$invalid`表示表单或控件内容是否未验证通过
- `$error`表示表单或控件内容验证时的错误提示信息

前面4个均返回布尔类型的值，最后一个返回一个错误对象

```javascript
<!doctype html>
<html ng-app="MyAPp">
<head>
  <meta charset="utf-8">
  <title></title>
  <style>
    body {font-size: 12px;}
    input {padding: 3px;}
  </style>
</head>
<body>
<form name="myForm" ng-submit="save()" ng-controller="MyController">
  <div>
    <input type="text" name="username" ng-model="name" required>
    <span ng-show="myForm.username.$error.required">
       用户名不能为空
    </span>
  </div>
  <div>
    <input type="email" name="email" ng-model="email" required>
    <span ng-show="myForm.email.$error.required">Email地址不能为空</sapn>
    <span ng-show="myForm.email.$error.email">Email格式不正确</span>
  </div>
  <div>
    <input type="submit" name="submit" ng-disabled="myForm.$invalid" value="提交">
  </div>
</form>

<script src="./angular.min.js"></script>
<script>
  var myform = angular.module('MyApp', []);
  myfrom.controller('MyController', ['$scope', function($scope){
    $scope.name = 'Kaindy7633';
    $scope.email = 'kaindy7633@gmail.com';
    $scope.save = function(){
      alert('保存成功');
    }  
  }]);
</script>
</body>
</html>
```

### 表单中的checkbox和radio控件

```javascript
<!doctype html>
<html ng-app="MyApp">
  <head>  
    <meta charset="UTF-8">  
    <title>Document</title>  
    <style>    
      body { font-size: 12px;}    
      input { padding: 3px;}  
    </style>
  </head>
  <body>
  <form name="myForm" ng-submit="save()" ng-controller="MyController">  
    <input type="checkbox" ng-model="a">同意  
    性别:  
    <input type="radio" ng-model="b" value="男">男  
    <input type="radio" ng-model="b" value="女">女  
    <input type="submit" vlaue="提交">  
    <p>{{c}}</p>
  </form>
  <script src="./angular.min.js"></script>
  <script>  
  var myform = angular.module('MyApp', []);  
  myform.controller('MyController', ['$scope', function($scope){    
    $scope.a = true;    
    $scope.b = '男';    
    $scope.save = function() {      
      $scope.c = '您选择的是:' + $scope.a + '和' + $scope.b;    }  }]);
  </script>
</body>
</html>
```

### 表单中的select控件

在Angular中，select控件可以借助`ng-options`指令将数组、对象等数据添加到`<option>`元素中

**(1)** 绑定简单的数组数据

在控制器中添加数组数据

```javascript
$scope.data = ['a', 'b', 'c', 'd'];
```

在select控件中，通过`ng-options`指令，采用`...for...in...`格式将数组数据与select控件绑定

```javascript
<select ng-model="a" ng-options="text for txt in data">
  <option value="">--请选择--</option>
</select>
```

```javascript
<!doctype html>
<html ng-app="MyApp">
<head>  
  <meta charset="UTF-8">  
  <title>Document</title>
</head>
<body>
  <form ng-controller="MyController">  
    <select ng-model="a" ng-options="txt for txt in data"> 
      <option value="">--请选择--</option>  
    </select>
  </form>
  <script src="./angular.min.js"></script>
  <script>  
  var myform = angular.module('MyApp', []); 
  myform.controller('MyController', ['$scope', function($scope){    
    $scope.data = ['A', 'B', 'C', 'D', 'E'];  
  }]);
  </script>
</body>
</html>
```

**(2)** 绑定简单的对象数据

在控制器中添加对象数据

```javascript
$scope.data = [
  {id: '1', name: 'A'},
  {id: '2', name: 'B'},
  {id: '3', name: 'C'},
  {id: '4', name: 'D'}
];
```

在控件中，采用`...as...for...in...`的格式将对象数据与select绑定

```javascript
<select ng-model="a" ng-options="txt.id as txt.name for txt in data">
  <option value="">--请选择--</option>
</select>
```

**(3)** 以分组的形式绑定对象数据

首先在控制器中添加对象数据

```javascript
$scope.data = [
  {id: '1', name: 'A', key: '大写'},
  {id: '2', name: 'B', key: '大写'},
  {id: '3', name: 'C', key: '小写'},
  {id: '4', name: 'D', key: '小写'}
];
```

如果在上述数据中，以key为分组依据，则可以采用`...as...group by...for...in...`的格式

```javascript
<select ng-model="a" ng-options="txt.id as txt.name group by txt.key for txt in data">
  <option value="">--请选择--</option>
</select>
```

综合示例：

```javascript
<!doctype html>
<html ng-app="MyApp">
<head>
  <meta charset="UTF-8">
  <title>Document</title>
</head>
<body>
<form name="myform" ng-controller="MyController">  
  <div>
    学制: 
   <select ng-model="school" ng-options="s.id as s.name for s in schoolData" ng-change="schoolChange(school)"> 
     <option value="">--请选择--</option>
    </select>
    <span>{{school_show}}</span>  
  </div>
  <div>
    班级:
   <select ng-model="class" ng-options="c.id as c.name group by c.grade for c in classData" ng-change="classChange(class)">
      <option value="">--请选择--</option>
    </select>
    <span>{{class_show}}</span>
  </div>
</form>
<script src="./angular.min.js"></script>
<script>
  var myapp = angular.module('MyApp', []);  
  myapp.controller('MyController', ['$scope', function($scope){    
    $scope.schoolData = [      
      {id: '1001', name: '小学'}, 
      {id: '1002', name: '初中'},
      {id: '1003', name: '高中'}    
    ];
    $scope.classData = [
      {id: '1001', name: '(1)班', grade: '一年级'},
      {id: '1002', name: '(2)班', grade: '一年级'}, 
      {id: '2001', name: '(1)班', grade: '二年级'},
      {id: '2002', name: '(2)班', grade: '二年级'},
      {id: '3001', name: '(1)班', grade: '三年级'},
      {id: '3002', name: '(2)班', grade: '三年级'}
    ];
    $scope.school = '';
    $scope.class = '';
    $scope.schoolChange = function(e) {      
      $scope.school_show = '您选择的是:' + e;
    }
    $scope.classChange = function(e) { 
     $scope.class_show = '您选择的是:' + e; 
    }  
 }]);
</script>
</body>
</html>
```

# Angular的过滤器和作用域

在Angular中，过滤器的功能主要是格式化数据表达式，且可以自定义过滤器。作用域(scope)主要服务于页面模板，在控制器和页面中起桥梁作用，保存模板中的数据对象，为模板中的元素提供方法和属性

## 过滤器

在Angular中，过滤器主要有三种形式，它们分别是：

**(1)** 单个过滤器，如：

```javascript
{{表达式 | 过滤器名}}
```

```javascript
{{8.88 | currency}}  // $8.88
```

**(2)** 多个过滤器，如：

```javascript
{{表达式 | 过滤器名1 | 过滤器名2 | ...}}
```

```javascript
{{8.88 | currency | filter | ...}}
```

**(3)** 带参数过滤器,如：

```javascript
{{表达式 | 过滤器名1 : 参数1 : 参数2 : ...}}
```

```javascript
{{8.88 | number : 1}}
```

### 排序方式过滤

```javascript
<!doctype html>
<html ng-app="MyApp">
<head>
  <meta charset="UTF-8">
  <title>Document</title>
  <link rel="stylesheet" href="./bootstrap.min.css">
  <style>
    body {padding: 15px;}
  </style>
</head>
<body>

<div ng-controller="stuController">
  <table class="table table-bordered table-responsive table-hover">
    <tr>
      <th>序号</th>
      <th>姓名</th>
      <th>性别</th>
      <th>年龄</th>
      <th>成绩</th>
    </tr>
    <!-- 在下面的ng-repeat指令后通过管道符'|'添加排序过滤器 -->
    <tr ng-repeat="stu in data | orderBy: 'score'">
      <td>{{$index+1}}</td>
      <td>{{stu.name}}</td>
      <td>{{stu.sex}}</td>
      <td>{{stu.age}}</td>
      <td>{{stu.score}}</td>
    </tr>
  </table>
</div>

<script src="./angular.min.js"></script>
<script>
  var stulist = angular.module('MyApp', []);
  stulist.controller('stuController', ['$scope', function($scope){
    $scope.bold = 'bold';
    $scope.data = [
      {name: '张明明', sex: '女', age: 24, score: 95},
      {name: '李青思', sex: '女', age: 27, score: 87},
      {name: '刘晓华', sex: '男', age: 28, score: 86},
      {name: '陈忠忠', sex: '男', age: 23, score: 97}
    ];
  }]);
</script>
</body>
</html>
```

上面的示例中视图模板通过`ng-repeat`指令绑定数据，调用`orderBy`过滤器对分数列进行排序，`orderBy`排序过滤器后面带了参数`score`，默认以`score`为标准进行升序排列，如果要降序排序，在`score`前面加个`-`即可

```javascript
<tr ng-repeat="stu in data | orderBy: '-score'">
```

我们还可以继续在后面加上过滤器，如`limitTo`,它的作用是限制列表显示列数

```javascript
<tr ng-repeat="stu in data | orderBy: '-score' | limitTo: 3">
<!-- 只显示3列数据 -->
```

### 匹配方式过滤

匹配方式过滤是将字符参数与列表中的各个成员属性值相匹配，如果包含则显示，匹配时不区分大小写。它有三种形式：

**(1)** 通过filter过滤器直接匹配包含字符参数的数据

```javascript
{{数据 | filter: '匹配字符'}}
```

```javascript
<!-- 在data数据中找到包含80的记录 -->
{{data | filter: 80}}
```

**(2)** 在字符参数中使用对象形式匹配指定属性的数据

```javascript
{{数据 | filter: 对象}}
```

```javascript
{{data | filter: {score: 80}}}
```

**(3)** 在字符参数中使用自定义函数匹配相应数据

```javascript
{{数据 | filter: 函数名称}}
```

```javascript
<!doctype html>
<html ng-app="MyApp">
<head>
  <meta charset="UTF-8">
  <title>Document</title>
  <link rel="stylesheet" href="./bootstrap.min.css">
  <style>
    body {padding: 15px;}
  </style>
</head>
<body>

<div ng-controller="stuController">
  <table class="table table-bordered table-responsive table-hover">
    <tr>
      <th>序号</th>
      <th>姓名</th>
      <th>性别</th>
      <th>年龄</th>
      <th>成绩</th>
    </tr>
    <!-- 调用findescore函数对数据进行过滤 -->
    <tr ng-repeat="stu in data | filter: findscore">
      <td>{{$index+1}}</td>
      <td>{{stu.name}}</td>
      <td>{{stu.sex}}</td>
      <td>{{stu.age}}</td>
      <td>{{stu.score}}</td>
    </tr>
  </table>
</div>

<script src="./angular.min.js"></script>
<script>
  var stulist = angular.module('MyApp', []);
  stulist.controller('stuController', ['$scope', function($scope){
    $scope.bold = 'bold';
    $scope.data = [
      {name: '张明明', sex: '女', age: 24, score: 95},
      {name: '李青思', sex: '女', age: 27, score: 87},
      {name: '刘晓华', sex: '男', age: 28, score: 86},
      {name: '陈忠忠', sex: '男', age: 23, score: 97}
    ];
    // 定义过滤函数，筛选成绩大于85且小于90的数据
    $scope.findscore = function(e) {
      return e.score > 85 && e.score < 90;
    }
  }]);
</script>
</body>
</html>
```

### 自定义过滤器

自定义过滤器需要在页面模块中注册一个过滤器的构造方法，该方法将返回一个以输入值为首个参数的函数，在函数体中实现过滤器的功能

接上面的例子，我们在模块stulist上自定义一个过滤器，它的作用是筛选出年龄在22到28之间的，且性别是被指定的数据

JS代码：

```javascript
/* 实现自定义过滤器,在模块上使用filter方法,第1个参数是过滤器名,第二个是实现函数
 * 在实现里直接返回一个函数
 * 过滤器筛选出年龄在22和28之间的,且性别被指定的数据
 */
stulist.filter('young', function(){
return function(e, type) {
  var _out = [];
  var _sex = type ? '男' : '女';
  for(var i=0; i< e.length; i++) {
    if(e[i].age > 22 && e[i].age < 28 && e[i].sex == _sex) {
      _out.push(e[i]);
    }
  }
  return _out;
}
});
```

html代码：

```javascript
<!-- 也可以将young这个过滤器的参数换成true或false -->
<tr ng-repeat="stu in data | young: 0">
  <td>{{$index+1}}</td>
  <td>{{stu.name}}</td>
  <td>{{stu.sex}}</td>
  <td>{{stu.age}}</td>
  <td>{{stu.score}}</td>
</tr>
```

## 过滤器的应用

### 表头排序

表头排序是指在使用列表方式显示数据时，用户如果单击列表某列的表头元素，那么列表中的全部数据将会自动按该列的属性值自动排序，默认为升序排列，再次单击会变为降序排列

html：

```javascript
<table class="table table-bordered table-responsive table-hover">
	<tr>
		<!-- 在每个表头中增加ng-click事件 -->
	  <th>序号</th>
	  <th ng-click="title='name'; desc=!desc">姓名</th>
	  <th ng-click="title='sex'; desc=!desc">性别</th>
	  <th ng-click="title='age'; desc=!desc">年龄</th>
	  <th ng-click="title='score'; desc=!desc">成绩</th>
	</tr>
	<!-- 为数据增加排序过滤器 -->
	<tr ng-repeat="stu in data | orderBy: title: desc">
	  <td>{{$index+1}}</td>
	  <td>{{stu.name}}</td>
	  <td>{{stu.sex}}</td>
	  <td>{{stu.age}}</td>
	  <td>{{stu.score}}</td>
	</tr>
</table>
```

javascript:

```javascript
var stulist = angular.module('MyApp', []);
stulist.controller('stuController', ['$scope', function($scope){
	$scope.data = [
	  {name: '张明明', sex: '女', age: 24, score: 95},
	  {name: '李青思', sex: '女', age: 27, score: 87},
	  {name: '刘晓华', sex: '男', age: 28, score: 86},
	  {name: '陈忠忠', sex: '男', age: 23, score: 97}
	];
	$scope.title = 'name';
	$scope.desc = 0;
}]);
```

### 字符查找

字符查找是指通过调用Angular中的`filter`过滤器，查找与过滤器冒号后字符参数相匹配的数据，如果匹配则显示，否则不显示

在上面的例子中，我们首先增加一个用于输入过滤关键字的`input`

```javascript
<!-- 在页面中增加input，用于输入过滤关键字 -->
<input type="text" ng-model="key" placeholder="请输入关键字">

<!-- 在循环中增加过滤器filter，对用户输入进行匹配 -->
<tr ng-repeat="stu in data | orderBy: title: desc | filter: {name:key}">
```

```javascript
// 在js代码中初始化key的值
$scope.key = '';
```

## 作用域概述

`$scope`对象实质上是一个作用域对象，它能存储数据模型，为表达式提供上下文环境和监听表达式的变化且传播时间，是视图与控制器之间的桥梁

### 作用域特点

- 它提供了一个`$watch`方法来监听数据模型的变化，`ng-model`指令就是通过该方法进行数据的监听，只要有一端发生变化，则另一端自动进行同步更新

- 它提供了一个`$apply`方法，为各种烈性的数据模型改变提供支撑，将它们引入到Angular可控制的范围中。

- 它为表达式提供了执行的环境，一个表达式必须在拥有该表达式属性的作用域中执行才更加合适

下面的示例说明`$watch`如何工作

```javascript
<!doctype html>
<html ng-app="MyApp">
<head>
  <meta charset="UTF-8">
  <title>Document</title>
  <link rel="stylesheet" href="./bootstrap.min.css">
</head>
<body ng-controller="MyController">

<div>
  <input type="text" ng-model="name" placeholder="请输入姓名">
</div>
<div>
  累计变化次数: {{count}}
</div>

<script src="./angular.min.js"></script>
<script>
  var myapp = angular.module('MyApp', []);
  myapp.controller('MyController', ['$scope', function($scope){
    $scope.name = '';
    $scope.count = 0;
    // 通过 $watch 方法监听name的变化次数
    $scope.$watch('name', function(){
      $scope.count++;
    })
  }])
</script>
</body>
</html>
```

### 作为数据模型的作用域

作用域是控制器与视图的桥梁，也是视图和指令的桥梁

## 作用域的层级和事件

作用域绑定页面元素后，便依据元素的层次关系形成了自己的层级关系，在这些层级关系中，他们可以通过事件的传播进行数据的通信

### 作用域的层级

作用域拥有自己的层级，且它有一个顶级作用域`$rootScope`，而下面的子级作用域可以创建多个，子级作用域可以继承父级作用域中的全部属性和方法，但同级作用域却不行。

```javascript
<!doctype html>
<html ng-app="MyApp">
<head>
  <meta charset="UTF-8">
  <title>Document</title>
  <link rel="stylesheet" href="./bootstrap.min.css">
</head>
<body>

<div ng-controller="parentController">
  <div ng-controller="childController_a">
    {{parent_name}}, 我是第一个子层控制器的内容
  </div>
  <div ng-controller="childController_b">
    {{parent_name}}, 我是第二个子层控制器的内容
  </div>
</div>

<script src="./angular.min.js"></script>
<script>
  var myapp = angular.module('MyApp', []);
  // 在父级控制器中定义parent_name变量
  myapp.controller('parentController', ['$scope', function($scope){
    $scope.parent_name = 'Hello';
  }]);
  // 自动继承父级作用域中的属性
  myapp.controller('childController_a', ['$scope', function($scope){
    // todo...
  }]);
  // 自动继承父级作用域中的属性
  myapp.controller('childController_b', ['$scope', function($scope){
    // todo...
  }]);
</script>
</body>
</html>
```

### 作用域事件的传播

在Angular中，作用域间有非常清晰的层次结构关系，最顶层的是`rootscope`作用域，其余的都是在它基础之上进行分支和嵌套的。

那么，我们有两种方法可以实现作用域之间的通信：

**(1)** 服务(service)

通过在各作用域之间创建一个单例的服务，由该服务来处理各个作用域间的数据通信

**(2)** 事件(event)

通过作用域之间的事件也可以进行数据通信，Angular提供了两个方法`$broadcasted`和`$emitted`

- `$broadcasted`方法将事件从父级作用域传播至子级作用域，它有两个参数，`eventname`，表示事件名称，`data`表示传播过程中携带的数据

- `$emitted`方法将事件从子级作用域传播至父级作用域，与上面的方法相同。

除了上面的两个方法外，还需要调用`$on`方法，在作用域中监控传播来的事件并获取相应的数据。

```javascript
$on(eventname, function(event, data) {
	// 接收传播事件的处理代码
})
```

# Angular的依赖注入

在Angular中创建一个对象时，需要依赖另一个对象，这是代码层的一种依赖关系，当这种依赖被声明后，Angular通过`injector`注入器将所依赖的对象进行注入操作

## 依赖注入介绍

### 依赖注入的原理

看下面的示例代码：

```javascript
<div ng-controller="MyController">
  <div class="{{cls}}">{{show}}</div>
  <button ng-click="onClick()">点我</button>
</div>
```

```javascript
var myapp = angular.module('MyApp', []);
myapp.config(function($controllerProvider) {
  $controllerProvider.register('MyController', ['$scope', function($scope) {
    $scope.cls = '';
    $scope.onClick = function () {
      $scope.cls = 'show';
      $scope.show = '点击后显示的内容';
    }
  }])
})
```

看上面的代码，与我们平时定义控制器的方式不一样

```javascript
myapp.controller('MyController', ['$scope', function($scope){
  // 控制器代码
}])
```

在Angular中，通过模块的config函数来声明需要注入的依赖对象，而声明的方式是通过调用provider服务。

但在Angular内部，控制器并不是由`provider`服务来创建的，而是由`controllerProvider`服务创建，在创建过程中，实际上是在config函数中调用`controllerProvider`服务的`register`方法，再调用`injector`注入器完成各个依赖对象的注入。


### 简单依赖注入的示例

在Angular中，config函数的功能是为定义的模板对象注入依赖的各种服务。除了用于注册控制器的controllerProvider服务外，还有一个`$provider`服务，其中它包含了如`provider`方法、`factory`方法、`service`方法和`value`方法，这些方法都可以通过服务创建一个自定义的依赖注入对象。

示例：

html：

```javascript
<div ng-controller="myCtrl">
  <div class="{{cls}}">{{text}}</div>
  <button ng-click="onClick(1)">早上</button>
  <button ng-click="onClick(2)">上午</button>
  <button ng-click="onClick(3)">下午</button>
  <button ng-click="onClick(4)">晚上</button>
</div>
```

```javascript
  var app = angular.module('myApp', []);
  app.config(function ($provide) {
    $provide.provider('myprovider', function () {
      this.$get = function () {
        return {
          val: function (name) {
            return name;
          }
        }
      }
    })
  });
  app.config(function ($provide) {
    $provide.factory('myfactory', function () {
      return {
        val: function (name) {
          return name;
        }
      }
    })
  });
  app.config(function ($provide) {
    $provide.value('myvalue', function (name) {
      return name;
    })
  });
  app.config(function ($provide) {
    $provide.service('myservice', function () {
      return {
        val: function (name) {
          return name;
        }
      }
    })
  });
  app.controller('myCtrl', ['$scope', 'myprovider', 'myfactory', 'myvalue', 'myservice',
  function ($scope, myprovider, myfactory, myvalue, myservice) {
    $scope.cls = '';
    $scope.onClick = function (t) {
      $scope.cls = 'show';
      switch (t) {
        case 1: $scope.text = myprovider.val('早上好'); break;
        case 2: $scope.text = myfactory.val('上午好'); break;
        case 3: $scope.text = myvalue('下午好'); break;
        case 4: $scope.text = myservice.val('晚上好'); break;
      }
    }
  }]);
```


## 依赖注入标记

每个Angular应用都是通过由注入器(`injector`)负责查找和创建依赖注入的服务，当注入器执行时，它需要一些标记，来判断需要注入什么样的依赖服务，而这些标记，就是依赖注入标记。

依赖注入标记根据声明的方式，分为：

- 推断式注入
- 标记式注入
- 行内式注入

### 推断式注入

推断式注入是一种猜测式的注入，在没有明确声明的情况下，Angular认为参数名称就是依赖注入的函数名，并在内部调用函数对象的`toString`方法，获取对应的参数列表，然后通过注入器(`injector`)将这些参数注入到应用实例中，从而实现依赖注入。

示例：

html:

```javascript
<div ng-controller="myCtrl">
  <input type="button" value="弹出对话框" ng-click="onClick('我是一个弹出对话框')">
</div>
```

javascript:

```javascript
var app = angular.module('myApp', []);
  app.factory('myfactory', function ($window) {
    return {
      show: function (text) {
        $window.alert(text);
      }
    }
  });
  var myCtrl = function ($scope, myfactory) {
    $scope.onClick = function (msg) {
      myfactory.show(msg);
    }
  }
  app.controller('myCtrl', myCtrl);
```

### 标记式注入

标记式注入明确了一个函数在执行过程中需要依赖的各项服务，它可以直接调用`$injector`属性来完成，它的属性值是一个数组，数组元素是需要注入的各项服务的名称，所以这种方式的注入顺序很重要

示例：

html：

```javascript
<div ng-controller="myCtrl">
  <div class="show">{{text}}</div>
  <input type="button" value="弹出" ng-click="onShow('我是一个弹出对话框')">
  <input type="button" value="显示" ng-click="onWrite('今天天气有点冷啊')">
</div>
```

javascript:

```javascript
var app = angular.module('myApp', []);
  app.factory('$show', ['$window', function ($window) {
    return {
      show: function (text) {
        $window.alert(text);
      }
    }
  }]);
  app.factory('$write', function () {
    return {
      write: function (text) {
        return text;
      }
    }
  });

  var myCtrl = function ($scope, $show, $write) {
    $scope.onShow = function (msg) {
      $show.show(msg);
    }
    $scope.onWrite = function (msg) {
      $scope.text = $write.write(msg);
    }
  }
  app.controller('myCtrl', myCtrl);
  app.$inject = ['$scope', '$show', '$write'];
```

这种注入方式由于服务名和函数参数名在名称和顺序的一一对应关系，使得服务名和函数体绑定在一起，因此这种方式可以在压缩或混淆后的代码中执行。

### 行内式注入

所谓行内式注入，就是在构建一个Angular对象时，允许将一个字符型数组作为对象的参数，而不仅仅是一个函数。

在这个数组中，除最后一个必须是函数体外，其余都代表注入对象中的服务名，而他们的名称和顺序与最后一个函数的参数是一一对应的。

示例：

html：

```javascript
<div ng-controller="myCtrl">
  <div class="show">{{text}}</div>
  <input type="button" value="求和" ng-click="onClick(5,10)">
</div>
```

```javascript
var app = angular.module('myApp', []);
  app.factory('$sum', function () {
    return {
      add: function (m, n) {
        return m + n;
      }
    }
  });
  app.controller('myCtrl', ['$scope', '$sum', function ($scope, $sum) {
    $scope.onClick = function (m, n) {
      $scope.text = m + " + " + n + ' = ' + $sum.add(m, n);
    }
  }])
```

这种方法更简洁，同样也能在压缩或混淆后的代码中执行

## $injector常用API

Angular中依赖注入离不开一个重要的对象--注入器(`$injector`)，整个Angular应用中的注入对象都由它负责定位和创建，它也有很多方法，如`get`、`has`、`invoke`等

### has和get方法

`has`方法的功能是根据传入的名称，从注册的列表中查找对应的服务，如果找到返回true，否则返回false

```javascript
injector.has(name)
```

- `injector`为获取的`$injector`对象
- `name`为需要查找的服务名称

最后返回一个布尔值

`get`方法返回指定名称的服务实例，获取到服务的实例对象后，就可以直接调用服务中的属性和方法

```javascript
injector.get(name)
```

- `injector`为获取的`$injector`对象
- `name`为需要返回实例的服务名称

执行代码后，将返回一个服务实例

```javascript
var app = angular.module('myApp', []);
  app.factory('$custom', function () {
    return {
      print: function (msg) {
        console.log(msg);
      }
    }
  });
  // 获取injector对象
  var injector = angular.injector(['app', 'ng']);
  // 通过has方法判断是否有$custom服务
  var has = injector.has('$custom');
  console.log(has);
  // 判断如果存在$custom服务，则调用其方法在控制台输出任意字符
  if (has) {
    var custom = injector.get('$custom');
    custom.print('控制台输入任意的内容！');
  }
  app.controller('myCtrl', ['$scope', '$custom', function ($scope, $custom) {
    // ....
  }]);
```

### invoke方法

`invoke`方法可以执行一个自定义的函数，除此之外，在执行函数时，还能传递变量给函数自身

```javascript
injector.invoke(fn, [self], [locals])
```

- `injector`为获取的`$injector`对象
- `fn`为需要执行的函数名称
- `self`是可选参数，它是一个对象，表示用于函数中的`this`变量
- `locals`可选参数，也是一个对象，它能为函数中的变量名的传递提供方法支持

```javascript
var myapp = angular.module('myApp', []);
  myapp.factory('$custom', function () {
    return {
      print: function (msg) {
        console.log(msg);
      }
    }
  });
  var injector = angular.injector(['myapp', 'ng']);
  var fun = function ($custom) {
    $custom.print('函数执行成功！');
  }
  injector.invoke(fun);
  myapp.controller('myCtrl', ['$scope', '$custom', function ($scope, $custom) {
    //...
  }])
```

### 依赖注入的应用场景

# Angular中的MVC模式

## MVC模式概述

### MVC简介

### 使用Angular中MVC的优势和缺点

- 提升服务器性能
- 减少项目开发时间
- 页面渲染缓慢
- 页面兼容性较差，不利于搜索引擎

## Model组件

在`Model`组件中，可以存储和处理数据，同时还可以在组件中自定义模板，通过模板实现与界面(View)层的通信和数据交互

### Model组件的基本概念

在Angular的MVC模式下，Model属于数据层，它即可以表示整个Anglar应用的数据模型对象，也可以只表示某个实体对象

Model数据模型对象依附于作用域，无论是整个模型对象或某个实体对象，都必须被Angular的作用域以属性的方式进行引用，这种引用可以显式或隐式的进行创建

html:

```javascript
<div ng-controller="myCtrl">
  <div class="show">{{name}}</div>
  <!-- 隐式的创建数据模型score -->
  <input type="text" value="95" ng-model="score">
  <div class="show">{{score}}</div>
</div>
```

javascript:

```javascript
var app = angular.module('myApp', []);
  app.controller('myCtrl', ['$scope', function ($scope) {
    // 显式的创建数据模型name
    $scope.name = '张三';
  }])
```

### 使用ngRepeater方式遍历Model对象

如果创建的模型对象是一个数组，那么就可以使用`ngRepeater`来遍历这个模型对象

html:

```javascript
<div ng-controller="myCtrl">
  <p ng-repeat="stu in data" class="show">
    <span>{{stu.name}}</span>
    <span>{{stu.sex}}</span>
  </p>
</div>
```

javascript:

```javascript
var app = angular.module('myApp', []);
  app.controller('myCtrl', ['$scope', function ($scope) {
    $scope.data = [
      {name: "李青思", sex: "女"},
      {name: "张明明", sex: "女"},
      {name: "刘晓华", sex: "男"},
      {name: "陈忠忠", sex: "男"}
    ];
  }])
```

## Controller组件

在Angular中，MVC中的C指的是Controller组件，即应用的控制器，本质上它是一个JavaScript的函数，用于衔接页面模板和逻辑代码，并通过添加对象和行为来增强模板中作用域的功能

### 控制器的属性和方法

在Angular中创建控制器是为了实现视图模板与逻辑代码的关联，而实现关联的方法是以`scope.$new`的方法向控制器中添加模型属性

html:

```javascript
<div ng-controller="myCtrl">
  <button ng-click="changeA()">李四</button>
  <button ng-click="changeB()">王二</button>
  <p class="show">我的名字叫： {{name}}</p>
</div>
```

javascript:

```javascript
var app = angular.module('myApp', []);
  app.controller('myCtrl', ['$scope', function ($scope) {
    $scope.name = '张三';
    $scope.changeA = function () {
      $scope.name = '李四';
    }
    $scope.changeB = function () {
      $scope.name = '王二';
    }
  }])
```

### 控制器方法中的参数

在控制器中添加的方法与普通的函数一样，都可以添加参数，在调用过程中传递实参

html:

```javascript
<div ng-controller="myCtrl">
  <div>
    <input type="text" ng-model="a" value="0">
    <span>{{type}}</span>
    <input type="text" ng-model="b" value="0">
    <span>=</span>
    <span>{{result}}</span>
  </div>
  <div>
    <button ng-click="change(1)">加法</button>
    <button ng-click="change(0)">乘法</button>
  </div>
</div>
```

javascript:

```javascript
var app = angular.module('myApp', []);
  app.controller('myCtrl', ['$scope', function ($scope) {
    $scope.type = '+';
    $scope.change = function (t) {
      if (t) {
        $scope.type = '+';
        $scope.result = parseInt($scope.a) + parseInt($scope.b);
      } else {
        $scope.type = '*';
        $scope.result = $scope.a * $scope.b;
      }
    }
  }])
```

### 控制器中属性和方法的继承

Angular中的继承与原生JavaScript有所不同，控制器中的继承是由视图模板的结构来定义的。处在子节点的模板控制器可以继承父节点所对应的模板控制器，即可以直接访问父节点控制器中的模型属性和方法，反之则不行。

html:

```javascript
<div ng-controller="mainCtrl">
  <div>
    {{name_a+'/'+name_b+'/'+name_c+'/'+score}}
  </div>
  <div ng-controller="parentCtrl">
    <div>
      {{name_a+'/'+name_b+'/'+name_c+'/'+score}}
    </div>
    <div ng-controller="childCtrl">
      <div>
        {{name_a+'/'+name_b+'/'+name_c+'/'+score}}
      </div>
    </div>
  </div>
</div>
```

javascript:

```javascript
var app = angular.module('myApp', []);
  app.controller('mainCtrl', ['$scope', function ($scope) {
    $scope.name_a = '张三';
    $scope.score = 60;
  }]);
  app.controller('parentCtrl', ['$scope', function ($scope) {
    $scope.name_b = '李四';
    $scope.score = 70;
  }]);
  app.controller('childCtrl', ['$scope', function ($scope) {
    $scope.name_c = '王二';
    $scope.score = 80;
  }])
```

一般来时候，一个控制器值包括一个对应视图模板的业务逻辑，不应将过多的页面DOM操作加入到控制器中，这样做会加大测试难度。另外，不属于视图业务逻辑的数据请求和获取，应尽量通过服务调用的形式来实现，而不是在控制器中实现。

## View组件

在Angular的MVC模式下，V就是视图层，即View组件。它的外形取决于视图模板，内部数据来源于控制器。我们可以通过`ng-view`指令加载和切换视图模板，并将视图组件通过`ng-controller`指令与控制器相绑定

### View组件中的模板切换

Angular应用由一个单页来实现，为了在视图模板中实现多个功能，需要在页面的局部进行刷新或切换，这样我们就需要在视图中引入`ng-view`指令，在控制器中引入`$routeProvider`服务

html:

```javascript
<div>
  <a href="#/">首页</a> |
  <a href="#/book">图书</a> |
  <a href="#/game">游戏</a>
</div>
<!-- 使用ng-view指令定义容器装载不同的页面内容 -->
<div ng-view></div>
```

javascript:

```javascript
<script src="./angular.min.js"></script>
// routeProvider没有集成在angular的源码中，需要单独引入
<script src="./angular-route.min.js"></script>
<script>
  var app = angular.module('myApp', ['ngRoute']);
  app.controller('indexController', ['$scope', function ($scope) {
    $scope.title = '这是首页';
  }]);
  app.controller('bookController', ['$scope', function ($scope) {
    $scope.title = '这是图书页';
  }]);
  app.controller('gameController', ['$scope', function ($scope) {
    $scope.title = '这是游戏页';
  }]);
  app.config(['$routeProvider', function ($routeProvider) {
    $routeProvider.when('/', {
      controller: 'indexController',
      template: '<div>{{title}}</div>'
    })
    .when('/book', {
      controller: 'bookController',
      template: '<div>{{title}}</div>'
    })
    .when('/game', {
      controller: 'gameController',
      template: '<div>{{title}}</div>'
    })
    .otherwise({
      redirectTo: '/'
    });
  }]);
</script>
```

### 在切换视图模板时传递参数

在切换视图模板时，我们还可以传递参数，并且可以将一个页面的文件名作为切换的模板地址。所以，我们可以将一个应用分隔成多个功能页，由它们完成不同的模块功能

html:

```javascript
<div ng-view></div>
```

javascript:

```javascript
<script src="../angular.min.js"></script>
<script src="../angular-route.min.js"></script>
<script>
  var app = angular.module('myApp', ['ngRoute']);
  app.controller('stuListController', ['$scope', function ($scope) {
    $scope.students = students;
  }]);
  app.controller('stuDetailController', ['$scope', '$routeParams',
    function ($scope, $routeParams) {
      for (var i=0; i<students.length; i++) {
        if (students[i].stuId == $routeParams.id) {
          $scope.student = students[i];
          break;
        }
      }
  }]);
  app.config(['$routeProvider', function ($routeProvider) {
    $routeProvider
    .when('/', {
      controller: 'stuListController',
      templateUrl: 'stuList.html'
    })
    .when('/view/:id', {
      controller: 'stuDetailController',
      templateUrl: 'stuDetail.html'
    })
    .otherwise({
      redirectTo: '/'
    });
  }]);
  var students = [
    {stuId: 1000, name: '张明明', sex: '女', score: 60},
    {stuId: 1001, name: '李青思', sex: '女', score: 80},
    {stuId: 1002, name: '刘晓华', sex: '男', score: 90},
    {stuId: 1003, name: '陈忠忠', sex: '男', score: 70}
  ];
</script>
```

# Angular中的服务

在Angular中，服务的本质是一些和控制器捆绑在一起的可替换的对象，通过这些对象提供了在应用的整个生命周期都存有数据的方法，当重载或刷新页面时，数据不会被清除，而且还与加载之前保持一致。

## Angular服务介绍

在Angular中服务是一种单例对象。服务主要的功能是为实现应用的功能提供数据和对象。它又可以分为内置服务和自定义服务

### 内置服务

Angular提供了很多内置服务，如`$scope`、`$http`、`$window`、`$location`等。

html：

```javascript
<div ng-controller="MyController">
  <div>当前的地址是： {{url}}</div>
  <button ng-click="onclick()">显示地址</button>
</div>
```

```javascript
var myapp = angular.module('MyApp', []);
myapp.controller('MyController', ['$scope', function($scope){
  $scope.onclick = function () {
    $scope.url = $location.absUrl();
  }
}])
```

`$location`服务除了包含`absUrl()`方法外，还有`search()`和`path()`等方法。同时它还提供了`$locationChangeStart`和`$locationChangeSuccess`方法

### 自定义服务

自定义服务有两种方法，一是使用内置的`$provider`服务，另一种是调用模块(Module)中的服务注册方法，如`factory`、`service`、`constant`和`value`等方法

html:

```javascript
<div ng-controller="myCtrl">
  <div>服务返回的值：
    <span>{{info('name')}}</span>
    <span>{{info('sex')}}</span>
    <span>{{info('score')}}</span>
  </div>
</div>
```

javascript:

```javascript
var app = angular.module('myApp', []);
  app.factory('$output', function () {
    var stu = {
      name: '张三',
      sex: '男',
      score: 60
    }
    return stu;
  });
  app.controller('myCtrl', ['$scope', '$output', function ($scope, $output) {
    $scope.info = function (n) {
      for (_n in $output) {
        if (_n == n) {
          return ($output[_n]);
        }
      }
    }
  }]);
```

## 创建Angular服务

在Angular中创建自定义服务，只需要先构建一个模块(Module)，然后在构建过程中调用内置的`$provide`服务，通过该服务的工厂函数来创建属于自己的Angular服务。除此之外，还可以调用模块中的`factory`、`service`、`constant`、`value`方法来创建。

### 使用`factory`方法自定义服务

在Angular中，最常用的创建自定义服务的，就是`factory`方法了

```javascript
app.factory(name, fn);
```

html:

```javascript
<div ng-controller="MyController">
  <div>{{str('我是factory返回的内容')}}</div>
  <div>{{name(1)}}</div>
</div>
```

javascript:

```javascript
var myapp = angular.module('MyApp', []);
myapp.factory('outfun', function () {
  return {
    str: function (s) {
      return s;
    }
  }
});
myapp.factory('outarr', function () {
  return ['张三', '李四', '王五'];
});
myapp.controller('MyController', function ($scope, outfun, outarr) {
  $scope.str = function (n) {
    return outfun.str(n);
  }
  $scope.name = function (n) {
    return outarr[n];
  }
});
```

### 使用`service`方法自定义服务

使用`service`方法也可以自定义服务，与`factory`不同的是，它可以接受一个构造函数

```javascript
app.service(name, fn)
```

其中，fn为构造函数，当注入该服务时，通过该函数并使用new关键字来实例化服务对象

html:

```javascript
<div ng-controller="MyController">
  <div class="show">姓名: {{name}}</div>
  <div class="show">邮件: {{email}}</div>
  <div class="show">{{title}}</div>
  <button ng-click="say()">主题</button>
</div>
```

javascript:

```javascript
var myapp = angular.module('MyApp', []);
  myapp.service('student', function () {
    this.name = 'Kaindy',
    this.email = 'kaindy7633@163.com',
    this.say = function () {
      return 'Hello, Angular!';
    }
  });
  myapp.controller('MyController', ['$scope', 'student', function ($scope, student){
    $scope.name = student.name;
    $scope.email = student.email;
    $scope.say = function () {
      $scope.title = student.say();
    }
  }]);
```

### 使用constant和value方法自定义服务

使用`constant`和`value`方法创建服务，常用于返回一个常量。

```javascript
app.constant(name, value)
app.value(name, value)
```

html:

```javascript
<div ng-controller="MyController">
  <div class="show">图书ISBN号: {{BOOK}}</div>
  <div class="show">美元兑换价: {{USD}}</div>
</div>
```

javascript:

```javascript
var myapp = angular.module('MyApp', []);
myapp.constant('$ISBN', {
	BOOK: '9898733238'
});
myapp.value('$RATE', {
	USD: 614.28
});
myapp.controller('MyController', function($scope, $ISBN, $RATE){
	var n = 600;
	angular.extend($RATE, {USD: n});
	$scope.BOOK = $ISBN.BOOK;
	$scope.USD = $RATE.USD;
})
```

## 管理服务的依赖

### 添加自定义服务依赖项方法

我们在自定义服务时，会添加其他各类对象或服务，有下面三种方式：

**(1)** 隐式声明

在参数中直接调用，但这种方式在代码压缩时注入的对象可能会失效

```javascript
app.factory('ServiceName', function(dep1, dep2) {})
```

**(2)** 调用`$inject`属性

将需要注入的服务对象包装成一个数组，作为`$inject`的属性值，但这种方式效率很低

```javascript
var sf = function(dep1, dep2) {};
sf.$inject = ['dep1', 'dep2'];
app.factory('ServieceName', sf);
```

**(3)** 显式声明

在创建服务的函数中，添加一个数组，在数组中按顺序声明需要注入的服务或对象名称，这种方式既高效也不会丢失代码，推荐使用

```javascript
app.factory('ServiceName', ['dep1', 'dep2', function(dep1, dep2) {} ])
```

html:

```javascript
<div ng-controller="MyController">
  <div class="show">你选择的是:{{result}}</div>
  <button ng-click="confirm('你真的要删除这条记录吗?')">删除</button>
</div>
```

javascript:

```javascript
var myapp = angular.module('MyApp', []);

myapp.service('notify', ['$window', function ($win) {
  return function (msg) {
    return $win.confirm(msg) ? '确定' : '取消';
  }
}]);

myapp.controller('MyController', ['$scope', 'notify', function ($scope, notify) {
  $scope.confirm = function (msg) {
    $scope.result = notify(msg);
  }
}]);
```

### 嵌套注入服务

在Angular中，有时需要将一个自定义的服务注入到另一个自定义的服务中，形成嵌套注入的形式，通常只需要将被注入的服务作为内置服务，采用显式声明的方式注入即可

html:

```javascript
<div ng-controller="MyController">
  <button ng-click="ask(false, '你输入的内容不正确')">提示框</button>
  <button ng-click="ask(true, '你真的要删除这条记录吗?')">询问框</button>
</div>
```

javascript:

```javascript
var myapp = angular.module('MyApp', []);
  // 使用factory定义confirm服务
  myapp.factory('confirm', ['$window', function ($win) {
    return function (msg) {
      $win.confirm(msg);
    }
  }]);
  // 将confirm服务显式的注入到notify服务中
  myapp.service('notify', ['$window', 'confirm', function ($win, con) {
    return function (t, msg) {
      return (t) ? con(msg) : $win.alert(msg);
    }
  }]);
  myapp.controller('MyController', ['$scope', 'notify', function ($scope, notify) {
    $scope.ask = function (t, msg) {
      notify(t, msg);
    }
  }])
```

## 添加服务的其他设置

创建好的服务一般比较复杂，如果后期需要修改，往往面临很高的风险，Angular为服务添加了一些设置项，如装饰器(decorator)，可以在不修改原代码的情况下为服务添加其他功能

### 服务的装饰器

装饰器(decorator)是Angular中内置服务`$provide`所特有的一项设置函数，通过它可以拦截服务在实例化时创建的一些功能，并对原有功能进行优化和替代。

```javascript
$provide.decorator('ServiceName', Fn)
```

- `$provide`表示注入后创建的服务对象
- `ServiceName`表示需要拦截的服务名称
- `Fn`表示服务在实例化时调用的函数，该函数在执行时需要添加一个名为`$delegate`的参数,该参数代表服务实例化后的对象，服务的新功能就是通过这个对象进行扩展和优化的

示例代码：

```javascript
<div ng-controller="MyController">
  <div class="show">姓名: {{stu.name}}</div>
  <div class="show">邮件: {{stu.email}}</div>
  <div class="show">主题: {{stu.title}}</div>
</div>
```

```javascript
var myapp = angular.module('MyApp', []);
  // 使用工厂函数factory定义student服务
  myapp.factory('student', function () {
    return {
      name: 'Kaindy',
      email: 'kaindy7633@gmail.com'
    }
  });
  // 使用$provider的装饰器decorator为服务student扩展一个title属性
  myapp.config(function ($provide) {
    $provide.decorator('student', function ($delegate) {
      $delegate.title = 'Hello, Angular!';
      return $delegate;
    })
  });

  myapp.controller('MyController', function ($scope, student) {
    $scope.stu = student;
  });
```

# Angular与服务端交互

在Angular中，封装了诸如`$http`、`$resource`等众多服务模块，供开发者与服务端交互时调用，同时，应用内部的缓存机制可加速交互时的数据通信，高效的处理客户端与服务端的数据交互

## 与服务端交互简介

Angular中的`$http`服务就是将以往的Ajax请求封装成了一个内部的服务模块来供开发者使用。

### 传统的Ajax方式与服务端交互

下面是传统的Ajax请求示例代码：

```javascript
<!doctype html>
<html>
<head>
  <meta charset="UTF-8">
  <title>传统Ajax与服务端交互</title>
  <style>
    .frame {font-size: 12px; width: 320px; float: left}
    ul {list-style-type: none; padding: 0; margin: 0}
    ul li {background-color: #f3f1f1; padding: 8px; float: left; border-bottom: 1px solid #666}
    ul li span {text-align: left; width: 86px; height: 18px; line-height: 18px; float: left}
    .show {width: 260px; padding: 8px; background-color: #eee;}
    .show .tip {font-size: 9px; color: #666; margin: 8px 3px}
  </style>
</head>
<body>
  <div class="frame">
    <ul id="stuInfo">
      <li>正在加载中......</li>
    </ul>
  </div>

  <script>
    (function () {
      var xhr = null;
      if (window.ActiveXObject) {
        xhr = new ActiveXObject("Microsoft.XMLHTTP")
      } else if (window.XMLHttpRequest) {
        xhr = new XMLHttpRequest();
      }

      xhr.onreadystatechange = function () {
        if (xhr.readyState == 4) {
          if (xhr.status === 200) {
            var HTML = '';
            var data = eval("(" + xhr.responseText + ")");
            for (var i=0; i<data.length; i++) {
              HTML += '<li><span>' + data[i].Code + '</span>';
              HTML += '<span>' + data[i].Name + '</span>';
              HTML += '<span>' + data[i].Score + '</span></li>';
            }
            document.getElementById('stuInfo').innerHTML = HTML;
          }
        }
      }
      xhr.open('GET', 'http://localhost/data/stu.php', true);
      xhr.send();
    })();
  </script>
</body>
</html>
```

PHP服务端代码：

```php
<?php
header('Content-type: text/json');
$stulist = array (
  array('Code'=>'10101', 'Name'=>'刘真真', 'Score'=>'530'),
  array('Code'=>'10102', 'Name'=>'张明吉', 'Score'=>'460'),
  array('Code'=>'10103', 'Name'=>'舒虎', 'Score'=>'660'),
  array('Code'=>'10104', 'Name'=>'周晓敏', 'Score'=>'500'),
  array('Code'=>'10105', 'Name'=>'卢明明', 'Score'=>'300'),
  array('Code'=>'10106', 'Name'=>'王小五', 'Score'=>'490')
);

echo json_encode($stulist);
?>
```

### 使用`$http`服务与服务端交互

在Angular中，与后端交互调用`$http`服务模块，它封装了Javascript中的`XMLHttpRequest`对象，接收一个对象作为参数，用于收集生成HTTP请求的配置内容，同时返回一个`promise`对象，该对象可以使用`success`和`error`两个回调方法

通用格式如下：

```javascript
$http.请求类型(url, [data], [config])
     .success (data, status, headers, config) {
       // 成功后的操作
     }     .error (data, status, headers, config) {
       // 错误时的操作
     }
```

- url: 表示一个相对或绝对的服务端请求路径
- 请求类型： 包括POST、GET、JSONP、DELETE、PUT和HEAD
- 回调参数data： 表示返回的数据体
- status：表示返回的状态值
- headers： 表示返回的头函数
- config： 表示发送HTTP请求的完整配置信息，一个对象

示例：

html：

```javascript
<div class="frame">
	<div class="tip">POST返回的结果是：{{result}}</div>
	<button ng-click="onclick()">发送</button>
</div>
```

javascript:

```javascript
var myapp = angular.module('MyApp', []);
	
	// 将客户端数据以POST方式通过$http服务发送到服务端
	// 需要调用config方法，注入$httpProvider服务
	// 并调用该服务对象重置发送数据时默认函数transformRequest和属性Content-Type的值
    myapp.config(function ($httpProvider) {
    	// 通过$httpProvider服务改写transformRequest和headers
      $httpProvider.defaults.transformRequest = function (obj) {
        var arrStr = [];
        for (var p in obj) {
          arrStr.push(encodeURIComponent(p) + '=' + encodeURIComponent(obj[p]));
        }
        return arrStr.join('&');
      }
      $httpProvider.defaults.headers.post = {
        'Content-Type': 'application/x-www-form-urlencoded'
      }
    });

    myapp.controller('MyController', ['$scope', '$http', function ($scope, $http) {
      var postData = {name: 'Kaindy'};
      $scope.onclick = function () {
        $http.post('post.php', postData)
             .success(function (data, status, headers, config) {
               $scope.result = data;
             })
             .error(function (data, status, headers, config) {
               $socpe.result = data;
             })
      }
    }]);
```

### 使用`$http`配置对象方式与服务端交互

上面的方式缺乏灵活性，而且代码量较多，我们可以将`$http`服务模板当成一个函数来使用，将构造XHR对象的所有配置项作为一个对象，并将对象定义为函数的形参，在调用时修改形参对象中的各属性值即可，调用格式如下：

```javascript
// $http中的形参是一个配置对象
$http({
  method:	// 请求方法，可以是PSOT、GET、JSONP、DELETE、PUT和HEAD
  url:		// 向服务器请求的地址
  data:		// 对象，作为消息体的一部分发送给服务端，常用于POST和PUT
  params:	// 字符串或对象，如果是对象将被自动按json格式序列化，并追加到URL后
  transformRequest: // 用于将请求头信息和请求体进行序列化，并生成一个数组发送给服务端
  transformResponse: // 用于将响应头信息和响应体进行反序列化，其实质就是解析服务器发送过来的被序列化后的数据
  cache:  // 如果为true，表示将缓存请求结果，反之则不缓存
  timeout: // 表示延迟发送HTTP请求的时间，单位是毫秒
})
```

示例代码：

html:

```javascript
<input type="text" ng-model="num">
<button ng-click="onclick()">验证奇偶</button>
<div class="tip">您输入的是： {{result}}</div>
```

javascript:

```javascript
var myapp = angular.module('MyApp', []);

    myapp.controller('MyController', ['$scope', '$http', function ($scope, $http) {
      // $scope.num = 0;
      // $scope.result = '偶数';
      $scope.onclick = function () {
        $http({
          method: 'GET',
          url: 'chk.php',
          params: {
            n: $scope.num
          }
        }).success(function (data, status, headers, config) {
          $scope.result = data;
        })
      }
    }]);
```

php：

```php
<?php
  function checkNum ($num) {
    return ($num % 2) ? true : false;
  }

  if (checkNum($_GET['n']) === true) {
    echo '奇数';
  } else {
    echo '偶数';
  }
?>
```

需要注意的是，在Angular中，执行`$http`函数后，它返回的内容其实一个是`promise`对象，可以直接通过链式的写法调用`then`方法获取成功和异常后的数据

```javascript
$http({
	// 配置对象
})
.success(fn1)
.error(fn2)
```

等价于：

```javascript
$http({
	// 配置对象
})
.then(fn1, fn2)
```

上面的fn1和fn2分别表示成功和错误时的返回函数，使用第二种方式获取的是服务端完整的响应对象，而使用`success`和`error`方法只是接收解析并处理后的响应对象

## Angular中的缓存

缓存的功能就是加快获取内容的速度，减少重复请求。因此，在Angular中，提供了专门的服务 - `$cacheFactory`来生成缓存对象，同时，`$http`服务中还可以开启缓存、自定义默认缓存名称

### `$cacheFactory`服务创建缓存对象

使用`$cacheFactoy`服务创建缓存对象，一般都以key/value形式存储，如下：

```javascript
$cacheFactoy(key, [options]);
```

参数key表示缓存对象的名称，可选参数options是一个对象，用于指定缓存的特征。一般情况下，会在这个对象中添加一个`capacity`属性，它是一个数字，用于说明缓存的最大容量，如该值为3，则只能缓存前3次请求。

创建或获取缓存对象后，就可以使用对象本身的方法进行缓存的操作

**(1)** `info`方法

`info`方法返回缓存对象的一些信息，包括大小、名称

```javascript
var cache = $cacheFactory('test');
console.log(cache.info());
```

**(2)** `put`方法

`put`方法向缓存对象中以key/value的形式添加缓存内容，并返回添加后的键值

```javascript
cache.put('c1', 'hello');
console.log(cache.put('c1', 'hello'));
```

**(3)** `get`方法

`get`方法获取键名对应的键值内容

```javascript
console.log(cache.get('c1'));  // hello
console.log(cache.get('c2'));  // undefined
```

**(4)** `remove`方法

`remove`方法可以移除指定键名的缓存

```javascript
cache.remove('c1');
```

**(5)** `removeAll`和`destory`方法

`removeAll`方法用于移除全部的缓存内容，并重置缓存结构，`destory`方法则是从`$cacheFactory`缓存注册表中删除所有的缓存引用条目，并重置缓存对象

示例代码：

```javascript
<div ng-controller="MyCtrl">
  <input type="text" ng-model="cname" size="6">
  <button ng-click="cset()">设置</button>
  <button ng-click="cshow()">显示</button>
  <button ng-click="cdel()">删除</button>
  <div>缓存值是: {{cvalue}}</div>
</div>
```

```javascript
var myapp = angular.module('MyApp', []);

  myapp.service('cache', function ($cacheFactory) {
    return $cacheFactory('test');
  });

  myapp.controller('MyCtrl', ['$scope', 'cache', function ($scope, cache) {
    $scope.cset = function () {
      if (cache.put('mytest', $scope.cname)) {
        alert('set cache success!');
      }
    }
    $scope.cshow = function () {
      var tcache = cache.get('mytest');
      $scope.cvalue = tcache ? tcache : '空值';
    }
    $scope.cdel = function () {
      cache.remove('mytest');
    }
  }])
```

### `$http`服务中的缓存

在Angular中，当调用`$http`方法与服务端进行数据交互时，也能使用缓存，方法是在配置对象中添加一个名为'cache'的属性，并将它的属性值设为true，表示开启请求缓存

示例代码：

```javascript
<div ng-controller="MyCtrl">
  <div>接收的内容是: {{result}}</div>
  <div>缓存的内容是: {{cache}}</div>
</div>
```

```javascript
var myapp = angular.module('MyApp', []);

  myapp.controller('MyCtrl', ['$scope', '$http', '$cacheFactory', function ($scope, $http, $cacheFactory) {
    var url = 'cache.php';
    // 在调用$http方法时，Angular内部自动创建$http缓存对象
    var cache = $cacheFactory.get('$http');
    $http({
      method: 'GET',
      url: url,
      cache: true
    })
    .then(function (data, status, headers, config) {
      $scope.result = data.data;
      var arrResp = cache.get(url);
      $scope.cache = arrResp[0] + ' - ' + arrResp[1];
    })
  }])
```

### 自定义`$http`服务中的缓存

在自定义缓存对象过程中，可以采用传递实例缓存的方法，将定义好的缓存对象添加到$http服务中

示例代码：

```javascript
<div ng-controller="MyCtrl">
  <div>接收内容是: {{result}}</div>
  <button ng-click="refresh()">刷新</button>
</div>
```

```javascript
var myapp =angular.module('MyApp', []);

  // 创建名为cache的服务，并返回一个名为mycache的缓存实例
  myapp.service('cache', ['$cacheFactory', function ($cacheFactory) {
    return $cacheFactory('mycache', {capacity: 3});
  }]);

  myapp.controller('MyCtrl', ['$scope', '$http', 'cache', function ($scope, $http, cache) {
    var url = 'cache.php';
    $http({
      method: 'GET',
      url: url,
      cache: cache	// 这里设置为cache，实现缓存实例的传递
    }).success(function (data, status, headers, config) {
      $scope.result = data;
      cache.put('c', data);
    })
    $scope.refresh = function () {
      var _c = cache.get('c');
      $scope.result = (_c) ? _c + '来源缓存' : '刷新失败!';
    }
  }])
```

## `$resource`服务

`$resource`服务能支持与RESTful的服务器进行无缝隙的数据交互，在调用`$resource`服务后，返回的`$resource`对象包含了多种与服务端进行交互的API，像`get`、`save`和`query`等

### `$resource`服务的使用和对象中的方法

`$resource`服务是一个可选模块，所以它没有被包含在Angular中，所以如果需要使用它，就需要使用`<script>`元素进行文件导入

```javascript
<script src="js/angular-resource.min.js"></script>
```

导入模块后，在应用的模型中通过下面的方式进行注入

```javascript
angular.module('myapp', ['ngResource'])
```

注入之后，就可以在控制器或其他自定义的服务中直接调用`$resource`服务了

```javascript
var obj = $resource(url, [, paramDefaults] [, actions]);
```

`obj`表示请求服务器指定url地址后返回的`$resource`对象，该对象就包含了与服务器进行数据交互的全部API

参数url表示请求服务器的地址，它允许使用占位符变量，该变量以`:`为前缀

```javascript
var obj = $resource('url?action=:act');
obj.$save(act : 'save');
// 在执行save后，实际发送地址就是：url?action=save
```

参数paramDefaults是一个对象，用于设置请求时的默认参数值

```javascript
var obj = $resource('url?action=:act', {
  act: 'save',
  a: '1',
  b: '2'
});
// 实际发送地址为：url?action=save&a=1&b=2
```

另一个可选参数actions也是一个对象，它的功能是扩展默认资源动作，比如可以在该对象中自定义新的方法

```javascript
var obj = $resource('url?action=:act', {
  // 定义请求默认值
}, {
  a: {
    method: 'get'
  }
});
```

然后我们就可以直接调用可选参数actions中自定义的方法a，即`obj.$a()`

调用`$resource`服务所返回的对象中包含5个与服务端交互的API，2个是GET类型，3个是非GET类型

**(1)** `$resource`对象中的GET类型请求

`$resource`对象中的两个GET类型请求分别是`get`和`query`方法

```javascript
var obj = $resource('url');
// get()方法
obj.get(params, successFn, errorFn);
// query()方法
obj.query(params, successFn, errorFn);
```

参数params是一个对象，用于添加随请求一起发送的数据，发生请求时该对象中的键值会被自动序列化并添加到url的后面。

successFn和errorFn分别表示成功和失败后的回调函数

它们的区别是，`get()`方法可以返回单个资源，而`query()`方法必须返回一个数组或集合类的资源

**(2)** `$resource`对象中的非GET类型请求

非GET类型请求有3个，分别是`save`、`delete`和`remove`方法

```javascript
var obj = $resource(url);

// save()方法
obj.save(params, postData, successFn, errorFn);

// delete()方法
obj.delete(params, postData, successFn, errorFn);

// remove()方法
obj.remove(params, postData, successFn, errorFn);
```

非GET类型请求与上面的GET请求类型相比，多了一个postData参数，它的功能是添加以非GET方式向服务端发送的数据体

`save()`方法在服务端保存数据，它将以POST方式向服务端发送请求，postData参数中添加的数据体也将一起被发送

`delte()`和`remove()`方法都是在删除服务端数据时使用，它们将携带postData参数中添加的数据体，以delete方式向服务端发送请求，它们的区别是，`remove`方法可以解决IE浏览器中`delete`是JavaScript保留字而导致的错误

综合示例：

html:

```javascript
<div ng-controller="MyCtrl">
  <ul>
    <li ng-repeat="item in items">
      <span>{{item.Code}}</span>
      <span>{{item.Name}}</span>
      <span>{{item.Sex}}</span>
    </li>
  </ul>
  <div>
    key值: <input type="text" ng-model="key">
    <button ng-click="save()">保存</button>
    <div>{{result}}</div>
  </div>
</div>
```

javascript:

```javascript
var myapp = angular.module('MyApp', ['ngResource']);

  myapp.config(function ($httpProvider) {
    $httpProvider.defaults.transformRequest = function (obj) {
      var arrStr = [];
      for (var p in obj) {
        arrStr.push(encodeURIComponent(p) + '=' + encodeURIComponent(obj[p]));
      }
      return arrStr.join('&');
    }
    $httpProvider.defaults.headers.post = {
      'Content-Type': 'application/x-www-form-urlencoded'
    }
  });

  myapp.controller('MyCtrl', ['$scope', '$resource', function ($scope, $resource) {
    var stus = $resource('info.php');
    stus.query({action: 'search'}, function (resp) {
      $scope.items = resp;
    });
    $scope.save = function () {
      var data = {
        key: $scope.key
      }
      stus.save({action: 'save'}, data, function (resp) {
        $scope.result = (resp[0] == '1') ? '保存成功' : '保存失败';
      })
    }
  }]);
```

PHP:

```php
<?php
header('Content-Type: text/json');

if ($_GET['action'] == 'search') {
  $stulist = array (
    array('Code'=>'1001', 'Name'=>'刘振', 'Sex'=>'男'),
    array('Code'=>'1002', 'Name'=>'李雨', 'Sex'=>'女')
  );
  echo json_encode($stulist);
} elseif ($_GET['action'] == 'save') {
  if ($_POST['key'] == '1010') {
    echo '1';
  } else {
    echo '0';
  }
}
?>
```

### 在`$resource`服务中自定义请求方法

在`$resource`服务中自定义请求方法，只需在调用`$resource`服务的方法中，添加第3个可选项参数actions，在参数对象中，通过key/value的方式自定义`$resource`对象方法。

示例代码：

html:

```javascript
<div ng-controller="MyCtrl">
  <div>{{r0}}</div>
  <div>{{r1}}</div>
  <div>{{r2}}</div>
  <button ng-click="click()">开始</button>
</div>
```

javascript:

```javascript
'use strict';
  var url = 'self.php?action=:act';
  var myapp = angular.module('MyApp', ['ngResource']);

  // 重置transformRequest和Content-Type,以便以POST方式通过$http发送数据
  myapp.config(function ($httpProvider) {
    $httpProvider.defaults.transformRequest = function (obj) {
      var arrStr = [];
      for (var p in obj) {
        arrStr.push(encodeURIComponent(p) + '=' + encodeURIComponent(obj[p]));
      }
      return arrStr.join('&');
    }
    $httpProvider.defaults.headers.post = {
      'Content-Type': 'application/x-www-form-urlencoded'
    }
  });

  // 通过factory工厂函数定义custom服务,返回$resource对象
  // 并在actions参数中自定义方法update
  myapp.factory('custom', ['$resource', function ($resource) {
    return $resource(url,
      {
        act: 'search'
      },
      {
        update: {
          method: 'POST',
          params: {
            update: true
          },
          isArray: false
        }
      });
  }]);

  myapp.controller('MyCtrl', ['$scope', 'custom', function ($scope, custom) {
    $scope.click = function () {
      custom.get({id: '1010'}, function (resp0) {
        $scope.r0 = (resp0[0] == '1') ? '查找成功' : '查找失败';
        resp0.key = '1011';
        resp0.$update({act: 'update'}, function (resp1) {
          $scope.r1 = (resp1[0] == '1') ? '更新成功' : '更新失败';
          resp1.key = '1012';
          resp1.$save({act: 'save'}, function (resp2) {
            $scope.r2 = (resp2[0] == '1') ? '保存成功' : '保存失败';
          })
        });
      });
    }
  }]);
```

PHP:

```php
<?php
if ($_GET['action'] == 'search') {
  if ($_GET['id'] == '1010') {
    echo '1';
  } else {
    echo '0';
  }
} elseif ($_GET['action'] == 'update') {
  if ($_POST['key'] == '1011' && $_GET['update'] == 'true') {
    echo '1';
  } else {
    echo '0';
  }
} elseif ($_GET['action'] == 'save') {
  if ($_POST['key'] == '1012') {
    echo '1';
  } else {
    echo '0';
  }
}
?>
```

## promise对象

在Ajax中，我们会添加回调函数来处理服务端返回的数据，但这种处理方法失去了控制流、异常处理，并会陷入层层的回调嵌套中。

promise是一种处理异步编程的模式，可以有效的解决回调的繁琐，并以一种同步的方式去处理业务流程

我们用一种拟物化的方式来说明pormise

比如有一名A客户，向B公司提出制作网页的需求，B公司答应3天内完成，这个承诺就是一个promise对象

它的本质就是A客户发起的一个延期业务，可以理解为通过`$q`对象调用`defer`方法创建了一个延期对象

在接下来的3天里，A客户与B公司交流开发进度，这可以理解为调用延期对象中的`notify`方法发送消息的过程

如果3天内，B公司正常将网页交付给A客户了，则可以理解为调用延期对象中`resolve`方法的过程

如果无法交付，则可以理解为调用延期对象中`reject`方法的过程

如果B公司将以前做过的一个相同的页面交付给了A客户，A客户也很满意，则可以理解为通过`$q`对象调用`then`方法的过程

总结promise中常用的各种方法：

- `defer()`
- `notify()`
- `resolve()`
- `reject()`
- `then()`

在Angular中创建一个promise对象，必须在模板中先注入`$q`服务，然后调用`defer()`方法创建一个延期对象

```javascript
var myapp = angular.module('MyApp', []);
myapp.controller('MyCtrl', ['$scope', '$q', function($scope, $q) {
  var defer = $q.defer();  // 创建延期对象
}])
```

`defer`是一个延期对象，包括3个方法，分别是`notify()`、`resolve()`和`reject()`，还有一个名为`promise`的属性

一旦创建了promise对象，就可以通过调用`then`方法来执行延期对象不同操作后的回调函数，`then`方法包含与操作相对应的3个回调函数

```javascript
promise.then(successCallback, errorCallback, notifyCallback);
```

`successCallback`表示执行resolve方法时的回调函数  
`errorCallback`表示执行reject方法时的回调函数  
`notifyCallback`表示执行notify方法时的回调函数  

示例代码：

html:

```javascript
<div ng-controller="MyCtrl">
  <div>{{t0}}</div>
  <div>{{t1}}</div>
  <button ng-click="action(true)">解决</button>
  <button ng-click="action(false)">拒绝</button>
</div>
```

```javascript
'use strict';
var myapp = angular.module('MyApp', []);

myapp.controller('MyCtrl', ['$scope', '$q', function ($scope, $q) {
  var defer = $q.defer();    // 定义延期对象
  $scope.action = function (type) {
    defer.notify(0);
    type ? defer.resolve(1) : defer.reject(1);
    // 创建promise对象
    var promise = defer.promise;
    // 调用promise的then方法完成回调处理
    promise.then(function (n) {
      n++;
      $scope.t1 = '已处理完成:' + n;
    }, function (n) {
      n++;
      $scope.t1 = '未完成原因:' + n;
    }, function (n) {
      n++;
      $scope.t0 = '正在处理中:' + n;
    });
  }
}]);
```

### promise对象在$http中的应用

在`$http`请求中使用promise对象，可以减少数据加载时的白框现象或等待加载的时间

示例代码：

html：

```javascript
<div ng-controller="MyCtrl">
  {{result}}
</div>
```

javascript:

```javascript
<script>
  'use strict';
  var myapp = angular.module('MyApp', []);

  myapp.factory('async', function ($q, $http) {
    var defer = $q.defer();
    $http.get('async.php')
    .success(function (data) {
      defer.resolve(data);
    })
    .error(function (reason) {
      defer.reject(reason);
    })
    return defer.promise;
  });

  myapp.controller('MyCtrl', ['$scope', 'async', function ($scope, async) {
    var promise = async;
    promise.then(function (resp) {
      $scope.result = '请求成功:' + resp;
    }, function (n) {
      $scope.result = '请求失败:' + resp;
    })
  }])
</script>
```

# Angular指令

## Angular指令概述

指令是一种执行的信号，一旦发布了这个指令，就要执行某项动作，HTML中的标签都可以理解为指令，但Angular中的指令要复杂很多，不但要创建元素，还要给元素附加某些特定的行为，因此，Angular中的指令是一个在特定DOM元素上执行的函数

### 指令定义的基础

在Angular中，定义指令需要调用`directive`方法，该方法接收两个参数：

```javascript
var app = angular.module('myapp', []);
app.directive(name, fn);
```

在定义的模块上使用`directive`方法创建一个指令，name为指令的名称，fn是一个函数，它将返回一个对象，在这个对象中，定义了这个指令的全部行为

```javascript
<div>
  <ts-hello></ts-hello>
  <div ts-hello></div>
  <div class="ts-hello"></div>
  <div data-ts-hello></div>
</div>
```

```javascript
<script>
  var app = angular.module('myapp', []);
  app.directive('tsHello', function () {
    return {
      restrict: 'EAC',
      template: '<h3>Hello, Angular!</h3>'
    }
  })
</script>
```

### 设置指令对象的基础属性

`replace`：它的属性值是布尔类型，当该属性值为true时，表示用模板中的内容替换指令标记，否则则不替换，直接显示指令标记，默认为false

`templateUrl`：它的属性值是一个URL地址，该地址指向一个模板页面

```javascript
<div>
  <ts-tplfile></ts-tplfile>
  <ts-tplscript></ts-tplscript>
  <ts-tplcache></ts-tplcache>
</div>
```

```javascript
<script>
  var app = angular.module('myapp', []);

  app.run(function ($templateCache) {
    $templateCache.put('cache', '<h3>模板内容来源于缓存</h3>')
  });

  app.directive('tsTplfile', function () {
    return {
      restrict: 'EAC',
      templateUrl: 'tpl.html'
    };
  });

  app.directive('tsTplscript', function () {
    return {
      restrict: 'EAC',
      templateUrl: 'tpl',
      replace: true
    }
  });

  app.directive('tsTplcache', function () {
    return {
      restrict: 'EAC',
      templateUrl: 'cache'
    }
  });
</script>
```

## Angular指令对象的重要属性

### 指令对象中的transclude属性

`transclude`属性的值是布尔值，默认为false，表示不开启，如果设置为true，则开启该属性，当开启后，则可以在模板中通过`ng-transclude`方式替换指令元素中的内容

```javascript
<ts-hello>
  <div>我是自定义指令在HTML里的内容</div>
</ts-hello>
```

```javascript
<script>
  var app = angular.module('MyApp', []);
  app.directive('tsHello', function () {
    return {
      restrict: 'EA',
      template: '<div ng-transclude></div>',
      replace: true,
      transclude: true
    }
  });
</script>
```

### 指令对象中的link属性

指令对象中的`link`属性的值是一个函数，在该函数中可以操控DOM元素对象，包括绑定元素的各类事件，定义事件触发时执行的内容

```javascript
link: function(scope, element, attrs) {
  // ...
}
```

`link`函数包含3个主要的参数：

- `scope`参数表示指令所在的作用域
- `element`参数表示指令中的元素，改元素可以通过Angular内部封装的jqLite框架进行调用
- `attrs`参数表示指令元素的属性集合通过这个参数可以获取元素中的各类属性

```javascript
<script type="text/ng-template" id="tpl">
  <button>点击按钮</button>
</script>

<div>
  <ts-tplscipt></ts-tplscipt>
  <div>{{content}}</div>
</div>
```

```javascript
<script>
  var app = angular.module('myapp', []);
  app.directive('tsTplscipt', function () {
    return {
      restrict: 'EAC',
      templateUrl: 'tpl',
      replace: true,
      link: function (scope, element, attrs) {
        element.bind('click', function () {
          scope.$apply(function () {
            scope.content = '这是点击后显示的内容';
          })
          attrs.$$element[0].disabled = true;
        })
      }
    }
  });
</script>
```

### 指令对象中的compile属性

该属性比起`link`属性使用的很少，该属性返回一个函数或对象。当返回一个函数时，该函数名称为`post`，而返回一个对象时，该对象中则包含两个名为`pre`和`post`方法函数，这两个函数名是系统提供的，不可修改。

```javascript
<div ng-controller="myctrl">
  <ts-a>
    <ts-b>
      {{tip}}
    </ts-b>
  </ts-a>
</div>
```

```javascript
<script>
  var app = angular.module('myapp', []);
  app.controller('myctrl', function ($scope) {
    $scope.tip = '跟踪compile执行过程';
  });

  app.directive('tsA', function () {
    return {
      restrict: 'EAC',
      compile: function (tEle, tAttrs, trans) {
        console.log('正在编译A指令');
        return {
          pre: function (scope, element, attrs) {
            console.log('正在执行A指令中的pre函数');
          },
          post: function (scope, element, attr) {
            console.log('正在执行A指令中的post函数');
          }
        }
      }
    }
  });

  app.directive('tsB', function () {
    return {
      restrict: 'EAC',
      compile: function (tEle, tAttrs, trans) {
        console.log('正在编译B指令');
        return {
          pre: function (scope, element, attrs) {
            console.log('正在执行B指令中pre函数');
          },
          post: function (scope, element, attrs) {
            console.log('正在执行B指令中的post函数');
          }
        }
      }
    }
  });
</script>
```

## Angular指令对象的scope属性

在Angular指令对象中，`scope`属性使用频率很高，它的值包含两种类型，一种是布尔值，另一类是JSON对象

### scope属性是布尔值

使用`scope`属性自定义指令时，默认是布尔类型，初始值为false。在这种情况下，指令中的作用域就是指令元素所在的作用域。我们将指令中的作用域称为子作用域，把指令元素所在作用域称为父作用域，当`scope`为`false`时，子作用域和父作用域完全相同，一方变化，则另一方也会自动发生变化

当`scope`为`true`时，则表示子作用域是独立创建的，父作用域中内容的改变会影响子作用域，但子作用域的内容发生变化，并不会修改父作用域中的内容

```javascript
<script type="text/ng-template" id="tpl">
  <div>{{message}}</div>
  <button ng-transclude></button>
</script>

<div>
  <input type="text" ng-model="message" placeholder="请输入提示内容">
  <ts-message>固定</ts-message>
</div>
```

```javascript
<script>
  var app = angular.module('myapp', []);
  app.directive('tsMessage', function () {
    return {
      restrict: 'EAC',
      templateUrl: 'tpl',
      transclude: true,
      scope: true,
      link: function (scope, element, attrs) {
        element.bind('click', function () {
          scope.$apply(function () {
            scope.message = '这是单击后的值';
          })
        })
      }
    }
  })
</script>
```

第二个例子：

html：

```javascript
<div ng-controller="myCtrl">
  父亲: {{name}}
  <input ng-model="name">
  <div my-directive></div>
</div>
```

```javascript
var app = angular.module('myApp', [])
  app.controller('myCtrl', ['$scope', function ($scope) {
    $scope.name = 'leifeng';
  }]);
  app.directive('myDirective', function () {
    return {
      restrict: 'EA',
      scope: true,	//父作用域发生改变，子作用域会变化，子作用域的变化不会影响父作用域
      template: '<div>儿子: {{name}}<input ng-model="name"></div>'
    }
  });
```

### scope属性是对象

除了将scope属性设置为布尔值之外，还可以设置成一个JSON对象，如果是对象，那么父作用域与子作用域是完全独立的，不存在任何关联

```javascript
app.directive('myDirective', function () {
  return {
    resrict: 'EA',
    scope: {},  //父作用域与子作用域相互不影响，改变任意一方都不会改变另一方
    template: //....
  }
})
```

这时，子作用域中如果需要添加属性，则可以通过`link`函数，在`scope`上添加，如果子作用域需要与调用父作用域的属性和方法，则需要在这个JSON对象中添加绑定策略

在JSON对象中添加的有3种绑定策略，分别是`@`、`=`和`&`

**(1)** `@绑定`

如果父作用域的属性内容修改了，子作用域对应的属性内容也会随之修改，而如果子作用域属性内容修改了，是不会影响父作用域对应的属性内容的。

html:

```javascript
<div ng-controller="myCtrl">
  父亲: {{name}}
  <input ng-model="name">
  <my-directive name="{{name}}"></my-directive>
</div>
```

javascript:

```javascript
<script>
  var app = angular.module('myApp', [])
  app.controller('myCtrl', ['$scope', function ($scope) {

  }]);
  app.directive('myDirective', function () {
    return {
      restrict: 'EA',
      scope: {
        name: '@'  //指令作用域中变量与父作用域中一致，直接使用@绑定
      },
      replace: true,
      template: '<div>儿子: {{name}}<input ng-model="name"></div>'
    }
  });
</script>
```

**(2)** `=绑定`

`=绑定`的功能是创建一个父作用域与子作用域可以同时共享的属性，即父作用域修改了该属性，子作用域也随之改变，反之亦然。

html：

```javascript
<div ng-controller="myCtrl">
  <input type="text" ng-model="color" placeholder="Enter a color">
  {{color}}
  <hello-world color='color'></hello-world>
   <!--注意上面自定义指令里属性的写法-->
</div>
```

javascript:

```javascript
<script>
  var app = angular.module('myApp', []);
  app.controller('myCtrl', ['$scope', function ($scope) {}]);
  app.directive('helloWorld', function () {
    return {
      restrict: 'EA',
      replace: true,
      scope: {
        color: '='
      },
      template: '<div style="background-color:{{color}}">Hello World<input type="text" ng-model="color"></div>'
    }
  });
</script>
```

**(3)** `&绑定`

`&绑定`的功能可以在独立的子作用域中直接调用父作用域的方法，在调用时可以向函数传递参数。

```javascript
<div ng-controller="myCtrl">
  <input type="text" ng-model="name" placeholder="Eneter a color">
  {{name}}
  <hello-world saysomething999="say();" name="kaindy"></hello-world>
</div>
```

javascript:

```javascript
<script>
  var app = angular.module('myApp', []);

  app.controller('myCtrl', ['$scope', function ($scope) {
    $scope.say = function () {
      alert('hello');
    }
    $scope.name = 'leifeng';
  }]);

  app.directive('helloWorld', function () {
    return {
      restrict: 'EA',
      replace: true,
      scope: {
        saysomething: '&saysomething999',
        name: '@'
      },
      template: '<button type="button" ng-bind="name" ng-init="saysomething();"></button>'
    }
  });
</script>
```

## Angular指令对象的require和controller属性

`require`和`controller`两个属性常用于多个自定义指令元素嵌套时，即当一个子元素指令需要与父元素指令通信时，就需要使用这两个属性

### require和controller属性的概念

`require`属性在创建子元素指令时添加，它的属性值用于描述与父元素指令通信时的方式，如`^`符号表示向外层寻找指定名称的指令，`?`符号表示即使没有找到，也不会出现异常

```javascript
require: "^?myDirective"
```

`controller`属性值是一个构造函数，在创建父元素指令时添加，并可以在函数中创建多个属性或方法。在添加后，这些属性和方法都会被实例的对象所继承，而这个实例对象则是子元素指令中`link`函数的第4个参数

也就是说，当在子元素指令中添加了`require`属性，并通过属性值指定父元素指令的名称，那么就可以通过子元素指令中`link`函数的第4个参数来访问父元素指令中`controller`属性添加的方法。

```javascript
controller: function () {
  this.a = function (childDirective) {
    // 方法a的函数体
  }
}
```

- `controller`的属性值对应一个构造函数
- `this`代表父元素指令本身
- `a`表示构造函数中的一个任意的方法
- `childDirective`形参表示子元素指令中的`scope`对象

html:

```javascript
<div>
  <!--父元素指令-->
  <ts-parent>
    <div>{{ptip}}</div>
    <!--子元素指令-->
    <ts-child>
      <div>{{ctip}}</div>
    </ts-child>
    <button ng-click="click()">换位</button>
  </ts-parent>
</div>
```

javascript:

```javascript
<script>
  var app = angular.module('myApp', []);

  app.directive('tsParent', function () {
    return {
      restrict: 'EA',
      controller: function ($scope, $compile, $http) {
        this.addChild = function (c) {
          $scope.ptip = '今天天气不错!';
          $scope.click = function () {
            $scope.tmp = $scope.ptip;
            $scope.ptip = c.ctip;
            c.ctip = $scope.tmp;
          }
        }
      }
    }
  });

  app.directive('tsChild', function () {
    return {
      restrict: 'EA',
      // 与父元素指令tsParent进行通信
      require: '^?tsParent',
      // 第4个参数表示父元素指令本身，可以调用定义在其上的方法
      link: function (scope, element, attrs, ctrl) {
        scope.ctip = '气温正好18摄氏度';
        ctrl.addChild(scope);
      }
    }
  });
</script>
```
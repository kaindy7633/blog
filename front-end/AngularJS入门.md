## 一、AngularJS 是什么？

AngularJS 是由 Misko Hevery 和 Adam Abrons 两个人共同创建的，在 2009 年卖给了 Google，它是一个构建动态 Web 应用的一个 Javascript 框架，目的是为了克服 HTML 在构建 Web 应用程序上的不足而设计的。

## 二、 AngularJS 的四大核心特性

- MVC
- 模块化
- 指令系统
- 双向数据绑定

其中指令系统和双向数据绑定是 AngularJS 特有的，主要区别于其他的前端 MVC 框架，如 BackBone

## 三、AngularJS 四大核心特性解析

### 1、AngularJS 的第一个核心特性：MVC

![](http://static.oschina.net/uploads/space/2016/0321/095401_9pjr_2399867.png)

MVC 是在 1979 年由 Trygve Reenskaug 第一次提出

Model：数据模型层

View：视图层，负责展示，一般我们能在页面上看到的都是

Controller：业务逻辑和控制逻辑

MVC 的好处是职责很清晰，代码模块化，下面我们来看一段代码

```javascript
<!DOCTYPE html>
<html ng-app="MyAngular">
<head>
	<meta charset="UTF-8">
	<title>AngularJS MVC</title>
</head>
<body>
	<div ng-controller="HelloAngular">
		<p>{{greeting.text}}, AngularJS</p>
	</div>
</body>
<script src="js/angular-1.4.6.min.js"></script>
<script>
	angular.module('MyAngular', [])
	.controller('HelloAngular', function($scope){
		$scope.greeting = {
			text: 'Hello'
		}
	})
</script>
</html>
```

从上面代码可以看出，在 html 标签里，使用`ng-app`定义了 AngularJS 的管理边界，也就是说，AngularJS 可以管理整个 html。

在 body 中的 div 里面定义了`ng-controller`，这就是 MVC 中的控制器，也就是 C，而整个 p 标签就是我们的视图层，也就是 V。

在最下面的 script 里，我们首先定义了一个 AngularJS 的模块 MyAngular，然后在这个模块上定了控制器 HelloAngular，里面的`text：'Hello'`，就是我们的 M 层。

### 2、AngularJS 的第二个核心特性：模块化

其实在上面的代码中，我们已经使用了 AngularJS 的模块化，下面我们来用另外一种方式来重写上面的 JS 代码部分

```javascript
var myModule = angular.module("MyAngular", []); //定义模块

myModule.controller("HelloAngular", [
  "$scope", //在模块上定义一个控制器方法helloAngular
  function helloAngular($scope) {
    $scope.greeting = {
      text: "Hello",
    };
  },
]);
```

上面第一排的代码为我们定义了一个模块 myModel，然后我们利用该模块的`controller`方法生成一个控制器。请注意，我们在定义`controller`控制器时，第一个参数是控制器名称，而第二个是在一个方括号里，方括号里的第一个成员是一个变量`$scope`，第二个成员是一个`Function`，这个`Function`的参数也叫`$scope`，也就是说，这里的代码告诉 Angular，请把第一个成员`$scope`注入到下面的方法中，这里也体现了 Angular 的依赖注入特性。

下面我们用一张图来说明下 AngularJS 的模块化

![](http://static.oschina.net/uploads/space/2016/0321/110650_7xid_2399867.png)

在 AngularJS 中，一切都是从模块开始的，创建了模块，我们就可以在这个模块上调用各种方法，如`Filter`、`Directive`、`Controller`等。

### 3、AngularJS 的第三个核心特性：指令系统

首先我们来看下下面的代码

```javascript
<!DOCTYPE html>
<html ng-app="MyModule">
    <head>
        <meta charset="utf-8" />
        <title>AngularJS - 指令系统</title>
    </head>

    <body>
        <hello></hello>
    </body>
    <script src="js/angular-1.4.6.min.js"></script>
    <script>
        var MyModule = angular.module('MyModule', []);
        MyModule.directive('hello', function(){
            return {
                restrict: 'E',
                template: '<div>Hi Everyone!</div>',
                replace: true
            }
        });
    </script>
</html>
```

上面的 HTML 代码中，我们可以看到`<hello></hello>`这样的标签，但是在 HTML 里，没有定义这杨的标签，浏览器引擎是不认识它的，这时，浏览器会忽略掉这个标签，Angular 怎么做呢？在下面的 JS 代码中，Angular 在已定义的模块 MyModule 上，使用了`directive`方法，在这个方法中，第一个参数就定义了 hello 这个标识符，用来说明在 HTML 中，hello 标签的意义，在返回的属性中有一个 template，它的作用就是说明这个标签会显示什么样的内容。

### 4、AngularJS 的第四个核心特性：双向数据绑定

![](http://static.oschina.net/uploads/space/2016/0321/113056_5wY0_2399867.png)

目前大多数的前端框架都是单向数据绑定，如 jQueryUI、Backbone、Flex 等。单向数据绑定是怎么做的呢？一般的做法是我们先生成模板（template），然后从后台获取数据（Model），通过绑定机制，将模板和数据结合起来生成 HTML 标签插入到文档流中（View）。

这样的单向数据绑定有什么问题吗？如果我们的数据有变化，那么按照这种流程，我们不得不重新将模板和新的数据再次生成 HTML 插入到文档流中，也就是需要重构 HMTL 页面。

那么 AngularJS 中的双向数据绑定又是怎么回事呢？

![](http://static.oschina.net/uploads/space/2016/0321/113907_kSP7_2399867.png)

双向数据绑定认为，视图和数据是对应的，借助事件机制，当视图发生变化时，数据模型也会发生相应的变化，而当数据模型发生变化时，视图会自动更新，这种场景应用最典型的就是我们的表单，当用户在表单中完成输入后，数据模型就会立刻拿到用户输入，下面我们用一段代码来说明下

```javascript
<!DOCTYPE html>
<html ng-app>
    <head>
        <meta charset="utf-8">
    </head>
    <body>
        <div>
            <input type="text" ng-model="greeting.text">
            <p>{{greeting.text}}, AngularJS</p>
        </div>
    </body>
    <script src="js/angular-1.4.6.min.js"></script>
</html>
```

当我们在表单中任意输入后，下面的 p 标签会马上显示出用户输入，代码中的双大括号表示一个取值表达式。

> 这是一个学习AngularJS中的一个栗子，todoList，把学习过程记录下来，便于以后练习。

首先，我们来创建html，为了美化我使用了BootStrap，代码如下：

```html
<!DOCTYPE html>
<html lang="zh-CN">
  <head>
    <meta charset="utf-8">
    <title>todoList</title>
    <link rel="stylesheet" href="http://cdn.bootcss.com/bootstrap/3.3.6/css/bootstrap.min.css">
  </head>
  <body style="padding: 10px;">
    <div class="input-group">
      <input type="text" class="form-control">
      <span class="input-group-btn">
        <button class="btn btn-default">提交</button>
      </span>
    </div>
    <h4>任务列表</h4>
    <ul class="list-group">
      <li class="list-group-item">1</li>
      <li class="list-group-item">2</li>
      <li class="list-group-item">3</li>
    </ul>
  </body>
  <script src="http://cdn.bootcss.com/angular.js/1.5.5/angular.min.js"></script>
  <script src="app.js"></script>
</html>
```

为了养成良好的习惯，我吧AngularJS的代码写在app.js文件里

我们先在html里使用`ng-app`来声明AngularJS的管理边界，并指定这个模块的名称todoList

```html
<html lang="zh-CN" ng-app="todoList">
```

app.js:

```javascript
'use strict';

angular.module('todoList', [])     // 使用angular的module方法声明模块todoList
.controller('TaskCtrl', function($scope){    //生成控制器TaskCtrl
  $scope.task = '';            //在$scope上定义变量task
  $scope.tasks = [];           //在$scope上定义空数组变量tasks
})
```

接着，我们在body标签中加入定义的控制器TaskCtrl

```html
<body ng-controller="TaskCtrl">
```

在input标签中使用`ng-model`指令绑定输入，也就是把输入与变量task绑定起来

```html
<input type="text" class="form-control" ng-model="task">
```

现在我们为提交按钮添加一个添加列表事件，在button里使用`ng-click`添加事件

```html
<button class="btn btn-default" ng-click="addItem()">提交</button>
```

在app.js里响应这个事件

```javascript
'use strict';

angular.module('todoList', [])     // 使用angular的module方法声明模块todoList
.controller('TaskCtrl', function($scope){    //生成控制器TaskCtrl
  $scope.task = '';            //在$scope上定义变量task
  $scope.tasks = [];           //在$scope上定义空数组变量tasks
  $scope.addItem = function() {
    $scope.tasks.push($scope.task);  
  }
})
```

最后我们在html里使用指令`ng-repeat`来遍历用户输入，并把他们显示到下面的列表当中

```html
<ul class="list-group">
  <li class="list-group-item" ng-repeat="item in tasks track by $index">
    {{item}}
  </li>
</ul>    
```

`ng-repeat`指令里的内容表示，使用项目下标来遍历并输入列表项

至此我们就完成了一个简单的Angular应用，todoList，但是有两个问题我们来完善下，一是项目列表可以添加一个删除，还有就是那个<h4>任务列表</h4>,可以在没有列表项时将其隐藏

我们先来隐藏这个<h4>任务列表</h4>,有两种方式，分别使用`ng-hide`和`ng-if`都可以实现

```h
<h4 ng-hide="tasks.length==0">任务列表</h4>
// 列表项数组长度为0时，将此标签隐藏
```

```h
<h4 ng-if="tasks.length > 0">任务列表</h4>
// 列表项数组长度大于0时才显示这个标签
```

在实际应用中推荐使用`ng-if`指令，因为这个指令不会在DOM中创建对应的标签，而`ng-hide`不管对应的标签是否隐藏或显示，都会创建。

而另外一个，在列表项中创建一个删除

```h
<ul class="list-group">
  <li class="list-group-item" ng-repeat="item in tasks track by $index">
    {{item}} <a ng-click="tasks.splice($index,1)">删除</a>
  </li>
</ul>
```

这个练习小项目我放在了github上，有兴趣的同学可以fork下。

github： https://github.com/kaindy7633/todoList

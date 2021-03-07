<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

**Table of Contents** _generated with [DocToc](https://github.com/thlorenz/doctoc)_

- [一、认识面向对象](#%E4%B8%80%E8%AE%A4%E8%AF%86%E9%9D%A2%E5%90%91%E5%AF%B9%E8%B1%A1)
- [二、基本面向对象](#%E4%BA%8C%E5%9F%BA%E6%9C%AC%E9%9D%A2%E5%90%91%E5%AF%B9%E8%B1%A1)
- [三、函数构造器对象](#%E4%B8%89%E5%87%BD%E6%95%B0%E6%9E%84%E9%80%A0%E5%99%A8%E5%AF%B9%E8%B1%A1)
- [四、深入 Javascript 面向对象](#%E5%9B%9B%E6%B7%B1%E5%85%A5javascript%E9%9D%A2%E5%90%91%E5%AF%B9%E8%B1%A1)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## 一、认识面向对象

1. 一切事物皆为对象 - JS 中一切东西都为对象
2. 对象具有封装和继承特性
3. 信息隐藏

## 二、基本面向对象

对象的声明，如下代码直接定义一个对象：

```javascript
//定义对象
var Person = {
  name: "LiuZhen", //对象属性
  age: 30, //对象属性
  eat: function () {
    //对象方法
    alert("正在吃...");
  },
};
```

我们可以为对象添加属性：

```javascript
Person.height = 100; //添加身高属性
```

也可以调用对象中的属性：

```javascript
console.log(Person.name); //调用对象属性
```

面向对象编程在小型项目中并没有优势，但随着项目的不断的迭代，越来越大，管理成了很大的问题，这时面向对象的代码构建方式就显现出它的优势。

## 三、函数构造器对象

定义一个空对象：

```javascript
function Person() {}
```

在对象的原型上添加对象属性和方法：

```javascript
Person.prototype = {
  name: "liuzhne",
  age: 30,
  eat: function () {
    alert("我正在吃...");
  },
};
```

接下来，实例化一个对象：

```javascript
var p = new Person();
```

然后我们就可以调用对象的属性和方法了：

```javascript
p.name;
p.age;
p.eat();
```

JS 的 `new` 关键字与 Java、C++里的完全是两回事，不可混淆。

## 四、深入 Javascript 面向对象

Java、C++等纯面向对象语言里有`Class`（类）概念，但在 JS 中没有（最新发布的 ES6 已加入），这里，我们可以使用 `Function` 来模拟类的实现，看下面的代码：

首先，我们创建一个函数（或者可以叫 JS 的类），并为它添加两个属性，name 和 age

```javascript
function People(name, age) {
  this._name = name;
  this._age = age;
}
```

接着，我们在这个函数的原型上添加一个方法：

```javascript
People.prototype.say = function () {
  alert("say something ...");
};
```

面向对象是可以实现继承的，现在我们来实现这个功能，我们在添加一个函数叫 Student

```javascript
function Student() {}
```

实现继承：

```javascript
Student.prototype = new People();
```

实例化一个对象，调用 say 方法：

```javascript
var s = new Student();
s.say();
```

完整代码如下：

```javascript
//定义父类
function People(name, age) {
  this._name = name;
  this._age = age;
}
//为父类添加公用方法
People.prototype.say = function () {
  alert("say something...");
};
//定义子类
function Student(name, age) {
  this._name = name;
  this._age = age;
}
//实现继承
Student.prototype = new People();
//实例化对象
var s = new Student("Liuzhen");
//调用say方法
s.say();
```

下面，我们来来子类添加一个方法，也叫 say

```javascript
//定义父类
function People(name, age) {
  this._name = name;
  this._age = age;
}
//为父类添加公用方法
People.prototype.say = function () {
  alert("say something...");
};
//定义子类
function Student(name, age) {
  this._name = name;
  this._age = age;
}
//实现继承
Student.prototype = new People();

/**********************************
 *    为子类Student添加say方法
 *********************************/
Student.prototype.say = function () {
  alert("我是子类Student里定义的say方法");
};

//实例化对象
var s = new Student("Liuzhen");
//调用say方法
s.say();
```

调用之后发现，我们已复写了父类中的 say 方法，执行的结果是子类中的 say。

那我们如何来调用父类中的 say 方法呢？

我们可以在重写父类 say 方法之前，重新定义一个对象，把 say 方法指定过去，如下代码：

```javascript
//定义父类
function People(name, age) {
  this._name = name;
  this._age = age;
}
//为父类添加公用方法
People.prototype.say = function () {
  alert("say something...");
};
//定义子类
function Student(name, age) {
  this._name = name;
  this._age = age;
}
//实现继承
Student.prototype = new People();

/**********************************
 *    定义一个对象将say方法赋值过去
 *********************************/
var ParentSay = Student.prototype.say;

/**********************************
 *    为子类Student添加say方法
 *********************************/
Student.prototype.say = function () {
  //在子类重写父类方法中测试调用父类的say方法
  ParentSay.call(this);
  alert("我是子类Student里定义的say方法");
};

//实例化对象
var s = new Student("Liuzhen");
//调用say方法
s.say();
```

下面，我们来把两个 Function 封装起来，达到信息隐藏的目的。

```javascript
//定义父类
(function () {
  var n = "Kaindy"; //这里定义的变量n，只能在这个函数中访问
  function People(name, age) {
    this._name = name;
    this._age = age;
  }
  //为父类添加公用方法
  People.prototype.say = function () {
    alert("say something...");
  };
  window.People = People; //把函数赋值给顶级窗口
})();
//定义子类
function Student(name, age) {
  this._name = name;
  this._age = age;
}
//实现继承
Student.prototype = new People();

/**********************************
 *    定义一个对象将say方法赋值过去
 *********************************/
var ParentSay = Student.prototype.say;

/**********************************
 *    为子类Student添加say方法
 *********************************/
Student.prototype.say = function () {
  //在子类重写父类方法中测试调用父类的say方法
  ParentSay.call(this);
  alert("我是子类Student里定义的say方法");
};

//实例化对象
var s = new Student("Liuzhen");
//调用say方法
s.say();
```

---------------------- 豪华滴分割线 ------------------------------------

现在我们来重写下上面的面向对象，采用对象赋值的方法

```javascript
//定义一个父类Function
function Person() {
  //定义一个空对象
  var _this = {};
  //在这里个空对象上定义一个sayHello方法
  _this.sayHello = function () {
    alert("Hello");
  };
  //返回这个对象
  return _this;
}

//定义一个子类Function
function Teacher() {
  //定义一个对象，把父类赋值给此对象
  var _this = Person();
  //返回此对象
  return _this;
}

//实例化
var t = Teacher();
t.sayHello();
```

好了，这种构建方法更简单明了，代码看上去更简洁，下面我们来实现对父类方法的重写

```javascript
//定义一个父类Function
function Person() {
  //定义一个空对象
  var _this = {};
  //在这里个空对象上定义一个sayHello方法
  _this.sayHello = function () {
    alert("Hello");
  };
  //返回这个对象
  return _this;
}

//定义一个子类Function
function Teacher() {
  //定义一个对象，把父类赋值给此对象
  var _this = Person();
  /*****************************************/
  //重写父类的sayHello方法
  _this.sayHello = function () {
    alert("T-Hello");
  };
  /*****************************************/
  //返回此对象
  return _this;
}

//实例化
var t = Teacher();
t.sayHello();
调用父类的sayHello方法;

//定义一个父类Function
function Person() {
  //定义一个空对象
  var _this = {};
  //在这里个空对象上定义一个sayHello方法
  _this.sayHello = function () {
    alert("Hello");
  };
  //返回这个对象
  return _this;
}

//定义一个子类Function
function Teacher() {
  //定义一个对象，把父类赋值给此对象
  var _this = Person();
  /*****************************************/
  //调用父类的sayHello方法
  var ParentSay = _this.sayHello;
  ParentSay.call(_this);
  /*****************************************/

  /*****************************************/
  //重写父类的sayHello方法
  _this.sayHello = function () {
    alert("T-Hello");
  };
  /*****************************************/
  //返回此对象
  return _this;
}

//实例化
var t = Teacher();
t.sayHello();
```

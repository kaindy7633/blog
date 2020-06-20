<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [一、this](#%E4%B8%80this)
- [二、call和apply](#%E4%BA%8Ccall%E5%92%8Capply)
  - [1、改变this指向](#1%E6%94%B9%E5%8F%98this%E6%8C%87%E5%90%91)
  - [2、`Function.prototype.bind`](#2functionprototypebind)
  - [3、借用其他对象的方法](#3%E5%80%9F%E7%94%A8%E5%85%B6%E4%BB%96%E5%AF%B9%E8%B1%A1%E7%9A%84%E6%96%B9%E6%B3%95)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

> `this`、`call` 和 `apply` 在Javascript编程中应用非常广泛，所以，我们必须先了解它们。

## 一、this

Javascript中的 `this` 总是指向一个对象，而它又是基于执行环境动态绑定，而非函数被声明时的环境。以下有4中情况可以用来分析。

当函数作为对象的方法时，`this` 指向该对象，看下面的代码：

```javascript
var obj = {
    a: 1,
    getA: function(){
        alert(this === obj);        //true
        alert(this.a);              //1
    }
};

obj.getA();
```

当作为普通函数调用时，此时的this总是指向全局对象window

```javascript
window.name = 'globalName';

var getName = function(){
    return this.name;
};

console.log(getName());        //globalName
```

下面来一个实际的例子，我们在一个div节点内部，定义一个局部的callback方法，当这个方法被当做普通函数调用时，callback内部的this就指向了window，如下代码：

```html
<html>
    <body>
        <div id="div1">我是一个Div</div>
    </body>
    <script>
    window.id = 'window';
    
    document.getElementById('div1').onclick = function(){
        alert(this.id);            //div1
        var callback = function(){
            alert(this.id);            //window
        }
        callback();
    };
    </script>
</html>
```

我们可以将callback函数分别写成 `alert(this === callback)` 和 `alert(this === window)` 来测试下。

那我们如何来解决这个问题呢，我们可以使用一个变量来保存div节点的引用

```html
<html>
    <body>
        <div id="div1">我是一个Div</div>
    </body>
    <script>
    window.id = 'window';
    
    document.getElementById('div1').onclick = function(){
        var that = this;
        alert(that.id);                //div1
        var callback = function(){
            alert(that.id);            //div1
        }
        callback();
    };
    </script>
</html>
```

在ES5的 `strict` 模式，这种 `this` 不会再指向window，而是 `undefined`

```javascript
function func(){
    "use strict";
    alert(this);            //undefined
}

func();
```

构造器的调用，当我们使用 `new` 运算符调用函数时，总会返回一个对象，那么构造器里的 `this` 就指向这个对象

```javascript
var myClass = function(){
    this.name = 'Kaindy';
};

var obj = new myClass();
alert(obj.name);            //Kaindy
```

`Function.prototype.call` 或 `Function.prototype.apply` 调用，可以动态的改变传入函数的 `this`

```javascript
var obj1 = {
    name: 'Kaindy',
    getName: function(){
        return this.name;
    }
};

var obj2 = {
    name: 'anne';
}

console.log(obj1.getName());                 //Kaindy
console.log(obj1.getName.call(obj2));        //anne
```

OK，我们再来看下下面的例子，丢失的 `this` ：

```javascript
var obj = {
    myName: 'Kaindy',
    getName: function(){
        return this.myName;
    }
};

console.log(obj.getName());            //Kaindy
var getName2 = obj.getName;
console.log(getName2());                //undefined
```

当obj调用其方法getName时，此时的this指向obj对象，所以打印出obj对象的myName属性值，然后当把对象obj的getName方法赋值给对象getName2时，此时是普通函数调用，`this` 就指向了全局 `window` 对象，所以会打印出`undefined`。

## 二、call和apply

下面我们来分析下 `call` 和 `apply`，它们是ES3为 `Function` 的原型定义的两个方法，它们的作用一样，区别只是在传入的参数的不同。

`apply` 接受两个参数，第一个指定函数体内 `this` 对象的指向，第二个是集合，可以是数组也可以是类数组，`apply` 方法把集合中的元素作为参数传递给被调用的函数

```javascript
var func = function(a, b, c){
    alert([a, b, c]);            //[1, 2, 3]
};

func.apply(null, [1, 2, 3]);
```

`call` 传入的参数不是固定的，第一个参数与 `apply` 相同，代表函数体内的 `this` 指向，从第二个参数开始，每个参数被依次传入函数

```javascript
var func = function(a, b, c){
    alert([a, b, c]);            //[1, 2, 3]
};

func.call(null, 1, 2, 3);
```

在Javascript内部，参数是用数组来表示的，所以，`apply` 比` call` 的使用率更高，如果我们明确参数的数量，想一目了然的表达形参与实参的对应关系，那么我们就使用 `call` 。

在使用 `apply` 或者 `call` 时，如果第一个参数使用 `null`，那么函数体内的 `this` 会指向默认的宿主对象，在浏览器中就是window，但在严格模式下，仍然为 `null`。

下面我们来看看apply和call的实际用途

### 1、改变this指向

```javascript
var obj1 = {
    name: 'sven';
};

var obj2 = {
    name: 'anne';
};

window.name = 'window';

var getName = function(){
    alert(this.name);
};

getName();            //window
getName.call(obj1);        //sven
getName.call(obj2);        //anne
```

当执行 `getName.call(obj1)` 的时候，`getName()` 函数体内的 `this` 就指向了 `obj1` 对象

我们再来看一个在实际开发中可能会遇到的例子，如页面中有一个id为div1的区块

```javascript
document.getElementById('div1').onclick = function(){
    alert(this.id);            //此处的this指向document.getElementById('div1')产生对象，输出div1
    var func = function(){
        alert(this.id);        //此处的this就指向全局对象window了，故输出undefined
    };
    func();
}
```

上面的代码中，事件函数有一个内部函数func，调用此函数时，`this` 就指向了 `window`，我们可以用 `call` 来修正它

```javascript
document.getElementById('div1').onclick = function(){
    alert(this.id);            //div1
    var func = function(){
        alert(this.id);        //div1
    };
    func.call(this);
}
```

### 2、`Function.prototype.bind`

大部分浏览器都实现了内置的 `Function.prototype.bind` ，用来指定函数内部的 `this` 指向。（这个内容不知道为什么要写，所以就略掉）

### 3、借用其他对象的方法

借用方法的第一种场景是“借用构造函数”，通过它可以实现一些类似继承的效果

```javascript
var A = function(name){
    this.name = name;
};

var B = function(){
    A.apply(this, arguments);
};

B.prototype.getName = function(){
    return this.name;
};

var b = new B('sven');
console.log(b.getName());        //sven
```

第二种场景是对函数的参数列表 `arguments` 进行一些操作，`arguments` 并非真正的数组，如果我们想往`arguments` 中添加一些元素，就可以借用 `Array.prototype.push` 方法

```javascript
(function(){
    Array.prototpye.push.call(argumets, 3);
    console.log(arguments);        [1,2,3]
})(1, 2);
```
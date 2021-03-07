> ECMAScript6(简称 ES6)，是 JavaScript 的下一代标准，因为 ES6 是在 2015 年发布的，所以又称 ECMAScript2015（ES6 === ECMAScript2015）

目前不是所有的浏览器都完全兼容 ES6,但很多程序猿已经开始使用 ES6 了，所以了解并逐步掌握 ES6，甚至在你的项目中使用 ES6,是非常有必要的，至少也要看得懂小伙伴写的 ES6 代码吧？

在说 ES6 之前，我们先来了解下`Babel`，这是个什么鬼？它是一个广泛使用的 ES6 转码器，可以将我们写的 ES6 代码转换成能在当前所有浏览器中执行的 ES5 代码。你可以在你习惯使用的工具中集成`Babel`，方便它来工作，具体使用请查看`Babel`官网(http://babeljs.io)

下面我们来看下最常用的一些 ES6 特性：

- let,const
- class,extends,super
- arrow functions
- template string
- destructuring
- default
- rest arguments

## let,const

`let`是用来声明变量的，与`var`相似，`const`是定义常量的。我们先来看下面的例子

```javascript
while (true) {
  var name = "obama";
  console.log(name); //obama
  break;
}

console.log(name); //obama
```

在 ES5 中只有全局作用域和函数作用域，没有块级作用域，所以上面的代码中，`while`循环体内的`name`变量覆盖了上面声明的全局`name`变量，最后输出的就是被覆盖的变量值。而`let`为 JavaScript 增加了块级作用域，用它声明的变量只在当前的代码块内有效。

```javascript
let name = "zach";
while (true) {
  let name = "obama";
  console.log(name); //obama
  break;
}

console.log(name); //zach
```

另外一个问题，就是计数循环

```javascript
var a = [];
for (var i = 0; i < 10; i++) {
  a[i] = function () {
    console.log(i);
  };
}
a[6](); //10
```

用`var`定义的 i 值，成了全局变量，会导致最后的 i 值是最后一轮循环完成后的值，而使用`let`就不会有这个问题。

```javascript
var a = [];
for (let i = 0; i < 10; i++) {
  a[i] = function () {
    console.log(i);
  };
}
a[6](); //6
```

下面我们再来看个例子，页面上有 5 个类名相同的元素，我们通过点击这些元素，分别弹出他们在集合中的序号

```javascript
var clickBoxs = documnet.querySelectorAll("clickBox");
for (var i = 0; i < clickBoxs.length; i++) {
  clickBoxs[i].onclick = function () {
    alert(i);
  };
}
```

很不幸，每次弹出的都是 5.for 循环中用 var 定义的 i，已经是全局变量，在执行弹出时，实际上 i 已经累加到了 5，如果我们将`var`换成`let`，就可以在每次点击的时候得到我们想要的结果。

再来想想如何使用闭包来解决这个问题呢？

```javascript
function iteratorFactory(i) {
  var onclick = function (e) {
    alert(i);
  };
  return onclick;
}

var clickBoxs = document.querySelectorAll("clickBox");
for (var i = 0; i < clickBoxs.length; i++) {
  clickBoxs[i].onclick = iteratorFactory(i);
}
```

`const`用来声明常量，一旦声明，常量的值是不能被改变的。

```javascript
const PI = Math.PI;
```

## class,extends,super

这三个特性让我们从 JavaScript 的原型面向对象中解脱出来，它们让 JavaScript 具有了像传统高级编程语言那样的写法。

```javascript
class Animal {
  constructor() {
    this.type = "animal";
  }

  says(message) {
    console.log(this.type + " says " + message);
  }
}

let animal = new Animal();
animal.says("hello"); //animal says hello

class Cat extends Animal {
  constructor() {
    super();
    this.type = "cat";
  }
}

let cat = new Cat();
cat.says("hello"); //cat says hello
```

上面的代码首先定义了一个`class`，里面有个`constructor`，这是构造函数，`this`关键字指向当前类的实例对象。 `class`之间可以通过`extends`关键字实现继承，上面的代码中，Cat 类通过`extends`继承了 Animal 类的所有属性和方法。 在子类中的`constructor`中，必须调用`super`方法，这是为了继承父类中的`this`。

## arrow function

箭头函数，这是 ES6 最常用的特性，用它来写`function`比 ES5 的更加简介和清晰。

```javascript
function(i){return i + 1;}        //ES5
(i) => i + 1;                    //ES6
```

如果有多行代码或代码比较复杂的，需要使用{}把代码包裹起来

```javascript
function (x, y) {
    x++;
    y--;
    return x + y;
}

(x, y) => {x++; y--; return x + y;}
```

箭头函数除了在写法上更加简洁之外，还有一个功能，更加明确了`this`的指向

```javascript
class Animal {
  constructor() {
    this.type = "animal";
  }

  says(message) {
    setTimeout(function () {
      console.log(this.type + " says " + message);
    }, 1000);
  }
}

var animal = new Animal();
animal.says("hi"); //undefined says hi
```

上面的例子运行后，得到的结果是`undefined says hi`，跟我们预想的不一样，是因为在`setTimeout`中，`this`已经指向了全局。现在，我们有两个传统的方法来解决

第一种，将`this`传递给`self`，也就是将`this`对象缓存起来

```javascript
says (message) {
    var self = this;
    setTimeout(function () {
        console.log(self.type + ' says ' + message);
    }, 1000);
}
```

第二种，使用`bind(this)`

```javascript
says (message) {
    setTimeout(function () {
        console.log(this.type + ' says ' + message);
    }.bind(this), 1000);
}
```

OK,现在我们有了箭头函数，就不用这么麻烦了。

```javascript
class Animal {
  constructor() {
    this.type = "animal";
  }

  says(message) {
    setTimeout(() => {
      console.log(this.type + " says " + message);
    }, 1000);
  }
}

var animal = new Animal();
animal.says("hi"); //animal says hi
```

使用箭头函数时，函数体内的`this`就是定义时所在的对象，而不是使用时的对象。

## template string

这玩意叫模板变量，它有什么用呢？ 当我们需要在 JS 中插入大量的 html 内容时，传统的写法很麻烦，所以我们经常会引入一些模板工具库，我们先来看下下面的代码

```javascript
$("#result").append(
  "There are <b>" +
    basket.count +
    "</b>" +
    "items in your basket, " +
    "<em>" +
    basket.onSale +
    "</em> are on sale!"
);
```

我们需要用一大堆的‘+’来链接文本和变量，而有了 ES6 的模板变量后，我们可以这样写

```javascript
$("#result").append(`
    There are <b>${basket.count}</b> items
    in your basket, <em>${basket.onSale}</em>
    are on sale!
`);
```

我们用反引号" ` "来标示起始和结束，用" ${} "来引用变量，而且所有的空格和缩进都会被保留。

## destructuring

ES6 允许按照一定的模式，从数组和对象中取值，对变量进行赋值，这被称为解构(Destructuring)。

```javascript
let cat = "ken";
let dog = "lili";
let zoo = { cat: cat, dog: dog };
console.log(zoo); //Object {cat: "ken", dog: "lili"}
```

在 ES6 中，我们可以这样写

```javascript
let cat = "ken";
let dog = "lili";
let zoo = { cat, dog };
console.log(zoo); //Object {cat: "ken", dog: "lili"}
```

反过来可以这么写

```javascript
let dog = { type: "animal", many: 2 };
let { type, many } = dog;
console.log(type, many); //animal 2
```

## default, rest

default 就是默认值的意思，如果在调用函数时候没有传参数,传统做法是加上这么一句，`type = type || 'cat'` 来指定默认值

```javascript
function animal(type) {
  type = type || "cat";
  console.log(type);
}

animal(); //cat
```

如果用 ES6，就可以这样写

```javascript
function animal(type = "cat") {
  console.log(type);
}

animal();
```

`rest`的语法也很简单，看例子

```javascript
function animals(...types) {
  console.log(types);
}

animals("cat", "dog", "fish"); //['cat', 'dog', 'fish']
```

如果不适用 ES6 的语法，那么我们必须使用 ES5 的`arguments`

以上就是 ES6 中最常用的语法，可以说这 20%的语法在使用中占了 80%的使用率。

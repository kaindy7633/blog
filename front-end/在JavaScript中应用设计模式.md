<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [在JavaScript中应用设计模式](#%E5%9C%A8javascript%E4%B8%AD%E5%BA%94%E7%94%A8%E8%AE%BE%E8%AE%A1%E6%A8%A1%E5%BC%8F)
  - [JavaScript中的面向对象编程](#javascript%E4%B8%AD%E7%9A%84%E9%9D%A2%E5%90%91%E5%AF%B9%E8%B1%A1%E7%BC%96%E7%A8%8B)
    - [概念](#%E6%A6%82%E5%BF%B5)
    - [封装、继承和多态](#%E5%B0%81%E8%A3%85%E7%BB%A7%E6%89%BF%E5%92%8C%E5%A4%9A%E6%80%81)
  - [UML类图](#uml%E7%B1%BB%E5%9B%BE)
  - [SOLID设计原则](#solid%E8%AE%BE%E8%AE%A1%E5%8E%9F%E5%88%99)
    - [设计准则](#%E8%AE%BE%E8%AE%A1%E5%87%86%E5%88%99)
    - [SOLID](#solid)
  - [JavaScript中常用的设计模式](#javascript%E4%B8%AD%E5%B8%B8%E7%94%A8%E7%9A%84%E8%AE%BE%E8%AE%A1%E6%A8%A1%E5%BC%8F)
    - [工厂模式](#%E5%B7%A5%E5%8E%82%E6%A8%A1%E5%BC%8F)
    - [单例模式](#%E5%8D%95%E4%BE%8B%E6%A8%A1%E5%BC%8F)
    - [适配器模式](#%E9%80%82%E9%85%8D%E5%99%A8%E6%A8%A1%E5%BC%8F)
    - [装饰器模式](#%E8%A3%85%E9%A5%B0%E5%99%A8%E6%A8%A1%E5%BC%8F)
    - [代理模式](#%E4%BB%A3%E7%90%86%E6%A8%A1%E5%BC%8F)
    - [外观模式](#%E5%A4%96%E8%A7%82%E6%A8%A1%E5%BC%8F)
    - [观察者模式](#%E8%A7%82%E5%AF%9F%E8%80%85%E6%A8%A1%E5%BC%8F)
    - [迭代器模式](#%E8%BF%AD%E4%BB%A3%E5%99%A8%E6%A8%A1%E5%BC%8F)
    - [状态模式](#%E7%8A%B6%E6%80%81%E6%A8%A1%E5%BC%8F)
  - [其他不常用设计模式](#%E5%85%B6%E4%BB%96%E4%B8%8D%E5%B8%B8%E7%94%A8%E8%AE%BE%E8%AE%A1%E6%A8%A1%E5%BC%8F)
    - [原型模式](#%E5%8E%9F%E5%9E%8B%E6%A8%A1%E5%BC%8F)
    - [桥接模式](#%E6%A1%A5%E6%8E%A5%E6%A8%A1%E5%BC%8F)
    - [组合模式](#%E7%BB%84%E5%90%88%E6%A8%A1%E5%BC%8F)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# 在JavaScript中应用设计模式

> 作为开发多年，一直在业务中不停的撸码，当你想到要提升时，设计模式必然是绕不过去的坎，我也一样，所以这里把JavaScript相关的设计模式知识整理一下，写成这篇Blog

## JavaScript中的面向对象编程

### 概念

说到面向对象，大多数前端工程师都知道，JavaScript不像Java、C#等高级语言有 `class` ，而最新的ES6标准，将JavaScript中的构造函数封装成了 `class`，但实际上，在JavaScript中， `class` 还是构造函数，它只是一个语法糖而已。

类（`class`）的概念，就是一个模板，由这个模板来生成各种对象。但JavaScript在设计之初，就没有类的概念，而是直接由对象生成对象，这一点是说的通的，而且这样的概念理解起来，比类更加简单明了。但在ES6之前，构造函数形式的面向对象过于复杂，ES6增加了"类"的概念，也是为了前端工程师更容易理解和使用面向对象。（后面的示例都会采用ES6的 `class` 来演示各种设计模式）

我们先来看下面的示例：

```js
// 类（构造函数）,它就是一个模板
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  eat() {
    console.log(`${this.name} eat something`);
  }

  speak() {
    console.log(`My name is ${this.name}, age ${this.age}`);
  }
}

// 实例化成对象
let kaindy = new Person('kaindy', 42);
kaindy.eat();
kaindy.speak();
```

### 封装、继承和多态

面向对象的三要素，封装、继承和多态是程序员都耳熟能详的概念了，但在JavaScript中，其实应用的并不是很广泛，特别是在函数式编程逐渐被广大工程师接受的情况下。

在JavaScript中，继承是使用的最多的特性，但由于JavaScript并没有提供一些特性来限制访问属性和方法，所以封装其实并不容易做到，多态在JavaScript中是天生存在的，同一方法根据传入参数的不同，会返回不同的结果。

```js
// 子类继承父类,我们可以创建一个Student类来继承上面的Person类
class Student extends Person {
  constructor(name, age, number) {
    super(name, age);  // 子类中必须使用super关键字来执行父类的构造函数
    this.number = number;  // 子类中特有的属性，学生的学号
  }

  study() {
    console.log(`${this.name} study, he's number is ${this.number}`);
  }
}

// 子类实例化
let xiaoming = new Student('xiaoming', 10, 'A123');
xiaoming.eat();
xiaoming.speak();
xiaoming.study();
```

封装在JavaScript中无法直接实现，在其他高级语言中，提供了 `public`、`protected` 和 `private` 关键字来限制属性和方法的访问，但在JavaScript中没有，所以无法使用代码来演示，但在我的实际工作中，已经开始使用 `TypeScript` 来写代码，在这个JavaScript的超集语言中，就提供了上述3个关键字来限制对属性和方法的访问，同时也避免了多种情况下的Bug的产生。

由于 `TypeScript` 是在编译阶段进行语法检查，且最后仍然是编译成JavaScript，所以从本质上说，JavaScript是没有封装的能力的。

至于多态，在Java等高级语言中，由于有接口、重写、重载等内置功能，所以多态在这些语言中表现比较多，应用场景也很多，在JavaScript中，我们只能去模拟，看下面的代码：

```js
class Person {
  construcotr(name) {
    this.name = name;
  }

  saySomething() {}
}

// A类继承Person类，并重写saySomething方法
class A extends Person {
  constructor(name) {
    super(name);
  }

  saySomething() {
    console.log(`I am A`);
  }
}

// B类同样继承Person类，也重写saySomething方法，但输出却与A类不同
class B extends Person {
  constructor(name) {
    super(name);
  }

  saySomething() {
    console.log(`I am B`);
  }
}
```

多态保持了子类的开发性和灵活性，将公共的部分定义在父类中，不同的部分由子类去实现或重写。

## UML类图

`UML` 类图是一种在设计阶段使用的对程序结构进行梳理的图形，它的全称是： `Unified Modeling Language`，即统一建模语言。

在设计模式中，`UML` 类图主要解决类的泛化和关联，所谓泛化即类之间的继承关系，而关联则是类之间的组合。

在做 `UML` 类图之前，必须要确定使用哪种工具，目前有两种，`MS Office Visio` 和 `processon`，我们这里就使用后者，它是一个站点，直接进入 `https://www.processon.com` 即可使用。

<img src="../../images/20190106163651.png" width="500px" />

## SOLID设计原则

### 设计准则

对设计我们有一套描述：

- 设计及按照一种思路或标准来实现功能
- 功能相同，可以有不同的设计方案来实现
- 伴随着需求的增加或修改，设计的作用才能体现出来

对于设计，业界也有一套准则可以被参考：

- 准则1：小即是美
- 准则2：让每个程序只做好一件事
- 准则3：快速建立原型
- 准则4：舍弃高效率而取可移植性
- 准则5：采用纯文本来存储数据
- 准则6：充分利用软件的杠杆效应（复用）
- 准则7：利用 `shell` 脚本来提高杠杆效应和可移植性
- 准则8：避免强制性的用户界面
- 准则9：让每个程序都成为过滤器

### SOLID

`SOLID` 是五大原则的单词首写字母，它们分别表示：

- `S` - 单一职责原则：一个模块只干一件事，功能完全分离开来
- `O` - 开放封闭原则：对扩展开发，对修改封闭
- `L` - 李氏置换原则：父类能出现的地方，子类都能出现
- `I` - 接口独立原则：接口与业务完全分离
- `D` - 依赖倒置原则：依赖接口和抽象，不依赖具体的实现

## JavaScript中常用的设计模式

设计模式一共被分为23种，按照功能分类，它们分为：创建型、组合型和行为型

### 工厂模式

工厂模式实际上是要对 `new` 的操作进行一个单独的封装。当遇到 `new` 操作时，就要考虑是否需要使用工厂模式。比如我们去肯德基吃汉堡，我们只需要去点一个汉堡，就坐等服务员送餐就可以了，客户无需关心汉堡的制作过程。

下面是工厂模式的 `UML` 类图

<img src="../../images/20190106202636.png" width="500px" />

下面是代码示例：

```js
// Product类，表示产品
class Product {
  constructor(name) {
    this.name = name;
  }

  init() {
    console.log(`init`);
  }

  fun1() {
    console.log(`fun1...`);
  }

  fun2() {
    console.log(`fun2...`);
  }
}

// 工厂类
class Creator {
  create(name) {
    return new Product(name);
  }
}

// 测试
let creator = new Creator();
let p = creator.create('p1');
p.init();
p.fun1();
```

工厂模式将构造函数和创建者（工厂类）分离开来，符合开放封闭原则。

### 单例模式

单例模式很好理解，就是一个类只有一个实例被初始化。比如在实际应用中，像登录框、购物车等都是单例模式的体现。但在JavaScript中实现单例有点问题，那就是我们无法去限制变量的访问机制，下面来看看Java代码是如何实现的：

```java
public class SingleObject {
  // 私有化的构造函数，外部无法访问
  private SingleObject(){
  }

  private SingleObject instance = null;
  // 获取对象的唯一接口
  public SingleObject getInstance() {
    if (instance == null) {
      instance = new SingleObject();  // 只会实例化一次
    }
    return instance;
  }

  // 对象方法
  public void login(username, password) {
    System.out.println('login...');
  }
}
```

上面的Java很清楚了，`private` 关键字限制了类的访问，所以在外部无法直接实例化，只能在内部实现，而内部只会返回一个实例。这样就达到了单例的效果。

而在JavaScript中却很难做到这点，因为JavaScript没有像 `private` 这样的关键字来实现对属性的访问限制。

```js
// 在JavaScript中实现单例模式
class SingleObject {
  login() {
    console.log(`Login...`);
  }
}

// 创建类SingleObject的静态方法
SingleObject.getInstance = (function() {
  let instance;
  return function() {
    if (!instance) {
      instance = new SingleObject();
    }
    return instance;
  }
})();
```

在JavaScript中实现单例，只是添加了一个静态方法，用于生成实例，这里，我们并不能限制使用者去 `new` 这个单例类，只能通过说明告诉使用者，直接调用 `getInstance` 方法来达到单例模式的效果。

### 适配器模式

所谓适配器模式，就是旧的接口已经不能满足需求，不能和现有的业务对接，这时需要在中间加一个适配器来转换这个接口。

`UML` 类图如下：

<img src="../../images/20190107213319.png" width="500px" />

下面是代码演示：

```js
// 原有接口
class Adaptee {
  specificRequest() {
    return `德国标准插头`;
  }
}

// 适配器
class Target {
  constructor() {
    this.adaptee = new Adaptee();
  }

  request() {
    let info = this.adaptee.specificRequest();
    return `${info} -> 转换器 -> 中国标准插头`;
  }
}

// 测试
let target = new Target();
target.request();
```

### 装饰器模式

装饰器模式表示在不改变对象原有的结构和功能的前提下，为该对象添加新功能。

<img src="../../images/20190108201649.png" width="500px" />

实现代码如下：

```js
// 待装饰的类，方法 draw 的作用是画一个圆形
class Circle {
  draw() {
    console.log(`画一个圆形`);
  }
}

// 装饰器
class Decorator {
  constructor(circle) {
    this.circle = circle;
  }

  draw() {
    this.circle.draw();
    this.setRedBorder(circle);
  }

  setRedBorder(circle) {
    console.log(`设置红色边框`);
  }
}

// 测试
let circle = new Circle();
let dec = new Decorator(circle);
dec.draw();
```

ES7已提供了装饰器功能，但目前的浏览器支持不是很好，需要 `babel-plugin-transform-decorators-legacy` 插件来对代码进行转换。安装之后就可以使用 `@` 语法来使用装饰器功能，装饰器功能可以对类和函数进行装饰。

下面我们先来看一个简单的示例：

```js
// 先定义装饰器, 它实际上就是一个函数
function testDec(target) {
  target.isDec = true;
}

// 通过 @ 语法对类使用装饰器
@testDec
class Demo {
  // ...
}

// 测试一下
console.log(Demo.isDec);  // true
```

上面的代码中，类 `Demo` 什么属性和方法都没有, 但通过装饰器，我们给该类加入了属性 `isDec` ，所以下面可以直接调用这个类的类属性 `isDec`。

我们还可以给装饰器加入参数，还是上面的例子：

```js
// 定义装饰器，加入参数
// 装饰器永远都会返回一个函数
function testDec(isDec) {
  return function(target) {
    target.isDec = isDec;
  }
}

// 装饰类，加入参数
@testDec(false)
class Demo {
  // ...
}

// 测试
console.log(Demo.isDec);    // false
```

下面来看一个 `mixins` 装饰器的示例

```js
// 定义装饰器 mixins
function mixins(...list) {
  return function(target) {
    Object.assign(target.prototype, ...list);
  }
}

// 定义参数对象
const Foo = {
  foo() { console.log(`foo...`); }
}

// 装饰类 MyClass
@mixins(Foo)
class MyClass {}

// 测试
let obj = new MyClass();
obj.foo();    // foo...
```

上面说过，装饰器可以装饰类和方法，下面我们来看一个装饰方法的例子：

```js
// 装饰器 readonly ,将对象属性转换为不可更改
function readonly(target, name, descriptor) {
  // descriptor 属性描述对象
  // {
  //   value: specifiedFunciton,
  //   enumerable: false,
  //   configurable: true,
  //   wriable: true
  // }
  // 将是否可写属性修改为 false
  descriptor.writable = false;
  return descriptor;
}

// 应用
class Person {
  constructor() {
    this.first = 'A';
    this.last = 'B';
  }

  // 装饰方法
  @readonly
  name() {
    return `${this.first} ${this.last}`;
  }
}

let p = new Person();
p.name();   // 执行方法，正常
p.name = function() {};   // 报错
```

下面是一个打印日志的装饰器

```js
// 装饰器 log
function log(target, name, descriptor) {
  // 这个 value 值实际上就是要装饰的方法
  let oldValue = descriptor.value;

  descriptor.value = function() {
    // 打印日志
    console.log(`Calling ${name} with`, arguments);
    return oldValue.apply(this, arguments);
  };

  return descriptor;
}

// 应用
class Math {
  // 装饰方法
  @log
  add(a, b) {
    return a + b;
  }
}
```

其实在网上已有一些优秀的开源的装饰器库供我们使用，`core-decorator` 就是一种，它提供常用的装饰器，比如上面的 `log`

### 代理模式

代理模式，看名字就知道它是干什么的。当使用者无权访问目标对象时，可以在中间加入代理，通过代理做授权和控制。

`UML` 类图如下：

<img src="../../images/20190109203200.png" width="500px" />

下面是代码实现：

```js
// 需要访问的类
class RealImg {
  constructor(fileName) {
    this.fileName = fileName;
    this.loadFromDisk();    // 模拟初始化时从本地加载
  }

  loadFromDisk() {
    console.log(`loading... ${this.fileName}`);
  }

  display() {
    console.log(`display... ${this.fileName}`);
  }
}

// 代理类，用于外部访问类RealImg
class ProxyImg {
  constructor(fileName) {
    this.realImg = new RealImg(fileName);
  }

  // 同样的display方法，暴露给外部访问的api，直接调用原生类的display方法
  display() {
    this.realImg.display();
  }
}

// 测试
let proxyImg = new ProxyImg('1.png');
proxyImg.display();
```

代理模式最常见的场景就是DOM的事件代理，当我们有多个相同DOM都需要绑定监听事件时，利用冒泡原理，就可以给它们的父元素绑定事件回调。

```js
let div = document.getElementById('div');
div.addEventListener('click', function(e) {
  let target = e.target;
  if (target.nodeName === 'A') {
    console.log(target.innerHTML);
  }
});
```

除此之外，ES6中新增的 `proxy` 特性，也是一种代理模式，我们可以想象一个实际场景，一个明星，如果我们先找他来代言，其实我们是跟明星的经纪人来谈代言细节的，而不是直接跟明星进行接触，下面我们可以使用ES6的 `proxy` 来模拟这个场景。

```js
// 明星
let star = {
  name: '张xx',
  age: 25,
  phone: '13910107328'
}

// 经纪人
let agent = new Proxy(star, {
  get: function(target, key) {
    if (key === 'phone') {
      // 如果请求电话，返回的是经纪人的电话，而非明星的
      return `18611112222`;
    }

    // 如果是要获取明星的代言价格
    if (key === 'price') {
      return 120000;
    }
    return target[key];
  },

  set: function(target, key, val) {
    // 商议代言价格
    if (key === 'customPrice') {
      if (val < 100000) {
        throw new Error('价格太低');
      } else {
        target[key] = val;
        return true;
      }
    }
  }
})
```

### 外观模式

外观模式比较好理解，实际上它为子系统的一组接口提供了一个高层接口，使用者使用这个高层接口。下面这张图可以很直观的体现外观模式：

<img src="../../images/20190114210940.png" width="500px" />

下面我们来看看它的 `UML` 类图：

<img src="../../images/20190114211214.png" width="500px" />

```js
// 外观模式函数，兼容传递4个参数和3个参数的情况
function bindEvent(elem, type, selector, fn) {
  if (fn ==- null) {
    fn = selector;
    selector = null;
  }

  // 其他代码...
}

// 调用
// 无论是不是传递了节点id参数，都可以使用这个函数
// 而无需为两种情况分别书写不同的函数
bindEvent(elem, 'click', '#div', fn);
bindEvent(elem, 'click', fn);
```

### 观察者模式

观察者模式在前端开发中使用的场景是最多的。它有两个核心：

- 发布 & 订阅
- 一对多

在实际生活中，其实有很多发布&订阅的例子，比如我们订了牛奶，那么牛奶商每天会把牛奶送到家门口的牛奶箱里，而无需我们自己去牛奶商那里拿。

再比如去咖啡店喝咖啡，订了咖啡之后，我们只需要在座位上等，咖啡好了，店员会送到我们的座位上。

一对多的意思很简单，就是我们既可以订牛奶，也可以订报纸等等，但这个一对多也包含一对一，也就是一个订阅者可以订阅多个事件发生，也可以只订阅一个事件发生。

<img src="../../images/20190114212847.png" width="500px" />

下面来看下实现代码：

```js
// 主题，保存状态
// 状态变化后出发所有观察者对象
class Subject {
  constructor() {
    this.state = 0;
    this.observers = [];    // 观察者列表
  }

  getState() {
    return this.state;
  }

  setState(state) {
    this.state = state;
    this.notifyAllObservers();    // 触发所有观察者
  }

  notifyAllObservers() {
    this.observers.forEach(observer => {
      observer.update();
    })
  }

  // 支持多个观察者
  attach(observer) {
    this.observers.push(observer);
  }
}

// 观察者
class Observer {
  constructor(name, subject) {
    this.name = name;
    this.subject = subject;
    this.subject.attach(this);
  }

  update() {
    console.log(`${this.name} update, state: ${this.subject.state}`);
  }
}

// 测试
let s = new Subject();
let o1 = new Observer('o1', s);

s.setState(1);
```

在实际应用场景中，所有的页面元素绑定事件都是观察者模式的实现。

```js
var btn = document.getElementById('div');
btn.addEventListener('click', function() {
  // 执行...
})
```

在ES6中的 `Promise` 也是一种观察者模式

```js
function loadImg(src) {
  let promise = new Promise(function(resolve, reject) {
    let img = document.createElement('img');
    img.onload = function() {
      resolve(img);
    }
    img.onerror = function() {
      reject('图片加载失败');
    }
    img.src = src;
  });
  return promise;
}

let result = loadImg('../../tupian.png');

// 调用then方法，实际就是Promise中观察者的表现
result.then(function(img) {
  // ....
})
.then(function(img) {
  // ....
})
```

在 `Nodejs` 中，也会有观察者模式

```js
const EventEmitter = require('events').EventEmitter;

const emitter1 = new EventEmitter();

// 监听some事件
emitter1.on('some', () => {
  // ...
})

// 触发some事件
emitter1.emit('some');
```

### 迭代器模式

迭代器模式，可以顺序访问一个集合，且使用者无需知道集合的内部结构。

```js
// 下面是三种使用迭代器模式的场景
var arr = [1, 2, 3];  // 普通数组
var nodeList = document.getElementsByTagName('a');    // 页面DOM集合
var $a = $('a');   // jQuery中的集合,对象

// 遍历数组，这个可直接使用forEach函数
arr.forEach(function(item) {
  console.log(item);
})

// 遍历nodeList，它不是一个数组，无法使用数组的函数方法进行遍历
var i, length = nodeList.length;
for (i = 0; i < lenght; i++) {
  console.log(nodeList[i]);
}

// 遍历jQuery对象
$a.each(function(key, elem) {
  console.log(key, elem);
})
```

实际上，迭代器模式要实现的就是使用一种方式来遍历上述甚至更多类型结构的集合的一种方法。

下面来看下迭代器模式的实现，先上 `UML` 类图

<img src="../../images/20190115211913.png" width="500px" />

下面是实现代码：

```js
// 迭代器
class Iterator {
  constructor(container) {
    this.list = container.list;
    this.index = 0;
  }

  next() {
    if (this.hasNext()) {
      return this.list[this.index++];
    }
    return null;
  }

  hasNext() {
    if (this.index >= this.list.length) {
      return false;
    }
    return true;
  }
}

class Container {
  constructor(list) {
    this.list = list;
  }

  // 生成遍历器
  getIterator() {
    return new Iterator(this);
  }
}

// 测试
let arr = [1, 2, 3, 4, 5];
let container = new Container(arr);
let iterator = container.getIterator();
while(iterator.hasNext()) {
  console.log(iterator.next());
}
```

在实际开发中，jQuery中的 `each` 方法就是迭代器模式的实现

```js
function each(data) {
  var $data = $(data);  // 生成迭代器
  $data.each(function(key, p) {
    console.log(key, p);
  })
}
```

另外一个就是ES6中的 `Iterator`。它实现了迭代器模式。在ES6中，存在多种有序集合的数据类型，它们包括 `Array`、`Map`、`Set`、`String`、`TypedArray`、`arguments`以及`NodeList`，所以，需要有一个统一的遍历接口来遍历所有的数据类型，注意，`Object`不是有序集合，它可以用 `Map` 结构来代替。

上面讲的数据类型都具有 `[Symbol.iterator]` 属性，属性值是一个函数，执行函数返回一个迭代器，这个迭代器有 `next` 方法可以用来顺序迭代子元素。

每次都去读取这个属性很麻烦，ES6为我们提供了 `for...of` 语法，它实际上就是 `iterator` 的一个语法糖。

### 状态模式

一个对象有状态变化，每次状态变化都会触发一个逻辑，所以，我们不能使用 `if...else` 来控制。现实场景中，常见的就是红绿黄灯，交通灯都会有这三种状态的变化。

下面来看下 `UML` 类图：

<img src="../../images/20190116202524.png" width="500px" />

```js
// 状态 （比如：红灯、绿灯、黄灯）
class State {
  constructor(color) {
    this.color = color
  }

  handle(context) {
    console.log(`turn to ${this.color} light`);
    context.setState(this);
  }
}

// 主体
class Context {
  constructor() {
    this.state = null;
  }

  // 获取状态
  getState() {
    return this.state;
  }

  // 设置状态
  setState(state) {
    this.state = state;
  }
}

// 测试
let context = new Context();

let green = new State('green');
let yellow = new State('yellow');
let red = new State('red');
```

## 其他不常用设计模式

### 原型模式

实际上就是 `clone` 自己，生成一个新对象。在Java中默认已有了 `clone` 接口，但JavaScript没有。

在JavaScript中，`Object.create` 这个API最接近原型模式的原理。

```js
// 基于原型创建一个对象
let prototype = {
  getName: function() {
    return this.first + ' ' + this.last;
  },

  say: function() {
    console.log('hello');
  }
}

let x = Object.create(prototype);
x.first = 'A';
x.last = 'B';
x.getName();
x.say();
```

### 桥接模式

桥接模式用于把抽象化与实现化解耦，使得二者可以独立变化。比如我们把要画一些有颜色的圆形和三角形的业务拆分开来，把画图和着色分开，代码如下：

```js
// 填充颜色类
class Color {
  constructor(name) {
    this.name = name;
  }
}

// 画图
class Shape {
  constructor(name, color) {
    this.name = name;
    this.color = color;
  }

  draw() {
    console.log(`${this.color.name} ${this.name}`);
  }
}

// 测试
let red = new Color('red');
let yellow = new Color('yellow');
let cricle = new Shape('circle', red);    // 红色的圆形
circle.draw();
let triangle = new Shape('triangle', yellow);  // 换色的三角形
triangle.draw();
```

### 组合模式

组合模式就是生成树形结构，表示整体-部分的关系，让整体和部分都具有一致的操作方式。我们可以用虚拟DOM中的 `VNode` 来形容这种模式

```js
{
  tag: 'div',
  attr: {
    id: 'div1',
    className: 'container'
  },
  children: [
    {
      tag: 'p',
      attr: {},
      children: ['123']
    },
    {
      tag: 'p',
      attr: {},
      children: ['456']
    }
  ]
}
```
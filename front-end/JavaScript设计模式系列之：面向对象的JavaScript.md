> JavaScript 没有提供传统面向对象语言中的类式继承，而是通过原型委托的方式来实现对象与对象之间的继承。JavaScript 也咩有在语言层面提供对抽象类和接口的支持

## 一、动态类型语言

编程语言按数据类型分类，大致可以分为静态类型语言和动态类型语言。

静态类型语言在编译时已确定变量类型，而动态语言类型的变量类型要到程序运行时被赋值后才能确定。

 静态类型语言的优点是在编译时就能发现类型不匹配的错误，且明确了数据类型，执行速度较快，而动态类型语言的优点就是代码量少，且比较灵活，但在运行时可能会发生类型相关的错误

Javascript 是一门典型的动态类型语言。

鸭子类型（duck typing），关于这个有一个故事：从前有个国王，他觉得这个世界上鸭子的叫声很美妙，于是召集大臣要组建一个 1000 只鸭子组成的合唱团，大臣们找遍了全国却只有 999 只，最后大臣们发现有一只鸡，它的叫声跟鸭子一模一样，于是这只鸡成为了鸭子合唱团的最后一员。

鸭子类型指导我们只关注对象的行为，而非对象本身，下面我们用代码来模拟上面的这个故事：

```javascript
var duck = {
  duckSinging: function () {
    console.log("嘎嘎嘎");
  },
};
var chicken = {
  duckSinging: function () {
    console.log("咯咯咯");
  },
};

var choir = []; //合唱团

var joinChoir = function (animal) {
  if (animal && typeof animal.duckSinging === "function") {
    choir.push(animal);
    console.log("恭喜加入合唱团");
    console.log("合唱团已有成员数量：" + choir.length);
  }
};

joinChoir(duck); //恭喜加入合唱团
joinChoir(chicken); //恭喜加入合唱团
```

鸭子类型的概念在动态类型语言的面向对象设计中非常重要，利用它我们可以在动态类型语言中实现“面向接口编程”，而不是“面向实现编程”。

## 二、多态

多态（polymorphism），它的含义是同一操作作用于不同的对象上，可以产生不同的解释和不同的执行效果，换句话说，给不同的对象发送同一消息时，这些对象会根据这个消息分别给出不同的反馈，下面举个栗子：

有一只鸭和一只鸡，它们都会叫，当主人向它们发出“叫”的指令时，鸭会“嘎嘎嘎”的叫，而鸡会“咯咯咯”的叫，两只动物会根据主人发出的同一指令，发出各自不同的声音。

下面我们来看一段多态的 Javascript 代码：

```javascript
var makeSound = function(animal) {
    if(animal instanceof Duck) {
        console.log('嘎嘎嘎');
    }else if(animal instanceof Chicken) {
        console.log('咯咯咯');
    }
};
var Duck = funcdtion(){};
var Chicken = function(){};

makeSound(new Duck());        //嘎嘎嘎
makeSound(new Chicken());     //咯咯咯
```

多态背后的思想就是把“做什么”和“谁去做及怎样去做”分离开，也就是将“不变的事”和“可能改变的事”分离开。很显然，上面的代码有问题，如果我们再增加一只狗，就要改动 makeSound 函数，修改代码是危险且不可取的，我们要让代码变得可扩展，我们将上面的代码进行改动，如下：

```javascript
//将不变的部分分离出来，这里就是所有的动物都会叫
var makeSound = function (animal) {
  animal.sound();
};

//将可变的部分封装起来
var Duck = function () {};
Duck.prototype.sound = function () {
  console.log("嘎嘎嘎");
};

var Chicken = function () {};
Chicken.prototype.sound = function () {
  console.log("咯咯咯");
};

makeSound(new Duck()); //嘎嘎嘎
makeSound(new Chicken()); //咯咯咯
```

如果我们需要增加一只动物，那么我们只需要增加代码即可，而不需要去改动 `makeSound`函数

```javascript
var Dog = function () {};
Dog.prototype.sound = function () {
  console.log("汪汪汪");
};
makeSound(new Dog()); //汪汪汪
```

由此可见，Javascript 的多态性是与生俱来的，它作为一门动态类型语言，既不会检查对象类型，也不会检查参数类型，从上面的例子看出，我们既可以往 `makeSound` 函数里传递` duck` 参数，也可以传递 `chicken` 参数，所以，一种动物是否能发出声音，只取决于它有没有 `makeSound` 方法，而不取决于它是否是某种类型的对象。

下面我们再来看一个在实际项目中可能会遇到的例子，假设我们要编写一个地图应用，有两家地图 API 可供选择，他们都提供了 show 方法，代码如下：

```javascript
var googleMap = {
  show: function () {
    console.log("开始渲染谷歌地图");
  },
};
var renderMap = function () {
  googleMap.show();
};

renderMap(); //开始渲染谷歌地图
```

现在我们需要把谷歌地图换成百度地图

```javascript
var googleMap = {
  show: function () {
    console.log("开始渲染谷歌地图");
  },
};

var baiduMap = {
  show: function () {
    console.log("开始渲染百度地图");
  },
};

var renderMap = function (type) {
  if (type === "google") {
    googleMap.show();
  } else if (type === "baidu") {
    baiduMap.show();
  }
};

renderMap("google"); //开始渲染谷歌地图
renderMap("baidu"); //开始渲染百度地图
```

OK,现在问题来了，如果我再增加一个搜搜地图呢？那就要改动 `renderMap` 函数，继续在里面添加条件分支语句，所以，看下面的代码：

```javascript
var googleMap = {
  show: function () {
    console.log("开始渲染谷歌地图");
  },
};

var baiduMap = {
  show: function () {
    console.log("开始渲染百度地图");
  },
};

//把相同的部分抽象出来，也就是显示地图
var renderMap = function (map) {
  if (map.show instanceof Function) {
    map.show();
  }
};

renderMap(googleMap); //开始渲染谷歌地图
renderMap(baiduMap); //开始渲染百度地图
```

这时，我们如果需要添加其他的地图 API

```javascript
var sosoMap = {
  show: function () {
    console.log("开始渲染搜搜地图");
  },
};

renderMap(sosoMap);
```

在 Javascript 中，函数是一等对象，函数本身也是对象，函数用来封装行为并能被四处传递，当我们向函数发出“调用”消息时，这些函数会返回不同的执行结果。

## 二、封装

封装的目的就是将信息隐藏，一般我们讨论的是对数据和实现进行封装，除此之外更广泛的是对封装类型和封装变化。

### 1、封装数据

在其他许多编程语言中提供了 `private` 、`public`、`protected` 等关键字来实现封装，但 Javascript 没有，我们只有依靠变量的作用域来实现，而且只能模拟出 `public`和 `private` 这两种封装特性

```javascript
var myObject = (function () {
  var _name = "sven"; //私有（private）变量
  return {
    getName: function () {
      //公开（public）方法
      return _name;
    },
  };
})();

console.log(myObject.getName()); //sven
console.log(myObject._name); //undefined
```

另外，在 ES6 中，可以通过 `Symbol` 来创建私有属性。

### 2、封装实现

封装的目的是将信息隐藏，封装应被视为"任何形式的封装"，也就是说，封装不仅仅是隐藏数据，还包括隐藏实现细节、设计细节以及隐藏对象的类型

封装实现使得对象内部的变化对于其他对象而言是透明的，是不可见的，这使得对象之间的耦合变得松散，对象之间只通过对外暴露的 API 接口  来通信

### 3、封装类型

封装类型就是把对象的真正类型隐藏在抽象类或接口之后，相比对象类型，客户更关心对象的行为。

在 JavaScript 中并没有对抽象类和接口的支持，所以 JavaScript 没有能力，也没有必要去做到这点。

### 4、封装变化

从设计模式的角度上看，封装在更重要的层面  体现为封装变化

通过封装变化的方式，把系统中稳定不变的部分和容易变化的部分隔离开来，找到变化并封装。

## 四、原型模式和基于原型继承的 JavaScript

 在以类为中心的面向对象编程语言中，类和对象的关系可以想象成铸模和铸件的关系，对象总是从  类中创建而来，而在原型编程思想中，类并不是必需的，对象未必需要从类中创建而来，一个对象是通过克隆另外一个对象所得到的。

**原型模式不单是一种设计模式，也被称为一种编程泛型**

Javascript 中继承是基于原型模式的，而像 Java、C++等这些是基于类的的面向对象语言，我们要创建一个对象，必须先定义一个 Class，然后从这个 Class 里实例化一个对象出来。然而 Javascript 中并没有类，所以，在 JavaScript 中对象是被克隆出来的，也就是一个对象通过克隆另一个对象来创建自己。

### 使用克隆的原型模式

原型模式是用于创建对象的一种模式，它并不关心对象的具体类型，而是找到一个对象，然后通过克隆来创建一个一模一样的对象。

原型模式的实现关键，是语言本身是否提供了 `clone` 方法，假设我们需要编写一个网页版的飞机大战游戏，这个飞机拥有分身技能，当使用这个技能时，页面上会出现多个同样的飞机，这时我们就需要使用到原型模式来克隆飞机。ES5 提供了 `Object.create` 方法来克隆对象

```javascript
var Plane = function () {
  this.blood = 100;
  this.attackLevel = 1;
  this.defenseLevel = 1;
};

var plane = new Plane();
plane.blood = 500;
plane.attackLevel = 10;
plane.defenseLevel = 7;

var clonePlane = Object.create(plane);
console.log(clonePlane); // Object {blood: 500, attackLevel: 10, defenseLevel: 7}
```

在不支持 `Object.create` 方法的浏览器中，可以使用以下代码

```javascript
Object.create =
  Object.create ||
  function (obj) {
    var F = function () {};
    F.prototype = obj;
    return new F();
  };
```

原型模式的真正  目的并非在于得到一个一模一样的对象，而是提供了一种便捷的方式去创建某个类型的对象，克隆只是创建对象的过程和手段

### 原型编程泛型的一些规则

 所有的对象都有一个原型对象，那么可想而知，必定会有一个  根对象，这个根对象就是 `Object`,  我们可以从 `Object` 去克隆一个对象 A，那么  `Object` 就是对象 A 的原型，如果再  从对象 A 克隆一个对象 B，那么对象 A 就是对象 B 的原型对象，它们之间就形成了一条原型链，基于原型链的委托机制就是原型继承的本质

原型继承遵循以下原则，Javascript 也不例外：

- a、所有的数据都是对象
- b、要得到一个对象，不是通过实例化类，而是找到一个对象作为原型并克隆它
- c、对象会记住它的原型
- d、如果对象无法响应某个请求，它会把这个请求委托给它自己的原型

### JavaScript 中的原型继承

Javascript 中存在一个根对象 `Object.prototype`,它是一个空对象，所有的对象都是从这个根对象中克隆而来的，`Object.prototype` 就是它们的原型。

```javascript
var obj1 = new Object();
var obj2 = {};

//利用ES5提供的Object.getPrototypeOf方法来查看它们的原型
console.log(Object.getPrototypeOf(obj1) === Object.prototype); //true
console.log(Object.getPrototypeOf(obj2) === Object.prototype); //true
```

通过 `new` 运算符从构造器中得到一个对象，看下面的代码：

```javascript
function Person(name) {
  this.name = name;
}

Person.prototype.getName = function () {
  return this.name;
};

var a = new Person("Kaindy");

console.log(a.name); //Kaindy
console.log(a.getName()); //Kaindy
console.log(Object.getPrototypeOf(a) === Person.prototype); //true
```

上面代码中的 Person 并不是一个类，而是函数构造器，Javascript 的函数既可以作为普通函数使用，也可以作为构造器调用，当使用 `new` 运算符时，函数就成了构造器，这个创建对象的过程，也就是先克隆了` Object.prototype`，然后再做其他的一些操作。

在 Javascript 中，每个对象都会记住它的原型，准确的说，应该是对象的构造器有原型。每个对象都有一个名为 `__proto__` 的隐藏属性，这个属性会指向它的构造器的原型对象

```javascript
var a = new Object();
console.log(a.__proto__ === Object.prototype); //true
```

实际上，每个对象就是通过自身隐藏的 `__proto__` 属性来记住自己的构造器原型.

如果对象无法响应请求，它会把这个请求委托给它的构造器的原型，我们来看下面的代码：

```javascript
var obj = { name: "Kaindy" };

var A = function () {};
A.prototype = obj;

var a = new A();
console.log(a.name); //Kaindy
```

我们来看下引擎做了什么，

首先，我们需要打印出对象 a 的 name 属性，尝试遍历对象 a 的所有属性，但没找到 name

接着，对象 a 把查找 name 属性这个请求委托给了它自己的构造器原型，也就是 `a.__proto__` ，而 `a.__proto__` 指向了 `A.prototype` ，`A.prototype` 被设置为了对象`obj`。

最后在 obj 中找到了 name 属性，并返回它的值。

结束：`Object.create` 是原型模式的天然实现，目前大多数主流浏览器都支持此方法，但它效率并不高，比通过构造函数创建对象要慢，最新的 ES6 带来了 `Class` 语法，看起来像一门基于类的语言，但原理还是通过原型机制来创建对象，看下面的代码：

```javascript
class Animal {
  constructor(name) {
    this.name = name;
  }
  getName() {
    return this.name;
  }
}

class Dog extends Animal {
  constructor(name) {
    super(name);
  }
  speak() {
    return "woof";
  }
}

var dog = new Dog("Scamp");
console.log(dog.geName() + " says " + dog.speak());
```

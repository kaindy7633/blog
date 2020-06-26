<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [精读ECMAScript 6.0](#%E7%B2%BE%E8%AF%BBecmascript-60)
  - [简介](#%E7%AE%80%E4%BB%8B)
  - [let和const](#let%E5%92%8Cconst)
    - [let 命令](#let-%E5%91%BD%E4%BB%A4)
    - [块级作用域](#%E5%9D%97%E7%BA%A7%E4%BD%9C%E7%94%A8%E5%9F%9F)
    - [const 命令](#const-%E5%91%BD%E4%BB%A4)
    - [顶层对象的属性](#%E9%A1%B6%E5%B1%82%E5%AF%B9%E8%B1%A1%E7%9A%84%E5%B1%9E%E6%80%A7)
    - [globalThis 对象](#globalthis-%E5%AF%B9%E8%B1%A1)
  - [解构赋值](#%E8%A7%A3%E6%9E%84%E8%B5%8B%E5%80%BC)
    - [数组的解构赋值](#%E6%95%B0%E7%BB%84%E7%9A%84%E8%A7%A3%E6%9E%84%E8%B5%8B%E5%80%BC)
    - [对象的解构赋值](#%E5%AF%B9%E8%B1%A1%E7%9A%84%E8%A7%A3%E6%9E%84%E8%B5%8B%E5%80%BC)
    - [字符串的解构赋值](#%E5%AD%97%E7%AC%A6%E4%B8%B2%E7%9A%84%E8%A7%A3%E6%9E%84%E8%B5%8B%E5%80%BC)
    - [数值和布尔值的解构赋值](#%E6%95%B0%E5%80%BC%E5%92%8C%E5%B8%83%E5%B0%94%E5%80%BC%E7%9A%84%E8%A7%A3%E6%9E%84%E8%B5%8B%E5%80%BC)
    - [函数参数的解构赋值](#%E5%87%BD%E6%95%B0%E5%8F%82%E6%95%B0%E7%9A%84%E8%A7%A3%E6%9E%84%E8%B5%8B%E5%80%BC)
    - [用途](#%E7%94%A8%E9%80%94)
  - [字符串的扩展](#%E5%AD%97%E7%AC%A6%E4%B8%B2%E7%9A%84%E6%89%A9%E5%B1%95)
    - [Unicode表示法](#unicode%E8%A1%A8%E7%A4%BA%E6%B3%95)
    - [遍历器接口](#%E9%81%8D%E5%8E%86%E5%99%A8%E6%8E%A5%E5%8F%A3)
    - [JSON.stringify() 的改造](#jsonstringify-%E7%9A%84%E6%94%B9%E9%80%A0)
    - [模板字符串](#%E6%A8%A1%E6%9D%BF%E5%AD%97%E7%AC%A6%E4%B8%B2)
  - [字符串新增方法](#%E5%AD%97%E7%AC%A6%E4%B8%B2%E6%96%B0%E5%A2%9E%E6%96%B9%E6%B3%95)
    - [String.fromCodePoint()](#stringfromcodepoint)
    - [String.raw()](#stringraw)
    - [实例方法：codePointAt()](#%E5%AE%9E%E4%BE%8B%E6%96%B9%E6%B3%95codepointat)
    - [实例方法：normalize()](#%E5%AE%9E%E4%BE%8B%E6%96%B9%E6%B3%95normalize)
    - [实例方法：includes(), startsWith(), endsWith()](#%E5%AE%9E%E4%BE%8B%E6%96%B9%E6%B3%95includes-startswith-endswith)
    - [实例方法：repeat()](#%E5%AE%9E%E4%BE%8B%E6%96%B9%E6%B3%95repeat)
    - [实例方法：padStart()，padEnd()](#%E5%AE%9E%E4%BE%8B%E6%96%B9%E6%B3%95padstartpadend)
    - [实例方法：trimStart()，trimEnd()](#%E5%AE%9E%E4%BE%8B%E6%96%B9%E6%B3%95trimstarttrimend)
    - [实例方法：matchAll()](#%E5%AE%9E%E4%BE%8B%E6%96%B9%E6%B3%95matchall)
  - [正则的扩展](#%E6%AD%A3%E5%88%99%E7%9A%84%E6%89%A9%E5%B1%95)
    - [RegExp 构造函数](#regexp-%E6%9E%84%E9%80%A0%E5%87%BD%E6%95%B0)
    - [字符串的正则方法](#%E5%AD%97%E7%AC%A6%E4%B8%B2%E7%9A%84%E6%AD%A3%E5%88%99%E6%96%B9%E6%B3%95)
    - [u 修饰符](#u-%E4%BF%AE%E9%A5%B0%E7%AC%A6)
    - [RegExp.prototype.unicode 属性](#regexpprototypeunicode-%E5%B1%9E%E6%80%A7)
    - [y 修饰符](#y-%E4%BF%AE%E9%A5%B0%E7%AC%A6)
    - [RegExp.prototype.sticky 属性](#regexpprototypesticky-%E5%B1%9E%E6%80%A7)
    - [RegExp.prototype.flags 属性](#regexpprototypeflags-%E5%B1%9E%E6%80%A7)
    - [s 修饰符：dotAll 模式](#s-%E4%BF%AE%E9%A5%B0%E7%AC%A6dotall-%E6%A8%A1%E5%BC%8F)
    - [具名组匹配](#%E5%85%B7%E5%90%8D%E7%BB%84%E5%8C%B9%E9%85%8D)
    - [String.prototype.matchAll()](#stringprototypematchall)
  - [数值的扩展](#%E6%95%B0%E5%80%BC%E7%9A%84%E6%89%A9%E5%B1%95)
    - [二进制和八进制表示法](#%E4%BA%8C%E8%BF%9B%E5%88%B6%E5%92%8C%E5%85%AB%E8%BF%9B%E5%88%B6%E8%A1%A8%E7%A4%BA%E6%B3%95)
    - [Number.isFinite(), Number.isNaN()](#numberisfinite-numberisnan)
    - [Number.parseInt(), Number.parseFloat()](#numberparseint-numberparsefloat)
    - [Number.isInteger()](#numberisinteger)
    - [Number.EPSILON](#numberepsilon)
    - [安全整数和 Number.isSafeInteger()](#%E5%AE%89%E5%85%A8%E6%95%B4%E6%95%B0%E5%92%8C-numberissafeinteger)
    - [Math 对象的扩展](#math-%E5%AF%B9%E8%B1%A1%E7%9A%84%E6%89%A9%E5%B1%95)
    - [对数方法](#%E5%AF%B9%E6%95%B0%E6%96%B9%E6%B3%95)
    - [双曲函数方法](#%E5%8F%8C%E6%9B%B2%E5%87%BD%E6%95%B0%E6%96%B9%E6%B3%95)
    - [指数运算符](#%E6%8C%87%E6%95%B0%E8%BF%90%E7%AE%97%E7%AC%A6)
    - [BigInt 数据类型](#bigint-%E6%95%B0%E6%8D%AE%E7%B1%BB%E5%9E%8B)
    - [BigInt 对象](#bigint-%E5%AF%B9%E8%B1%A1)
    - [BigInt的转换规则](#bigint%E7%9A%84%E8%BD%AC%E6%8D%A2%E8%A7%84%E5%88%99)
    - [数学运算](#%E6%95%B0%E5%AD%A6%E8%BF%90%E7%AE%97)
  - [函数的扩展](#%E5%87%BD%E6%95%B0%E7%9A%84%E6%89%A9%E5%B1%95)
    - [函数参数的默认值](#%E5%87%BD%E6%95%B0%E5%8F%82%E6%95%B0%E7%9A%84%E9%BB%98%E8%AE%A4%E5%80%BC)
    - [rest 参数](#rest-%E5%8F%82%E6%95%B0)
    - [严格模式](#%E4%B8%A5%E6%A0%BC%E6%A8%A1%E5%BC%8F)
    - [name 属性](#name-%E5%B1%9E%E6%80%A7)
    - [箭头函数](#%E7%AE%AD%E5%A4%B4%E5%87%BD%E6%95%B0)
    - [尾调用优化](#%E5%B0%BE%E8%B0%83%E7%94%A8%E4%BC%98%E5%8C%96)
    - [函数参数的尾逗号](#%E5%87%BD%E6%95%B0%E5%8F%82%E6%95%B0%E7%9A%84%E5%B0%BE%E9%80%97%E5%8F%B7)
    - [Function.prototype.toString()](#functionprototypetostring)
    - [catch 命令的参数省略](#catch-%E5%91%BD%E4%BB%A4%E7%9A%84%E5%8F%82%E6%95%B0%E7%9C%81%E7%95%A5)
  - [数组的扩展](#%E6%95%B0%E7%BB%84%E7%9A%84%E6%89%A9%E5%B1%95)
    - [扩展运算符](#%E6%89%A9%E5%B1%95%E8%BF%90%E7%AE%97%E7%AC%A6)
    - [Array.from()](#arrayfrom)
    - [Array.of()](#arrayof)
    - [数组实例的 copyWithin()](#%E6%95%B0%E7%BB%84%E5%AE%9E%E4%BE%8B%E7%9A%84-copywithin)
    - [数组实例的 find() 和 findIndex()](#%E6%95%B0%E7%BB%84%E5%AE%9E%E4%BE%8B%E7%9A%84-find-%E5%92%8C-findindex)
    - [数组实例的 fill()](#%E6%95%B0%E7%BB%84%E5%AE%9E%E4%BE%8B%E7%9A%84-fill)
    - [数组实例的 entries()，keys() 和 values()](#%E6%95%B0%E7%BB%84%E5%AE%9E%E4%BE%8B%E7%9A%84-entrieskeys-%E5%92%8C-values)
    - [数组实例的 includes()](#%E6%95%B0%E7%BB%84%E5%AE%9E%E4%BE%8B%E7%9A%84-includes)
    - [数组实例的 flat()，flatMap()](#%E6%95%B0%E7%BB%84%E5%AE%9E%E4%BE%8B%E7%9A%84-flatflatmap)
    - [数组的空位](#%E6%95%B0%E7%BB%84%E7%9A%84%E7%A9%BA%E4%BD%8D)
    - [Array.prototype.sort() 的排序稳定性](#arrayprototypesort-%E7%9A%84%E6%8E%92%E5%BA%8F%E7%A8%B3%E5%AE%9A%E6%80%A7)
  - [对象的扩展](#%E5%AF%B9%E8%B1%A1%E7%9A%84%E6%89%A9%E5%B1%95)
    - [属性的简洁表示法](#%E5%B1%9E%E6%80%A7%E7%9A%84%E7%AE%80%E6%B4%81%E8%A1%A8%E7%A4%BA%E6%B3%95)
    - [属性名表达式](#%E5%B1%9E%E6%80%A7%E5%90%8D%E8%A1%A8%E8%BE%BE%E5%BC%8F)
    - [方法的 name 属性](#%E6%96%B9%E6%B3%95%E7%9A%84-name-%E5%B1%9E%E6%80%A7)
    - [属性的可枚举性和遍历](#%E5%B1%9E%E6%80%A7%E7%9A%84%E5%8F%AF%E6%9E%9A%E4%B8%BE%E6%80%A7%E5%92%8C%E9%81%8D%E5%8E%86)
    - [super 关键字](#super-%E5%85%B3%E9%94%AE%E5%AD%97)
    - [对象的扩展运算符](#%E5%AF%B9%E8%B1%A1%E7%9A%84%E6%89%A9%E5%B1%95%E8%BF%90%E7%AE%97%E7%AC%A6)
    - [链判断运算符](#%E9%93%BE%E5%88%A4%E6%96%AD%E8%BF%90%E7%AE%97%E7%AC%A6)
    - [Null 判断运算符](#null-%E5%88%A4%E6%96%AD%E8%BF%90%E7%AE%97%E7%AC%A6)
  - [对象的新增方法](#%E5%AF%B9%E8%B1%A1%E7%9A%84%E6%96%B0%E5%A2%9E%E6%96%B9%E6%B3%95)
    - [Object.is()](#objectis)
    - [Object.assign()](#objectassign)
    - [Object.getOwnPropertyDescriptors()](#objectgetownpropertydescriptors)
    - [__proto__属性，Object.setPrototypeOf()，Object.getPrototypeOf()](#__proto__%E5%B1%9E%E6%80%A7objectsetprototypeofobjectgetprototypeof)
      - [__proto__属性](#__proto__%E5%B1%9E%E6%80%A7)
      - [Object.setPrototypeOf()](#objectsetprototypeof)
      - [Object.getPrototypeOf()](#objectgetprototypeof)
    - [Object.keys()，Object.values()，Object.entries()](#objectkeysobjectvaluesobjectentries)
      - [Object.keys()](#objectkeys)
      - [Object.values()](#objectvalues)
      - [Object.entries()](#objectentries)
    - [Object.fromEntries()](#objectfromentries)
  - [Symbol](#symbol)
    - [Symbol.prototype.description](#symbolprototypedescription)
    - [作为属性名的 Symbol](#%E4%BD%9C%E4%B8%BA%E5%B1%9E%E6%80%A7%E5%90%8D%E7%9A%84-symbol)
    - [消除魔术字符串](#%E6%B6%88%E9%99%A4%E9%AD%94%E6%9C%AF%E5%AD%97%E7%AC%A6%E4%B8%B2)
    - [属性名的遍历](#%E5%B1%9E%E6%80%A7%E5%90%8D%E7%9A%84%E9%81%8D%E5%8E%86)
    - [Symbol.for()，Symbol.keyFor()](#symbolforsymbolkeyfor)
    - [模块的 Singleton 模式](#%E6%A8%A1%E5%9D%97%E7%9A%84-singleton-%E6%A8%A1%E5%BC%8F)
    - [内置的 Symbol 值](#%E5%86%85%E7%BD%AE%E7%9A%84-symbol-%E5%80%BC)
      - [Symbol.hasInstance](#symbolhasinstance)
      - [Symbol.isConcatSpreadable](#symbolisconcatspreadable)
      - [Symbol.species](#symbolspecies)
      - [Symbol.match](#symbolmatch)
      - [Symbol.replace](#symbolreplace)
      - [Symbol.search](#symbolsearch)
      - [Symbol.split](#symbolsplit)
      - [Symbol.iterator](#symboliterator)
      - [Symbol.toPrimitive](#symboltoprimitive)
      - [Symbol.toStringTag](#symboltostringtag)
      - [Symbol.unscopables](#symbolunscopables)
  - [Set和Map数据结构](#set%E5%92%8Cmap%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84)
    - [Set](#set)
      - [基本用法](#%E5%9F%BA%E6%9C%AC%E7%94%A8%E6%B3%95)
      - [Set 实例的属性和方法](#set-%E5%AE%9E%E4%BE%8B%E7%9A%84%E5%B1%9E%E6%80%A7%E5%92%8C%E6%96%B9%E6%B3%95)
      - [遍历操作](#%E9%81%8D%E5%8E%86%E6%93%8D%E4%BD%9C)
    - [WeakSet](#weakset)
      - [含义](#%E5%90%AB%E4%B9%89)
      - [语法](#%E8%AF%AD%E6%B3%95)
    - [Map](#map)
      - [含义和基本用法](#%E5%90%AB%E4%B9%89%E5%92%8C%E5%9F%BA%E6%9C%AC%E7%94%A8%E6%B3%95)
      - [实例的属性和操作方法](#%E5%AE%9E%E4%BE%8B%E7%9A%84%E5%B1%9E%E6%80%A7%E5%92%8C%E6%93%8D%E4%BD%9C%E6%96%B9%E6%B3%95)
      - [遍历方法](#%E9%81%8D%E5%8E%86%E6%96%B9%E6%B3%95)
      - [与其他数据结构的互相转换](#%E4%B8%8E%E5%85%B6%E4%BB%96%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E7%9A%84%E4%BA%92%E7%9B%B8%E8%BD%AC%E6%8D%A2)
    - [WeakMap](#weakmap)
      - [含义](#%E5%90%AB%E4%B9%89-1)
      - [WeakMap 的语法](#weakmap-%E7%9A%84%E8%AF%AD%E6%B3%95)
  - [Proxy](#proxy)
    - [概述](#%E6%A6%82%E8%BF%B0)
    - [Proxy 实例的方法](#proxy-%E5%AE%9E%E4%BE%8B%E7%9A%84%E6%96%B9%E6%B3%95)
      - [get()](#get)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# 精读ECMAScript 6.0

## 简介

ECMAScript 6.0（以下简称 ES6）是 JavaScript 语言的下一代标准，在2015年6月正式发布。它的目标，是使得 JavaScript 语言可以用来编写复杂的大型应用程序，成为企业级开发语言。

ECMAScript 和 JavaScript 的关系是，前者是后者的规格，后者是前者的一种实现

## let和const

### let 命令

ES6 新增了 `let` 命令，用来声明变量，用法类似于 `var`

不存在变量提升:  `var` 命令会发生“变量提升”现象，即变量可以在声明之前使用，值为 `undefined`,  `let`命令改变了语法行为，它所声明的变量一定要在声明后使用，否则报错。


暂时性死区：只要块级作用域内存在` let` 命令，它所声明的变量就“绑定”（binding）这个区域，不再受外部的影响。

在代码块内，使用 `let` 命令声明变量之前，该变量都是不可用的。这在语法上，称为“暂时性死区”（temporal dead zone，简称 TDZ）。

ES6 规定暂时性死区和 `let` 、`const` 语句不出现变量提升，主要是为了减少运行时错误，防止在变量声明前就使用这个变量，从而导致意料之外的行为

`let` 不允许在相同作用域内，重复声明同一个变量

### 块级作用域

`ES5` 只有全局作用域和函数作用域，没有块级作用域，这带来很多不合理的场景

- 内层变量可能会覆盖外层变量
- 用来计数的循环变量泄露为全局变量

`let`实际上为 `JavaScript` 新增了块级作用域。

`ES5` 规定，函数只能在顶层作用域和函数作用域之中声明，不能在块级作用域声明，`ES6` 引入了块级作用域，明确允许在块级作用域之中声明函数

### const 命令

`const`声明一个只读的常量。一旦声明，常量的值就不能改变.

`const`的作用域与`let`命令相同：只在声明所在的块级作用域内有效。`const`命令声明的常量也是不提升，同样存在暂时性死区，只能在声明的位置后面使用。

`const`实际上保证的，并不是变量的值不得改动，而是变量指向的那个内存地址所保存的数据不得改动。对于简单类型的数据（数值、字符串、布尔值），值就保存在变量指向的那个内存地址，因此等同于常量。但对于复合类型的数据（主要是对象和数组），变量指向的内存地址，保存的只是一个指向实际数据的指针，`const`只能保证这个指针是固定的（即总是指向另一个固定的地址），至于它指向的数据结构是不是可变的，就完全不能控制了

`ES5` 只有两种声明变量的方法：`var`命令和`function`命令。ES6 除了添加`let`和`const`命令，后面还会提到，另外两种声明变量的方法：`import`命令和`class`命令。所以，ES6 一共有 6 种声明变量的方法。

### 顶层对象的属性

顶层对象，在浏览器环境指的是`window`对象，在`Node` 指的是`global`对象

`ES6` 为了保持兼容性，`var`命令和`function`命令声明的全局变量，依旧是顶层对象的属性；另一方面规定，`let`命令、`const`命令、`class`命令声明的全局变量，不属于顶层对象的属性

### globalThis 对象

`JavaScript` 语言存在一个顶层对象，它提供全局环境（即全局作用域）,但这个顶层对象在各种实现里面是不统一的

- 浏览器里面，顶层对象是`window`，但 `Node` 和 `Web Worker` 没有`window`。
- 浏览器和 `Web Worker` 里面，`self`也指向顶层对象，但是 `Node` 没有`self`。
- `Node` 里面，顶层对象是`global`，但其他环境都不支持。

`ES2020` 在语言标准的层面，引入`globalThis`作为顶层对象。也就是说，任何环境下，`globalThis`都是存在的，都可以从它拿到顶层对象，指向全局环境下的`this`

## 解构赋值

### 数组的解构赋值

`ES6` 允许按照一定模式，从数组和对象中提取值，对变量进行赋值，这被称为解构（Destructuring）

```javascript
let [a, b, c] = [1, 2, 3];
```

如果解构不成功，变量的值就等于`undefined`

对于 `Set` 结构，也可以使用数组的解构赋值。

```javascript
let [x, y, z] = new Set(['a', 'b', 'c']);
x // "a"
```

事实上，只要某种数据结构具有 `Iterator` 接口，都可以采用数组形式的解构赋值

```javascript
function* fibs() {
  let a = 0;
  let b = 1;
  while (true) {
    yield a;
    [a, b] = [b, a + b];
  }
}

let [first, second, third, fourth, fifth, sixth] = fibs();
sixth // 5
```

解构赋值允许指定默认值

```javascript
let [foo = true] = [];
foo // true

let [x, y = 'b'] = ['a']; // x='a', y='b'
let [x, y = 'b'] = ['a', undefined]; // x='a', y='b'
```

### 对象的解构赋值

解构不仅可以用于数组，还可以用于对象

```javascript
let { foo, bar } = { foo: 'aaa', bar: 'bbb' };
foo // "aaa"
bar // "bbb"
```

对象的解构与数组有一个重要的不同。数组的元素是按次序排列的，变量的取值由它的位置决定；而对象的属性没有次序，变量必须与属性同名，才能取到正确的值

```javascript
let { bar, foo } = { foo: 'aaa', bar: 'bbb' };
foo // "aaa"
bar // "bbb"

let { baz } = { foo: 'aaa', bar: 'bbb' };
baz // undefined
```

对象的解构赋值，可以很方便地将现有对象的方法，赋值到某个变量

```javascript
// 例一
let { log, sin, cos } = Math;

// 例二
const { log } = console;
log('hello') // hello
```

对象的解构也可以指定默认值。

```javascript
var {x = 3} = {};
x // 3

var {x, y = 5} = {x: 1};
x // 1
y // 5

var {x: y = 3} = {};
y // 3

var {x: y = 3} = {x: 5};
y // 5

var { message: msg = 'Something went wrong' } = {};
msg // "Something went wrong"
```

### 字符串的解构赋值

字符串也可以解构赋值。这是因为此时，字符串被转换成了一个类似数组的对象

```javascript
const [a, b, c, d, e] = 'hello';
a // "h"
b // "e"
c // "l"
d // "l"
e // "o"
```

### 数值和布尔值的解构赋值

解构赋值时，如果等号右边是数值和布尔值，则会先转为对象

```javascript
let {toString: s} = 123;
s === Number.prototype.toString // true

let {toString: s} = true;
s === Boolean.prototype.toString // true
```

### 函数参数的解构赋值

函数的参数也可以使用解构赋值

```javascript
function add([x, y]){
  return x + y;
}

add([1, 2]); // 3
```

### 用途

- 交换变量的值

  ```javascript
  let x = 1;
  let y = 2;

  [x, y] = [y, x];
  ```

- 从函数返回多个值

  ```javascript
  // 返回一个数组

  function example() {
    return [1, 2, 3];
  }
  let [a, b, c] = example();

  // 返回一个对象

  function example() {
    return {
      foo: 1,
      bar: 2
    };
  }
  let { foo, bar } = example();
  ```

- 函数参数的定义

  ```javascript
  // 参数是一组有次序的值
  function f([x, y, z]) { ... }
  f([1, 2, 3]);

  // 参数是一组无次序的值
  function f({x, y, z}) { ... }
  f({z: 3, y: 2, x: 1});
  ```

- 提取 `JSON` 数据

  ```javascript
  let jsonData = {
    id: 42,
    status: "OK",
    data: [867, 5309]
  };

  let { id, status, data: number } = jsonData;

  console.log(id, status, number);
  // 42, "OK", [867, 5309]
  ```

- 函数参数的默认值

  ```javascript
  jQuery.ajax = function (url, {
    async = true,
    beforeSend = function () {},
    cache = true,
    complete = function () {},
    crossDomain = false,
    global = true,
    // ... more config
  } = {}) {
    // ... do stuff
  };
  ```

- 遍历 `Map` 结构

  任何部署了 Iterator 接口的对象，都可以用for...of循环遍历。Map 结构原生支持 Iterator 接口，配合变量的解构赋值，获取键名和键值就非常方便

  ```javascript
  const map = new Map();
  map.set('first', 'hello');
  map.set('second', 'world');

  for (let [key, value] of map) {
    console.log(key + " is " + value);
  }
  // first is hello
  // second is world
  ```

- 输入模块的指定方法

  ```javascript
  const { SourceMapConsumer, SourceNode } = require("source-map");
  ```

## 字符串的扩展

### Unicode表示法

`ES6` 加强了对 `Unicode` 的支持，允许采用`\uxxxx`形式表示一个字符，其中`xxxx`表示字符的 `Unicode` 码点

```javascript
"\u0061"
// "a"
```

但是，这种表示法只限于码点在`\u0000~\uFFFF`之间的字符,`ES6` 对这一点做出了改进，只要将码点放入大括号，就能正确解读该字符

```javascript
"\u{20BB7}"
// "𠮷"

"\u{41}\u{42}\u{43}"
// "ABC"

let hello = 123;
hell\u{6F} // 123

'\u{1F680}' === '\uD83D\uDE80'
// true
```

### 遍历器接口

`ES6` 为字符串添加了遍历器接口，使得字符串可以被`for...of`循环遍历。

```javascript
for (let codePoint of 'foo') {
  console.log(codePoint)
}
// "f"
// "o"
// "o"
```

### JSON.stringify() 的改造

根据标准，`JSON` 数据必须是 `UTF-8` 编码。但是，现在的`JSON.stringify()`方法有可能返回不符合 `UTF-8` 标准的字符串

为了确保返回的是合法的 `UTF-8` 字符，`ES2019` 改变了`JSON.stringify()`的行为。如果遇到`0xD800`到`0xDFFF`之间的单个码点，或者不存在的配对形式，它会返回转义字符串，留给应用自己决定下一步的处理

### 模板字符串

`ES6` 引入了模板字符

```javascript
$('#result').append(`
  There are <b>${basket.count}</b> items
   in your basket, <em>${basket.onSale}</em>
  are on sale!
`);
```

模板字符串（template string）是增强版的字符串，用反引号（`）标识。它可以当作普通字符串使用，也可以用来定义多行字符串，或者在字符串中嵌入变量

```javascript
// 普通字符串
`In JavaScript '\n' is a line-feed.`

// 多行字符串
`In JavaScript this is
 not legal.`

console.log(`string text line 1
string text line 2`);

// 字符串中嵌入变量
let name = "Bob", time = "today";
`Hello ${name}, how are you ${time}?`
```

模板字符串中嵌入变量，需要将变量名写在`${}`之中,大括号内部可以放入任意的 `JavaScript` 表达式，可以进行运算，以及引用对象属性

```javascript
let x = 1;
let y = 2;

`${x} + ${y} = ${x + y}`
// "1 + 2 = 3"

`${x} + ${y * 2} = ${x + y * 2}`
// "1 + 4 = 5"

let obj = {x: 1, y: 2};
`${obj.x + obj.y}`
// "3"
```

## 字符串新增方法

### String.fromCodePoint()

`ES5` 提供 `String.fromCharCode()` 方法，用于从 `Unicode` 码点返回对应字符，但是这个方法不能识别码点大于 `0xFFFF` 的字符

`ES6` 提供了`String.fromCodePoint()`方法，可以识别大于`0xFFFF`的字符，弥补了`String.fromCharCode()`方法的不足

```javascript
String.fromCodePoint(0x20BB7)
// "𠮷"
String.fromCodePoint(0x78, 0x1f680, 0x79) === 'x\uD83D\uDE80y'
// true
```

### String.raw()

`ES6` 还为原生的 `String` 对象，提供了一个`raw()`方法。该方法返回一个斜杠都被转义（即斜杠前面再加一个斜杠）的字符串，往往用于模板字符串的处理方法

```javascript
String.raw`Hi\n${2+3}!`
// 实际返回 "Hi\\n5!"，显示的是转义后的结果 "Hi\n5!"

String.raw`Hi\u000A!`;
// 实际返回 "Hi\\u000A!"，显示的是转义后的结果 "Hi\u000A!"
```

### 实例方法：codePointAt()

`JavaScript` 内部，字符以 `UTF-16` 的格式储存，每个字符固定为2个字节。对于那些需要4个字节储存的字符（`Unicode` 码点大于`0xFFFF`的字符），`JavaScript` 会认为它们是两个字符

`ES6` 提供了`codePointAt()`方法，能够正确处理 4 个字节储存的字符，返回一个字符的码点

```javascript
let s = '𠮷a';

s.codePointAt(0) // 134071
s.codePointAt(1) // 57271

s.codePointAt(2) // 97
```

`codePointAt()`方法可以用来测试一个字符由两个字节还是由四个字节组成的

```javascript
function is32Bit(c) {
  return c.codePointAt(0) > 0xFFFF;
}

is32Bit("𠮷") // true
is32Bit("a") // false
```

### 实例方法：normalize()

`ES6` 提供字符串实例的`normalize()`方法，用来将字符的不同表示方法统一为同样的形式，这称为 `Unicode` 正规化

```javascript
'\u01D1'.normalize() === '\u004F\u030C'.normalize()
// true
```

### 实例方法：includes(), startsWith(), endsWith()

传统上，`JavaScript` 只有`indexOf`方法，可以用来确定一个字符串是否包含在另一个字符串中。`ES6` 又提供了三种新方法:

- `includes()`：返回布尔值，表示是否找到了参数字符串。
- `startsWith()`：返回布尔值，表示参数字符串是否在原字符串的头部。
- `endsWith()`：返回布尔值，表示参数字符串是否在原字符串的尾部。

```javascript
let s = 'Hello world!';

s.startsWith('Hello') // true
s.endsWith('!') // true
s.includes('o') // true
```

这三个方法都支持第二个参数，表示开始搜索的位置

```javascript
let s = 'Hello world!';

s.startsWith('world', 6) // true
s.endsWith('Hello', 5) // true
s.includes('Hello', 6) // false
```

### 实例方法：repeat()

`repeat`方法返回一个新字符串，表示将原字符串重复n次

```javascript
'x'.repeat(3) // "xxx"
'hello'.repeat(2) // "hellohello"
'na'.repeat(0) // ""
```

### 实例方法：padStart()，padEnd()

`ES2017` 引入了字符串补全长度的功能。如果某个字符串不够指定长度，会在头部或尾部补全。`padStart()`用于头部补全，`padEnd()`用于尾部补全

```javascript
'x'.padStart(5, 'ab') // 'ababx'
'x'.padStart(4, 'ab') // 'abax'

'x'.padEnd(5, 'ab') // 'xabab'
'x'.padEnd(4, 'ab') // 'xaba'
```

`padStart()`和`padEnd()`一共接受两个参数，第一个参数是字符串补全生效的最大长度，第二个参数是用来补全的字符串

### 实例方法：trimStart()，trimEnd()

`ES2019` 对字符串实例新增了`trimStart()`和`trimEnd()`这两个方法。它们的行为与`trim()`一致，`trimStart()`消除字符串头部的空格，`trimEnd()`消除尾部的空格。它们返回的都是新字符串，不会修改原始字符串

```javascript
const s = '  abc  ';

s.trim() // "abc"
s.trimStart() // "abc  "
s.trimEnd() // "  abc"
```

### 实例方法：matchAll()

`matchAll()`方法返回一个正则表达式在当前字符串的所有匹配

## 正则的扩展

### RegExp 构造函数

在 `ES` 中的 `RegExp` 构造函数的参数有两种情况:

- 参数是字符串，这时第二个参数表示正则表达式的修饰符（`flag`）

  ```javascript
  var regex = new RegExp('xyz', 'i');
  // 等价于
  var regex = /xyz/i;
  ```

- 参数是一个正则表示式，这时会返回一个原有正则表达式的拷贝

  ```javascript
  var regex = new RegExp(/xyz/i);
  // 等价于
  var regex = /xyz/i;
  ```

在 `ES6` 中，如果`RegExp`构造函数第一个参数是一个正则对象，那么可以使用第二个参数指定修饰符。而且，返回的正则表达式会忽略原有的正则表达式的修饰符，只使用新指定的修饰符

```javascript
new RegExp(/abc/ig, 'i').flags
// "i"
```

### 字符串的正则方法

字符串对象共有 4 个方法，可以使用正则表达式：

- `match()` `String.prototype.match` 调用 `RegExp.prototype[Symbol.match]`
- `replace()` `String.prototype.replace` 调用 `RegExp.prototype[Symbol.replace]`
- `search()` `String.prototype.search` 调用 `RegExp.prototype[Symbol.search]`
- `split()` `String.prototype.split` 调用 `RegExp.prototype[Symbol.split]`

### u 修饰符

`ES6` 对正则表达式添加了`u`修饰符，含义为“Unicode 模式”，用来正确处理大于`\uFFFF`的 `Unicode` 字符

```javascript
/^\uD83D/u.test('\uD83D\uDC2A') // false
/^\uD83D/.test('\uD83D\uDC2A') // true
```

### RegExp.prototype.unicode 属性

正则实例对象新增`unicode`属性，表示是否设置了`u`修饰符

```javascript
const r1 = /hello/;
const r2 = /hello/u;

r1.unicode // false
r2.unicode // true
```

### y 修饰符

`ES6` 为正则表达式添加了`y`修饰符，叫做“粘连”（sticky）修饰符

`y`修饰符的作用与`g`修饰符类似，也是全局匹配，后一次匹配都从上一次匹配成功的下一个位置开始。不同之处在于，`g`修饰符只要剩余位置中存在匹配即可，而`y`修饰符确保匹配必须从剩余的第一个位置开始，这也就是“粘连”的涵义

```javascript
var s = 'aaa_aa_a';
var r1 = /a+/g;
var r2 = /a+/y;

r1.exec(s) // ["aaa"]
r2.exec(s) // ["aaa"]

r1.exec(s) // ["aa"]
r2.exec(s) // null
```

### RegExp.prototype.sticky 属性

与`y`修饰符相匹配，`ES6` 的正则实例对象多了`sticky`属性，表示是否设置了`y`修饰符。

```javascript
var r = /hello\d/y;
r.sticky // true
```

### RegExp.prototype.flags 属性

`ES6` 为正则表达式新增了`flags`属性，会返回正则表达式的修饰符

```javascript
// ES5 的 source 属性
// 返回正则表达式的正文
/abc/ig.source
// "abc"

// ES6 的 flags 属性
// 返回正则表达式的修饰符
/abc/ig.flags
// 'gi'
```

### s 修饰符：dotAll 模式

正则表达式中，点（.）是一个特殊字符，代表任意的单个字符，但是有两个例外。一个是四个字节的 `UTF-16` 字符，这个可以用`u`修饰符解决；另一个是行终止符（line terminator character）

`ES2018` 引入`s`修饰符，使得`.`可以匹配任意单个字符。

这被称为`dotAll`模式，即点（`dot`）代表一切字符。所以，正则表达式还引入了一个`dotAll`属性，返回一个布尔值，表示该正则表达式是否处在`dotAll`模式

```javascript
const re = /foo.bar/s;
// 另一种写法
// const re = new RegExp('foo.bar', 's');

re.test('foo\nbar') // true
re.dotAll // true
re.flags // 's'
```

### 具名组匹配

`ES2018` 引入了具名组匹配（Named Capture Groups），允许为每一个组匹配指定一个名字，既便于阅读代码，又便于引用

```javascript
const RE_DATE = /(?<year>\d{4})-(?<month>\d{2})-(?<day>\d{2})/;

const matchObj = RE_DATE.exec('1999-12-31');
const year = matchObj.groups.year; // 1999
const month = matchObj.groups.month; // 12
const day = matchObj.groups.day; // 31
```

如果具名组没有匹配，那么对应的`groups`对象属性会是`undefined`

有了具名组匹配以后，可以使用解构赋值直接从匹配结果上为变量赋值

```javascript
let {groups: {one, two}} = /^(?<one>.*):(?<two>.*)$/u.exec('foo:bar');
one  // foo
two  // bar
```

### String.prototype.matchAll()

`ES2020` 增加了`String.prototype.matchAll()`方法，可以一次性取出所有匹配。不过，它返回的是一个遍历器（Iterator），而不是数组

```javascript
const string = 'test1test2test3';

// g 修饰符加不加都可以
const regex = /t(e)(st(\d?))/g;

for (const match of string.matchAll(regex)) {
  console.log(match);
}
// ["test1", "e", "st1", "1", index: 0, input: "test1test2test3"]
// ["test2", "e", "st2", "2", index: 5, input: "test1test2test3"]
// ["test3", "e", "st3", "3", index: 10, input: "test1test2test3"]
```

遍历器转为数组是非常简单的，使用`...`运算符和`Array.from()`方法就可以了

```javascript
// 转为数组方法一
[...string.matchAll(regex)]

// 转为数组方法二
Array.from(string.matchAll(regex))
```

## 数值的扩展

### 二进制和八进制表示法

`ES6` 提供了二进制和八进制数值的新的写法，分别用前缀`0b`（或`0B`）和`0o`（或`0O`）表示

```javascript
0b111110111 === 503 // true
0o767 === 503 // true
```

从 `ES5` 开始，在严格模式之中，八进制就不再允许使用前缀`0`表示，`ES6` 进一步明确，要使用前缀`0o`表示

```javascript
// 非严格模式
(function(){
  console.log(0o11 === 011);
})() // true

// 严格模式
(function(){
  'use strict';
  console.log(0o11 === 011);
})() // Uncaught SyntaxError: Octal literals are not allowed in strict mode
```

### Number.isFinite(), Number.isNaN()

`ES6` 在`Number`对象上，新提供了`Number.isFinite()`和`Number.isNaN()`两个方法

`Number.isFinite()`用来检查一个数值是否为有限的（`finite`），即不是`Infinity`

```javascript
Number.isFinite(15); // true
Number.isFinite(0.8); // true
Number.isFinite(NaN); // false
Number.isFinite(Infinity); // false
Number.isFinite(-Infinity); // false
Number.isFinite('foo'); // false
Number.isFinite('15'); // false
Number.isFinite(true); // false
```

如果参数类型不是数值，`Number.isFinite`一律返回`false`

`Number.isNaN()`用来检查一个值是否为`NaN`

```javascript
Number.isNaN(NaN) // true
Number.isNaN(15) // false
Number.isNaN('15') // false
Number.isNaN(true) // false
Number.isNaN(9/NaN) // true
Number.isNaN('true' / 0) // true
Number.isNaN('true' / 'true') // true
```

### Number.parseInt(), Number.parseFloat()

`ES6` 将全局方法`parseInt()`和`parseFloat()`，移植到`Number`对象上面，行为完全保持不变。

```javascript
// ES5的写法
parseInt('12.34') // 12
parseFloat('123.45#') // 123.45

// ES6的写法
Number.parseInt('12.34') // 12
Number.parseFloat('123.45#') // 123.45
```

### Number.isInteger()

`Number.isInteger()`用来判断一个数值是否为整数

```javascript
Number.isInteger(25) // true
Number.isInteger(25.1) // false
```

`JavaScript` 内部，整数和浮点数采用的是同样的储存方法，所以 `25` 和 `25.0` 被视为同一个值。

```javascript
Number.isInteger(25) // true
Number.isInteger(25.0) // true
```

如果参数不是数值，`Number.isInteger`返回`false`

如果对数据精度的要求较高，不建议使用`Number.isInteger()`判断一个数值是否为整数

### Number.EPSILON

`ES6` 在`Number`对象上面，新增一个极小的常量`Number.EPSILON`。根据规格，它表示 1 与大于 1 的最小浮点数之间的差

```javascript
Number.EPSILON === Math.pow(2, -52)
// true
Number.EPSILON
// 2.220446049250313e-16
Number.EPSILON.toFixed(20)
// "0.00000000000000022204"
```

·Number.EPSILON`可以用来设置“能够接受的误差范围”。比如，误差范围设为 2 的-50 次方（即Number.EPSILON * Math.pow(2, 2)），即如果两个浮点数的差小于这个值，我们就认为这两个浮点数相等。因此，`Number.EPSILON`的实质是一个可以接受的最小误差范围

```javascript
function withinErrorMargin (left, right) {
  return Math.abs(left - right) < Number.EPSILON * Math.pow(2, 2);
}

0.1 + 0.2 === 0.3 // false
withinErrorMargin(0.1 + 0.2, 0.3) // true

1.1 + 1.3 === 2.4 // false
withinErrorMargin(1.1 + 1.3, 2.4) // true
```

### 安全整数和 Number.isSafeInteger()

`JavaScript` 能够准确表示的整数范围在`-2^53`到`2^53`之间（不含两个端点），超过这个范围，无法精确表示这个值

```javascript
Math.pow(2, 53) // 9007199254740992

9007199254740992  // 9007199254740992
9007199254740993  // 9007199254740992

Math.pow(2, 53) === Math.pow(2, 53) + 1
// true
```

`ES6` 引入了`Number.MAX_SAFE_INTEGER`和`Number.MIN_SAFE_INTEGER`这两个常量，用来表示这个范围的上下限

```javascript
Number.MAX_SAFE_INTEGER === Math.pow(2, 53) - 1
// true
Number.MAX_SAFE_INTEGER === 9007199254740991
// true

Number.MIN_SAFE_INTEGER === -Number.MAX_SAFE_INTEGER
// true
Number.MIN_SAFE_INTEGER === -9007199254740991
// true
```

`Number.isSafeInteger()`则是用来判断一个整数是否落在这个范围之内

```javascript
Number.isSafeInteger('a') // false
Number.isSafeInteger(null) // false
Number.isSafeInteger(NaN) // false
Number.isSafeInteger(Infinity) // false
Number.isSafeInteger(-Infinity) // false

Number.isSafeInteger(3) // true
Number.isSafeInteger(1.2) // false
Number.isSafeInteger(9007199254740990) // true
Number.isSafeInteger(9007199254740992) // false

Number.isSafeInteger(Number.MIN_SAFE_INTEGER - 1) // false
Number.isSafeInteger(Number.MIN_SAFE_INTEGER) // true
Number.isSafeInteger(Number.MAX_SAFE_INTEGER) // true
Number.isSafeInteger(Number.MAX_SAFE_INTEGER + 1) // false
```

### Math 对象的扩展

`ES6` 在 `Math` 对象上新增了 17 个与数学相关的方法。所有这些方法都是静态方法，只能在 `Math` 对象上调用

- `Math.trunc()`方法用于去除一个数的小数部分，返回整数部分

  ```javascript
  Math.trunc(4.1) // 4
  Math.trunc(4.9) // 4
  Math.trunc(-4.1) // -4
  Math.trunc(-4.9) // -4
  Math.trunc(-0.1234) // -0
  ```

- Math.sign()方法用来判断一个数到底是正数、负数、还是零。对于非数值，会先将其转换为数值

  它会返回五种值:

  - 参数为正数，返回+1；
  - 参数为负数，返回-1；
  - 参数为 0，返回0；
  - 参数为-0，返回-0;
  - 其他值，返回NaN

  ```javascript
  Math.sign(-5) // -1
  Math.sign(5) // +1
  Math.sign(0) // +0
  Math.sign(-0) // -0
  Math.sign(NaN) // NaN
  ```

- Math.cbrt()方法用于计算一个数的立方根

  ```javascript
  Math.cbrt(-1) // -1
  Math.cbrt(0)  // 0
  Math.cbrt(1)  // 1
  Math.cbrt(2)  // 1.2599210498948732
  ```

- Math.clz32()方法将参数转为 32 位无符号整数的形式，然后返回这个 32 位值里面有多少个前导 0

  ```javascript
  Math.clz32(0) // 32
  Math.clz32(1) // 31
  Math.clz32(1000) // 22
  Math.clz32(0b01000000000000000000000000000000) // 1
  Math.clz32(0b00100000000000000000000000000000) // 2
  ```

- Math.imul()方法返回两个数以 32 位带符号整数形式相乘的结果，返回的也是一个 32 位的带符号整数

  ```javascript
  Math.imul(2, 4)   // 8
  Math.imul(-1, 8)  // -8
  Math.imul(-2, -2) // 4
  ```

- Math.fround()方法返回一个数的32位单精度浮点数形式

  ```javascript
  Math.fround(0)   // 0
  Math.fround(1)   // 1
  Math.fround(2 ** 24 - 1)   // 16777215
  ```

- Math.hypot()方法返回所有参数的平方和的平方根

  ```javascript
  Math.hypot(3, 4);        // 5
  Math.hypot(3, 4, 5);     // 7.0710678118654755
  Math.hypot();            // 0
  Math.hypot(NaN);         // NaN
  Math.hypot(3, 4, 'foo'); // NaN
  Math.hypot(3, 4, '5');   // 7.0710678118654755
  Math.hypot(-3);          // 3
  ```

### 对数方法

`ES6` 新增了 4 个对数相关方法

- `Math.expm1(x)`返回 `ex - 1`，即`Math.exp(x) - 1`

  ```javascript
  Math.expm1(-1) // -0.6321205588285577
  Math.expm1(0)  // 0
  Math.expm1(1)  // 1.718281828459045
  ```

- `Math.log1p(x)`方法返回`1 + x`的自然对数，即`Math.log(1 + x)`。如果`x`小于`-1`，返回`NaN`

  ```javascript
  Math.log1p(1)  // 0.6931471805599453
  Math.log1p(0)  // 0
  Math.log1p(-1) // -Infinity
  Math.log1p(-2) // NaN
  ```

- Math.log10()返回以 10 为底的`x`的对数。如果`x`小于 0，则返回 `NaN`

  ```javascript
  Math.log10(2)      // 0.3010299956639812
  Math.log10(1)      // 0
  Math.log10(0)      // -Infinity
  Math.log10(-2)     // NaN
  Math.log10(100000) // 5
  ```

- Math.log2()返回以 2 为底的`x`的对数。如果`x`小于 0，则返回 `NaN`

  ```javascript
  Math.log2(3)       // 1.584962500721156
  Math.log2(2)       // 1
  Math.log2(1)       // 0
  Math.log2(0)       // -Infinity
  Math.log2(-2)      // NaN
  Math.log2(1024)    // 10
  Math.log2(1 << 29) // 29
  ```

### 双曲函数方法

`ES6` 新增了 6 个双曲函数方法。

- `Math.sinh(x)` 返回x的双曲正弦（hyperbolic sine）
- `Math.cosh(x)` 返回x的双曲余弦（hyperbolic cosine）
- `Math.tanh(x)` 返回x的双曲正切（hyperbolic tangent）
- `Math.asinh(x)` 返回x的反双曲正弦（inverse hyperbolic sine）
- `Math.acosh(x)` 返回x的反双曲余弦（inverse hyperbolic cosine）
- `Math.atanh(x)` 返回x的反双曲正切（inverse hyperbolic tangent）

### 指数运算符

`ES2016` 新增了一个指数运算符（`**`）

```javascript
2 ** 2 // 4
2 ** 3 // 8
```

### BigInt 数据类型

`JavaScript` 所有数字都保存成 `64` 位浮点数，这给数值的表示带来了两大限制。

一是数值的精度只能到 `53` 个二进制位（相当于 `16` 个十进制位），大于这个范围的整数，`JavaScript` 是无法精确表示的，这使得 `JavaScript` 不适合进行科学和金融方面的精确计算。二是大于或等于2的1024次方的数值，`JavaScript` 无法表示，会返回`Infinity`。

`ES2020` 引入了一种新的数据类型 `BigInt`（大整数），来解决这个问题。`BigInt` 只用来表示整数，没有位数的限制，任何位数的整数都可以精确表示。

```javascript
const a = 2172141653n;
const b = 15346349309n;

// BigInt 可以保持精度
a * b // 33334444555566667777n

// 普通整数无法保持精度
Number(a) * Number(b) // 33334444555566670000
```

为了与 `Number` 类型区别，`BigInt` 类型的数据必须添加后缀`n`

`BigInt` 与普通整数是两种值，它们之间并不相等。

```javascript
42n === 42 // false
```

`typeof`运算符对于 `BigInt` 类型的数据返回`bigint`。

```javascript
typeof 123n // 'bigint'
```

`BigInt` 可以使用负号（-），但是不能使用正号（+），因为会与 `asm.js` 冲突。

```javascript
-42n // 正确
+42n // 报错
```

### BigInt 对象

`JavaScript` 原生提供`BigInt`对象，可以用作构造函数生成 `BigInt` 类型的数值

```javascript
BigInt(123) // 123n
BigInt('123') // 123n
BigInt(false) // 0n
BigInt(true) // 1n
```

`BigInt` 对象继承了 `Object` 对象的两个实例方法:

- `BigInt.prototype.toString()`
- `BigInt.prototype.valueOf()`

继承了 `Number` 对象的一个实例方法:

- `BigInt.prototype.toLocaleString()`

此外，还提供了三个静态方法。

- `BigInt.asUintN(width, BigInt)`： 给定的 BigInt 转为 0 到 2width - 1 之间对应的值。
- `BigInt.asIntN(width, BigInt)`：给定的 BigInt 转为 -2width - 1 到 2width - 1 - 1 之间对应的值。
- `BigInt.parseInt(string[, radix])`：近似于Number.parseInt()，将一个字符串转换成指定进制的 BigInt。

```javascript
const max = 2n ** (64n - 1n) - 1n;

BigInt.asIntN(64, max)
// 9223372036854775807n
BigInt.asIntN(64, max + 1n)
// -9223372036854775808n
BigInt.asUintN(64, max + 1n)
// 9223372036854775808n
```

### BigInt的转换规则

可以使用`Boolean()`、`Number()`和`String()`这三个方法，将 `BigInt` 可以转为布尔值、数值和字符串类型

```javascript
Boolean(0n) // false
Boolean(1n) // true
Number(1n)  // 1
String(1n)  // "1"
```

### 数学运算

`BigInt` 类型的`+`、`-`、`*`和`**`这四个二元运算符，与 `Number` 类型的行为一致。除法运算`/`会舍去小数部分，返回一个整数

```javascript
9n / 5n
// 1n
```

## 函数的扩展

### 函数参数的默认值

`ES6` 允许为函数的参数设置默认值，即直接写在参数定义的后面

```javascript
function log(x, y = 'World') {
  console.log(x, y);
}

log('Hello') // Hello World
log('Hello', 'China') // Hello China
log('Hello', '') // Hello
```

参数变量是默认声明的，所以不能用`let`或`const`再次声明

```javascript
function foo(x = 5) {
  let x = 1; // error
  const x = 2; // error
}
```

使用参数默认值时，函数不能有同名参数

参数默认值可以与解构赋值的默认值，结合起来使用

```javascript
function foo({x, y = 5}) {
  console.log(x, y);
}

foo({}) // undefined 5
foo({x: 1}) // 1 5
foo({x: 1, y: 2}) // 1 2
foo() // TypeError: Cannot read property 'x' of undefined
```

通常情况下，定义了默认值的参数，应该是函数的尾参数

```javascript
// 例一
function f(x = 1, y) {
  return [x, y];
}

f() // [1, undefined]
f(2) // [2, undefined]
f(, 1) // 报错
f(undefined, 1) // [1, 1]

// 例二
function f(x, y = 5, z) {
  return [x, y, z];
}

f() // [undefined, 5, undefined]
f(1) // [1, 5, undefined]
f(1, ,2) // 报错
f(1, undefined, 2) // [1, 5, 2]
```

指定了默认值以后，函数的`length`属性，将返回没有指定默认值的参数个数。也就是说，指定了默认值后，`length`属性将失真

```javascript
(function (a) {}).length // 1
(function (a = 5) {}).length // 0
(function (a, b, c = 5) {}).length // 2
```

### rest 参数

`ES6` 引入 `rest` 参数（形式为`...变量名`），用于获取函数的多余参数，这样就不需要使用`arguments`对象了。`rest` 参数搭配的变量是一个数组，该变量将多余的参数放入数组中

```javascript
function add(...values) {
  let sum = 0;

  for (var val of values) {
    sum += val;
  }

  return sum;
}

add(2, 5, 3) // 10
```

注意，`rest` 参数之后不能再有其他参数（即只能是最后一个参数），否则会报错

```javascript
// 报错
function f(a, ...b, c) {
  // ...
}
```

### 严格模式

从 `ES5` 开始，函数内部可以设定为严格模式, `ES2016` 做了一点修改，规定只要函数参数使用了默认值、解构赋值、或者扩展运算符，那么函数内部就不能显式设定为严格模式，否则会报错

```javascript
// 报错
function doSomething(a, b = a) {
  'use strict';
  // code
}

// 报错
const doSomething = function ({a, b}) {
  'use strict';
  // code
};

// 报错
const doSomething = (...a) => {
  'use strict';
  // code
};

const obj = {
  // 报错
  doSomething({a, b}) {
    'use strict';
    // code
  }
};
```

### name 属性

`ES6` 对函数的 `name` 的行为做出了一些修改。如果将一个匿名函数赋值给一个变量，`ES5` 的`name`属性，会返回空字符串，而 `ES6` 的`name`属性会返回实际的函数名

```javascript
var f = function () {};

// ES5
f.name // ""

// ES6
f.name // "f"
```

### 箭头函数

`ES6` 允许使用“箭头”（`=>`）定义函数

```javascript
var f = v => v;

// 等同于
var f = function (v) {
  return v;
};
```

如果箭头函数不需要参数或需要多个参数，就使用一个圆括号代表参数部分

```javascript
var f = () => 5;
// 等同于
var f = function () { return 5 };

var sum = (num1, num2) => num1 + num2;
// 等同于
var sum = function(num1, num2) {
  return num1 + num2;
};
```

箭头函数可以与变量解构结合使用

```javascript
const full = ({ first, last }) => first + ' ' + last;

// 等同于
function full(person) {
  return person.first + ' ' + person.last;
}
```

箭头函数的一个用处是简化回调函数

```javascript
// 正常函数写法
[1,2,3].map(function (x) {
  return x * x;
});

// 箭头函数写法
[1,2,3].map(x => x * x);
```

```javascript
// 正常函数写法
var result = values.sort(function (a, b) {
  return a - b;
});

// 箭头函数写法
var result = values.sort((a, b) => a - b);
```

箭头函数有几个使用注意点。

- 函数体内的`this`对象，就是定义时所在的对象，而不是使用时所在的对象。

- 不可以当作构造函数，也就是说，不可以使用`new`命令，否则会抛出一个错误。

- 不可以使用`arguments`对象，该对象在函数体内不存在。如果要用，可以用 `rest` 参数代替。

- 不可以使用`yield`命令，因此箭头函数不能用作 `Generator` 函数

### 尾调用优化

尾调用（Tail Call）是函数式编程的一个重要概念，就是指某个函数的最后一步是调用另一个函数

```javascript
function f(x){
  return g(x);
}
```

尾调用之所以与其他调用不同，就在于它的特殊的调用位置。

我们知道，函数调用会在内存形成一个“调用记录”，又称“调用帧”（call frame），保存调用位置和内部变量等信息。如果在函数`A`的内部调用函数`B`，那么在`A`的调用帧上方，还会形成一个`B`的调用帧。等到`B`运行结束，将结果返回到`A`，`B`的调用帧才会消失。如果函数`B`内部还调用函数`C`，那就还有一个`C`的调用帧，以此类推。所有的调用帧，就形成一个“调用栈”（call stack）

尾调用由于是函数的最后一步操作，所以不需要保留外层函数的调用帧，因为调用位置、内部变量等信息都不会再用到了，只要直接用内层函数的调用帧，取代外层函数的调用帧就可以了

```javascript
function f() {
  let m = 1;
  let n = 2;
  return g(m + n);
}
f();

// 等同于
function f() {
  return g(3);
}
f();

// 等同于
g(3);
```

这就叫做“尾调用优化”（Tail call optimization），即只保留内层函数的调用帧。如果所有函数都是尾调用，那么完全可以做到每次执行时，调用帧只有一项，这将大大节省内存。这就是“尾调用优化”的意义

函数调用自身，称为递归。如果尾调用自身，就称为尾递归

```javascript
function factorial(n) {
  if (n === 1) return 1;
  return n * factorial(n - 1);
}

factorial(5) // 120
```

我们将上面的阶乘函数优化成尾递归

```javascript
function factorial(n, total) {
  if (n === 1) return total;
  return factorial(n - 1, n * total);
}

factorial(5, 1) // 120
```

来看看斐波拉契数列的例子：

```javascript
function Fibonacci (n) {
  if ( n <= 1 ) {return 1};

  return Fibonacci(n - 1) + Fibonacci(n - 2);
}

Fibonacci(10) // 89
Fibonacci(100) // 超时
Fibonacci(500) // 超时
```

尾递归优化过的 `Fibonacci` 数列实现如下

```javascript
function Fibonacci2 (n , ac1 = 1 , ac2 = 1) {
  if( n <= 1 ) {return ac2};

  return Fibonacci2 (n - 1, ac2, ac1 + ac2);
}

Fibonacci2(100) // 573147844013817200000
Fibonacci2(1000) // 7.0330367711422765e+208
Fibonacci2(10000) // Infinity
```

`ES6` 明确规定，所有 `ECMAScript` 的实现，都必须部署“尾调用优化”。这就是说，`ES6` 中只要使用尾递归，就不会发生栈溢出

尾递归的实现，往往需要改写递归函数，确保最后一步只调用自身, 这很不直观，解决这个问题有两个方法：

- 在尾递归函数之外，再提供一个正常形式的函数

  ```javascript
  function tailFactorial(n, total) {
    if (n === 1) return total;
    return tailFactorial(n - 1, n * total);
  }

  function factorial(n) {
    return tailFactorial(n, 1);
  }

  factorial(5) // 120
  ```

  或者通过柯里化的方式，柯里化（currying），是将多参数的函数转换成单参数的形式

  ```javascript
  function currying(fn, n) {
    return function (m) {
      return fn.call(this, m, n);
    };
  }

  function tailFactorial(n, total) {
    if (n === 1) return total;
    return tailFactorial(n - 1, n * total);
  }

  const factorial = currying(tailFactorial, 1);

  factorial(5) // 120
  ```

- 采用 `ES6` 的函数默认值

  ```javascript
  function factorial(n, total = 1) {
    if (n === 1) return total;
    return factorial(n - 1, n * total);
  }

  factorial(5) // 120
  ```

`ES6` 的尾调用优化只在严格模式下开启，正常模式是无效的

尾递归优化只在严格模式下生效，那么正常模式下,就自己实现尾递归优化。它的原理非常简单，尾递归之所以需要优化，原因是调用栈太多，造成溢出，那么只要减少调用栈，就不会溢出。怎么做可以减少调用栈呢？就是采用“循环”换掉“递归”。

```javascript
// 递归函数
function sum(x, y) {
  if (y > 0) {
    return sum(x + 1, y - 1);
  } else {
    return x;
  }
}

sum(1, 100000)
// Uncaught RangeError: Maximum call stack size exceeded(…)

// 使用蹦床函数（trampoline）可以将递归执行转为循环执行
function trampoline(f) {
  while (f && f instanceof Function) {
    f = f();
  }
  return f;
}

// 改写上面的 sum 递归
function sum(x, y) {
  if (y > 0) {
    return sum.bind(null, x + 1, y - 1);
  } else {
    return x;
  }
}

// 现在使用蹦床函数执行
trampoline(sum(1, 100000))
// 100001
```

然后，蹦床函数并不是真正的尾递归优化，下面的代码实现才是

```javascript
function tco(f) {
  var value;
  var active = false;
  var accumulated = [];

  return function accumulator() {
    accumulated.push(arguments);
    if (!active) {
      active = true;
      while (accumulated.length) {
        value = f.apply(this, accumulated.shift());
      }
      active = false;
      return value;
    }
  };
}

var sum = tco(function(x, y) {
  if (y > 0) {
    return sum(x + 1, y - 1)
  }
  else {
    return x
  }
});

sum(1, 100000)
// 100001
```

### 函数参数的尾逗号

`ES2017` 允许函数的最后一个参数有尾逗号（trailing comma）

```javascript
function clownsEverywhere(
  param1,
  param2,
) { /* ... */ }

clownsEverywhere(
  'foo',
  'bar',
);
```

### Function.prototype.toString()

`ES2019` 对函数实例的`toString()`方法做出了修改。`toString()`方法返回函数代码本身，以前会省略注释和空格, 修改后的`toString()`方法，明确要求返回一模一样的原始代码

```javascript
function /* foo comment */ foo () {}

foo.toString()
// "function /* foo comment */ foo () {}"
```

### catch 命令的参数省略

`JavaScript` 语言的`try...catch`结构，以前明确要求`catch`命令后面必须跟参数，接受`try`代码块抛出的错误对象, `ES2019` 做出了改变，允许`catch`语句省略参数

```javascript
try {
  // ...
} catch {
  // ...
}
```

## 数组的扩展

### 扩展运算符

扩展运算符（spread）是三个点（`...`）。它好比 `rest` 参数的逆运算，将一个数组转为用逗号分隔的参数序列

```javascript
console.log(...[1, 2, 3])
// 1 2 3

console.log(1, ...[2, 3, 4], 5)
// 1 2 3 4 5

[...document.querySelectorAll('div')]
// [<div>, <div>, <div>]
```

该运算符主要用于函数调用

```javascript
function push(array, ...items) {
  array.push(...items);
}

function add(x, y) {
  return x + y;
}

const numbers = [4, 38];
add(...numbers) // 42
```

扩展运算符后面还可以放置表达式

```javascript
const arr = [
  ...(x > 0 ? ['a'] : []),
  'b',
];
```

由于扩展运算符可以展开数组，所以不再需要`apply`方法，将数组转为函数的参数了。

```javascript
// ES5 的写法
function f(x, y, z) {
  // ...
}
var args = [0, 1, 2];
f.apply(null, args);

// ES6的写法
function f(x, y, z) {
  // ...
}
let args = [0, 1, 2];
f(...args);
```

求数组中的最大值

```javascript
Math.max(...[14, 3, 77])
```

通过`push`函数，将一个数组添加到另一个数组的尾部

```javascript
let arr1 = [0, 1, 2];
let arr2 = [3, 4, 5];
arr1.push(...arr2);
```

扩展运算符有以下应用：

- 复制数组，用扩展运算符复制数组，得到的是副本，而非地址值的拷贝

  ```javascript
  const a1 = [1, 2];
  // 写法一
  const a2 = [...a1];
  // 写法二
  const [...a2] = a1;
  ```

- 合并数组

  ```javascript
  [...arr1, ...arr2, ...arr3]
  ```

- 与解构赋值结合, 扩展运算符可以与解构赋值结合起来，用于生成数组

  ```javascript
  // ES5
  a = list[0], rest = list.slice(1)
  // ES6
  [a, ...rest] = list
  ```

  ```javascript
  const [first, ...rest] = [1, 2, 3, 4, 5];
  first // 1
  rest  // [2, 3, 4, 5]

  const [first, ...rest] = [];
  first // undefined
  rest  // []

  const [first, ...rest] = ["foo"];
  first  // "foo"
  rest   // []
  ```

- 扩展运算符还可以将字符串转为真正的数组

  ```javascript
  [...'hello']
  // [ "h", "e", "l", "l", "o" ]
  ```

- 实现了 `Iterator` 接口的对象

  任何定义了遍历器（`Iterator`）接口的对象，都可以用扩展运算符转为真正的数组

  ```javascript
  let nodeList = document.querySelectorAll('div');
  let array = [...nodeList];
  ```

- `Map` 和 `Set` 结构，`Generator` 函数

  ```javascript
  let map = new Map([
    [1, 'one'],
    [2, 'two'],
    [3, 'three'],
  ]);

  let arr = [...map.keys()]; // [1, 2, 3]
  ```

  `Generator` 函数运行后，返回一个遍历器对象，因此也可以使用扩展运算符

  ```javascript
  const go = function*(){
    yield 1;
    yield 2;
    yield 3;
  };

  [...go()] // [1, 2, 3]
  ```

### Array.from()

`Array.from`方法用于将两类对象转为真正的数组：类似数组的对象（`array-like object`）和可遍历（`iterable`）的对象（包括 `ES6` 新增的数据结构 `Set` 和 `Map`）

```javascript
let arrayLike = {
    '0': 'a',
    '1': 'b',
    '2': 'c',
    length: 3
};

// ES5的写法
var arr1 = [].slice.call(arrayLike); // ['a', 'b', 'c']

// ES6的写法
let arr2 = Array.from(arrayLike); // ['a', 'b', 'c']
```

实际应用中，常见的类似数组的对象是 `DOM` 操作返回的 `NodeList` 集合，以及函数内部的`arguments`对象。`Array.from`都可以将它们转为真正的数组

```javascript
// NodeList对象
let ps = document.querySelectorAll('p');
Array.from(ps).filter(p => {
  return p.textContent.length > 100;
});

// arguments对象
function foo() {
  var args = Array.from(arguments);
  // ...
}
```

`Array.from`还可以接受第二个参数，作用类似于数组的`map`方法，用来对每个元素进行处理，将处理后的值放入返回的数组

```javascript
Array.from(arrayLike, x => x * x);
// 等同于
Array.from(arrayLike).map(x => x * x);

Array.from([1, 2, 3], (x) => x * x)
// [1, 4, 9]
```

### Array.of()

`Array.of`方法用于将一组值，转换为数组

```javascript
Array.of(3, 11, 8) // [3,11,8]
Array.of(3) // [3]
Array.of(3).length // 1
```

`Array.of`基本上可以用来替代`Array()`或`new Array()`，并且不存在由于参数不同而导致的重载。它的行为非常统一

`Array.of`总是返回参数值组成的数组。如果没有参数，就返回一个空数组

### 数组实例的 copyWithin()

数组实例的`copyWithin()`方法，在当前数组内部，将指定位置的成员复制到其他位置（会覆盖原有成员），然后返回当前数组

```javascript
Array.prototype.copyWithin(target, start = 0, end = this.length)
```

它接受三个参数:

- `target`（必需）：从该位置开始替换数据。如果为负值，表示倒数。
- `start`（可选）：从该位置开始读取数据，默认为 0。如果为负值，表示从末尾开始计算。
- `end`（可选）：到该位置前停止读取数据，默认等于数组长度。如果为负值，表示从末尾开始计算。

这三个参数都应该是数值，如果不是，会自动转为数值, 下面是一些例子：

```javascript
// 将3号位复制到0号位
[1, 2, 3, 4, 5].copyWithin(0, 3, 4)
// [4, 2, 3, 4, 5]

// -2相当于3号位，-1相当于4号位
[1, 2, 3, 4, 5].copyWithin(0, -2, -1)
// [4, 2, 3, 4, 5]

// 将3号位复制到0号位
[].copyWithin.call({length: 5, 3: 1}, 0, 3)
// {0: 1, 3: 1, length: 5}

// 将2号位到数组结束，复制到0号位
let i32a = new Int32Array([1, 2, 3, 4, 5]);
i32a.copyWithin(0, 2);
// Int32Array [3, 4, 5, 4, 5]

// 对于没有部署 TypedArray 的 copyWithin 方法的平台
// 需要采用下面的写法
[].copyWithin.call(new Int32Array([1, 2, 3, 4, 5]), 0, 3, 4);
// Int32Array [4, 2, 3, 4, 5]
```

### 数组实例的 find() 和 findIndex()

数组实例的`find`方法，用于找出第一个符合条件的数组成员。它的参数是一个回调函数，所有数组成员依次执行该回调函数，直到找出第一个返回值为`true`的成员，然后返回该成员。如果没有符合条件的成员，则返回`undefined`

```javascript
[1, 4, -5, 10].find((n) => n < 0)
// -5
```

`find`方法的回调函数可以接受三个参数，依次为当前的值、当前的位置和原数组

```javascript
[1, 5, 10, 15].find(function(value, index, arr) {
  return value > 9;
}) // 10
```

数组实例的`findIndex`方法的用法与`find`方法非常类似，返回第一个符合条件的数组成员的位置，如果所有成员都不符合条件，则返回`-1`

```javascript
[1, 5, 10, 15].findIndex(function(value, index, arr) {
  return value > 9;
}) // 2
```

这两个方法都可以接受第二个参数，用来绑定回调函数的`this`对象

```javascript
function f(v){
  return v > this.age;
}
let person = {name: 'John', age: 20};
[10, 12, 26, 15].find(f, person);    // 26
```

### 数组实例的 fill()

`fill`方法使用给定值，填充一个数组

```javascript
['a', 'b', 'c'].fill(7)
// [7, 7, 7]

new Array(3).fill(7)
// [7, 7, 7]
```

`fill`方法还可以接受第二个和第三个参数，用于指定填充的起始位置和结束位置

```javascript
['a', 'b', 'c'].fill(7, 1, 2)
// ['a', 7, 'c']
```

### 数组实例的 entries()，keys() 和 values()

`ES6` 提供三个新的方法——`entries()`，`keys()`和`values()`——用于遍历数组。它们都返回一个遍历器对象，可以用`for...of`循环进行遍历，唯一的区别是`keys()`是对键名的遍历、`values()`是对键值的遍历，`entries()`是对键值对的遍历

```javascript
for (let index of ['a', 'b'].keys()) {
  console.log(index);
}
// 0
// 1

for (let elem of ['a', 'b'].values()) {
  console.log(elem);
}
// 'a'
// 'b'

for (let [index, elem] of ['a', 'b'].entries()) {
  console.log(index, elem);
}
// 0 "a"
// 1 "b"
```

也可以手动调用遍历器对象的next方法，进行遍历

```javascript
let letter = ['a', 'b', 'c'];
let entries = letter.entries();
console.log(entries.next().value); // [0, 'a']
console.log(entries.next().value); // [1, 'b']
console.log(entries.next().value); // [2, 'c']
```

### 数组实例的 includes()

`Array.prototype.includes`方法返回一个布尔值，表示某个数组是否包含给定的值，与字符串的`includes`方法类似。`ES2016` 引入了该方法

```javascript
[1, 2, 3].includes(2)     // true
[1, 2, 3].includes(4)     // false
[1, 2, NaN].includes(NaN) // true
```

该方法的第二个参数表示搜索的起始位置，默认为`0`。如果第二个参数为负数，则表示倒数的位置，如果这时它大于数组长度（比如第二个参数为-4，但数组长度为3），则会重置为从`0`开始

### 数组实例的 flat()，flatMap()

数组的成员有时还是数组，`Array.prototype.flat()`用于将嵌套的数组“拉平”，变成一维的数组。该方法返回一个新数组，对原数据没有影响。

```javascript
[1, 2, [3, 4]].flat()
// [1, 2, 3, 4]
```

`flat()`默认只会“拉平”一层，如果想要“拉平”多层的嵌套数组，可以将`flat()`方法的参数写成一个整数，表示想要拉平的层数，默认为1

```javascript
[1, 2, [3, [4, 5]]].flat()
// [1, 2, 3, [4, 5]]

[1, 2, [3, [4, 5]]].flat(2)
// [1, 2, 3, 4, 5]
```

### 数组的空位

数组的空位指，数组的某一个位置没有任何值。比如，`Array`构造函数返回的数组都是空位。

```javascript
Array(3) // [, , ,]
```

### Array.prototype.sort() 的排序稳定性

排序稳定性（stable sorting）是排序算法的重要属性，指的是排序关键字相同的项目，排序前后的顺序不变

```javascript
const arr = [
  'peach',
  'straw',
  'apple',
  'spork'
];

const stableSorting = (s1, s2) => {
  if (s1[0] < s2[0]) return -1;
  return 1;
};

arr.sort(stableSorting)
// ["apple", "peach", "straw", "spork"]
```

常见的排序算法之中，插入排序、合并排序、冒泡排序等都是稳定的，堆排序、快速排序等是不稳定的。不稳定排序的主要缺点是，多重排序时可能会产生问题, `ES2019` 明确规定，`Array.prototype.sort()`的默认排序算法必须稳定

## 对象的扩展

### 属性的简洁表示法

`ES6` 允许在大括号里面，直接写入变量和函数，作为对象的属性和方法

```javascript
const foo = 'bar';
const baz = {foo};
baz // {foo: "bar"}

// 等同于
const baz = {foo: foo};
```

除了属性简写，方法也可以简写

```javascript
const o = {
  method() {
    return "Hello!";
  }
};

// 等同于

const o = {
  method: function() {
    return "Hello!";
  }
};
```

### 属性名表达式

`JavaScript` 定义对象的属性，有两种方法

```javascript
// 方法一
obj.foo = true;

// 方法二
obj['a' + 'bc'] = 123;
```

`ES6` 允许字面量定义对象时，用方法二（表达式）作为对象的属性名，即把表达式放在方括号内。

```javascript
let propKey = 'foo';

let obj = {
  [propKey]: true,
  ['a' + 'bc']: 123
};
```

### 方法的 name 属性

函数的`name`属性，返回函数名。对象方法也是函数，因此也有`name`属性

```javascript
const person = {
  sayName() {
    console.log('hello!');
  },
};

person.sayName.name   // "sayName"
```

### 属性的可枚举性和遍历

对象的每个属性都有一个描述对象（`Descriptor`），用来控制该属性的行为。`Object.getOwnPropertyDescriptor`方法可以获取该属性的描述对象

```javascript
let obj = { foo: 123 };
Object.getOwnPropertyDescriptor(obj, 'foo')
//  {
//    value: 123,
//    writable: true,
//    enumerable: true,
//    configurable: true
//  }
```

描述对象的`enumerable`属性，称为“可枚举性”，如果该属性为`false`，就表示某些操作会忽略当前属性。

目前，有四个操作会忽略`enumerable`为`false`的属性。

- `for...in`循环：只遍历对象自身的和继承的可枚举的属性。
- `Object.keys()`：返回对象自身的所有可枚举的属性的键名。
- `JSON.stringify()`：只串行化对象自身的可枚举的属性。
- `Object.assign()`： 忽略`enumerable`为`false`的属性，只拷贝对象自身的可枚举的属性。

总的来说，操作中引入继承的属性会让问题复杂化，大多数时候，我们只关心对象自身的属性。所以，尽量不要用`for...in`循环，而用`Object.keys()`代替

`ES6` 一共有 5 种方法可以遍历对象的属性:

- `for...in`循环遍历对象自身的和继承的可枚举属性（不含 `Symbol` 属性）
- `Object.keys`返回一个数组，包括对象自身的（不含继承的）所有可枚举属性（不含 `Symbol` 属性）的键名。
- `Object.getOwnPropertyNames`返回一个数组，包含对象自身的所有属性（不含 `Symbol` 属性，但是包括不可枚举属性）的键名
- `Object.getOwnPropertySymbols`返回一个数组，包含对象自身的所有 `Symbol` 属性的键名。
- `Reflect.ownKeys`返回一个数组，包含对象自身的（不含继承的）所有键名，不管键名是 `Symbol` 或字符串，也不管是否可枚举

### super 关键字

`ES6` 新增了关键字`super`，它指向当前对象的原型对象

```javascript
const proto = {
  foo: 'hello'
};

const obj = {
  foo: 'world',
  find() {
    return super.foo;
  }
};

Object.setPrototypeOf(obj, proto);
obj.find() // "hello"
```

### 对象的扩展运算符

`ES2018` 将这个扩展运算符引入了对象

对象的解构赋值用于从一个对象取值，相当于将目标对象自身的所有可遍历的（`enumerable`）、但尚未被读取的属性，分配到指定的对象上面。所有的键和它们的值，都会拷贝到新对象上面

```javascript
let { x, y, ...z } = { x: 1, y: 2, a: 3, b: 4 };
x // 1
y // 2
z // { a: 3, b: 4 }
```

**注意: 解构赋值的拷贝是浅拷贝，即如果一个键的值是复合类型的值（数组、对象、函数）、那么解构赋值拷贝的是这个值的引用，而��是这个值的副本**

对象的扩展运算符（`...`）用于取出参数对象的所有可遍历属性，拷贝到当前对象之中。

```javascript
let z = { a: 3, b: 4 };
let n = { ...z };
n // { a: 3, b: 4 }
```

数组是特殊的对象，所以对象的扩展运算符也可以用于数组。

```javascript
let foo = { ...['a', 'b', 'c'] };
foo
// {0: "a", 1: "b", 2: "c"}
```

如果扩展运算符后面是一个空对象，则没有任何效果。

```javascript
{...{}, a: 1}
// { a: 1 }
```

如果扩展运算符后面不是对象，则会自动将其转为对象。

```javascript
// 等同于 {...Object(1)}
{...1} // {}
```


对象的扩展运算符等同于使用`Object.assign()`方法

```javascript
let aClone = { ...a };
// 等同于
let aClone = Object.assign({}, a);
```

扩展运算符可以用于合并两个对象。

```javascript
let ab = { ...a, ...b };
// 等同于
let ab = Object.assign({}, a, b);
```

与数组的扩展运算符一样，对象的扩展运算符后面可以跟表达式。

```javascript
const obj = {
  ...(x > 1 ? {a: 1} : {}),
  b: 2,
};
```

### 链判断运算符

`ES2020` 引入了“链判断运算符”（optional chaining operator）`?.`

```javascript
const firstName = message?.body?.user?.firstName || 'default';
const fooValue = myForm.querySelector('input[name=foo]')?.value
```

链判断运算符有三种用法:

- `obj?.prop` // 对象属性
- `obj?.[expr]` // 同上
- `func?.(...args)` // 函数或对象方法的调用

```javascript
// 判断对象方法是否存在，如果存在则立即执行
iterator.return?.()
```

下面是这个运算符常见的使用形式：

```javascript
a?.b
// 等同于
a == null ? undefined : a.b

a?.[x]
// 等同于
a == null ? undefined : a[x]

a?.b()
// 等同于
a == null ? undefined : a.b()

a?.()
// 等同于
a == null ? undefined : a()
```

### Null 判断运算符

`ES2020` 引入了一个新的 `Null` 判断运算符`??`。它的行为类似`||`，但是只有运算符左侧的值为`null`或`undefined`时，才会返回右侧的值

```javascript
const headerText = response.settings.headerText ?? 'Hello, world!';
const animationDuration = response.settings.animationDuration ?? 300;
const showSplashScreen = response.settings.showSplashScreen ?? true;
```

这个运算符跟链判断运算符 `?.` 配合使用，为`null`或`undefined`的值设置默认值。

```javascript
const animationDuration = response.settings?.animationDuration ?? 300;
```

## 对象的新增方法

### Object.is()

`ES6` 提出“Same-value equality”（同值相等）算法, `Object.is`就是部署这个算法的新方法。它用来比较两个值是否严格相等，与严格比较运算符（`===`）的行为基本一致

```javascript
Object.is('foo', 'foo')
// true
Object.is({}, {})
// false
```

同时它也解决了 `ES5` 中的两个问题：+0不等于-0，NaN等于自身

```javascript
// ES5
+0 === -0 //true
NaN === NaN // false

Object.is(+0, -0) // false
Object.is(NaN, NaN) // true
```

### Object.assign()

`Object.assign`方法用于对象的合并，将源对象（`source`）的所有可枚举属性，复制到目标对象（`target`）

```javascript
const target = { a: 1 };

const source1 = { b: 2 };
const source2 = { c: 3 };

Object.assign(target, source1, source2);
target // {a:1, b:2, c:3}
```

`Object.assign`方法的第一个参数是目标对象，后面的参数都是源对象

如果只有一个参数，`Object.assign`会直接返回该参数。

```javascript
const obj = {a: 1};
Object.assign(obj) === obj // true
```

如果该参数不是对象，则会先转成对象，然后返回。

```javascript
typeof Object.assign(2) // "object"
```

由于`undefined`和`null`无法转成对象，所以如果它们作为参数，就会报错。

```javascript
Object.assign(undefined) // 报错
Object.assign(null) // 报错
```

`Object.assign`拷贝的属性是有限制的，只拷贝源对象的自身属性（不拷贝继承属性），也不拷贝不可枚举的属性（`enumerable: false`）

```javascript
Object.assign({b: 'c'},
  Object.defineProperty({}, 'invisible', {
    enumerable: false,
    value: 'hello'
  })
)
// { b: 'c' }
```

注意点：

- `Object.assign`方法实行的是浅拷贝，而不是深拷贝。也就是说，如果源对象某个属性的值是对象，那么目标对象拷贝得到的是这个对象的引用

  ```javascript
  const obj1 = {a: {b: 1}};
  const obj2 = Object.assign({}, obj1);

  obj1.a.b = 2;
  obj2.a.b // 2
  ```

- 对于这种嵌套的对象，一旦遇到同名属性，`Object.assign`的处理方法是替换，而不是添加

  ```javascript
  const target = { a: { b: 'c', d: 'e' } }
  const source = { a: { b: 'hello' } }
  Object.assign(target, source)
  // { a: { b: 'hello' } }
  ```

- `Object.assign`可以用来处理数组，但是会把数组视为对象

  ```javascript
  Object.assign([1, 2, 3], [4, 5])
  // [4, 5, 3]
  ```

- `Object.assign`只能进行值的复制，如果要复制的值是一个取值函数，那么将求值后再复制

  ```javascript
  const source = {
    get foo() { return 1 }
  };
  const target = {};

  Object.assign(target, source)
  // { foo: 1 }
  ```
  
常见用途:

- 为对象添加属性

  ```javascript
  class Point {
    constructor(x, y) {
      Object.assign(this, {x, y});
    }
  }
  ```

- 为对象添加方法

  ```javascript
  Object.assign(SomeClass.prototype, {
    someMethod(arg1, arg2) {
      ···
    },
    anotherMethod() {
      ···
    }
  });

  // 等同于下面的写法
  SomeClass.prototype.someMethod = function (arg1, arg2) {
    ···
  };
  SomeClass.prototype.anotherMethod = function () {
    ···
  };
  ```

- 克隆对象

  ```javascript
  function clone(origin) {
    return Object.assign({}, origin);
  }
  ```

- 合并多个对象

  ```javascript
  const merge =
    (target, ...sources) => Object.assign(target, ...sources);
  ```

- 为属性指定默认值

  ```javascript
  const DEFAULTS = {
    logLevel: 0,
    outputFormat: 'html'
  };

  function processContent(options) {
    options = Object.assign({}, DEFAULTS, options);
    console.log(options);
    // ...
  }
  ```

### Object.getOwnPropertyDescriptors()

`ES5` 的`Object.getOwnPropertyDescriptor()`方法会返回某个对象属性的描述对象（`descriptor`）。`ES2017` 引入了`Object.getOwnPropertyDescriptors()`方法，返回指定对象所有自身属性（非继承属性）的描述对象

```javascript
const obj = {
  foo: 123,
  get bar() { return 'abc' }
};

Object.getOwnPropertyDescriptors(obj)
// { foo:
//    { value: 123,
//      writable: true,
//      enumerable: true,
//      configurable: true },
//   bar:
//    { get: [Function: get bar],
//      set: undefined,
//      enumerable: true,
//      configurable: true } }
```

该方法的引入目的，主要是为了解决`Object.assign()`无法正确拷贝`get`属性和`set`属性的问题

### __proto__属性，Object.setPrototypeOf()，Object.getPrototypeOf()

`JavaScript` 语言的对象继承是通过原型链实现的。`ES6` 提供了更多原型对象的操作方法

#### __proto__属性

`__proto__`属性（前后各两个下划线），用来读取或设置当前对象的原型对象（`prototype`）。目前，所有浏览器（包括 IE11）都部署了这个属性

```javascript
// es5 的写法
const obj = {
  method: function() { ... }
};
obj.__proto__ = someOtherObj;

// es6 的写法
var obj = Object.create(someOtherObj);
obj.method = function() { ... };
```

虽然 `__proto__` 属性已成为 `ES6` 的标准，但无论从语义的角度，还是从兼容性的角度，都不要使用这个属性，而是使用以下API：

- `Object.setPrototypeOf()`（写操作）
- `Object.getPrototypeOf()`（读操作）
- `Object.create()`（生成操作）

#### Object.setPrototypeOf()

`Object.setPrototypeOf()`方法的作用与`__proto__`相同，用来设置一个对象的原型对象（`prototype`），返回参数对象本身。它是 `ES6` 正式推荐的设置原型对象的方法。

```javascript
// 格式
Object.setPrototypeOf(object, prototype)

// 用法
const o = Object.setPrototypeOf({}, null);
```

例子：

```javascript
let proto = {};
let obj = { x: 10 };
Object.setPrototypeOf(obj, proto);

proto.y = 20;
proto.z = 40;

obj.x // 10
obj.y // 20
obj.z // 40
```

#### Object.getPrototypeOf()

该方法与`Object.setPrototypeOf`方法配套，用于读取一个对象的原型对象

```javascript
function Rectangle() {
  // ...
}

const rec = new Rectangle();

Object.getPrototypeOf(rec) === Rectangle.prototype
// true

Object.setPrototypeOf(rec, Object.prototype);
Object.getPrototypeOf(rec) === Rectangle.prototype
// false
```

### Object.keys()，Object.values()，Object.entries()

#### Object.keys()

`ES5` 引入了`Object.keys`方法，返回一个数组，成员是参数对象自身的（不含继承的）所有可遍历（`enumerable`）属性的键名

```javascript
var obj = { foo: 'bar', baz: 42 };
Object.keys(obj)
// ["foo", "baz"]
```

`ES2017` 引入了跟`Object.keys`配套的`Object.values`和`Object.entries`，作为遍历一个对象的补充手段，供`for...of`循环使用

```javascript
let {keys, values, entries} = Object;
let obj = { a: 1, b: 2, c: 3 };

for (let key of keys(obj)) {
  console.log(key); // 'a', 'b', 'c'
}

for (let value of values(obj)) {
  console.log(value); // 1, 2, 3
}

for (let [key, value] of entries(obj)) {
  console.log([key, value]); // ['a', 1], ['b', 2], ['c', 3]
}
```

#### Object.values()

`Object.values`方法返回一个数组，成员是参数对象自身的（不含继承的）所有可遍历（`enumerable`）属性的键值

```javascript
const obj = { foo: 'bar', baz: 42 };
Object.values(obj)
// ["bar", 42]
```

`Object.values`只返回对象自身的可遍历属性。

```javascript
const obj = Object.create({}, {p: {value: 42}});
Object.values(obj) // []
```

#### Object.entries()

`Object.entries()`方法返回一个数组，成员是参数对象自身的（不含继承的）所有可遍历（`enumerable`）属性的键值对数组。

```javascript
const obj = { foo: 'bar', baz: 42 };
Object.entries(obj)
// [ ["foo", "bar"], ["baz", 42] ]
```

`Object.entries`的基本用途是遍历对象的属性

```javascript
let obj = { one: 1, two: 2 };
for (let [k, v] of Object.entries(obj)) {
  console.log(
    `${JSON.stringify(k)}: ${JSON.stringify(v)}`
  );
}
// "one": 1
// "two": 2
```

`Object.entries`方法的另一个用处是，将对象转为真正的`Map`结构。

```javascript
const obj = { foo: 'bar', baz: 42 };
const map = new Map(Object.entries(obj));
map // Map { foo: "bar", baz: 42 }
```

### Object.fromEntries()

`Object.fromEntries()`方法是`Object.entries()`的逆操作，用于将一个键值对数组转为对象。

```javascript
Object.fromEntries([
  ['foo', 'bar'],
  ['baz', 42]
])
// { foo: "bar", baz: 42 }
```

## Symbol

`ES6` 引入`Symbol`, 是为了解决对象属性可能会重复的问题

`ES6` 引入了一种新的原始数据类型`Symbol`，表示独一无二的值。它是 `JavaScript` 语言的第七种数据类型，前六种是：`undefined`、`null`、布尔值（`Boolean`）、字符串（`String`）、数值（`Number`）、对象（`Object`）。

`Symbol` 值通过`Symbol`函数生成。这就是说，对象的属性名现在可以有两种类型，一种是原来就有的字符串，另一种就是新增的 `Symbol` 类型

```javascript
let s = Symbol();

typeof s
// "symbol"
```

`Symbol`函数前不能使用`new`命令，否则会报错

`Symbol`函数可以接受一个字符串作为参数，表示对 `Symbol` 实例的描述，主要是为了在控制台显示，或者转为字符串时，比较容易区分

```javascript
let s1 = Symbol('foo');
let s2 = Symbol('bar');

s1 // Symbol(foo)
s2 // Symbol(bar)

s1.toString() // "Symbol(foo)"
s2.toString() // "Symbol(bar)"
```

### Symbol.prototype.description

创建 `Symbol` 的时候，可以添加一个描述。

```js
const sym = Symbol('foo');
```

`ES2019` 提供了一个实例属性`description`，直接返回 `Symbol` 的描述。

```js
const sym = Symbol('foo');

sym.description // "foo"
```

### 作为属性名的 Symbol

由于每一个 `Symbol` 值都是不相等的，这意味着 `Symbol` 值可以作为标识符，用于对象的属性名，就能保证不会出现同名的属性

```js
let mySymbol = Symbol();

// 第一种写法
let a = {};
a[mySymbol] = 'Hello!';

// 第二种写法
let a = {
  [mySymbol]: 'Hello!'
};

// 第三种写法
let a = {};
Object.defineProperty(a, mySymbol, { value: 'Hello!' });

// 以上写法都得到同样结果
a[mySymbol] // "Hello!"
```

`Symbol` 类型还可以用于定义一组常量，保证这组常量的值都是不相等的

```js
const log = {};

log.levels = {
  DEBUG: Symbol('debug'),
  INFO: Symbol('info'),
  WARN: Symbol('warn')
};
console.log(log.levels.DEBUG, 'debug message');
console.log(log.levels.INFO, 'info message');
```

### 消除魔术字符串

魔术字符串指的是，在代码之中多次出现、与代码形成强耦合的某一个具体的字符串或者数值。风格良好的代码，应该尽量消除魔术字符串，改由含义清晰的变量代替, 常用的消除魔术字符串的方法，就是把它写成一个变量

```js
const shapeType = {
  triangle: 'Triangle'
};

function getArea(shape, options) {
  let area = 0;
  switch (shape) {
    case shapeType.triangle:
      area = .5 * options.width * options.height;
      break;
  }
  return area;
}

getArea(shapeType.triangle, { width: 100, height: 100 });
```

### 属性名的遍历

`Symbol` 作为属性名，遍历对象的时候，该属性不会出现在`for...in`、`for...of`循环中，也不会被`Object.keys()`、`Object.getOwnPropertyNames()`、`JSON.stringify()`返回

`Object.getOwnPropertySymbols()`方法，可以获取指定对象的所有 `Symbol` 属性名。该方法返回一个数组，成员是当前对象的所有用作属性名的 `Symbol` 值

```js
const obj = {};
let a = Symbol('a');
let b = Symbol('b');

obj[a] = 'Hello';
obj[b] = 'World';

const objectSymbols = Object.getOwnPropertySymbols(obj);

objectSymbols
// [Symbol(a), Symbol(b)]
```

使用`for...in`循环和`Object.getOwnPropertyNames()`方法都得不到 `Symbol` 键名，需要使用`Object.getOwnPropertySymbols()`方法

另一个新的 API，`Reflect.ownKeys()`方法可以返回所有类型的键名，包括常规键名和 `Symbol` 键名

```js
let obj = {
  [Symbol('my_key')]: 1,
  enum: 2,
  nonEnum: 3
};

Reflect.ownKeys(obj)
//  ["enum", "nonEnum", Symbol(my_key)]
```

### Symbol.for()，Symbol.keyFor()

`Symbol.for()`方法接受一个字符串作为参数，然后搜索有没有以该参数作为名称的 `Symbol` 值。如果有，就返回这个 `Symbol` 值，否则就新建一个以该字符串为名称的 `Symbol` 值，并将其注册到全局。

```js
let s1 = Symbol.for('foo');
let s2 = Symbol.for('foo');

s1 === s2 // true
```

`Symbol.for()`与`Symbol()`这两种写法，都会生成新的 `Symbol`。它们的区别是，前者会被登记在全局环境中供搜索，后者不会

`Symbol.keyFor()`方法返回一个已登记的 `Symbol` 类型值的`key`

```js
let s1 = Symbol.for("foo");
Symbol.keyFor(s1) // "foo"

let s2 = Symbol("foo");
Symbol.keyFor(s2) // undefined
```

### 模块的 Singleton 模式

`Singleton` 模式指的是调用一个类，任何时候返回的都是同一个实例

在 `Nodejs` 中实现 `Singleton` 模式，只需要把实例放到顶层对象 `Global` 里就可以了，但问题是这个放在顶层对象中的实例可以被修改，此时可以通过 `Symbol` 来实现

### 内置的 Symbol 值

`ES6` 还提供了 11 个内置的 `Symbol` 值，指向语言内部使用的方法

#### Symbol.hasInstance

对象的`Symbol.hasInstance`属性，指向一个内部方法。当其他对象使用`instanceof`运算符，判断是否为该对象的实例时，会调用这个方法

```js
class MyClass {
  [Symbol.hasInstance](foo) {
    return foo instanceof Array;
  }
}

[1, 2, 3] instanceof new MyClass() // true
```

#### Symbol.isConcatSpreadable

对象的`Symbol.isConcatSpreadable`属性等于一个布尔值，表示该对象用于`Array.prototype.concat()`时，是否可以展开

```js
let arr1 = ['c', 'd'];
['a', 'b'].concat(arr1, 'e') // ['a', 'b', 'c', 'd', 'e']
arr1[Symbol.isConcatSpreadable] // undefined

let arr2 = ['c', 'd'];
arr2[Symbol.isConcatSpreadable] = false;
['a', 'b'].concat(arr2, 'e') // ['a', 'b', ['c','d'], 'e']
```

#### Symbol.species

对象的`Symbol.species`属性，指向一个构造函数。创建衍生对象时，会使用该属性

```js
class MyArray extends Array {
}

const a = new MyArray(1, 2, 3);
const b = a.map(x => x);
const c = a.filter(x => x > 1);

b instanceof MyArray // true
c instanceof MyArray // true
```

```js
class MyArray extends Array {
  static get [Symbol.species]() { return Array; }
}
```

上面代码中，由于定义了`Symbol.species`属性，创建衍生对象时就会使用这个属性返回的函数，作为构造函数

#### Symbol.match

对象的`Symbol.match`属性，指向一个函数。当执行`str.match(myObject)`时，如果该属性存在，会调用它，返回该方法的返回值

```js
String.prototype.match(regexp)
// 等同于
regexp[Symbol.match](this)

class MyMatcher {
  [Symbol.match](string) {
    return 'hello world'.indexOf(string);
  }
}

'e'.match(new MyMatcher()) // 1
```

#### Symbol.replace

对象的`Symbol.replace`属性，指向一个方法，当该对象被`String.prototype.replace`方法调用时，会返回该方法的返回值。

```js
String.prototype.replace(searchValue, replaceValue)
// 等同于
searchValue[Symbol.replace](this, replaceValue)
```

#### Symbol.search

对象的`Symbol.search`属性，指向一个方法，当该对象被`String.prototype.search`方法调用时，会返回该方法的返回值。

```js
String.prototype.search(regexp)
// 等同于
regexp[Symbol.search](this)

class MySearch {
  constructor(value) {
    this.value = value;
  }
  [Symbol.search](string) {
    return string.indexOf(this.value);
  }
}
'foobar'.search(new MySearch('foo')) // 0
```

#### Symbol.split

对象的`Symbol.split`属性，指向一个方法，当该对象被`String.prototype.split`方法调用时，会返回该方法的返回值。

```js
String.prototype.split(separator, limit)
// 等同于
separator[Symbol.split](this, limit)
```

#### Symbol.iterator

对象的`Symbol.iterator`属性，指向该对象的默认遍历器方法

```js
const myIterable = {};
myIterable[Symbol.iterator] = function* () {
  yield 1;
  yield 2;
  yield 3;
};

[...myIterable] // [1, 2, 3]
```

#### Symbol.toPrimitive

对象的`Symbol.toPrimitive`属性，指向一个方法。该对象被转为原始类型的值时，会调用这个方法，返回该对象对应的原始类型值

`Symbol.toPrimitive`被调用时，会接受一个字符串参数，表示当前运算的模式，一共有三种模式。

- `Number`：该场合需要转成数值
- `String`：该场合需要转成字符串
- `Default`：该场合可以转成数值，也可以转成字符串

```js
let obj = {
  [Symbol.toPrimitive](hint) {
    switch (hint) {
      case 'number':
        return 123;
      case 'string':
        return 'str';
      case 'default':
        return 'default';
      default:
        throw new Error();
     }
   }
};

2 * obj // 246
3 + obj // '3default'
obj == 'default' // true
String(obj) // 'str'
```

#### Symbol.toStringTag

对象的`Symbol.toStringTag`属性，指向一个方法。在该对象上面调用`Object.prototype.toString`方法时，如果这个属性存在，它的返回值会出现在`toString`方法返回的字符串之中，表示对象的类型

#### Symbol.unscopables

对象的`Symbol.unscopables`属性，指向一个对象。该对象指定了使用`with`关键字时，哪些属性会被`with`环境排除

## Set和Map数据结构

### Set

#### 基本用法

`ES6` 提供了新的数据结构 `Set`。它类似于数组，但是成员的值都是唯一的，没有重复的值。

`Set`本身是一个构造函数，用来生成 `Set` 数据结构

```js
const s = new Set();

[2, 3, 5, 4, 5, 2, 2].forEach(x => s.add(x));

for (let i of s) {
  console.log(i);
}
// 2 3 5 4
```

`Set`函数可以接受一个数组（或者具有 `iterable` 接口的其他数据结构）作为参数，用来初始化。

```js
// 例一
const set = new Set([1, 2, 3, 4, 4]);
[...set]
// [1, 2, 3, 4]

// 例二
const items = new Set([1, 2, 3, 4, 5, 5, 5, 5]);
items.size // 5

// 例三
const set = new Set(document.querySelectorAll('div'));
set.size // 56

// 类似于
const set = new Set();
document
 .querySelectorAll('div')
 .forEach(div => set.add(div));
set.size // 56
```

`Set`也成为一种去除数组重复成员的方法

```js
// 去除数组的重复成员
[...new Set(array)]
```

也可以用于去除字符串里面的重复字符

```js
[...new Set('ababbc')].join('')
// "abc"
```

#### Set 实例的属性和方法

`Set` 结构的实例有以下属性:

- `Set.prototype.constructor`：构造函数，默认就是`Set`函数。
- `Set.prototype.size`：返回`Set`实例的成员总数。

`Set` 实例的方法分为两大类：操作方法（用于操作数据）和遍历方法（用于遍历成员）。下面先介绍四个操作方法。

- `Set.prototype.add(value)`：添加某个值，返回 `Set` 结构本身。
- `Set.prototype.delete(value)`：删除某个值，返回一个布尔值，表示删除是否成功。
- `Set.prototype.has(value)`：返回一个布尔值，表示该值是否为`Set`的成员。
- `Set.prototype.clear()`：清除所有成员，没有返回值

```js
s.add(1).add(2).add(2);
// 注意2被加入了两次

s.size // 2

s.has(1) // true
s.has(2) // true
s.has(3) // false

s.delete(2);
s.has(2) // false
```

`Array.from`方法可以将 `Set` 结构转为数组

```js
const items = new Set([1, 2, 3, 4, 5]);
const array = Array.from(items);
```

#### 遍历操作

`Set` 结构的实例有四个遍历方法，可以用于遍历成员。

- `Set.prototype.keys()`：返回键名的遍历器
- `Set.prototype.values()`：返回键值的遍历器
- `Set.prototype.entries()`：返回键值对的遍历器
- `Set.prototype.forEach()`：使用回调函数遍历每个成员

`keys`方法、`values`方法、`entries`方法返回的都是遍历器对象

```js
let set = new Set(['red', 'green', 'blue']);

for (let item of set.keys()) {
  console.log(item);
}
// red
// green
// blue

for (let item of set.values()) {
  console.log(item);
}
// red
// green
// blue

for (let item of set.entries()) {
  console.log(item);
}
// ["red", "red"]
// ["green", "green"]
// ["blue", "blue"]
```

`Set` 结构可以直接用`for...of`循环遍历

```js
let set = new Set(['red', 'green', 'blue']);

for (let x of set) {
  console.log(x);
}
// red
// green
// blue
```

`Set` 结构的实例与数组一样，也拥有`forEach`方法，用于对每个成员执行某种操作，没有返回值

```js
let set = new Set([1, 4, 9]);
set.forEach((value, key) => console.log(key + ' : ' + value))
// 1 : 1
// 4 : 4
// 9 : 9
```

扩展运算符（`...`）内部使用`for...of`循环，所以也可以用于 `Set` 结构

```js
let set = new Set(['red', 'green', 'blue']);
let arr = [...set];
// ['red', 'green', 'blue']
```

扩展运算符和 `Set` 结构相结合，就可以去除数组的重复成员。

```js
let arr = [3, 5, 2, 2, 5, 5];
let unique = [...new Set(arr)];
// [3, 5, 2]
```

数组的`map`和`filter`方法也可以间接用于 `Set `

```js
let set = new Set([1, 2, 3]);
set = new Set([...set].map(x => x * 2));
// 返回Set结构：{2, 4, 6}

let set = new Set([1, 2, 3, 4, 5]);
set = new Set([...set].filter(x => (x % 2) == 0));
// 返回Set结构：{2, 4}
```

使用 `Set` 可以很容易地实现并集（`Union`）、交集（`Intersect`）和差集（`Difference`）

```js
let a = new Set([1, 2, 3]);
let b = new Set([4, 3, 2]);

// 并集
let union = new Set([...a, ...b]);
// Set {1, 2, 3, 4}

// 交集
let intersect = new Set([...a].filter(x => b.has(x)));
// set {2, 3}

// （a 相对于 b 的）差集
let difference = new Set([...a].filter(x => !b.has(x)));
// Set {1}
```

### WeakSet

#### 含义

`WeakSet` 的成员只能是对象，而不能是其他类型的值

```js
const ws = new WeakSet();
ws.add(1)
// TypeError: Invalid value used in weak set
ws.add(Symbol())
// TypeError: invalid value used in weak set
```

`WeakSet` 中的对象都是弱引用，即垃圾回收机制不考虑 `WeakSet` 对该对象的引用，也就是说，如果其他对象都不再引用该对象，那么垃圾回收机制会自动回收该对象所占用的内存，不考虑该对象还存在于 `WeakSet` 之中

`ES6` 规定 `WeakSet` 不可遍历

#### 语法

`WeakSet` 是一个构造函数，可以使用`new`命令，创建 `WeakSet` 数据结构

```js
const ws = new WeakSet();
```

作为构造函数，`WeakSet` 可以接受一个数组或类似数组的对象作为参数, 该数组的所有成员，都会自动成为 `WeakSet` 实例对象的成员。

```js
const a = [[1, 2], [3, 4]];
const ws = new WeakSet(a);
// WeakSet {[1, 2], [3, 4]}
```

`WeakSet` 结构有以下三个方法:

- `WeakSet.prototype.add(value)`：向 `WeakSet` 实例添加一个新成员。
- `WeakSet.prototype.delete(value)`：清除 `WeakSet` 实例的指定成员。
- `WeakSet.prototype.has(value)`：返回一个布尔值，表示某个值是否在 `WeakSet` 实例之中。

```js
const ws = new WeakSet();
const obj = {};
const foo = {};

ws.add(window);
ws.add(obj);

ws.has(window); // true
ws.has(foo);    // false

ws.delete(window);
ws.has(window);    // false
```

`WeakSet` 没有`size`属性，没有办法遍历它的成员

`WeakSet` 的一个用处，是储存 `DOM` 节点，而不用担心这些节点从文档移除时，会引发内存泄漏

### Map

#### 含义和基本用法

`JavaScript` 的对象（`Object`），本质上是键值对的集合（`Hash` 结构），但是传统上只能用字符串当作键

`ES6` 提供了 `Map` 数据结构。它类似于对象，也是键值对的集合，但是“键”的范围不限于字符串，各种类型的值（包括对象）都可以当作键

```js
const m = new Map();
const o = {p: 'Hello World'};

m.set(o, 'content')
m.get(o) // "content"

m.has(o) // true
m.delete(o) // true
m.has(o) // false
```

作为构造函数，`Map` 也可以接受一个数组作为参数。该数组的成员是一个个表示键值对的数组

```js
const map = new Map([
  ['name', '张三'],
  ['title', 'Author']
]);

map.size // 2
map.has('name') // true
map.get('name') // "张三"
map.has('title') // true
map.get('title') // "Author"
```

不仅仅是数组，任何具有 `Iterator` 接口、且每个成员都是一个双元素的数组的数据结构都可以当作`Map`构造函数的参数

```js
const set = new Set([
  ['foo', 1],
  ['bar', 2]
]);
const m1 = new Map(set);
m1.get('foo') // 1

const m2 = new Map([['baz', 3]]);
const m3 = new Map(m2);
m3.get('baz') // 3
```

#### 实例的属性和操作方法

- `size`属性返回 `Map` 结构的成员总数

  ```js
  const map = new Map();
  map.set('foo', true);
  map.set('bar', false);

  map.size // 2
  ```

- `Map.prototype.set(key, value)`, `set`方法设置键名`key`对应的键值为`value`，然后返回整个 `Map` 结构。如果`key`已经有值，则键值会被更新，否则就新生成该键

  ```js
  const m = new Map();

  m.set('edition', 6)        // 键是字符串
  m.set(262, 'standard')     // 键是数值
  m.set(undefined, 'nah')    // 键是 undefined
  ```

- `Map.prototype.get(key)`, `get`方法读取`key`对应的键值，如果找不到`key`，返回`undefined`

  ```js
  const m = new Map();

  const hello = function() {console.log('hello');};
  m.set(hello, 'Hello ES6!') // 键是函数

  m.get(hello)  // Hello ES6!
  ```

- `Map.prototype.has(key)`, `has`方法返回一个布尔值，表示某个键是否在当前 `Map` 对象之中。

  ```js
  const m = new Map();

  m.set('edition', 6);
  m.set(262, 'standard');
  m.set(undefined, 'nah');

  m.has('edition')     // true
  m.has('years')       // false
  m.has(262)           // true
  m.has(undefined)     // true
  ```

- `Map.prototype.delete(key)`, `delete`方法删除某个键，返回`true`。如果删除失败，返回`false`。

  ```js
  const m = new Map();
  m.set(undefined, 'nah');
  m.has(undefined)     // true

  m.delete(undefined)
  m.has(undefined)       // false
  ```

- `Map.prototype.clear()`, `clear`方法清除所有成员，没有返回值。

  ```js
  let map = new Map();
  map.set('foo', true);
  map.set('bar', false);

  map.size // 2
  map.clear()
  map.size // 0
  ```

#### 遍历方法

`Map` 结构原生提供三个遍历器生成函数和一个遍历方法。

- `Map.prototype.keys()`：返回键名的遍历器。
- `Map.prototype.values()`：返回键值的遍历器。
- `Map.prototype.entries()`：返回所有成员的遍历器。
- `Map.prototype.forEach()`：遍历 `Map` 的所有成员。

```js
const map = new Map([
  ['F', 'no'],
  ['T',  'yes'],
]);

for (let key of map.keys()) {
  console.log(key);
}
// "F"
// "T"

for (let value of map.values()) {
  console.log(value);
}
// "no"
// "yes"

for (let item of map.entries()) {
  console.log(item[0], item[1]);
}
// "F" "no"
// "T" "yes"

// 或者
for (let [key, value] of map.entries()) {
  console.log(key, value);
}
// "F" "no"
// "T" "yes"

// 等同于使用map.entries()
for (let [key, value] of map) {
  console.log(key, value);
}
// "F" "no"
// "T" "yes"
```

`Map` 结构转为数组结构，比较快速的方法是使用扩展运算符（`...`）。

```js
const map = new Map([
  [1, 'one'],
  [2, 'two'],
  [3, 'three'],
]);

[...map.keys()]
// [1, 2, 3]

[...map.values()]
// ['one', 'two', 'three']

[...map.entries()]
// [[1,'one'], [2, 'two'], [3, 'three']]

[...map]
// [[1,'one'], [2, 'two'], [3, 'three']]
```

结合数组的`map`方法、`filter`方法，可以实现 `Map` 的遍历和过滤

```js
const map0 = new Map()
  .set(1, 'a')
  .set(2, 'b')
  .set(3, 'c');

const map1 = new Map(
  [...map0].filter(([k, v]) => k < 3)
);
// 产生 Map 结构 {1 => 'a', 2 => 'b'}

const map2 = new Map(
  [...map0].map(([k, v]) => [k * 2, '_' + v])
    );
// 产生 Map 结构 {2 => '_a', 4 => '_b', 6 => '_c'}
```

#### 与其他数据结构的互相转换

- `Map` 转为数组, `Map` 转为数组最方便的方法，就是使用扩展运算符（`...`）。

  ```js
  const myMap = new Map()
    .set(true, 7)
    .set({foo: 3}, ['abc']);
  [...myMap]
  // [ [ true, 7 ], [ { foo: 3 }, [ 'abc' ] ] ]
  ```

- 数组 转为 `Map`, 将数组传入 `Map` 构造函数，就可以转为 `Map`。

  ```js
  new Map([
    [true, 7],
    [{foo: 3}, ['abc']]
  ])
  // Map {
  //   true => 7,
  //   Object {foo: 3} => ['abc']
  // }
  ```

- `Map` 转为对象, 如果所有 `Map` 的键都是字符串，它可以无损地转为对象。

  ```js
  function strMapToObj(strMap) {
    let obj = Object.create(null);
    for (let [k,v] of strMap) {
      obj[k] = v;
    }
    return obj;
  }

  const myMap = new Map()
    .set('yes', true)
    .set('no', false);
  strMapToObj(myMap)
  // { yes: true, no: false }
  ```

- 对象转为 `Map`, 对象转为 `Map` 可以通过`Object.entries()`。

  ```js
  let obj = {"a":1, "b":2};
  let map = new Map(Object.entries(obj));
  ```

- `Map` 转为 `JSON`
  
  `Map` 转为 `JSON` 要区分两种情况。一种情况是，`Map` 的键名都是字符串，这时可以选择转为对象 `JSON`。

  ```js
  function strMapToJson(strMap) {
    return JSON.stringify(strMapToObj(strMap));
  }

  let myMap = new Map().set('yes', true).set('no', false);
  strMapToJson(myMap)
  // '{"yes":true,"no":false}'
  ```

  另一种情况是，`Map` 的键名有非字符串，这时可以选择转为数组 `JSON`。

  ```js
  function mapToArrayJson(map) {
    return JSON.stringify([...map]);
  }

  let myMap = new Map().set(true, 7).set({foo: 3}, ['abc']);
  mapToArrayJson(myMap)
  // '[[true,7],[{"foo":3},["abc"]]]'
  ```

- `JSON` 转为 `Map`

  `JSON` 转为 `Map`，正常情况下，所有键名都是字符串。

  ```js
  function jsonToStrMap(jsonStr) {
    return objToStrMap(JSON.parse(jsonStr));
  }

  jsonToStrMap('{"yes": true, "no": false}')
  // Map {'yes' => true, 'no' => false}
  ```

### WeakMap

#### 含义

`WeakMap`结构与`Map`结构类似，也是用于生成键值对的集合。

```js
// WeakMap 可以使用 set 方法添加成员
const wm1 = new WeakMap();
const key = {foo: 1};
wm1.set(key, 2);
wm1.get(key) // 2

// WeakMap 也可以接受一个数组，
// 作为构造函数的参数
const k1 = [1, 2, 3];
const k2 = [4, 5, 6];
const wm2 = new WeakMap([[k1, 'foo'], [k2, 'bar']]);
wm2.get(k2) // "bar"
```

`WeakMap`与`Map`的区别有两点:

- `WeakMap`只接受对象作为键名（`null`除外），不接受其他类型的值作为键名。

  ```js
  const map = new WeakMap();
  map.set(1, 2)
  // TypeError: 1 is not an object!
  map.set(Symbol(), 2)
  // TypeError: Invalid value used as weak map key
  map.set(null, 2)
  // TypeError: Invalid value used as weak map key
  ```

- `WeakMap`的键名所指向的对象，不计入垃圾回收机制

`WeakMap` 键名所引用的对象都是弱引用，即垃圾回收机制不将该引用考虑在内。因此，只要所引用的对象的其他引用都被清除，垃圾回收机制就会释放该对象所占用的内存

基本上，如果你要往对象上添加数据，又不想干扰垃圾回收机制，就可以使用 `WeakMap`。一个典型应用场景是，在网页的 `DOM` 元素上添加数据，就可以使用`WeakMap`结构。当该 `DOM` 元素被清除，其所对应的`WeakMap`记录就会自动被移除。

```js
const wm = new WeakMap();

const element = document.getElementById('example');

wm.set(element, 'some information');
wm.get(element) // "some information"
```

注意，`WeakMap` 弱引用的只是键名，而不是键值。键值依然是正常引用。

```js
const wm = new WeakMap();
let key = {};
let obj = {foo: 1};

wm.set(key, obj);
obj = null;
wm.get(key)
// Object {foo: 1}
```

#### WeakMap 的语法

`WeakMap` 与 `Map` 在 `API` 上的区别主要是两个，一是没有遍历操作（即没有`keys()`、`values()`和`entries()`方法），也没有`size`属性, 无法清空，即不支持`clear`方法

`WeakMap`只有四个方法可用：`get()`、`set()`、`has()`、`delete()`

```js
const wm = new WeakMap();

// size、forEach、clear 方法都不存在
wm.size // undefined
wm.forEach // undefined
wm.clear // undefined
```

## Proxy

### 概述

`Proxy` 用于修改某些操作的默认行为，等同于在语言层面做出修改，所以属于一种“元编程”（meta programming），即对编程语言进行编程。

`Proxy` 可以理解成，在目标对象之前架设一层“拦截”，外界对该对象的访问，都必须先通过这层拦截，因此提供了一种机制，可以对外界的访问进行过滤和改写.

```js
var obj = new Proxy({}, {
  get: function (target, propKey, receiver) {
    console.log(`getting ${propKey}!`);
    return Reflect.get(target, propKey, receiver);
  },
  set: function (target, propKey, value, receiver) {
    console.log(`setting ${propKey}!`);
    return Reflect.set(target, propKey, value, receiver);
  }
});
```

`ES6` 原生提供 `Proxy` 构造函数，用来生成 `Proxy` 实例。

```js
var proxy = new Proxy(target, handler);
```

`Proxy` 支持的拦截操作一览，一共 13 种。

- `get(target, propKey, receiver)`：拦截对象属性的读取，比如`proxy.foo`和`proxy['foo']`。
- `set(target, propKey, value, receiver)`：拦截对象属性的设置，比如`proxy.foo = v`或`proxy['foo'] = v`，返回一个布尔值。
- `has(target, propKey)`：拦截`propKey in proxy`的操作，返回一个布尔值。
- `deleteProperty(target, propKey)`：拦截d`elete proxy[propKey]`的操作，返回一个布尔值。
- `ownKeys(target)`：拦截`Object.getOwnPropertyNames(proxy)`、`Object.getOwnPropertySymbols(proxy)`、Object.keys(proxy)、for...in循环，返回一个数组。该方法返回目标对象所有自身的属性的属性名，而`Object.keys()`的返回结果仅包括目标对象自身的可遍历属性。
- `getOwnPropertyDescriptor(target, propKey)`：拦截`Object.getOwnPropertyDescriptor(proxy, propKey)`，返回属性的描述对象。
- `defineProperty(target, propKey, propDesc)`：拦截`Object.defineProperty(proxy, propKey, propDesc）`、`Object.defineProperties(proxy, propDescs)`，返回一个布尔值。
- `preventExtensions(target)`：拦截`Object.preventExtensions(proxy)`，返回一个布尔值。
- `getPrototypeOf(target)`：拦截`Object.getPrototypeOf(proxy)`，返回一个对象。
- `isExtensible(target)`：拦截`Object.isExtensible(proxy)`，返回一个布尔值。
- `setPrototypeOf(target, proto)`：拦截`Object.setPrototypeOf(proxy, proto)`，返回一个布尔值。如果目标对象是函数，那么还有两种额外操作可以拦截。
- `apply(target, object, args)`：拦截 `Proxy` 实例作为函数调用的操作，比如`proxy(...args)`、`proxy.call(object, ...args)`、`proxy.apply(...)`。
- `construct(target, args)`：拦截 `Proxy` 实例作为构造函数调用的操作，比如`new proxy(...args)`

### Proxy 实例的方法

#### get()

`get`方法用于拦截某个属性的读取操作，可以接受三个参数，依次为目标对象、属性名和 `proxy` 实例本身（严格地说，是操作行为所针对的对象），其中最后一个参数可选。

```js
var person = {
  name: "张三"
};

var proxy = new Proxy(person, {
  get: function(target, propKey) {
    if (propKey in target) {
      return target[propKey];
    } else {
      throw new ReferenceError("Prop name \"" + propKey + "\" does not exist.");
    }
  }
});

proxy.name // "张三"
proxy.age // 抛出一个错误
```





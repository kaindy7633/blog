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
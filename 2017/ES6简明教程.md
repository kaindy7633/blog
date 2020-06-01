# ES6简明教程

## 目录

- <a href="#let">let和const</a>
- <a href="#字符串的扩展">字符串的扩展</a>
- <a href="#正则的扩展">正则的扩展</a>
- <a href="#函数的扩展">函数的扩展</a>
- <a href="#数组的扩展">数组的扩展</a>
- <a href="#对象的扩展">对象的扩展</a>
- <a href="#Symbol">Symbol</a>
- <a href="#Set和Map数据结构">Set和Map数据结构</a>
- <a href="#Promise对象">Promise对象</a>
- <a href="#Iterator和for...of循环">Iterator和for...of循环</a>
- <a href="#Generator函数">Generator函数</a>
- <a href="#Generator的异步应用">Generator的异步应用</a>
- <a href="#async函数">async函数</a>
- <a href="#Class">Class</a>
- <a href="#Class继承">Class继承</a>
- <a href="#修饰器">修饰器</a>
- <a href="#Module语法">Module语法</a>
- <a href="#编程风格">编程风格</a>
- <a href="#ArrayBuffer">ArrayBuffer</a>

<h2 id="let">let和const命令</h2>

### let

ES6新增了`let`命令，用于声明变量。`let`声明的变量只在其所在代码块内有效。

ES6之前我们使用`var`定义变量会存在变量提升，值为`undefined`,`let`改变了这种行为，使用`let`定义变量不存在提升问题。

`let`不允许在相同作用域内重复声明同一个变量，否则会报错。

ES5只有全局作用域和函数作用域，ES6的`let`实际上为JavaScript增加了块级作用域，且允许块级作用域任意嵌套。

### const

`const`用于声明一个只读常量，一旦声明，常量的值就不能改变，且声明时必须立即初始化。

`const`声明的常量同样只在所在的块级作用域中有效，且也不存在提升，只能在声明后使用。

## 变量的解构赋值

### 数组的解构赋值

ES6允许按照一定模式从数组和对象中提取值，然后对变量进行赋值，这被称为解构。

```js
let [a, b, c] = [1, 2, 3]
a   // 1
b   // 2
c   // 3
```

同时，解构赋值允许指定默认值

```js
let [foo = true] = []
foo  // true
```

### 对象的解构赋值

对象的解构赋值与数组有一个不同点，数组的元素是按次序排列，变量的取值由他的位置决定，而对象的属性没有次序，变量必须与属性同名才能取到正确的值。

```js
let { bar, foo } = { foo: 'aaa', bar: 'bbb' }
foo  // aaa
bar  // bbb
```

### 字符串的解构赋值

字符串也可以解构赋值

```js
const [a, b, c, d, e] = 'hello'
a  // h
b  // e
c  // l
d  // l
e  // o
```

### 结构赋值的用途

交换变量的值

```js
let x = 1
let y = 2
[x, y] = [y, x]
```

从函数返回多个值

```js
// 返回一个数组
function example () {
  return [1, 2, 3]
}
let [a, b, c] = example()

// 返回一个对象
function example () {
  return { foo: 1, bar: 2 }
}
let { foo, bar } = example()
```

函数参数的定义

```js
function f ([x, y, z]) { // ... }
f([1, 2, 3])

function f({ x, y, z }) {}
f({z: 3, y: 2, x: 1})
```

<h2 id="字符串的扩展">字符串的扩展</h2>

### 字符的Unicode表示

ES6加强了对`Unicode`的支持，并扩展了字符串对象。

JavaScript允许使用`\uxxxx`的形式表示一个字符，其中`xxxx`表示字符的`Unicode`码点，但这个码点只限于`\u0000` ~ `\uFFFF`之间的字符，超出就不能表示。ES6做出了改进，将这部分放进大括号中就能正确解读。

`"\u{20BB7}"`

### codePointAt

ES6提供了`codePointAt`方法，能够正确处理4个字节存储的字符，返回一个字符的码点。

```js
var s = '中a'
s.codePointAt(0)    // 20013
s.codePointAt(1)    // 48
```

`codePointAt`方法返回的是码点的十进制，如果想要十六进制，可以使用`toString`方法转换。

```js
s.codePointAt(0).toString(16)   // "4e2d"
```

### String.fromCodePoint

ES5提供了`String.fromCharCode`方法用于从码点返回对应的字符。但它不能识别32位的UTF-16字符。ES6提供了`String.fromCodePoint`方法，可以识别大于`0xFFFF`的字符。

### 字符串的遍历器接口

ES6为字符串添加了遍历器接口，使得字符串可以由`for...of`循环遍历。

```js
for (let codePoint of 'foo') {
  console.log(codePoint)
}

// f
// o
// o
```

### at()

ES5对字符串对象提供了`charAt`方法，返回字符串给定位置的字符，但该方法不能识别码点大于`0xFFFF`的字符。

`at`方法时一个提案，可以识别`Unicode`大于`0xFFFF`的字符。

### normalize()

ES6为字符串实例提供了`normalize`方法，用来将字符的不同表示方法统一为同样的形式。

### includes()、startsWith()和endsWith()

ES6提供了3个方法来确定一个字符串是否包含在另一个字符串中，ES5中只有使用`indexOf`

- `includes()`: 返回布尔值，表示是否找到参数字符串
- `startsWith()`: 返回布尔值，表示参数字符串是否在源字符串的头部
- `endsWith()`: 返回布尔值，表示参数字符串是否在源字符串的尾部

```js
var s = 'Hello world!'
s.startsWith('Hello')   // true
s.endsWith('!')   // true
s.includes('o')   // true
```

上述3个方法都支持第二个参数，表示开始搜索的位置

```js
s.startsWith('world', 6)    // true
s.endsWith('Hello', 5)    // true
s.includes('Hello', 6)    // false
```

### repeat()

`repeat`方法返回一个新字符串，表示将原字符串重复n次

```js
'x'.repeat(3)   // 'xxx'
```

### padStart()、padEnd()

ES7引入了字符串补全长度的功能，如果某个字符串不够指定长度，会在头部或尾部补全。`padStart()`用于头部补全，`padEnd()`用于尾部补全。

```js
'x'.padStart(5, 'ab')   // ababx
'x'.padStart(4, 'ab')   // abax
'x'.padEnd(5, 'ab')     // 'xabab'
'x'.padEnd(4, 'ab')     // 'xaba'
```

### 模板字符串

ES6引入模板字符串，它是增强的字符串，用反引号(`)标识，它可以作为普通字符串使用，也可以定义多行字符串，或者在字符串中插入变量。

```js
`In JavaScript '\n' is a line-fead`
```

使用模板字符串来表示多行字符串，所有的空格和缩进都会被保留在输出中。如果不想要换行，可以使用`trim()`方法消除。

```js
`
<ul>
  <li>First</li>
  <li>Second</li>
</ul>
`.trime()
```

模板字符串插入变量使用`${}`。除了可以插入变量，也可以插入一个函数。

<h2 id="正则的扩展">正则的扩展</h2>

### RegExp构造函数

在ES5中，使用`new RegExp()`定义正则时，如果第一个参数是正则对象，则不允许使用第二个参数定义修饰符，ES6修改了这个行为，允许在第二个参数中定义修饰符。

```js
new RegExp(/abc/ig, 'i').flags    // i
```

### 字符串的正则方法

字符串对象共有4个正则方法：

- `match()`
- `replace()`
- `search()`
- `split()`

### u修饰符

ES6增加了`u`修饰符，含义是'Unicode模式'，用来处理大于 `\uFFFF` 的Unicdoe字符串。

### y修饰符

ES6增加了`y`修饰符，叫做"粘连"修饰符，`y`修饰符和`g`修饰符的作用类似，都是全局匹配。

## 数值的扩展

### 二进制和八进制

ES6提供了二进制和八进制的新写法，分别使用前缀`0b`（或`0B`）和`0o`(或`0O`)表示

```js
0b111110111 === 503   // true
0o767 === 503   // true
```

如果要讲使用`0b`和`0x`前缀的字符串数值转为十进制，要使用`Number`方法.

### Number.isFinite()、Number.isNaN()

ES6在`Number`对象上提供了`Number.isFinite()`和`Number.isNaN()`两个方法。前者用来检查一个数值是否为有限的。

```js
Number.isFinite(15)   // true
Number.isFinite(Infinity)   // false
Number.isFinite('foo')      // false
```

后者用来检查一个值是否为`NaN`

```js
Number.isNaN(NaN)   // true
Number.isNaN(15)    // false
```

### Number.parseInt()、Number.parseFloat()

ES6将全局方法`parseInt()`和`parseFloat()`移植到了`Number`对象上，行为完全保持不变。

```js
Number.parseInt('12.34')    // 12
Number.parseFloat('123.45#')    // 123.45
```

### Numbewr.isInteger()

`Number.isInteger()`用来判断一个值是否为整数。

```js
Number.isInteger(25)    // true
Number.isInteger(25.0)    // true
Number.isInteger(25.1)    // false
```

### Number.EPSILON

ES6在`Number`对象上新增了一个极小的常量：`Number.EPSILON`

新增这个极小的常量，目的在于为浮点数计算设置一个误差范围，如果这个误差小于`Number.EPSILON`，那么我们就认为得到了正确结果。

### 安全整数和Number.isSafeInteger()

JavaScript能准确表示的整数范围在 -2<sup>53</sup>到2<sup>53</sup>之间，不含两个端点，超出则无法正常表示。ES6引入了`Number.MAX_SAFE_INTEGER`和`Number.MIN_SAFE_INTEGER`两个常量，用来表示这个范围的上下限。

```js
Number.MAX_SAFE_INTEGER === Math.pow(2, 53) - 1   // true
Number.MIN_SAFE_INTEGER === -Number.MAX_SAFE_INTEGER    // true
```

`Number.isSafeInteger()`则是用来判断一个整数是否在这个范围内。

```js
Number.isSafeInteger('a')   // false
Number.isSafeInteger(null)    // false
Number.isSafeInteger(Infinity)      // false
Number.isSafeInteger(3)   // true
```

### Math对象的扩展

ES6在`Math`对象上新增了17个与数学相关的方法，这些方法都是静态方法，只能在`Math`对象上调用。

| 方法 | 描述 |
| --- | --- |
| Math.trunc() | 去除一个数的小数部分，返回整数部分 |
| Math.sign() | 判断一个数到底是正数、负数，还是零 |
| Math.cbrt() | 用于计算一个数的立方根 |
| Math.clz32() | 返回一个数的32位无符号整数形式有多少个前导0 |
| Math.imul() | 返回两个数以32位带符号整数形式相乘的结果，返回一个32位的带符号整数 |
| Math.fround() | 返回一个数的单精度浮点数形式 |
| Math.hypot() | 返回所有参数的平方和的平方根 |
| Math.expm1() | 返回e<sup>x</sup>-1，即`Math.exp(x)-1` |
| Math.log1p() | 返回`ln(1+x)`，即`Math.log(1+x)`。如果x小于-1，则返回`NaN` |
| Math.log10() | 返回以10为底的x的对数，如果x小于0，则返回`NaN` |
| Math.log2() | 返回以2为底的x的对数，如果x小于0，则返回`NaN` |
| Math.sinh(x) | 返回x的双曲正弦 |
| Math.cosh(x) | 返回x的双曲余弦 |
| Math.tanh(x) | 返回x的双曲正切 |
| Math.asinh(x) | 返回x的反双曲正弦 |
| Math.acosh(x) | 返回x的反双曲余弦 |
| Math.atanh(x) | 返回x的反双曲正切 |
| Math.signbit() | 判断一个值得正负，但如果参数是-0，则返回-0 |

### 指数运算符

ES6新增了指数运算符（**）

```js
2**2    // 4
2**3    // 8
```

### Integer数据类型

JavaScript中所有的数字都保存成64位浮点数，所以整数的精确程度只能到53个二进制位，大于这个范围，JavaScript就不能精确的表示，现在ES6有一个提案，引入新的数据类型 `Integet`(整数)，整数类型的数据只用来表示整数，没有位数限制。

<h2 id="函数的扩展">函数的扩展</h2>

### 函数参数的默认值

ES6允许为函数的参数设置默认值，即直接写在参数定义的后面。

```js
function log(x, y = 'World') {
  console.log(x, y)
}

log('Hello')    // Hello World
log('Hello', 'China')   // Hello China
log('Hello', '')    // Hello
```

参数变量是默认声明的，所以不能使用`let`或`const`再次声明

```js
function foo(x = 5) {
  let x = 1       // error
  const x = 2     // error
}
```

参数默认值可以与解构赋值的默认值结合起来使用

```js
function foo({ x, y = 5 }) {
  console.log(x, y)
}

foo({})   // undefined, 5
foo({ x: 1 })     // 1, 5
foo({ x: 1, y: 2 })   // 1, 2
```

定义了默认值的参数一般都会在函数参数的末尾，非尾部的参数是无法设置默认值的。

指定了默认值后，函数的`length`属性将返回没有指定默认值的参数个数，也就是说指定了默认值后，`length`属性将失真。

```js
(function(a){}).length    // 1
(function(a = 5){}).length       // 0
(function(a, b, c = 5){}).length    // 2
```

### rest参数

ES6引入了`rest`参数，（形式为"...变量名"），用于获取函数多余的参数，这样就不需要`arguments`对象了。`rest`参数搭配的是一个数组，多余的参数都在这个数组当中。

```js
function add (...values) {
  let sum = 0

  for (let val of values) {
    sum += val
  }

  return sum
}

add(2, 5, 3)    // 10
```

`rest`参数之后不能再有其他参数，否则会报错。函数的`length`属性不包含`rest`参数。

### 严格模式

ES5中我们可以在函数内部设定严格模式。ES6做出了修改，如果函数参数使用了默认值、解构赋值或扩展运算符，那么函数内部就不能显式的设定为严格模式，否则会报错。

```js
function doSomething (a, b = a) {
  'use strict'
  // 报错
}

const doSomething = function ({ a, b }) {
  'use strict'
  // 报错
}
```

### name属性

函数的`name`属性返回该函数的函数名。ES6对这个属性做出了修改，如果将一个匿名函数赋值给一个变量，ES5返回空字符串，ES6会返回实际的函数名。

```js
let f = function () {}

// ES5
f.name    // ''

// ES6
f.name    // 'f'
```

### 箭头函数

ES6允许使用箭头（"=>"）来定义函数

```js
let f = v => v
```

使用箭头函数时的注意事项：

- 函数体内的`this`对象就是定义时所在的对象，而不是使用时所在的对象
- 不可以当做构造函数使用
- 不可以使用`arguments`对象，该对象在函数体内不存在，可以用`rest`参数代替
- 不可以使用`yield`命令，箭头函数不能用作`Generator`函数

箭头函数可以嵌套，在箭头函数内部还可以继续使用箭头函数。

### 绑定this

箭头函数可以用来绑定`this`对象，减少显式绑定`this`对象的写法(`call`、`apply`和`bind`)。但它有局限性，ES7提出了函数绑定运算符。

函数绑定运算符是并排的双冒号(::)，双冒号左边是一个对象，右边是一个函数，该运算符会自动将左边的对象作为上下文环境绑定到右边的函数上。

### 尾调用优化

尾调用是函数式编程中的概念，简单来说，就是指某个哈数的最后一步是调用另一个函数。

<h2 id="数组的扩展">数组的扩展</h2>

### 扩展运算符

扩展运算符就是三个点（...），将一个数组转为用逗号分隔的参数序列

```js
console.log(...[1, 2, 3])
// 1 2 3
```

扩展运算符的应用如下：

- 合并数组

  ```js
  const more = [3, 4]
  [1, 2, ...more]
  // [1, 2, 3, 4]
  ```

- 与解构赋值结合使用生成数组
- 将函数返回的多个值组成数组或对象，然后使用扩展运算符将它们展开
- 将字符串转为真正的数组

  ```js
  [...'hello']
  // ['h', 'e', 'l', 'l', 'o']
  ```

- 实现`Iterator`接口的对象

  ```js
  let nodeList = document.querySelectAll('div')
  let array = [...nodeList]
  ```

### Array.from()

`Array.from()`方法用于将两类对象转为真正的数组，一类是类似数组的对象，一类是可遍历的对象，包括ES6的`Set`和`Map`

```js
let arrayLike = {
  '0': 'a',
  '1': 'b',
  '2': 'c',
  length: 3
}

let arr2 = Array.from(arrayLike)
```

实际操作中，常见的类似数组的对象包括DOM操作返回的`NodeList`集合,以及函数内部的`arguments`对象，`Array.from`都可以将它们转为真正的数组。

`Array.from`还可以接收第二个参数，用来对每个元素进行处理，将处理后的值放入返回的数组。

```js
Array.from(arrayList, x => x * x)
```

### Array.of()

`Array.of`用于将一组值转为数组

```js
Array.of(3, 1, 8)   // [3, 1, 8]
```

它总是返回参数值组成的数组，如果没有参数，将返回一个空数组。

### Array.prototpye.copyWithin

数组实例的`copyWithin`方法会在当前数组内部将指定位置的成员复制到其他位置，然后返回当前数组，这个方法会修改当前数组

```js
Array.prototype.copyWithin(target, start=0, end=this.length)
```

```js
[1, 2, 3, 4, 5].copyWithin(0, 3)
// [4, 5, 3, 4, 5]
```

### find()和findeIndex()

数组实例的 `find` 方法用于找出第一个符合条件的数组成员，它的参数是一个回调函数，所有数组成员依次执行该回调函数，直到找出第一个返回值为 `true` 的成员，然后返回该成员，如果没有找到，则返回 `undefined`

```js
[1, 4, -5, -10].find(n => n < 0)
// -5

[1, 5, 10, 15].find((value, index, arr) => {
  return value > 9
})
// 10
```

数组实例的 `findIndex` 方法与 `find` 类似，返回第一个符合条件的数组成员的位置，如果没找到返回 `-1`

```js
[1, 5, 10, 15].findIndex((value, index, arr) => {
  return value > 9
})
// 2
```

### fill

数组实例的 `fill` 方法使用给定的值填充一个数组

```js
['a', 'b', 'c'].fill(7)
// [7, 7, 7]

new Array(3).fill('a')
// ['a', 'a', 'a']
```

### entries()、 keys()和values()

ES6提供了3个新方法用于遍历数组，`entries()` 、 `keys()` 和 `values()`，它们都返回一个遍历器对象，可以使用 `for...of`循环遍历。

```js
// keys方法对键名进行遍历
for (let index of ['a', 'b'].keys()) {
  console.log(index)
}
// 0
// 1

// values方法对键值进行遍历
for (let ele of ['a', 'b'].values()) {
  console.log(ele)
}
// 'a'
// 'b'

// entries方法对键值对遍历
for (let [index, ele] of ['a', 'b'].entries()) {
  console.log(index, ele)
}
// 0 'a'
// 1 'b'
```

### includes

`Array.prototype.includes`方法返回一个布尔值，表示某个数组是否包含了给定的值，与字符串的 `includes` 方法类似。

```js
[1, 2, 3].includes(2)   // true
[1, 2, 3].includes(4)   // false
[1, 2, NaN].includes(NaN)   // true
```

`includes` 方法的第二个参数表示搜索的起始位置，默认为0

<h2 id="对象的扩展">对象的扩展</h2>

### 属性的简洁表示

ES6允许直接写入变量和函数作为对象的属性和方法，只写属性名，表示属性值就是属性名所代表的变量值

```js
const foo = 'bar'
const obj = {
  foo
}

// 等同于
const obj = {
  foo: bar
}

// 方法简写
const obj2 = {
  method () {
    // ...
  }
}

// 等同于
const obj2 = {
  method: function () {
    // ...
  }
}
```

### 属性名表达式

ES6允许定义字面量对象时，把表达式放在方括号中表示属性名

```js
let propKey = 'foo'
let obj = {
  [proKey]: true,
  ['a' + 'b']: 123
}
```

### name属性

函数的 `name` 属性返回函数名，对象中的方法也是函数，也有 `name` 属性。

```js
const person = {
  sayName () {
    // ...
  }
}

person.sayName.name   // 'sayName'
```

### Object.is

ES6部署了 `Object.is` 方法来比较两个值是否相等，它与 `===` 原理一致，并解决了 `NaN` 不等于 `NaN` 和 `+0` 等于 `-0` 的问题。

```js
// bad
NaN === NaN   // false
+0 === -0     // true

// good
Object.is(NaN, NaN)   // true
Object.is(+0, -0)     // false
```

### Object.assign

`Object.assign` 方法用于将源对象(source)的所有可枚举属性复制到目标对象(target)

```js
let target = { a: 1 }
let source = { b: 2 }
Object.assign(target, source)   // { a: 1, b: 2 }
```

`Object.assign` 执行的是浅复制，而不是深复制，如果源对象某个属性的值是对象，那么木白哦对象复制得到的是这个对象的引用。

```js
let source = { a: { b: 1 } }
let target = Object.assign({}, source)
// 修改源对象中属性a的值，将会改变目标对象中的值
source.a.b = 100
target.a.b    // 100
```

### 属性的可枚举性

对象的每一个属性都具有一个描述对象(Descriptor)，用于控制改属性的行为。`Object.getOwnPropertyDescriptor` 方法可以获取该属性的描述对象

```js
let obj = { foo: 123 }
Object.getOwnPorpertyDescriptor(obj, 'foo')
// {
//    value: 123,
//    writable: true,
//    enumerable: true,
//    configurable: true
// }
```

目前只有 `for...in` 会返回对象继承的属性，所以为了规避复杂性，可使用 `Object.keys()` 来代替 `for...in`

### 属性的遍历

- `for...in`
- `Object.keys(obj)`
- `Object.getOwnPropertyNames(obj)`
- `Object.getOwnPropertySymbols(obj)`
- `Reflect.ownKeys(obj)`

### __proto__、Object.setPrototypeOf()和Object.getPrototypeOf()

`__proto__` 用来设置或读取当前对象的 `prototype` 对象，但推荐使用这个属性，而是使用ES6的 `Object.setPrototypeOf`、`Object.getPrototypeOf` 和 `Object.create()`

`Object.setPrototypeOf` 方法用来设置一个对象的 `prototype` 对象，返回参数对象本身。

```js
// 格式
Object.setPrototypeOf(object, prototype)

// 用法
let proto = {}
let obj = { x: 10 }

Object.setPrototypeOf(obj, proto)

proto.y = 20
proto.z = 30

obj.x // 10
obj.y // 20
obj.z // 30
```

`Object.getPrototypeOf` 方法用来读取一个对象的 `prototype` 对象

```js
Object.getPrototypeOf(obj)
// { y: 20, z: 30 }
```

### Object.keys()、Object.values()和Object.entries()

#### Object.keys()

ES6引入 `Object.keys()` 方法，返回一个数组，成员是参数对象自身的(不含继承的)所有可遍历(`enumerable`)属性的键名

```js
const obj = { foo: 'bar', baz: 42 }
Object.keys(obj)
// ['foo', 'baz']
```

#### Object.values()

`Object.vlaues()` 方法返回一个数组，成员是参数对象自身的(不含继承的)所有可遍历的(enumerable)属性的键值

```js
const obj = { foo: 'bar', baz: 42 }
Object.values(obj)
// ['bar', 42]
```

#### Object.entries()

`Object.entries()` 方法返回一个数组，成员是参数对象自身的(不含继承的)所有可遍历的(enumerable)属性的键值对数组。

```js
const obj = { foo: 'bar', baz: 42 }
Object.entries(obj)
// [['foo', 'bar'], ['baz', 42]]
```

它的基本作用就是用来遍历对象属性的

```js
const obj = { one: 1, two: 2 }
for (let [key, value] of Object.entries(obj)) {
  console.log(`${JSON.stringify(key)} : ${JSON.stringify(value)}`)
}
// 'one': 1
// 'two': 2
```

另外可以它可以将对象转换为 `Map` 结构

```js
const obj = { foo: 'bar', baz: 42 }
const map = new Map(Object.entries(obj))
map // Map { foo: 'bar', baz: 42 }
```

### 对象的扩展运算符

ES6在数组中引入了扩展运算符

```js
const [a, ...b] = [1, 2, 3]
a  // 1
b  // [2, 3]
```

ES2017将这个运算符引入到了对象之中。

```js
// 对象中的解构赋值
let { x, y, ...z } = { x: 1, y: 2, a: 3, b: 4 }
x  // 1
y  // 2
z  // { a: 3, b: 4 }
```

对象中的扩展运算符(`...`)，用于取出参数对象的所有可遍历属性，并将其复制到当前对象之中。

```js
let z = { a: 3, b: 4 }
let n = { ...z }
n // { a: 3, b: 4 }
```

### Object.getOwnPropertyDescriptors()

在ES5中， `Object.getOwnPropertyDescriptors` 方法用来返回某个对象属性的描述对象

```js
const obj = { foo: 100 }
Object.getOwnPropertyDescriptor(obj, 'foo')
// Object {
//   value: 100,
//   writable: true,
//   enumerable: true,
//   configurable: true
//}
```

ES2017引入了 `Object.getOwnPropertyDescriptors()` 方法，返回指定对象所有自身属性(非继承属性)的描述对象

```js
const obj = {
  foo: 100,
  get bar () { return 'abc' }
}

Object.getOwnPropertyDescriptors(obj)
// Object {
//   foo: {
//     configurable: true,
//     enumerable: true,
//     value: 100,
//     writable: true
//   },
//   bar: {
//     get: [Function: bar],
//     set: undefined,
//     enumerable: true,
//     configurable: true
//   }
// }
```

<h2 id="Symbol">Symbol</h2>

### 概述

ES6引入了一种新的原始(基本)数据类型：`Symbol`，表示独一无二的值。它是JavaScript中的第7种数据类型：`Undefined`、`Null`、`Boolean`、`String`、`Number` 和 `Object`。

ES5中的对象的键名必须使用字符串，但容易造成命名冲突，引入 `Symbol` 可以解决这个问题。

`Symbol` 的值通过 `Symbol` 函数生成，现在对象中的属性名可以有两种形式：一种就是原来的字符串，而另外一种就是新增的 `Symbol` 类型

```js
let s = Symbol()
typeof s    // "Symbol"
```

`Symbol` 函数可以接受一个字符串作为参数，表示对 `Symbol` 实例的描述。

```js
let s1 = Symbol('foo')
let s2 = Symbol('bar')

s1    // Symbol(foo)
s2    // Symbol(bar)
```

### 作为对象属性名的Symbol

`Symbol` 值可以作为标识符用于对象的属性名，保证不会出现同名的属性。

```js
cosnt mySymbol = Symbol()

// 第一种写法
let a = {}
a[mySymbol] = 'Hello'

// 第二种写法
let a = {
  [mySymbol]: 'Hello'
}

// 第三种写法
let a = {}
Object.defineProperty(a, mySymbol, { value: 'Hello' })
```

注意：`Symbol` 值作为对象属性名时不能使用点运算符。在对象内部，使用 `Symbol` 值定义属性时， `Symbol` 值必须放在方括号中。

### 属性名的遍历

如果在一个对象中存在 `Symbol` 类型的属性，则只能通过 `Object.getOwnPropertySymbols` 方法来返回它们，其他如：`for..in`、`for...of`、`Object.keys()` 和 `Object.getOwnPropertyNames()` 都不能返回它。

`Object.getOwnPropertySymbols` 方法返回一个数组，成员是当前对象的所有用作属性名的 `Symbol` 值。

```js
let obj = {}
let a = Symbol('a')
let b = Symbol('b')

obj[a] = 'Hello'
obj[b] = 'World'

let objSymbols = Object.getOwnPropertySymbols(obj)
objSymbols    // [Symbol(a), Symbol(b)]
```

那么如果一个对象中既存在普通字符串类型键名，也存在 `Symbol` 类型，该怎么办呢？ 

`Reflect.ownKeys` 方法可以返回所有类型的键名，包括常规键名和 `Symbol` 类型的键名

```js
let obj = {
  [Symbol('mySymbol')]: 1,
  enum: 2,
  nonEnum: 3
}

Reflect.ownKeys(obj)
// ['enum', 'nonEnum', Symbol(mySymbol)]
```

### Symbol.for()、Symbol.keyFor()

#### Symbol.for()

`Symbol.for()` 方法接受一个字符串作为参数，然后搜索有没有以该参数作为名称的 `Symobl` 值，如果有就返回这个 `Symbol` 值，否则新建并返回一个以该字符串作为名称的 `Symobl` 值。

```js
let s1 = Symbol.for('foo')
let s2 = Symbol.for('foo')

s1 === s2   // true
```

#### Symbol.keyFor()

`Symbol` 方法每次都会生成新的值，而 `Symbol.for` 会先查找要生成的值是否已登记，如果有则直接返回，没有才会生成。`Symbol.keyFor()` 方法用于返回一个已登录的 `Symobl` 类型值的 `key`

```js
let s1 = Symbol.for('foo')
Symbol.keyFor(s1)   // 'foo'

let s2 = Symbol('foo')
Symbol.keyFor(s2)   // 没有登记，返回undefined
```

### 内置的Symbol值

- `Symbol.hasInstance`: 该属性指向一个内部方法，对象使用 `instanceof` 运算符时会调用这个方法，判断该对象是否为某个构造函数的实例
- `Symbol.isConcatSpreadable`: 该属性等于一个布尔值，表示该对象使用 `Array.prototype.concat()` 时是否可以展开。
- `Symbol.species`： 该属性指向当前对象的构造函数
- `Symbol.match`
- `Symbol.repalce`
- `Symbol.search`
- `Symbol.split`
- `Symbol.iterator`
- `Symobl.toPrimitive`
- `Symbol.toStringTag`
- `Symbol.unscopables`

<h2 id="Set和Map数据结构">Set和Map数据结构</h2>

### Set

#### 基础用法

ES6提供了新的数据结构： `Set`, 它类似于数组，但成员的值都是唯一的。 `Set` 本身是一个构造函数，可以用来生成 `Set` 数据结构。

```js
const s = new Set()

[2, 3, 4, 5, 5, 2, 2].forEach(x => s.add(x))

for (let i of s) {
  console.log(i)
}

// 2, 3, 4, 5
```

`Set` 可以接受一个数组（或其他具有 `iterable` 接口的数据结构）作为参数，用来初始化。

```js
const set = new Set([1, 2, 3, 4, 4])
[...set]
// [1, 2, 3, 4]
```

由于 `Set` 数据结构中的成员是不会重复的，所以它可以用来做数组去重

```js
[...new Set(array)]
```

#### Set实例的属性和方法

`Set` 的实例具有以下属性：

- `Set.prototype.constructor`：构造函数，默认为 `Set` 函数
- `Set.prototype.size`：返回 `Set` 实例的成员总数

`Set` 实例的方法分为两大类，一类是数据操作，一类是成员遍历

- `add(value)`：添加某个值，返回 `Set` 结构本身。
- `delete(value)`：删除一个值，返回一个布尔值，表示删除是否成功
- `has(value)`：返回一个布尔值，表示参数是否为 `Set` 的成员
- `clear()`：清除所有成员，没有返回值。

#### 遍历操作：

- `keys()`：返回键名的遍历器
- `values()`：返回键值的遍历器
- `entries()`：返回键值对的遍历器
- `forEach()`：使用回调函数遍历每个成员

```js
// Set没有键名，所以 keys和values 方法的行为一致
let set = new Set(['red', 'green', 'blue'])

for (let item of set.keys()) {
  console.log(item)
}
// red
// green
// blue

for (let item of set.values()) {
  console.log(item)
}
// red
// green
// blue

for (let item of set.entries()) {
  console.log(item)
}
// ['red', 'red']
// ['green', 'green']
// ['blue', 'blue']

let set = new Set([1, 2, 3]);
set.forEach((value, key) => {
  console.log(value)
})
// 1
// 2
// 3
```

#### 应用场景

扩展运算符(`...`)也可以用于 `Set` 结构

```js
let set = new Set(['red', 'green', 'blue']);
let arr = [...set];
// ['red', 'green', 'blue']
```

扩展运算符和 `Set` 结构相结合就是实现数组去重。

```js
let arr = [3, 5, 2, 2, 5, 5];
let unique = [...new Set(arr)];
// [3, 5, 2]
```

数组的 `map` 方法和 `filter` 方法也可以用于 `Set`

```js
let set = new Set([1, 2, 3]);
set = new Set([...set].map(x => x * 2));
// Set { 2, 4, 6 }

let set = new Set([1, 2, 3, 4, 5]);
set = new Set([...set].filter(x => (x % 2) === 0));
// Set { 2, 4 }
```

使用 `Set` 结构实现并集(Union)、交集(Intersect)和差集(Difference)

```js
let a = new Set([1, 2, 3]);
let b = new Set([4, 3, 2]);

// 并集
let union = new Set([...a, ...b]);
// Set { 1, 2, 3, 4 }

// 交集
let intersect = new Set([...a].filter(x => b.has(x)));
// Set { 2, 3 }

// 差集
let difference = new Set([...a].filter(x => !b.has(x)));
// Set { 1 }
```

### WeakSet

#### 含义

`WeakSet` 结构与 `Set` 类似，也是不重复的值得集合。但它与 `Set` 有两个区别：

- `WeakSet` 的成员只能是对象，而不能是其他类型的值。
- `WeakSet` 中的对象都是弱引用，即垃圾回收机制会忽略掉 `WeakSet` 对这些对象的引用，也就是说，如果这些成员对象没有其他的引用了，就会被回收，释放内存。

因此，`WeakSet` 无法被遍历。后面的 `WeakMap` 同样具有这样的特性。

#### 语法

`WeakSet` 是一个构造函数，使用 `new` 创建 `WeakSet` 数据结构。

```js
const ws = new WeakSet();
```

`WeakSet` 结构有以下3个方法：

- `WeakSet.prototype.add(value)`: 添加新成员
- `WeakSet.prototype.delete(value)`: 删除指定成员
- `WeakSet.prototype.has(value)`: 判断值是否在 `WeakSet` 实例中，返回布尔值。

```js
const ws = new WeakSet();
const obj = {};
const foo = {};

ws.add(window);
ws.add(obj);

ws.has(window);   // true
ws.has(foo);      // false

ws.delete(window);
ws.has(window);  // false
```

`WeakSet` 最主要的使用场景是存储 DOM 节点，而不用担心这些节点从文档移除时会引发内存泄漏。

### Map

ES6引入了 `Map` 数据结构，它是一种键值对的集合，类似于对象，对象的键只能是字符串，但 `Map` 的键可以是任何数据类型，包括对象，`Map` 是一种比 `Object` 更合理的 `hash` 结构。

```js
const m = new Map();
const o = { p: 'Hello World' };

m.set(o, 'content');
m.get(o);  // content

m.has(o);   // true
m.delete(o);   // true
m.has(o);   // false
```

`Map` 也可以接受一个数组作为参数，该数组的成员是表示键值对的数组。

```js
const map = new Map([
  ['name', '张三'],
  ['title', 'Author']
])

map.size;   // 2
map.has('name');    // true
map.get('name');    // 张三
map.has('title');   // true
map.get('title');   // Author
```

#### Map实例的属性和方法

- `size`：该属性返回 `Map` 结构的成员总数

  ```js
  const map = new Map();
  map.set('foo', true);
  map.set('bar', false);

  map.size;   // 2
  ```

- `set(key, value)`: 该方法设置 `key` 对应的键值，返回整个 `Map`。

  ```js
  const m = new Map();
  m.set('edition', 6);
  m.set(262, 'standard');
  m.set(undefined, 'nah');
  ```

  `set`方法也支持链式写法：

  ```js
  let map = new Set().set(1, 'a').set(2, 'b').set(3, 'c');
  ```

- `get(key)`: 该方法读取 `key` 对应的键值，如果找不到，则返回 `undefined`

  ```js
  const m = new Map();
  m.set(function(){ console.log('hello') }, 'Hello ES6!');

  m.get(hello);   // Hello ES6!
  ```

- `has(key)`: 该方法返回布尔值，表示某个键是否在 `Map` 结构中。

  ```js
  const m = new Map();

  m.set('editon', 6);
  m.set(262, 'standard');
  m.set(undefined, 'nah');

  m.has('edition');   // true
  m.has('years');     // false
  m.has(262);         // true
  m.has(undefined);   // true
  ```

- `delete(key)`: 该方法删除某个键，返回 `true`, 如果删除失败，返回 `false`

  ```js
  const m = new Map();
  m.set(undefined, 'nah');
  m.has(undefined);     // true

  m.delete(undefined);
  m.has(undefined);   // false
  ```

- `clear()`：该方法删除所有成员，没有返回值。

  ```js
  let map = new Map();
  map.set('foo', true);
  map.set('bar', false);
  map.size;   // 2
  map.clear();
  map.size;   // 0
  ```

#### 遍历方法

`Map` 原生提供3个遍历器生成哈数和一个遍历方法

- `keys()`：返回键名的遍历器。
- `values()`：返回键值的遍历器。
- `entries()`：返回所有成员的遍历器。
- `forEach()`：遍历所有成员。

### WeakMap

`WeakMap` 结构与 `Map` 相似，都是键值对的集合。它与 `Map` 区别如下：

- `WeakMap` 只接受对象作为键名(`null` 除外)。
- `WeakMap` 的键名指向的对象不计入垃圾回收机制。

## Proxy

`Proxy` 用于修改某些操作的默认行为，所以属于一种元编程，即对编程语言进行编程。

`Proxy` 可以理解成在目标对象前架设一个"拦截"层，外界对该对象的访问都必须通过该层拦截，因此它提供了一种机制可以对外界的访问进行过滤和改写。

```js
var obj = new Proxy({}, {
  get: function(target, key, receiver) {
    console.log(`getting ${key}`);
	return Reflect.get(target, key, receiver);
  },
  set: function(target, key, value, receiver) {
    console.log(`setting ${key}`);
    return Reflect.set(target, key, value, receiver);
  }
})

obj.count = 1
// setting count
// 1

++obj.count
// getting count
// setting count
// 2
```

ES6原生提供 `Proxy` 构造函数，用于生成 `Proxy` 实例。

```js
// 下面的target是目标对象（需要被拦截的对象）
// handler也是对象，定义了拦截操作
var proxy = new Proxy(target, handler);
```

### Proxy的实例方法

#### get()

`get()` 用于拦截某个属性的读取操作

```js
const person = {
  name: '张三'
}

const proxy = new Proxy(person, {
  get: function(target, property) {
    if (property in target) {
      return target[property];
    } else {
      throw new Error();
    }
  }
})

proxy.name;     // 张三
proxy.age;      // Error
```

### set()

`set()` 用于拦截某个属性的赋值操作。

```js
let person = new Proxy({}, {
  set: function(obj, prop, value) {
    if (prop === 'age) {
      if (!Number.isInteger(value)) {
        throw new Error('age is not an integer')
      }
      if (value > 200) {
        throw new Error('age seems invalid')
      }
    }
    obj[prop] = value;
  }
})

person.age = 100;
person.age = 'abc';   // Error
person.age = 250;     // Error
```

### apply()

`apply()` 方法拦截函数的调用、`call` 和 `apply` 操作。

```js
const target = function() { return `I am a target` }
const handler = {
  apply: function () {
    return `I am the proxy`
  }
}

const p = new Proxy(target, handler);
p();    // I am the proxy
```

### has()

`has()` 方法用来拦截 `HasProperty` 操作，即判断对象是否具有某个属性。

```js
const handler = {
  has(target, key) {
    if (key[0] === '_') {
      return false;
    }
    return key in target;
  }
}

cosnt target = { _prop: 'foo', prop: 'foo' };
const proxy = new Proxy(target, handler);
'_prop' in proxy;  // false
```

### construct()

`construct()` 方法用于拦截 `new` 命令。

```js
const handler = {
  construct(target, args, newTarget) {
    return new target(...args);
  }
}
```

### deleteProperty()

`deleteProperty()` 方法用于拦截 `delete` 操作

### defineProperty()

`defineProperty()` 方法拦截 `Object.defineProperty` 操作。

### getOwnPropertyDescriptor()

`getOwnPropertyDescriptor` 方法拦截 `Object.getOwnPropertyDescriptor`

### getPrototypeOf()

`getPrototypeOf` 方法拦截获取对象原型的操作。

### isExtensible()

`isExtensible` 方法拦截 `Object.isExtensible` 操作。

### ownKeys()

`ownKeys` 方法用来拦截对象自身属性的读取操作。

### preventExtensions()

`preventExtensions` 方法拦截 `Object.preventExtensions()` 该方法返回一个布尔值。

### setPrototypeOf()

`setPrototypeOf` 用于拦截 `Object.setPrototypeOf` 方法。

## Reflect

`Reflect` 与 `Proxy` 一样，也是ES6为操作对象而提供的新的API。它的设计目的如下：

- 将 `Object` 对象上的一些明显属于语言内部的方法，比如 `Object.defineProperty` 放到 `Reflect` 对象上来。
- 修改某些 `Object` 方法的返回结果，让其变得更加合理。
- 让 `Object` 操作都变成函数行为。
- `Reflect` 对象的方法与 `Proxy` 对象的方法一一对应。

`Reflect` 对象上一共有13个静态方法，它们如下：

- `Reflect.get(target, name, receiver)`: 该方法查找并返回 `target` 对象的 `name` 属性，如果没有该属性，则返回 `undefined`

  ```js
  var myObejct = {
    foo: 1,
    bar: 2,
    get baz() {
      return this.foo + this.bar;
    }
  }

  Reflect.get(myObject, 'foo');  // 1
  Reflect.get(myObject, 'bar');  // 2
  Reflect.get(myObject, 'baz');  // 3
  ```

- `Reflect.set(target, name, value, receiver)`
- `Reflect.has(obj, name)`
- `Reflect.deleteProperty(obj, name)`
- `Reflect.construct(target, args)`
- `Reflect.getPrototypeOf(obj)`
- `Reflect.setPrototypeOf(obj, newProto)`
- `Reflect.apply(func, thisArg, args)`
- `Reflect.defineProperty(target, propertyKey, attributes)`
- `Reflect.getOwnPropertyDescriptor(target, propertyKey)`
- `Reflect.isExtensible(target)`
- `Reflect.preventExtensions(target)`
- `Reflect.ownKeys(target)`

<h2 id="Promise对象">Promise对象</h2>

### 概念

`Promise` 是一种异步编程的解决方案，它比回调函数和事件更加合理和强大，ES6原生提供 `Promise` 对象。

`Promise` 简单来说，就是一个容器，里面保存着某个未来才会结束的事件的结果。从语法上来讲，它是一个对象，可以从它哪里获取异步操作的消息。`Promise` 对象有以下两个特点：

- 对象的状态不受外界的影响。`Promise` 有3种状态：`Pending` （进行中）、`Fulfilled` (已成功)和 `Rejected` (已失败).

- 一旦状态改变就不会再变，任何时候都可以得到这个结果。

`Promise` 对象可以将异步操作以同步的方式表达出来。它也有缺点：无法被取消，一旦新建它就会立即执行，中途无法被取消。

### 用法

ES6中，`Promise` 对象是一个构造函数，用来生成 `Promise` 实例。

```js
var promise = new Promise(function(resolve, reject) {
  // ...
  if (/* 异步成功 */) {
    resolve(value);
  } else {
    reject(error);
  }
})
```

`Promise` 构造函数接受一个函数作为参数，该函数的参数分别是 `resolve` 和 `reject` ，它们是两个函数，表示异步操作成功和失败。

`Promise` 实例生成后可以使用 `then` 方法分别指定 `resolve` 状态 和 `reject` 状态的回调函数。

```js
promise.then(function(value) {
  // success
}, function(error) {
  // failure
})
```

### Promise.prototype.then()

`then` 方法时定义在原型对象 `Promise.prototype` 上的，它的作用是为 `Promise` 实例添加状态改变时的回调函数。

`then` 方法返回的是一个新的 `Promise` 实例，不是原来的那个，因此可以采用链式写法，在 `then` 方法的后面调用另一个 `then` 方法。

```js
getJSON('/posts.json').then(function(json) {
  return json.post;
}).then(function(post) {
  // ...
})
```

### Promise.prototype.catch()

`catch` 方法用于指定发生错误时的回调函数。

```js
getJSON('/posts.json').then(function(posts) {
  // ...
}).catch(function(error) {
  console.log(error);
})
```

### Promise.all()

`Promise.all` 方法用于将多个 `Promise` 实例包装成一个新的 `Promise` 实例。

```js
var p = Promise.all([p1, p2, p3]);
```

下面是一个具体的例子：

```js
// 生成一个Promise对象的数组
var promises = [2, 3, 4].map(id => {
  return getJSON(`/post/${id}.json`);
})

Promise.all(promises).then(posts => {
  // ...
}).catch(reason) {
  // ...
}
```

### Promise.race()

### Promise.resolve()

`Promise.resolve` 将现有的对象转换为 `Promise` 对象。

```js
cosnt jsPromise = Promise.resolve($.ajax('/xxx.json'));
```

### Promise.reject()

`Promise.reject` 方法返回一个新的 `Promise` 实例，状态为 `Rejected`

### done()和finally()

无论 `Promise` 在调用链中以 `then` 或者 `catch` 结尾，它们如果抛出错误，都无法被捕获，可以使用 `done` 方法结尾，可以保证捕获抛出的错误。

```js
asyncFunc()
.then(f1)
.catch(r1)
.then(f2)
.done();
```

而 `finally` 方法用于指定不管 `Promise` 对象最后状态如何都回被执行的操作。它可以接收普通函数作为参数，这个函数参数无论如何都回被执行。

```js
server.listen(0)
.then(function() {
  // ...
}).finally(server.stop);
```

<h2 id="Iterator和for...of循环">Iterator和for...of循环</h2>

### 概念

遍历器（Iterator）是一种接口，为各种不同的数据结构提供统一的访问机制。任何数据结构，只要部署了 `Iterator` 接口，就可以完成遍历操作。

`Iterator` 的遍历过程如下：

1、 创建一个对象指针，指向当前数据结构的起始位置，本质上它是一个指针对象。
2、 第一次调用指针对象的 `next` 方法，可以将指针指向数据结构的第一个成员。
3、 第二次调用指针对象的 `next` 方法，指针就指向数据结构的第二个成员。
4、 不断的调用指针对象的 `next` 方法，直到它指向数据结构的结束位置。

每次调用 `next` 方法都会返回数据结构的当前成员信息，包含 `value` 和 `done`，表示属性的值和遍历是否结束。

```js
// 模拟next方法的函数
function makeIterator(array) {
  var nextIndex = 0;
  return {
    next: function() {
      return nextIndex < array.lenght ?
        { value: array[nextIndex++], done: false } :
        { value: undefined, done: true };
    }
  }
}

var it = makeIterator(['a', 'b']);
it.next();    // { value: "a", done: false }
it.next();    // { value: "b", done: false }
it.next();    // { value: undefined, done: true }
```

### 默认Iterator接口

`Iterator` 接口的目的是为所有数据结构提供统一的访问机制，即 `for...of` 循环。数据结构只要部署了 `Iterator` 接口，这种数据结构就被称为可遍历的。

在ES6中，默认的 `Iterator` 接口部署在数据结构的 `Symbol.iterator` 属性上。如果数据结构具有 `Symbol.iterator` 属性，那么它就是可被遍历的。

```js
cosnt obj = {
  [Symbol.iterator]: function() {
    return {
      next: function() {
        return {
          value: 1,
          done: true
        }
      }
    }
  }
}
```

在ES6中，某些数据结构原生具备 `Iterator` 结构，比如数组，它们可以不用任何处理就可以被 `for...of` 循环遍历。除了数组原生具备 `Iterator` 接口外，还有 `Map`、`Set`、`String`、`TypedArray`、`arguments` 和 `NodeList`。

对于原生部署 `Iterator` 接口的数据结构，我们无需手动编写遍历器生成函数， `for...of`会自动遍历它们。但 `Object` 却没有部署，那是因为对象属性的先后顺序是不确定的。

除了 `for...of` 循环会默认调用 `Symbol.iterator` 方法外，下面的几个场合也会调用。

- 解构赋值：对数组和 `Set` 结构进行解构赋值时，会默认调用 `Symbol.iterator` 方法。

  ```js
  let set = new Set().add('a').add('b').add('c');
  let [x, y] = set;
  // x: 'a'  y: 'b'

  let [first, ...rest] = set;
  // first: 'a' rest = [b, c]
  ```

- 扩展运算符：扩展运算符(`...`)也会调用默认的 `Iterator` 接口。

  ```js
  var str = 'hello';
  [...str];   // ['h', 'e', 'l', 'l', 'o'
  ```

- yield*

### 字符串的Iterator接口

字符串是一个类似数组的对象，也具有原生的 `Iterator` 接口。

```js
var str = 'abc';
typeof str[Symbol.iterator];    // function

const iterator = str[Symbol.iterator]();
iterator.next();   // { value: 'a', done: false }
iterator.next();   // { value: 'b', done: false }
iterator.next();   // { value: 'c', done: false }
iterator.next();   // { value: undefined, done: true }
```

### 遍历器对象的 return 和 throw

遍历器对象除了有 `next` 方法，还具有 `return` 方法和 `throw` 方法。

`return` 方法使用的场景是当 `for...of` 循环提前退出时，会触发 `return` 方法。比如退出后需要释放资源等操作。

```js
function readLinesSync(file) {
  return {
    next() {
      return { done: true }
    },
    return() {
      file.close();
      return { done: true }
    }
  }
}
```

### for...of循环

ES6引入了 `for...of` 循环作为遍历所有数据结构的统一方法。

`for...of` 循环实际上调用的是数据结构的 `Symbol.iterator` 方法。它的使用范围包括数组、`Set`、`Map`、类数组对象(`arguments`和`NodeList`)、还有 `Generator` 对象和字符串。

- 数组, 数组原生具备 `iterator` 接口。

  ```js
  const arr = ['red', 'green', 'blue'];
  for (let v of arr) {
    console.log(v);   // red green blue
  }
  ```

- `Set` 和 `Map` 数据结构，它们原生具有 `Iterator` 接口，可以直接使用 `for...of` 循环。

  ```js
  const engines = new Set(['Gecko', 'Trident', 'Webkit', 'Webkit']);
  for (let e of engines) {
    console.log(e);
  }
  // Gecko
  // Trident
  // Webkit

  let es6 = new Map();
  es6.set('edition', 6);
  es6.set('committee', 'TC39');
  es6.set('standard', 'ECMA-262');
  for (let [name, value] of es6) {
    console.log(`${name}: ${value}`);
  }
  // edition: 6
  // committee: TC39
  // standard: ECMA-262
  ```

- 类似数组的对象，比如: 字符串、 `argumenst` 和 `NodeList`

  ```js
  // 字符串
  let str = 'hello';
  for(let s of str) {
    console.log(s); // h e l l o
  }

  // DOM NodeList对象
  let paras = document.querySelectorAll('p');
  for(let p of paras) {
    p.classList.add('test');
  }

  // arguments
  function printArgs() {
    for(let x of arguments) {
      console.log(x);
    }
  }
  ```

- 对象原生不具备 `Iterator` 接口，所以它不能直接被 `for...of` 循环遍历。通常有两种解决方法：

  第一种方法是使用 `Object.keys()` 将对象的键名生成一个数组，然后遍历这个数组

  ```js
  for (let key of Object.keys(obj)) {
    console.log(`${key}: obj[key]`);
  }
  ```

  另一个方法时使用 `Generator` 函数将对象重新包装一下。

  ```js
  function* entries(obj) {
    for (let key of Object.keys(obj)) {
      yield [key, obj[key]];
    }
  }

  const obj = { a: 1, b: 2, c: 3 };
  for (let [key, value] of entries(obj)) {
    console.log(`${key}: ${value}`);
  }

  // a: 1
  // b: 2
  // c: 3
  ```

<h2 id="Generator函数">Generator函数</h2>

### 概念

`Generator` 是ES6提供的一种异步编程解决方案。

从语法上讲，我们可以将它看做是一个状态机，封装了多个内部状态。它还是一个遍历器生成函数，返回的遍历器对象可以遍历 `Generator` 函数内部的每一个状态。

从形式上讲，`Generator` 就是一个普通函数，但有两个特别的特征，一是在声明的关键字 `function` 后面有一个星号(`*`),二是函数体内使用了 `yield` 语句定义不同的内部状态。（`yield`：产出）

```js
function* helloWorldGenerator() {
  yield 'hello';
  yield 'world';
  yield 'ending';
}

var hw = helloWorldGenerator();
```

调用 `Generator` 函数后，它并不会执行，也不会返回执行结果，而是一个指向内部状态的指针对象。所以必须调用遍历器对象的 `next` 方法，使得指针指向下一个状态。

```js
hw.next();    // { value: 'hello', done: false }
hw.next();    // { value: 'world', done: false }
hw.next();    // { value: 'ending', done: false }
hw.next();    // { value: undefined, done: true }
```

### next

`next` 方法可以带有一个参数，该参数会被当做上一条 `yield` 语句的返回值。

```js
function* f() {
  for (var i = 0; true; i++) {
    var reset = yield i;
    if (reset) { i = -1 }
  }
}

var g = f();

g.next();   // { value: 0, done: false }
g.next();   // { value: 1, done: false }
g.next(true);   // { value: 0, done: false }
// 无限循环的 Generator
```

### for...of

`for...of` 循环可以自动遍历 `Generator` 生成的 `Iterator` 对象，且无需调用 `next` 方法。

```js
function* foo() {
  yield 1;
  yield 2;
  yield 3;
  return 4;
}

for (let v of foo()) {
  console.log(v);
}
// 1 2 3
```

下面是一个利用 `Generator` 和 `for...of` 实现斐波拉切数列的例子：

```js
function* fibonacci() {
  let [prev, curr] = [0, 1];
  for (;;) {
    [prev, curr] = [curr, prev + curr];
    yield curr;
  }
}

for (let n of fibonacci()) {
  if (n > 1000) break;
  console.log(n)
}
```

原生的JavaScript对象没有遍历接口，不能使用 `for..of` 循环，通过 `Generator` 加上接口就可以了。

```js
function* objectEntries(obj) {
  let propKeys = Reflect.ownKeys(obj);
  for (let propKey of propKeys) {
    yield [propKey, obj[propKey]];
  }
}

let jane = { first: 'Jane', last: 'Deo' };

for (let [key, value] of objectEntries(jane)) {
  console.log(`${key}: ${value}`);
}
// first: Jane
// last: Deo
```

还有另外一种写法，将 `Generator` 函数加到对象的 `Symbol.iterator` 属性上。

```js
function* objectEntries() {
  let propKeys = Object.keys(this);

  for (let propKey of propKeys) {
    yield [propKey, this[propKey]];
  }
}

let jane = { first: 'Jane', last: 'Deo' };
jane[Symbol.iterator] = objectEntries;

for (let [key, value] of jane) {
  console.log(`${key}: ${value}`);
}
// first: Jane
// last: Deo
```

### Generator.prototype.throw()

`Generator` 函数返回的遍历器对象都有一个 `throw` 方法，可以在函数体外抛出错误，然后在 `Generator` 函数体内捕获。

```js
var g = function* () {
  try {
    yield;
  } catch (e) {
    console.log('内部捕获', e);
  }
}
```

### Generator.prototype.return()

`Generator` 函数返回的遍历器对象海鸥一个 `return` 方法，可以返回给定的值，并终结 `Generator` 函数的遍历。

```js
function* gen() {
  yield 1;
  yield 2;
  yield 3;
}

var g = gen();

g.next();   // { value: 1, done: false }
g.return('foo');    // { value: 'foo', done: true }
g.next();   // { value: undefined, done: true }
```

### Generator函数作为对象属性

`Generator` 函数也可以做为对象的属性：

```js
let obj = {
  * myGeneratorMethod() {
    // ...
  }
}
```

### Generator函数的this

`Generator` 函数总是返回一个遍历器，这个遍历器是 `Generator` 函数的实例，它继承了 `Generator.prototype` 对象上的方法。

```js
function* g() {}

g.prototype.hello = function() {
  return 'hi';
};

let obj = g();

obj instanceof g;   // true
obj.hello();    // 'hi'
```
 
<h2 id="Generator的异步应用">Generator的异步应用</h2>

### 异步

所谓异步，可以理解为一个任务不是直接完成的，而是将任务分割成两个部分，先执行第一段，然后转而执行其他任务，等第一段完成后再回过头来执行剩余的第二段。

在JavaScript中对异步编程的实现就是回调函数，也就是把任务的第二段写在一个函数中，等重新执行任务时直接调用这个函数，我们成为 `callback`。

```js
// 读取文件
fs.readFile('/etc/passwd', 'utf-8', function(err, data) {
  if (err) throw err;
  console.log(data);
})
```

使用回调函数处理异步本身没有问题，问题在于多层的回调函数调用会使得程序难以维护和阅读。我们称为"调用地狱".为了解决这个问题，`Promise`就被提出来了， 它不是一个新的语法功能，而是一种新的写法。将回调函数改成了链式调用。

```js
readFile(fileA)
.then(function(data) {
  //...
})
.then(funtion(data) {
  //...
})
.catch(err) {
  //...
}
```

`Promise` 提供 `then` 方法加载回调函数， `catch` 方法捕获错误。

### Generator函数

传统语言中的异步编程解决方案中有一种叫"协程"，意思就是多个线程相互协作，完成异步任务。它的大概流程如下：

- 协程A开始执行
- 协程A执行到一半，进入暂停状态，将控制权转移给协程B
- 一段时间后，协程B交换执行权
- 协程A恢复执行

```js
function* asyncJob() {
  // ...其他代码
  var f = yield readFile(fileA);
  // ...其他代码
}
```

<h2 id="async函数">async函数</h2>

### 含义

ES2017引入了 `async` 函数，它其实就是 `Generator` 函数的语法糖。

```js
var asyncReadFile = async function() {
  var f1 = await readFile('/etc/fstab');
  var f2 = await readFile('/etc/shells');
  console.log(f1.toString());
  console.log(f2.toString());
}
```

`async` 具有以下特点：

- 内置执行器
- 更好的语义
- 更广的适用性
- 返回值是 `Promise`

### 用法

`async` 函数返回一个 `Promise` 对象，可以使用 `then` 方法添加回调函数，当函数执行时，遇到 `await` 就是先返回，等到异步操作完成，再执行后面的语句。

```js
async function getStockPriceByName(name) {
  var symbol = await getStockSymbol(name);
  var stockPrice = await getStockPrice(symbol);
  return stockPrice;
}

getStockPriceByName('goog').then(function(result) {
  console.log(result);
})
```

### 语法

`async` 函数返回一个 `Promise` 对象。`async` 函数内部的 `return` 语句返回的值会成为 `then` 方法回调函数的参数。

```js
async function f() {
  return 'hello, world';
}

f().then(v => console.log(v));
// 'hello world'
```

`async` 函数内部抛出的错误会导致返回的 `Promise` 对象变为 `reject` 状态，抛出的错误对象会被 `catch` 方法回调函数接收到。

```js
async function f() {
  throw new Error('出错了');
}

f().then(
  v => console.log(v),
  e => console.log(e);
)
// Error: 出错了
```

`async` 函数返回的 `Promise` 对象必须等到内部所有 `await` 命令后面的 `Promise` 对象执行完成后才会发生状态改变，除非遇到 `return` 或抛出错误，也就是说，只有 `async` 函数内部的异步操作执行完，才会执行 `then` 方法指定的回调函数。

正常情况下， `await` 命令后面是一个 `Promise` 对象，如果不是，会被转成一个立即 `resolve` 的 `Promise` 对象。如果 `async` 里有多个 `await` 命令，当前面的 `await` 失败(`reject`)，则后面的都不会被执行。我们可以将 `await` 放在 `try...catch` 中，或者在 `await` 后面跟上错误处理 `catch`，就可以避免这种情况，后面的 `await` 都会被处理。

```js
async function f() {
  try {
    await Promise.reject('出错了');
  } catch(e) {
    // ...
  }
  return await Promise.resolve('hello world');
}
```

如果 `await` 后面的异步操作出错，那么就等同于 `async` 函数返回的 `Promise` 对象被 `reject`。

```js
async function f() {
  await new Promise(function(resolve, reject) {
    throw new Error('Error')；
  })
}

f()
.thne(v => console.log(v))
.catch(e => console.log(e));
```

解决方法就是把他们都放在 `try...catch` 当中，如果有多个 `await` 命令，也是如此。

```js
async function f() {
  try {
    await new Promise(function(resolve, reject) {
      throw new Error('Error');
    })
  } catch(e) {}

  return await ('...');
}
```

使用 `async` 的注意点如下：

- 把 `await` 命令放在 `try...catch` 中。
- 多个 `await` 命令的异步操作如果不存在继发关系，则让他们同时进行(`Promise.all`)
- `await` 命令只能在 `async` 中使用
 
<h2 id="Class">Class</h2>

### 简介

在ES6之前，我们都是通过构造函数定义并生成新对象。

```js
function Point(x, y) {
  this.x = x;
  this.y = y;
}

Point.prototype.toString = function() {
  return this.x + this.y;
}

var p = new Point(1, 2);
```

ES6为我们引入了类，作为对象的模板，通过 `class` 关键字可以定义类。其他它就是一个语法糖。

```js
class Point {
  constructor(x, y) {
    this.x = x;
    this.y = y;
  }

  toString() {
    return this.x + this.y;
  }
}
```

上面的定义中，`constructor` 方法就是构造方法，而 `this` 关键字代表实例对象。

使用类时，也是调用 `new` 方法实例化一个对象。而在类中定义的所有方法都会存在于类的 `prototype` 属性上。

类和模块的内部默认使用严格模式，所以不需要显式的指定 `use strict`。

### constructor方法

`constructor` 方法是类的默认方法，通过 `new` 命令生成对象时会自动调用该方法，一个类必须有 `constructor` 方法，如果没有显式定义，则一个空的 `constructor` 方法会被默认添加。

### 类的实例对象

与ES5一样，生成实例对象使用 `new` 操作符

```js
class Point {}
var p = new Point();
```

### Class表达式

与函数一样， `Class` 也可以使用表达式的形式定义

```js
const MyClass = class Me {
  getClassName() {
    return Me.name;
  }
}

let inst = new MyClass();
```

### this的指向

类的方法内部如果含有 `this`，它将默认指向类的实例。

### Getter和Setter

在类的内部可以使用 `get` 和 `set` 关键字对某个属性设置存值函数和取值函数，拦截该属性的存取行为。

```js
class MyClass {
  constructor() {
    // ...
  }

  get prop() {
    return 'getter';
  }

  set prop(value) {
    console.log(`setter: ${value}`);
  }
}

let inst = new MyClass();
inst.prop = 123;
// setter: 123
```

### 静态方法

如果在类的一个方法前加上 `static` 关键字，表示该方法不会被实例继承，可以直接通过类来调用。

```js
class Foo {
  static classMethod() {
    return 'hello';
  }
}

Foo.classMethod();    // hello
```

注意：父类的静态方法可以被子类继承。

<h2 id="Class继承">Class继承</h2>

### 简介

`Class` 可以通过 `extends` 关键字实现继承

```js
class Point {
}

class ColorPoint extends Point {
  constructor(x, y, color) {
    super(x, y);    // 调用父类的 constructor(x, y)
    this.color = color;
  }

  toString() {
    return `${this.color} ${super.toString()}`;   // 调用父类的toString
  }
}
```

`super` 关键字表示父类的构造函数，用来新建父类的 `this` 对象。子类必须在 `constructor` 方法中调用 `super` 方法。

### Object.getPrototypeOf

`Object.getPrototypeOf` 方法可以用来从子类上获取父类，因此这个方法可以用来判断一个类是否继承了另一个类。

```js
Object.getPrototypeOf(ColorPoint) === Point;    // true
```

### super关键字

`super` 关键字既可以当做函数使用，也可以当做对象使用。

第一种情况当 `super` 作为函数调用时代表父类的构造函数，子类构造函数必须执行一次 `super` 函数。

```js
class A {}

class B extends A {
  constructor() {
    super();
  }
}
```

第二种情况，`super` 作为对象时在普通方法中指向父类的原型对象，在静态方法中指向父类。

<h2 id="修饰器">修饰器</h2>

### 类的装饰器

装饰器(`Decorator`)是一个函数，用来修改类的行为。

```js
@testable
class MyTestableClass {
  // ...
}

function testable(target) {
  target.isTestable = true;
}

MyTestableClass.isTestable;  // true
```

上面是为一个类添加了静态属性，如果想要添加实例属性，可以通过目标类的 `prototype` 对象进行操作。

```js
function testable(target) {
  target.prototype.isTestable = true;
}

@testable
class MyTestableClass {}
```

### 方法的装饰

装饰器可以装饰类，也可以装饰类的属性。

```js
class Person {
  @readonly
  name() {
    return `${this.first} ${this.last}`;
  }
}

function readonly(taraget, name, descriptor) {
  // descriptor 对象原来的值
  // {
  //    value: specifiedFunction,
  //    enumerable: false,
  //    configurable: true,
  //    writeable: true
  // }
  descriptor.writable = false;
  return descriptor;
}
```

<h2 id="Module语法">Module语法</h2>

### 概述

ES6模块不是对象，而是通过 `export` 命令显式指定输出的代码，再通过 `import` 命令输入。

```js
// ES6模块
import { stat, exists, readFile } from 'fs';
```

ES6模块自动采用严格模式，不管有没有在模块头部加上 `use strict`，严格模式有以下限制：

- 变量必须在声明后才能使用
- 函数参数不能有同名属性
- 不能使用 `with` 语句
- 不能对只读属性进行赋值操作
- 不能使用前缀 `0` 表示八进制
- 不能删除不可删除的属性
- 不能删除变量 `delete prop`
- `eval` 不会在它的外层作用域引入变量
- `eval` 和 `arguments` 不能被重新赋值
- `arguments` 不能自动反映函数参数的变化
- 不能使用 `arguments.callee`
- 不能使用 `arguments.caller`

### export命令

模块功能主要由两个命令构成： `export` 和 `import`。`export` 命令用于规定模块的对外接口，`import` 命令用于输入其他模块提供的功能。

一个文件就是一个模块，该文件内的所有变量，外部都无法访问，所以该文件使用 `export` 关键字输出这些需要被外部引用的变量。

```js
// profile.js
export var firstName = 'Kaindy';
export var lastName = 'Liu';
export var year = 1986;
```

下面是另一种写法：

```js
var firstName = 'Kaindy';
var lastName = 'Liu';
var year = 1986;

export { firstName, lastName, year };
```

`export` 输出的变量是原名，可以使用 `as` 关键字重命名。

### import命令

使用了 `export` 命令定义了模块的对外接口后，就可以使用 `import` 命令加载这些模块了。

```js
// main.js
import { firstName, lastName, year } from './profile';

function setName(element) {
  element.textContent = firstName + ' ' + lastName;
}
```

### 整体加载

我们可以使用整体加载，即星号(`*`)，来指定一个对象，所有输出值都加载在这个对象上。

```js
// circle.js
export function area() {
  // ...
}

export function circumference() {
  // ...
}
```

```js
// main.js
import * as circle from './circle.js';

console.log(circle.area());
console.log(circle.circumference());
```

### export default

我们可以使用 `export default` 命令为模块指定默认输出。

<h2 id="编程风格">编程风格</h2>

### 块级作用域

- 使用 `let` 取代 `var`，可以直接禁止使用 `var`。
- 在 `let` 和 `const` 之间，优先使用 `const`。
- 静态字符串一律使用单引号或反引号，不使用双引号，动态字符串使用反引号.
- 使用数组成员对变量赋值时，优先使用解构赋值。
- 定义多行对象时，最后一个成员使用逗号结尾。对象尽量静态化，一旦定义不要随意添加新的属性，若必须添加，则应使用 `Object.assign` 方法
- 使用扩展运算符（`...`） 来复制数组。
- 立即执行函数可以写成箭头函数的形式。
- 注意区分 `Object` 和 `Map`，只有模拟实体对象时才使用 `Object`，如果是需要 `key:value` 的数据结构，则使用 `Map`，因为 `Map` 有内建的遍历机制。
- 总是使用 `class` 替代 `prototype` 操作，因为 `class` 写法更简洁。
- 总是使用 `import` 取代 `require` 的写法。

<h2 id="ArrayBuffer">ArrayBuffer</h2>

`ArrayBuffer`、`TypedArray` 视图和 `DataView` 视图是JavaScript操作二进制数据的接口。ES6将它们纳入规范，它们都以数组语法处理二进制数据，统称为二进制数组。

二进制数组由3类对象组成：

- `ArrayBuffer` 对象：代表内存中的一段二进制数据，可以通过视图进行操作。
- `TypedArray` 视图：共包含9种类型的视图，比如 `Uint8Array`（无符号8位整数）数组视图、`Int16Array` （16位整数）数组视图等。
- `DataView` 视图：可以自定义复合格式的视图。

### ArrayBuffer对象

`ArrayBuffer` 对象代表存储二进制数据的一段内存，它不能直接进行读或写，必须通过视图（`TypedArray`和`DataView`）读写，视图的作用就是以指定格式解读二进制数据。

`ArrayBuffer` 是一个构造函数，可分配一段可以存放数据的连续内存区域。

```js
let buf = new ArrayBuffer(32);
// 参数是需要分配的内存大小
```

为了能读写这段内存，需要为它指定视图，创建 `DataView` 视图，需要提供 `ArrayBuffer` 对象实例作为参数

```js
let buf = new ArrayBuffer(32);
let dataView = new DataView(buf);
dataView.getUint8(0); // 0
```

`TypedArray` 视图与 `DataView` 视图的一个区别是，它不是一个构造函数，而是一组构造函数，代表不同的数据格式。

```js
let buf = new ArrayBuffer(32);

let x1 = new Int32Array(buf);
x1[0] = 1;

let x2 = new Uint8Array(buf);
x2[0] = 2;

x1[0];  // 2
```

下面是一些 `ArrayBuffer` 对象原型上的属性和方法：

- `ArrayBuffer.prototype.byteLength`： 该属性返回所分配的内存区域的字节长度

  ```js
  let buffer = new ArrayBuffer(32);
  buffer.byteLength;    // 32
  ```

- `ArrayBuffer.prototype.slice`： 该方法允许将内存区域的一部分复制生成一个新的 `ArrayBuffer` 对象。

  ```js
  let newBuffer = buffer.slice(0, 3);
  ```

- `ArrayBuffer` 有一个静态方法 `isView` ，返回布尔值，表示参数是否为 `ArrayBuffer` 的视图实例。

  ```js
  let buffer = new ArrayBuffer(32);
  ArrayBuffer.isView(buffer);   // false

  let v = new Int32Array(buffer);
  ArrayBuffer.isView(v);      // true
  ```

### TypedArray视图

`ArrayBuffer` 可以存放多种数据类型，不同的数据类型有不同的解读方式，这就叫做视图。

`ArrayBuffer` 有两种视图，一种是 `TypedArray` 视图，另一种是 `DataView`视图。前者的数据成员都是同一数据类型，而后者的成员可以是不同的数据类型。

---
更新完毕
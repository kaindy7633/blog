<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [深入浅出Typescript](#%E6%B7%B1%E5%85%A5%E6%B5%85%E5%87%BAtypescript)
  - [前言](#%E5%89%8D%E8%A8%80)
  - [开始](#%E5%BC%80%E5%A7%8B)
    - [工具](#%E5%B7%A5%E5%85%B7)
    - [安装](#%E5%AE%89%E8%A3%85)
    - [环境](#%E7%8E%AF%E5%A2%83)
    - [编写第一个 TypeScript 程序](#%E7%BC%96%E5%86%99%E7%AC%AC%E4%B8%80%E4%B8%AA-typescript-%E7%A8%8B%E5%BA%8F)
  - [Typescript的原始类型](#typescript%E7%9A%84%E5%8E%9F%E5%A7%8B%E7%B1%BB%E5%9E%8B)
    - [布尔类型](#%E5%B8%83%E5%B0%94%E7%B1%BB%E5%9E%8B)
    - [数字](#%E6%95%B0%E5%AD%97)
    - [字符串](#%E5%AD%97%E7%AC%A6%E4%B8%B2)
    - [空值](#%E7%A9%BA%E5%80%BC)
    - [Null 和 Undefined](#null-%E5%92%8C-undefined)
    - [Symbol](#symbol)
    - [BigInt](#bigint)
  - [Typescript中的其他类型](#typescript%E4%B8%AD%E7%9A%84%E5%85%B6%E4%BB%96%E7%B1%BB%E5%9E%8B)
    - [any](#any)
    - [unknown](#unknown)
    - [never](#never)
    - [数组](#%E6%95%B0%E7%BB%84)
    - [元组（Tuple）](#%E5%85%83%E7%BB%84tuple)
    - [Object](#object)
  - [枚举类型](#%E6%9E%9A%E4%B8%BE%E7%B1%BB%E5%9E%8B)
    - [数字枚举](#%E6%95%B0%E5%AD%97%E6%9E%9A%E4%B8%BE)
    - [字符串枚举](#%E5%AD%97%E7%AC%A6%E4%B8%B2%E6%9E%9A%E4%B8%BE)
    - [异构枚举](#%E5%BC%82%E6%9E%84%E6%9E%9A%E4%B8%BE)
    - [反向映射](#%E5%8F%8D%E5%90%91%E6%98%A0%E5%B0%84)
    - [常量枚举](#%E5%B8%B8%E9%87%8F%E6%9E%9A%E4%B8%BE)
    - [联合枚举与枚举成员的类型](#%E8%81%94%E5%90%88%E6%9E%9A%E4%B8%BE%E4%B8%8E%E6%9E%9A%E4%B8%BE%E6%88%90%E5%91%98%E7%9A%84%E7%B1%BB%E5%9E%8B)
    - [联合枚举类型](#%E8%81%94%E5%90%88%E6%9E%9A%E4%B8%BE%E7%B1%BB%E5%9E%8B)
    - [枚举合并](#%E6%9E%9A%E4%B8%BE%E5%90%88%E5%B9%B6)
    - [为枚举添加静态方法](#%E4%B8%BA%E6%9E%9A%E4%B8%BE%E6%B7%BB%E5%8A%A0%E9%9D%99%E6%80%81%E6%96%B9%E6%B3%95)
  - [接口(interface)](#%E6%8E%A5%E5%8F%A3interface)
    - [接口的使用](#%E6%8E%A5%E5%8F%A3%E7%9A%84%E4%BD%BF%E7%94%A8)
    - [可选属性](#%E5%8F%AF%E9%80%89%E5%B1%9E%E6%80%A7)
    - [只读属性](#%E5%8F%AA%E8%AF%BB%E5%B1%9E%E6%80%A7)
    - [函数类型](#%E5%87%BD%E6%95%B0%E7%B1%BB%E5%9E%8B)
    - [属性检查](#%E5%B1%9E%E6%80%A7%E6%A3%80%E6%9F%A5)
    - [可索引类型](#%E5%8F%AF%E7%B4%A2%E5%BC%95%E7%B1%BB%E5%9E%8B)
    - [继承接口](#%E7%BB%A7%E6%89%BF%E6%8E%A5%E5%8F%A3)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# 深入浅出Typescript

## 前言

`Typescript`被誉为 `JavaScript` 的超集, 它可以使用一些尚在提案阶段的语法特性，可以有控制访问符，而最主要的区别就是 `TypeScript` 是一门静态语言

`TypeScript` 是静态弱类型语言，这跟`C`语言是一样的，并不是所谓的强类型，因为要兼容 `JavaScript`， 所以 `TypeScript` 几乎不限制 `JavaScript` 中原有的隐式类型转换，它对类型的隐式转换是有容忍度的，而真正的静态强类型语言比如 `Java`、`C#` 是不会容忍隐式转换的

优点：

- 规避大量低级错误，避免时间浪费，省时
- 减少多人协作项目的成本，大型项目友好，省力
- 良好代码提示，不用反复文件跳转或者翻文档，省心

## 开始

### 工具

在开始使用 `TypeScript` 前你最好有以下准备：

- `Node.js` > 8.0，最好是最新的稳定版（目前是V10.16.3 ）
- 一个包管理工具 `npm` 或者 `yarn`
- 一个文本编辑器或者 `IDE` (如： `vscode`)

### 安装

`TypeScript` 的安装很简单，你可以通过`npm`直接在全局安装 `TypeScript`。

```bash
> npm install -g typescript
```

### 环境

创建一个目录：

```bash
mkdir ts-study && cd ts-study
```

接着创建 `src` 目录：

```bash
mkdir src && touch src/index.ts
```

用`npm`将目录初始化：

```bash
npm init
```

使用 `TypeScript` 的话通常也需要初始化：

```bash
tsc --init
```

这个时候你会发现目录下多了一个`tsconfig.json`文件.

这是 `TypeScript` 的配置文件，里面已经包含官方初始化的一些配置以及注释，我们现在进行自定义的配置：

```json
{
  "compilerOptions": {
    "target": "es5",                            // 指定 ECMAScript 目标版本: 'ES5'
    "module": "commonjs",                       // 指定使用模块: 'commonjs', 'amd', 'system', 'umd' or 'es2015'
    "moduleResolution": "node",                 // 选择模块解析策略
    "experimentalDecorators": true,             // 启用实验性的ES装饰器
    "allowSyntheticDefaultImports": true,       // 允许从没有设置默认导出的模块中默认导入。
    "sourceMap": true,                          // 把 ts 文件编译成 js 文件的时候，同时生成对应的 map 文件
    "strict": true,                             // 启用所有严格类型检查选项
    "noImplicitAny": true,                      // 在表达式和声明上有隐含的 any类型时报错
    "alwaysStrict": true,                       // 以严格模式检查模块，并在每个文件里加入 'use strict'
    "declaration": true,                        // 生成相应的.d.ts文件
    "removeComments": true,                     // 删除编译后的所有的注释
    "noImplicitReturns": true,                  // 不是函数的所有返回路径都有返回值时报错
    "importHelpers": true,                      // 从 tslib 导入辅助工具函数
    "lib": ["es6", "dom"],                      // 指定要包含在编译中的库文件
    "typeRoots": ["node_modules/@types"],
    "outDir": "./dist",
    "rootDir": "./src"
  },
  "include": [                                  // 需要编译的ts文件一个*表示文件匹配**表示忽略文件的深度问题
    "./src/**/*.ts"
  ],
  "exclude": [
    "node_modules",
    "dist",
    "**/*.test.ts",
  ]
}
```

然后在`package.json`中加入我们的`script`命令：

```json
{
  "name": "ts-study",
  "version": "1.0.0",
  "description": "",
  "main": "src/index.ts",
  "scripts": {
    "build": "tsc", // 编译
    "build:w": "tsc -w" // 监听文件，有变动即编译
  },
  "author": "",
  "license": "ISC",
  "devDependencies": {
    "typescript ": "^3.6.4"
  }
}
```

### 编写第一个 TypeScript 程序

在`src/index.ts`中输入以下代码:

```ts
function greeter(person) {
    return "Hello, " + person
}

const user = "Jane User"
```

上面的代码会得到一个错误警告，表示参数具有隐式的类型转换，这是在`tsconfig.js`中配置的，所以我们为参数加上类型说明

```ts
function greeter(person: string) {
  return `Hello ${person}`
}
```

## Typescript的原始类型

`TypeScript`的原始类型包括: `boolean`、`number`、`string`、`void`、`undefined`、`null`、`symbol`、`bigint`。

### 布尔类型

我们用 `boolean` 来表示布尔类型，注意开头是小写的，如果你在`Typescript`文件中写成 `Boolean` 那代表是 `JavaScript` 中的布尔对象

```ts
const isLoading: boolean = false
```

### 数字

`JavaScript`中的二进制、十进制、十六进制等数都可以用 `number` 类型表示。

```ts
const decLiteral: number = 6
const hexLiteral: number = 0xf00d
const binaryLiteral: number = 0b1010
const octalLiteral: number = 0o744
```

### 字符串

```ts
const book: string = '深入浅出 Typescript'
```

### 空值

表示没有任何类型，当一个函数没有返回值时，你通常会见到其返回值类型是 `void`：

```ts
function warnUser(): void {
    alert("This is my warning message");
}
```

实际上只有`null`和`undefined`可以赋给`void`:

```ts
const a: void = undefined
```

### Null 和 Undefined

`TypeScript` 里，`undefined` 和 `null` 两者各自有自己的类型分别叫做 `undefined` 和 `null`，和`void`相似，它们的本身的类型用处不是很大：

```ts
let a: undefined = undefined;
let b: null = null;
```

默认情况下 `null` 和 `undefined` 是所有类型的子类型，就是说你可以把 `null` 和 `undefined` 赋值给 `number` 类型的变量。

但是在正式项目中一般都是开启 `--strictNullChecks` 检测的，即 `null` 和 `undefined` 只能赋值给 `any` 和它们各自(一个例外是 undefined 是也可以分配给void)，可以规避非常多的问题

### Symbol

`Symbol` 是在`ES2015`之后成为新的原始类型,它通过 `Symbol` 构造函数创建:

```ts
const sym1 = Symbol('key1');
const sym2 = Symbol('key2');
```

而且 `Symbol` 的值是唯一不变的：

```ts
Symbol('key1') === Symbol('key1') // false
```

### BigInt

`BigInt` 类型在 `TypeScript3.2` 版本被内置，使用 `BigInt` 可以安全地存储和操作大整数，即使这个数已经超出了`JavaScript`构造函数 `Number` 能够表示的安全整数范围。

在 `JavaScript` 中采用双精度浮点数,这导致精度有限，比如 `Number.MAX_SAFE_INTEGER` 给出了可以安全递增的最大可能整数，即`2**53-1`,我们看一下案例:

```ts
const max = Number.MAX_SAFE_INTEGER;

const max1 = max + 1
const max2 = max + 2

max1 === max2 //true
```

`max1`与`max2`居然相等？这就是超过精读范围造成的问题，而`BigInt`正是解决这类问题而生的:

```ts
// 注意，这里是 JavaScript 代码，并不是 typescript
const max = BigInt(Number.MAX_SAFE_INTEGER);

const max1 = max + 1n
const max2 = max + 2n

max1 === max2 // false
```

如果类型是 `BigInt` ,那么数字后面需要加 `n`

在`TypeScript`中，`number` 类型虽然和 `BigInt` 都是有表示数字的意思，但是实际上两者类型是不同的:

```ts
declare let foo: number;
declare let bar: bigint;

foo = bar; // error: Type 'bigint' is not assignable to type 'number'.
bar = foo; // error: Type 'number' is not assignable to type 'bigint'.
```

## Typescript中的其他类型

上面我们认识了 `Typescript` 中的常见类型，在 `Typescript` 中，还有一些其他类型

- 计算机类型系统理论中的顶级类型，如：`any` 和 `unknown`
- 类型系统中的底部类型，如： `never`
- 非原始类型，如： `object`、数组和元祖

### any

我们可以在需要的时候使用 `any` 类型来标记一些我们还不确定类型的变量或值，比如不希望类型检查器对这些值进行检查而是直接让它们编译通过

```ts
let notSure: any = 4;
notSure = 'manybe a string instead';
```

`any`类型是多人协作项目的大忌，很可能把`Typescript`变成`AnyScript`，通常在不得已的情况下，不应该首先考虑使用此类型

### unknown

`unknown` 是 `TypeScript 3.0` 引入了新类型,是 `any` 类型对应的安全类型。

`unknown` 和 `any` 的主要区别是 `unknown` 类型会更加严格:在对`unknown`类型的值执行大多数操作之前,我们必须进行某种形式的检查,而在对 `any` 类型的值执行操作之前,我们不必进行任何检查。

`unknown` 与 `any` 的不同之处,虽然它们都可以是任何类型,但是当 `unknown` 类型被确定是某个类型之前,它不能被进行任何操作比如实例化、`getter`、函数执行等等

`unknown` 可以帮我们缩小值的类型范围

```ts
function getValue(value: unknown): string {
  // 这里由于把value的类型缩小为Date实例的范围内,所以`value.toISOString()`
  if (value instanceof Date) { 
    return value.toISOString();
  }

  return String(value);
}
```

### never

`never` 类型表示的是那些永不存在的值的类型，`never` 类型是任何类型的子类型，也可以赋值给任何类型；然而，没有类型是 `never` 的子类型或可以赋值给 `never` 类型（除了never本身之外）。

即使`any`也不可以赋值给`never`。

两个场景中 `never` 比较常见:

```ts
// 抛出异常的函数永远不会有返回值
function error(message: string): never {
    throw new Error(message);
}

// 空数组，而且永远是空的
const empty: never[] = []
```

### 数组

数组有两种类型定义方式，一种是使用泛型:

```ts
const list: Array<number> = [1, 2, 3]
```

另一种使用更加广泛那就是在元素类型后面接上 `[]`:

```ts
const list: number[] = [1, 2, 3]
```

### 元组（Tuple）

元组类型与数组类型非常相似，表示一个已知元素数量和类型的数组，它跟数组的区别是各元素的类型不必相同。

比如，你可以定义一对值分别为`string`和`number`类型的元组。

```ts
let x: [string, number];
x = ['hello', 10, false] // Error
x = ['hello'] // Error
```

元组的类型如果多出或者少于规定的类型是会报错的，必须严格跟事先声明的类型一致，即使是顺序错了，也会导致抛出异常

```ts
let x: [string, number];
x = ['hello', 10]; // OK
x = [10, 'hello']; // Error
```

我们可以把元组看成严格版的数组，比如`[string, number]`我们可以看成是:

```ts
interface Tuple extends Array<string | number> {
  0: string;
  1: number;
  length: 2;
}
```

元组继承于数组，但是比数组拥有更严格的类型检查。

### Object

`object` 表示非原始类型，也就是除 `number`，`string`，`boolean`，`symbol`，`null` 或 `undefined` 之外的类型。

```ts
// 这是下一节会提到的枚举类型
enum Direction {
    Center = 1
}

let value: object

value = Direction
value = [1]
value = [1, 'hello']
value = {}
```

我们看到,普通对象、枚举、数组、元组通通都是 `object` 类型。

## 枚举类型

枚举用于声明一组命名的常数,当一个变量有几种可能的取值时,可以将它定义为枚举类型

### 数字枚举

当我们声明一个枚举类型,它们的值是默认的数字类型,而且默认从`0`开始依次累加:

```ts
enum Direction {
  Up,
  Down,
  Left,
  Right
}

console.log(Direction.Up === 0); // true
console.log(Direction.Down === 1); // true
console.log(Direction.Left === 2); // true
console.log(Direction.Right === 3); // true
```

当我们把第一个值赋值后,后面也会根据第一个值进行累加:

```ts
enum Direction {
    Up = 10,
    Down,
    Left,
    Right
}

console.log(Direction.Up, Direction.Down, Direction.Left, Direction.Right); 
// 10 11 12 13
```

### 字符串枚举

枚举类型的值其实也可以是字符串类型：

```ts
enum Direction {
    Up = 'Up',
    Down = 'Down',
    Left = 'Left',
    Right = 'Right'
}

console.log(Direction['Right'], Direction.Up); // Right Up
```

### 异构枚举

如果字符串枚举和数字枚举混合使用，那么它就是异构枚举

```ts
enum BooleanLikeHeterogeneousEnum {
    No = 0,
    Yes = "YES",
}
```

通常情况下我们很少会这样使用枚举，但是从技术的角度来说，它是可行的。

### 反向映射

我们看一个例子：

```ts
enum Direction {
    Up,
    Down,
    Left,
    Right
}

console.log(Direction.Up === 0); // true
console.log(Direction.Down === 1); // true
console.log(Direction.Left === 2); // true
console.log(Direction.Right === 3); // true
```

我们可以通过枚举名字获取枚举值，同时我们也可以通过枚举值获取枚举名字

```ts
enum Direction {
    Up,
    Down,
    Left,
    Right
}

console.log(Direction[0]); // Up
```

### 常量枚举

枚举其实可以被 `const` 声明为常量的, 我们看以下例子:

```ts
const enum Direction {
    Up = 'Up',
    Down = 'Down',
    Left = 'Left',
    Right = 'Right'
}

const a = Direction.Up;
```

被编译为 `JavaScript` 后:

```js
var a = "Up";
```

这就是常量枚举的作用,因为下面的变量 `a` 已经使用过了枚举类型,之后就没有用了,也没有必要存在与 `JavaScript` 中了, `TypeScript` 在这一步就把 `Direction` 去掉了,我们直接使用 `Direction` 的值即可,这是性能提升的一个方案。

如果你非要 `TypeScript` 保留对象 `Direction` ,那么可以添加编译选项 `--preserveConstEnums`

### 联合枚举与枚举成员的类型

如果枚举的所有成员都是字面量类型的值，那么枚举的每个成员和枚举值本身都可以作为类型来使用，

- 任何字符串字面量,如：

  ```ts
  const enum Direction {
      Up = 'Up',
      Down = 'Down',
      Left = 'Left',
      Right = 'Right'
  }
  ```

- 任何数字字面量,如：

  ```ts
  enum Direction {
      Up,
      Down,
      Left,
      Right
  }
  ```

- 应用了一元`-`符号的数字字面量,如:

  ```ts
  enum Direction {
      Up = -1,
      Down = -2,
      Left = -3,
      Right = -4,
  }
  ```

### 联合枚举类型

```ts
enum Direction {
    Up,
    Down,
    Left,
    Right
}

declare let a: Direction

enum Animal {
    Dog,
    Cat
}

a = Direction.Up // ok
a = Animal.Dog // 不能将类型“Animal.Dog”分配给类型“Direction”
```

我们把 `a` 声明为 `Direction` 类型，可以看成我们声明了一个联合类型 `Direction.Up | Direction.Down | Direction.Left | Direction.Right`，只有这四个类型其中的成员才符合要求

### 枚举合并

我们可以分开声明枚举,他们会自动合并

```ts
enum Direction {
    Up = 'Up',
    Down = 'Down',
    Left = 'Left',
    Right = 'Right'
}

enum Direction {
    Center = 1
}
```

### 为枚举添加静态方法

借助 `namespace` 命名空间，我们可以给枚举添加静态方法。

我们举个简单的例子，假设有十二个月份:

```ts
enum Month {
    January,
    February,
    March,
    April,
    May,
    June,
    July,
    August,
    September,
    October,
    November,
    December,
}
```

我们要编写一个静态方法，这个方法可以帮助我们把夏天的月份找出来:

```ts
function isSummer(month: Month) {
    switch (month) {
        case Month.June:
        case Month.July:
        case Month.August:
            return true;
        default:
            return false
    }
}

想要把两者结合就需要借助命名空间的力量了:

``
namespace Month {
    export function isSummer(month: Month) {
        switch (month) {
            case Month.June:
            case Month.July:
            case Month.August:
                return true;
            default:
                return false
        }
    }
}

console.log(Month.isSummer(Month.January)) // false
```

## 接口(interface)

`TypeScript` 的核心原则之一是对值所具有的结构进行类型检查,它有时被称做“鸭式辨型法”或“结构性子类型化”。

在`TypeScript`里，接口的作用就是为这些类型命名和为你的代码或第三方代码定义契约。

### 接口的使用

比如我们有一个函数，这个函数接受一个 `User` 对象，然后返回这个 `User` 对象的 `name` 属性:

```ts
const getUserName = (user) => user.name  // 报错 ，参数 "user" 隐式具有 "any" 类型
```

我们必须用一种类型描述这个 `user` 参数，但是这个类型又不属于上一节介绍到的各种基本类型。

这个时候我们需要 `interface` 来描述这个类型:

```ts
interface User {
    name: string
    age: number
    isMale: boolean
}

const getUserName = (user: User) => user.name
```

这个接口 `User` 描述了参数 `user` 的结构，当然接口不会去检查属性的顺序，只要相应的属性存在并且类型兼容即可

### 可选属性

当我们定义某个 `interface` 时，其中的属性有可能是可选的，那么我们应该如何用接口描述这种情况呢?

我们可以用可选属性描述这种情况, 即在属性后面加上 `?` 号

```ts
interface User {
    name: string
    age?: number
    isMale: boolean
}
```

当我们看到代码提示的时候，这个属性既可能是后面定义的类型也可能是`undefined`

### 只读属性

我们可以利用 `readonly` 把一个属性变成只读性质，此后我们就无法对他进行修改

```ts
interface User {
    name: string
    age?: number
    readonly isMale: boolean
}
```

一旦我们要修改只读属性，就会出现警告

### 函数类型

如果属性值是一个函数，该怎么描述呢?

一种是直接在 `interface` 内部描述函数:

```ts
interface User {
    name: string
    age?: number
    readonly isMale: boolean
    say: (words: string) => string
}
```

另一种方法，我们可以先用接口直接描述函数类型:

```ts
interface Say {
    (words: string) : string
}
```

然后再在其他类型描述中使用：

```ts
interface User {
    name: string
    age?: number
    readonly isMale: boolean
    say: Say
}
```

### 属性检查

对象字面量当被赋值给变量或作为参数传递的时候，会被特殊对待而且经过“额外属性检查”。 如果一个对象字面量存在任何“目标类型”不包含的属性时，你会得到一个错误

```ts
interface Config {
  width?: number;
}

function  CalculateAreas(config: Config): { area: number} {
  let square = 100;
  if (config.width) {
      square = config.width * config.width;
  }
  return {area: square};
}

let mySquare = CalculateAreas({ widdth: 5 });  // error: 'widdth' not expected in type 'Config'
```

目前，解决这类问题有三种方式：

- 使用类型断言：

  ```ts
  let mySquare = CalculateAreas({ widdth: 5 } as Config);
  ```

- 添加字符串索引签名：

  ```ts
  interface Config {
    width?: number;
    [propName: string]: any;
  }
  ```

- 将字面量赋值给另外一个变量：

  ```ts
  let options: any = { widdth: 5 };
  let mySquare = CalculateAreas(options);
  ```

### 可索引类型

当某个属性包含多个不确定类型值的时候，我们可以使用可索引类型表示，可索引类型具有一个索引签名，它描述了对象索引的类型，还有相应的索引返回值类型。

```ts
interface Phone {
    [name: string]: string
}

interface User {
    name: string
    age?: number
    readonly isMale: boolean
    say: () => string
    phone: Phone
}
```

### 继承接口

`interface` 支持继承

```ts
interface VIPUser extends User {
    broadcast: () => void
}
```

你甚至可以继承多个接口:

```ts
interface VIPUser extends User, SupperUser {
    broadcast: () => void
}
```


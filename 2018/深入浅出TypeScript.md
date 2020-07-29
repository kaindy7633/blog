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
  - [类(Class)](#%E7%B1%BBclass)
    - [抽象类](#%E6%8A%BD%E8%B1%A1%E7%B1%BB)
    - [访问限定符](#%E8%AE%BF%E9%97%AE%E9%99%90%E5%AE%9A%E7%AC%A6)
      - [public](#public)
      - [private](#private)
      - [protected](#protected)
    - [class 可以作为接口](#class-%E5%8F%AF%E4%BB%A5%E4%BD%9C%E4%B8%BA%E6%8E%A5%E5%8F%A3)
  - [函数(Function)](#%E5%87%BD%E6%95%B0function)
    - [定义函数类型](#%E5%AE%9A%E4%B9%89%E5%87%BD%E6%95%B0%E7%B1%BB%E5%9E%8B)
    - [函数的参数详解](#%E5%87%BD%E6%95%B0%E7%9A%84%E5%8F%82%E6%95%B0%E8%AF%A6%E8%A7%A3)
      - [可选参数](#%E5%8F%AF%E9%80%89%E5%8F%82%E6%95%B0)
      - [默认参数](#%E9%BB%98%E8%AE%A4%E5%8F%82%E6%95%B0)
      - [剩余参数](#%E5%89%A9%E4%BD%99%E5%8F%82%E6%95%B0)
    - [重载（Overload）](#%E9%87%8D%E8%BD%BDoverload)
  - [泛型（generic）](#%E6%B3%9B%E5%9E%8Bgeneric)
    - [初识泛型](#%E5%88%9D%E8%AF%86%E6%B3%9B%E5%9E%8B)
    - [多个类型参数](#%E5%A4%9A%E4%B8%AA%E7%B1%BB%E5%9E%8B%E5%8F%82%E6%95%B0)
    - [泛型变量](#%E6%B3%9B%E5%9E%8B%E5%8F%98%E9%87%8F)
    - [泛型接口](#%E6%B3%9B%E5%9E%8B%E6%8E%A5%E5%8F%A3)
    - [泛型类](#%E6%B3%9B%E5%9E%8B%E7%B1%BB)
    - [泛型约束](#%E6%B3%9B%E5%9E%8B%E7%BA%A6%E6%9D%9F)
    - [泛型约束与索引类型](#%E6%B3%9B%E5%9E%8B%E7%BA%A6%E6%9D%9F%E4%B8%8E%E7%B4%A2%E5%BC%95%E7%B1%BB%E5%9E%8B)
    - [使用多重类型进行泛型约束](#%E4%BD%BF%E7%94%A8%E5%A4%9A%E9%87%8D%E7%B1%BB%E5%9E%8B%E8%BF%9B%E8%A1%8C%E6%B3%9B%E5%9E%8B%E7%BA%A6%E6%9D%9F)
    - [泛型与 new](#%E6%B3%9B%E5%9E%8B%E4%B8%8E-new)
  - [类型断言与类型守卫](#%E7%B1%BB%E5%9E%8B%E6%96%AD%E8%A8%80%E4%B8%8E%E7%B1%BB%E5%9E%8B%E5%AE%88%E5%8D%AB)
    - [类型断言](#%E7%B1%BB%E5%9E%8B%E6%96%AD%E8%A8%80)
    - [双重断言](#%E5%8F%8C%E9%87%8D%E6%96%AD%E8%A8%80)
    - [类型守卫](#%E7%B1%BB%E5%9E%8B%E5%AE%88%E5%8D%AB)
      - [instanceof](#instanceof)
      - [in](#in)
      - [字面量类型守卫](#%E5%AD%97%E9%9D%A2%E9%87%8F%E7%B1%BB%E5%9E%8B%E5%AE%88%E5%8D%AB)
  - [类型兼容性](#%E7%B1%BB%E5%9E%8B%E5%85%BC%E5%AE%B9%E6%80%A7)
    - [结构类型](#%E7%BB%93%E6%9E%84%E7%B1%BB%E5%9E%8B)
    - [函数的类型兼容性](#%E5%87%BD%E6%95%B0%E7%9A%84%E7%B1%BB%E5%9E%8B%E5%85%BC%E5%AE%B9%E6%80%A7)
    - [枚举的类型兼容性](#%E6%9E%9A%E4%B8%BE%E7%9A%84%E7%B1%BB%E5%9E%8B%E5%85%BC%E5%AE%B9%E6%80%A7)
    - [类的类型兼容性](#%E7%B1%BB%E7%9A%84%E7%B1%BB%E5%9E%8B%E5%85%BC%E5%AE%B9%E6%80%A7)
    - [泛型的类型兼容性](#%E6%B3%9B%E5%9E%8B%E7%9A%84%E7%B1%BB%E5%9E%8B%E5%85%BC%E5%AE%B9%E6%80%A7)
  - [高级类型之交叉类型、联合类型、类型别名](#%E9%AB%98%E7%BA%A7%E7%B1%BB%E5%9E%8B%E4%B9%8B%E4%BA%A4%E5%8F%89%E7%B1%BB%E5%9E%8B%E8%81%94%E5%90%88%E7%B1%BB%E5%9E%8B%E7%B1%BB%E5%9E%8B%E5%88%AB%E5%90%8D)
    - [交叉类型](#%E4%BA%A4%E5%8F%89%E7%B1%BB%E5%9E%8B)
    - [联合类型](#%E8%81%94%E5%90%88%E7%B1%BB%E5%9E%8B)
    - [类型别名](#%E7%B1%BB%E5%9E%8B%E5%88%AB%E5%90%8D)
  - [可辨识联合类型](#%E5%8F%AF%E8%BE%A8%E8%AF%86%E8%81%94%E5%90%88%E7%B1%BB%E5%9E%8B)
    - [字面量类型](#%E5%AD%97%E9%9D%A2%E9%87%8F%E7%B1%BB%E5%9E%8B)
    - [类型字面量](#%E7%B1%BB%E5%9E%8B%E5%AD%97%E9%9D%A2%E9%87%8F)
    - [可辨识联合类型](#%E5%8F%AF%E8%BE%A8%E8%AF%86%E8%81%94%E5%90%88%E7%B1%BB%E5%9E%8B-1)

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

## 类(Class)

传统的面向对象语言基本都是基于类的，在 `ES6` 之后，`JavaScript` 拥有了 `class` 关键字，其本质依然是构造函数

### 抽象类

抽象类做为其它派生类的基类使用,它们一般不会直接被实例化,不同于接口,抽象类可以包含成员的实现细节。

`abstract` 关键字是用于定义抽象类和在抽象类内部定义抽象方法。

比如我们创建一个 `Animal` 抽象类:

```ts
abstract class Animal {
    abstract makeSound(): void;
    move(): void {
        console.log('roaming the earch...');
    }
}
```

我们不能直接实例化抽象类，通常需要我们创建子类继承基类,然后可以实例化子类。

```ts
class Cat extends Animal {

    makeSound() {
        console.log('miao miao')
    }
}

const cat = new Cat()

cat.makeSound() // miao miao
cat.move() // roaming the earch...
```

### 访问限定符

传统面向对象语言通常都有访问限定符，`TypeScript` 中有三类访问限定符，分别是: `public`、`private`、`protected`。

#### public

在 `TypeScript` 的类中，成员都默认为 `public`, 被此限定符修饰的成员是可以被外部访问。

```ts
class Car {
    public run() {
        console.log('启动...')
    }
}

const car = new Car()

car.run() // 启动...
```

#### private

当成员被设置为 `private` 之后, 被此限定符修饰的成员是只可以被类的内部访问

#### protected

当成员被设置为 `protected` 之后, 被此限定符修饰的成员是只可以被类的内部以及类的子类访问。

```ts
class Car {
    protected run() {
        console.log('启动...')
    }
}

class GTR extends Car {
    init() {
        this.run()
    }
}

const car = new Car()
const gtr = new GTR()

car.run() // [ts] 属性“run”受保护，只能在类“Car”及其子类中访问。
gtr.init() // 启动...
gtr.run() // [ts] 属性“run”受保护，只能在类“Car”及其子类中访问。
```

### class 可以作为接口

上一节我们讲到接口（`interface`），实际上类（`class`）也可以作为接口。而把 `class` 作为 `interface` 使用，在 `React` 工程中是很常用的

我们先声明一个类，这个类包含组件 `props` 所需的类型和初始值：

```ts
// props的类型
export default class Props {
  public children: Array<React.ReactElement<any>> | React.ReactElement<any> | never[] = []
  public speed: number = 500
  public height: number = 160
  public animation: string = 'easeInOutQuad'
  public isAuto: boolean = true
  public autoPlayInterval: number = 4500
  public afterChange: () => {}
  public beforeChange: () => {}
  public selesctedColor: string
  public showDots: boolean = true
}
```

当我们需要传入 `props` 类型的时候直接将 `Props` 作为接口传入，此时 `Props` 的作用就是接口，而当需要我们设置`defaultProps`初始值的时候，我们只需要:

```ts
public static defaultProps = new Props()
```

`Props` 的实例就是 `defaultProps` 的初始值，这就是 `class` 作为接口的实际应用，我们用一个 `class` 起到了接口和设置初始值两个作用，方便统一管理，减少了代码量。

## 函数(Function)

函数是 `JavaScript` 应用程序的基础,它帮助你实现抽象层、模拟类、信息隐藏和模块。

在 `TypeScript` 里,虽然已经支持类、命名空间和模块,但函数仍然是主要的定义行为的地方,`TypeScript` 为 `JavaScript` 函数添加了额外的功能，让我们可以更容易地使用。

### 定义函数类型

在 TypeScript 中定义函数:

```ts
const add = (a: number, b: number) => a + b
```

实际上我们只定义了函数的两个参数类型，这个时候整个函数虽然没有被显式定义，但是实际上 `TypeScript` 编译器是能『感知』到这个函数的类型的

### 函数的参数详解

#### 可选参数

一个函数的参数可能是不存在的，这就需要我们使用可选参数来定义.

我们只需要在参数后面加上 `?` 即代表参数可能不存在。

```ts
const add = (a: number, b?: number) => a + (b ? b : 0)
```

参数`b`有`number`与`undefined`两种可能。

#### 默认参数

默认参数在 `JavaScript` 同样存在，即在参数后赋值即可。

```ts
const add = (a: number, b = 10) => a + b
```

#### 剩余参数

剩余参数与`JavaScript`种的语法类似，需要用 `...` 来表示剩余参数，而剩余参数 `rest` 则是一个由`number`组成的数组，在本函数中用 `reduce` 进行了累加求和。

```ts
const add = (a: number, ...rest: number[]) => rest.reduce(((a, b) => a + b), a)
```

### 重载（Overload）

```ts
// 重载
interface Direction {
  top: number,
  bottom?: number,
  left?: number,
  right?: number
}
function assigned(all: number): Direction
function assigned(topAndBottom: number, leftAndRight: number): Direction
function assigned(top: number, right: number, bottom: number, left: number): Direction

function assigned (a: number, b?: number, c?: number, d?: number) {
  if (b === undefined && c === undefined && d === undefined) {
    b = c = d = a
  } else if (c === undefined && d === undefined) {
    c = a
    d = b
  }
  return {
    top: a,
    right: b,
    bottom: c,
    left: d
  }
}

assigned(1)
assigned(1,2)
assigned(1,2,3)
assigned(1,2,3,4)
```

## 泛型（generic）

### 初识泛型

我们需要一个变量，这个变量代表了传入的类型，然后再返回这个变量，它是一种特殊的变量，只用于表示类型而不是值。

这个类型变量在 `TypeScript` 中就叫做「泛型」。

```ts
function returnItem<T>(para: T): T {
    return para
}
```

我们在函数名称后面声明泛型变量 `<T>`，它用于捕获开发者传入的参数类型（比如说`string`），然后我们就可以使用`T`(也就是`string`)做参数类型和返回值类型

### 多个类型参数

定义泛型的时候，可以一次定义多个类型参数，比如我们可以同时定义泛型 `T` 和 泛型 `U`：

```js
function swap<T, U>(tuple: [T, U]): [U, T] {
    return [tuple[1], tuple[0]];
}

swap([7, 'seven']); // ['seven', 7]
```

### 泛型变量

泛型变量 `T` 当做类型的一部分使用，而不是整个类型

```ts
function getArrayLength<T>(arg: Array<T>) {
  
  console.log((arg as Array<any>).length) // ok
  return arg
}
```

### 泛型接口

泛型也可用于接口声明，以上面的函数为例，如果我们将其转化为接口的形式。

```ts
interface ReturnItemFn<T> {
    (para: T): T
}
```

### 泛型类

泛型除了可以在函数中使用，还可以在类中使用，它既可以作用于类本身，也可以作用与类的成员函数。

```ts
class Stack<T> {
    private arr: T[] = []

    public push(item: T) {
        this.arr.push(item)
    }

    public pop() {
        this.arr.pop()
    }
}
```

泛型类看上去与泛型接口差不多， 泛型类使用 <> 括起泛型类型，跟在类名后面。

### 泛型约束

上面的类泛型 `T` 可以是任意类型，如果我们要约束这个类型范围，可以用 `<T extends xx>` 的方式

```ts
type Params = number | string;

class Stack<T extends Params> {
  private arr: T[] = [];

  public push(item: T) {
    this.arr.push(item)
  }

  public pop() {
    this.arr.pop();
  }
}
```

### 泛型约束与索引类型

我们先看一个常见的需求，我们要设计一个函数，这个函数接受两个参数，一个参数为对象，另一个参数为对象上的属性，我们通过这两个参数返回这个属性的值，比如：

```ts
function getValue(obj: object, key: string) {
  return obj[key] // error
}
```

我们会得到一段报错，这是新手 `TypeScript` 开发者常常犯的错误，编译器告诉我们，参数 `obj` 实际上是 `{}`,因此后面的 `key` 是无法在上面取到任何值的。

因为我们给参数 `obj` 定义的类型就是 `object`，在默认情况下它只能是 `{}`，但是我们接受的对象是各种各样的，我们需要一个泛型来表示传入的对象类型，比如 `T extends object`:

```ts
function getValue<T extends object>(obj: T, key: string) {
  return obj[key] // error
}
```

这依然解决不了问题，因为我们第二个参数 `key` 是不是存在于 `obj` 上是无法确定的，因此我们需要对这个 `key` 也进行约束，我们把它约束为只存在于 `obj` 属性的类型，这个时候需要借助到后面我们会进行学习的索引类型进行实现 `<U extends keyof T>`，我们用索引类型 `keyof T` 把传入的对象的属性类型取出生成一个联合类型，这里的泛型 `U` 被约束在这个联合类型中，这样一来函数就被完整定义了：

```ts
function getValue<T extends object, U extends keyof T>(obj: T, key: U) {
  return obj[key] // ok
}
```

比如我们传入以下对象：

```ts
const a = {
  name: 'xiaomuzhu',
  id: 1
}
```

这个时候 `getValue` 第二个参数 `key` 的类型被约束为一个联合类型 `name | id`,他只可能是这两个之一

### 使用多重类型进行泛型约束

我们刚才学习了通过单一类型对泛型进行约束的方式，那么我们再设想以下场景，如果我们的泛型需要被约束，它只被允许实现以下两个接口的类型呢？

```ts
interface FirstInterface {
  doSomething(): number
}

interface SecondInterface {
  doSomethingElse(): string
}
```

我们或许会在一个类中这样使用：

```ts
class Demo<T extends FirstInterface, SecondInterface> {
  private genericProperty: T

  useT() {
    this.genericProperty.doSomething()
    this.genericProperty.doSomethingElse() // 类型“T”上不存在属性“doSomethingElse”
  }
}
```

但是只有 `FirstInterface` 约束了泛型 `T`，`SecondInterface` 并没有生效，上面的方法并不能用两个接口同时约束泛型，那么我们这样使用呢：

```ts
class Demo<T extends FirstInterface, T extends SecondInterface> { // 标识符“T”重复
  ...
}
```

上述的语法就是错误的，那么应该如何用多重类型约束泛型呢?

比如我们就可以将接口 `FirstInterface` 与 `SecondInterface` 作为超接口来解决问题：

```ts
interface ChildInterface extends FirstInterface, SecondInterface {

}
```

这个时候 `ChildInterface` 是 `FirstInterface` 与 `SecondInterface` 的子接口，然后我们通过泛型约束就可以达到多类型约束的目的。

```ts
class Demo<T extends ChildInterface> {
  private genericProperty: T

  useT() {
    this.genericProperty.doSomething()
    this.genericProperty.doSomethingElse()
  }
}
```

我们还可以利用交叉类型来进行多类型约束，如下：

```ts
interface FirstInterface {
  doSomething(): number
}

interface SecondInterface {
  doSomethingElse(): string
}

class Demo<T extends FirstInterface & SecondInterface> {
  private genericProperty: T

  useT() {
    this.genericProperty.doSomething() // ok
    this.genericProperty.doSomethingElse() // ok
  }
}
```

以上就是我们在多个类型约束泛型中的使用技巧。

### 泛型与 new

我们假设需要声明一个泛型拥有构造函数，比如：

```ts
function factory<T>(type: T): T {
  return new type() // This expression is not constructable.
}
```

编译器会告诉我们这个表达式不能构造，因为我们没有声明这个泛型 `T` 是构造函数，这个时候就需要 `new` 的帮助了。

```ts
function factory<T>(type: {new(): T}): T {
  return new type() // ok
}
```

参数 `type` 的类型 `{new(): T}` 就表示此泛型 `T` 是可被构造的，在被实例化后的类型是泛型 `T`

## 类型断言与类型守卫

### 类型断言

有些情况下 `TS` 并不能正确或者准确得推断类型,这个时候可能产生不必要的警告或者报错。

比如初学者经常会遇到的一类问题:

```ts
const person = {};

person.name = 'xiaomuzhu'; // Error: 'name' 属性不存在于 ‘{}’
person.age = 20; // Error: 'age' 属性不存在于 ‘{}’
```

这个时候该怎么办？由于类型推断，这个时候 `person` 的类型就是 `{}`，根本不存在后添加的那些属性，虽然这个写法在`js`中完全没问题，但是开发者知道这个 `person` 实际是有属性的，只是一开始没有声明而已，但是 `typescript` 不知道啊，所以就需要类型断言了:

```ts
interface Person {
  name: string;
  age: number;
}

const person = {} as Person;

person.name = 'xiaomuzhu';
person.age = 20;
```

但是类型断言不要滥用,在万不得已的情况下使用要谨慎,因为你强制把某类型断言会造成 `TypeScript` 丧失代码提示的能力。

### 双重断言

虽然类型断言是有强制性的,但并不是万能的,因为一些情况下也会失效:

```ts
interface Person {
	name: string;
	age: number;
}

const person = 'xiaomuzhu' as Person; // Error
```

这个时候会报错,很显然不能把 `string` 强制断言为一个接口 `Person `,但是并非没有办法,此时可以使用双重断言:

```ts
interface Person {
	name: string;
	age: number;
}

const person = 'xiaomuzhu' as any as Person; // ok
```

先把类型断言为 `any` 再接着断言为你想断言的类型就能实现双重断言，当然上面的例子肯定说不通的，双重断言我们也更不建议滥用，但是在一些少见的场景下也有用武之地，当你遇到事记得有双重断言这个操作即可。

### 类型守卫

类型守卫说白了就是缩小类型的范围，我们看几个例子就容易理解了。

#### instanceof

`instanceof` 类型保护是通过构造函数来细化类型的一种方式.

```ts
class Person {
    name = 'xiaomuzhu';
    age = 20;
}

class Animal {
    name = 'petty';
    color = 'pink';
}

function getSometing(arg: Person | Animal) {
    // 类型细化为 Person
    if (arg instanceof Person) {
        console.log(arg.color); // Error，因为arg被细化为Person，而Person上不存在 color属性
        console.log(arg.age); // ok
    }
    // 类型细化为 Person
    if (arg instanceof Animal) {
        console.log(arg.age); // Error，因为arg被细化为Animal，而Animal上不存在 age 属性
        console.log(arg.color); // ok
    }
}
```

#### in

跟上面的例子类似，`x in y` 表示 `x` 属性在 `y` 中存在。

```ts
class Person {
	name = 'xiaomuzhu';
	age = 20;
}

class Animal {
	name = 'petty';
	color = 'pink';
}

function getSometing(arg: Person | Animal) {
	if ('age' in arg) {
		console.log(arg.color); // Error
		console.log(arg.age); // ok
	}
	if ('color' in arg) {
		console.log(arg.age); // Error
		console.log(arg.color); // ok
	}
}
```

#### 字面量类型守卫

这个功能很重要，在后面的联合辨析类型中会用到此特性，当你在联合类型里使用字面量类型时，它可以帮助检查它们是否有区别:

```ts
type Foo = {
  kind: 'foo'; // 字面量类型
  foo: number;
};

type Bar = {
  kind: 'bar'; // 字面量类型
  bar: number;
};

function doStuff(arg: Foo | Bar) {
  if (arg.kind === 'foo') {
    console.log(arg.foo); // ok
    console.log(arg.bar); // Error
  } else {
    console.log(arg.foo); // Error
    console.log(arg.bar); // ok
  }
}
```

## 类型兼容性

类型兼容性用于确定一个类型是否能赋值给其他类型，这看起来并没有什么太大用处，而实际上当我们了解了兼容性之后才会规避之后实际编程中的很多低级错误。

### 结构类型

`TypeScript` 里的类型兼容性是基于「结构类型」的，结构类型是一种只使用其成员来描述类型的方式，其基本规则是，如果 `x` 要兼容 `y`，那么 `y` 至少具有与 `x` 相同的属性。

我们做一个简单的实验，我们构建一个类 `Person`, 然后声明一个接口 `Dog`，`Dog` 的属性 `Person` 都拥有，而且还多了其他属性，这种情况下 `Dog` 兼容了 `Person`。

```ts
class Person {
    constructor(public weight: number, public name: string, public born: string) {

    }
}

interface Dog {
    name: string
    weight: number
}

let x: Dog

x = new Person(120, 'cxk', '1996-12-12') // OK
```

但如果反过来，`Person` 并没有兼容 `Dog`，因为 `Dog` 的属性比 `Person` 要少了一个。

### 函数的类型兼容性

函数类型的兼容性判断，要查看 `x` 是否能赋值给 `y`，首先看它们的参数列表。

`x` 的每个参数必须能在 `y` 里找到对应类型的参数,注意的是参数的名字相同与否无所谓，只看它们的类型。

这里，`x` 的每个参数在 `y` 中都能找到对应的参数，所以允许赋值:

```ts
let x = (a: number) => 0;
let y = (b: number, s: string) => 0;

y = x; // OK
x = y; // Error 不能将类型“(b: number, s: string) => number”分配给类型“(a: number) => number”。
```

那么当函数的参数中出现了可选参数或者 `rest` 参数时会怎么样呢？

```ts
let foo = (x: number, y: number) => {};
let bar = (x?: number, y?: number) => {};
let bas = (...args: number[]) => {};

foo = bar = bas;
bas = bar = foo;
```

如果你在 `tsconfig.json` 默认配置下上面的兼容性都是没问题的，但是在我们严格检测的环境下还是会报错的

原因就是可选类型的参数可能为 `undefined`，在这种情况下不能与 `number` 兼容。

当我们把 `strictNullChecks` 设置为 `false` 时上述代码是兼容的。

那么甚至他们的参数数量都不一致呢?

```ts
let foo = (x: number, y: number) => {};
let bar = (x?: number) => {};

foo = bar // ok
bar = foo //报错
```

我们看到参数较多的 `foo` 兼容了 `bar`。

### 枚举的类型兼容性

枚举与数字类型相互兼容:

```ts
enum Status {
  Ready,
  Waiting
}

let status = Status.Ready;
let num = 0;

status = num;
num = status;
```

### 类的类型兼容性

仅仅只有实例成员和方法会相比较，构造函数和静态成员不会被检查:

```ts
class Animal {
  feet: number;
  constructor(name: string, numFeet: number) {}
}

class Size {
  feet: number;
  constructor(meters: number) {}
}

let a: Animal;
let s: Size;

a = s; // OK
s = a; // OK
```

私有的和受保护的成员必须来自于相同的类:

```ts
class Animal {
  protected feet: number;
}
class Cat extends Animal {}

let animal: Animal;
let cat: Cat;

animal = cat; // ok
cat = animal; // ok

class Size {
  protected feet: number;
}

let size: Size;

animal = size; // ERROR
size = animal; // ERROR
```

### 泛型的类型兼容性

泛型本身就是不确定的类型,它的表现根据是否被成员使用而不同.

就比如下面代码:

```ts
interface Person<T> {

}

let x : Person<string>
let y : Person<number>

x = y // ok
y = x // ok
```

由于没有被成员使用泛型,所以这里是没问题的。

那么我们再看下面:

```ts
interface Person<T> {
    name: T
}

let x : Person<string>
let y : Person<number>

x = y // 不能将类型“Person<number>”分配给类型“Person<string>”。
y = x // 不能将类型“Person<string>”分配给类型“Person<number>”。
```

这里由于泛型 `T` 被成员 `name` 使用了,所以类型不再兼容。

## 高级类型之交叉类型、联合类型、类型别名

### 交叉类型

交叉类型是将多个类型合并为一个类型。 这让我们可以把现有的多种类型叠加到一起成为一种类型，它包含了所需的所有类型的特性。

在 `JavaScript` 中，混入是一种非常常见的模式，在这种模式中，你可以从两个对象中创建一个新对象，新对象会拥有着两个对象所有的功能。

交叉类型可以让你安全的使用此种模式：

```ts
interface IAnyObject {
    [prop: string]: any
}

function mixin<T extends IAnyObject, U extends IAnyObject>(first: T, second: U): T & U {
  const result = <T & U>{};
  for (let id in first) {
    (<T>result)[id] = first[id];
  }
  for (let id in second) {
    if (!result.hasOwnProperty(id)) {
      (<U>result)[id] = second[id];
    }
  }

  return result;
}
  
const x = mixin({ a: 'hello' }, { b: 42 });

// 现在 x 拥有了 a 属性与 b 属性
const a = x.a;
const b = x.b;
```

### 联合类型

在 `JavaScript` 中，你希望属性为多种类型之一，如字符串或者数组。

这就是联合类型所能派上用场的地方（它使用 `|` 作为标记，如 `string | number`）。

```ts
function formatCommandline(command: string[] | string) {
  let line = '';
  if (typeof command === 'string') {
    line = command.trim();
  } else {
    line = command.join(' ').trim();
  }
}
```

联合类型表示一个值可以是几种类型之一，我们用竖线（`|`）分隔每个类型，所以`number | string | boolean`表示一个值可以是`number`、`string`、或`boolean`。

### 类型别名

类型别名会给一个类型起个新名字,类型别名有时和接口很像,但是可以作用于原始值、联合类型、元组以及其它任何你需要手写的类型.

你可以使用 `type SomeName = someValidTypeAnnotation`的语法来创建类型别名:

```ts
type some = boolean | string

const b: some = true // ok
const c: some = 'hello' // ok
const d: some = 123 // 不能将类型“123”分配给类型“some”
```

此外类型别名可以是泛型:

```ts
type Container<T> = { value: T };
```

也可以使用类型别名来在属性里引用自己：

```ts
type Tree<T> = {
    value: T;
    left: Tree<T>;
    right: Tree<T>;
}
```

类型别名看起来跟 `interface` 非常像，那么应该如何区分两者？

`interface` 只能用于定义对象类型，而 `type` 的声明方式除了对象之外还可以定义交叉、联合、原始类型等，类型声明的方式适用范围显然更加广泛。

但是`interface`也有其特定的用处：

- `interface` 方式可以实现接口的 `extends` 和 `implements`
- `interface` 可以实现接口合并声明

```ts
type Alias = { num: number }
interface Interface {
    num: number;
}
declare function aliased(arg: Alias): Alias;
declare function interfaced(arg: Interface): Interface;
```

此外,接口创建了一个新的名字,可以在其它任何地方使用,类型别名并不创建新名字,比如,错误信息就不会使用别名。

## 可辨识联合类型

在开始之前我们要先搞清楚两个概念「类型字面量」与「字面量类型」,因为会在可辨识联合类型的学习中用到类型字面量的特性.

这看起来非常绕,但是「类型字面量」与「字面量类型」的关系就如同雷锋和雷峰塔一样,它们只是名字有些像,所以容易造成混淆,所以我们专门把两者放在同一节,主要聊一下两者的不同.

### 字面量类型

字面量（`Literal Type`）主要分为 真值字面量类型（`boolean literal types`）、数字字面量类型（`numeric literal types`）、枚举字面量类型（`enum literal types`）、大整数字面量类型（`bigInt literal types`）和字符串字面量类型（`string literal types`）。

```ts
const a: 2333 = 2333 // ok
const ab : 0b10 = 2 // ok
const ao : 0o114 = 0b1001100 // ok
const ax : 0x514 = 0x514 // ok
const b : 0x1919n = 6425n // ok
const c : 'xiaomuzhu' = 'xiaomuzhu' // ok
const d : false = false // ok

const g: 'github' = 'pronhub' // 不能将类型“"pronhub"”分配给类型“"github"”
```

字面量类型的要和实际的值的字面量一一对应,如果不一致就会报错,比如最后一个例子中字面量类型是 `github`,但是值却是 `pronhub`,这就会产生报错.

当字面量类型与联合类型结合的时候,用处就显现出来了,它可以模拟一个类似于枚举的效果:

```ts
type Direction = 'North' | 'East' | 'South' | 'West';

function move(distance: number, direction: Direction) {
    // ...
}
```

### 类型字面量

类型字面量(`Type Literal`)不同于字面量类型（`Literal Type`),它跟 `JavaScript` 中的对象字面量的语法很相似:

```ts
type Foo = {
  baz: [
    number,
    'xiaomuzhu'
  ];
  toString(): string;
  readonly [Symbol.iterator]: 'github';
  0x1: 'foo';
  "bar": 12n;
};
```

你会发现这个结构跟 `interface` 也有点相似,我们在类型别名那一节讲过,在一定程度上类型字面量可以代替接口.

### 可辨识联合类型

我们先假设一个场景,现在有两个功能,一个是创建用户即 `create`,一个是删除用户即 `delete`.

我们先定义一下这个接口,由于创建用户不需要`id`,是系统随机生成的,而删除用户是必须用到 `id` 的,那么代码如下:

```ts
interface Info {
    username: string
}

interface UserAction {
    id?: number
    action: 'create' | 'delete'
    info: Info
}
```

上面的接口是不是有什么问题?

是的,当我们创建用户时是不需要 `id` 的,但是根据上面接口产生的情况,以下代码是合法的:

```ts
const action:UserAction = {
    action:'create',
    id: 111,
    info: {
        username: 'xiaomuzhu'
    }
}
```

但是我们明明不需要 `id` 这个字段,因此我们得用另外的方法,这就用到了上面提到的「类型字面量」了:

```ts
type UserAction = | {
    id: number
    action: 'delete'
    info: Info
} |
{
    action: 'create'
    info: Info
}
```

这似乎完美解决了,那么我们创建一个函数分别处理 `create` 和 `delete` 两者情况,两者的不同之处就在于一个有 `id` 另一个没 `id` 这个字段:

```ts
const UserReducer = (userAction: UserAction) => {
    console.log(userAction.id)
    ...
}
```

我们发现在编写过程中 IDE 就报错了:

类型别名 `UserAction` 是有两个类型字面量联合而成的,我们不知道其中传入的是有没有 `id` 字段的那个类型字面量,因此我们需要找到方法区分出到底是哪个类型字面量.

大家有没有想到最开始提到的「字面量类型」,它的特性不就是唯一性吗?这就是区分两者的钥匙:

```ts
const UserReducer = (userAction: UserAction) => {
    switch (userAction.action) {
        case 'delete':
            console.log(userAction.id);
            break;
        default:
            break;
    }
}
```

我们上面提到了 `userAction.action` 就是辨识的关键,被称为可辨识的标签,我们发现上面这种模式要想实现必须要三个要素:

- 具有普通的单例类型属性—可辨识的特征,上文中就是 `delete` 与 `create` 两个有唯一性的字符串字面量
- 一个类型别名包含联合类型
- 类型守卫的特性,比如我们必须用 `if switch` 来判断 `userAction.action` 是属于哪个类型作用域即 `delete` 与 `create`
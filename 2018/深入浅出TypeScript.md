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


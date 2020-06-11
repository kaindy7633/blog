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


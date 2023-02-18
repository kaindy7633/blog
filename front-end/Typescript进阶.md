<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Typescript进阶](#typescript%E8%BF%9B%E9%98%B6)
  - [原始类型和对象类型](#%E5%8E%9F%E5%A7%8B%E7%B1%BB%E5%9E%8B%E5%92%8C%E5%AF%B9%E8%B1%A1%E7%B1%BB%E5%9E%8B)
    - [原始类型的注解](#%E5%8E%9F%E5%A7%8B%E7%B1%BB%E5%9E%8B%E7%9A%84%E6%B3%A8%E8%A7%A3)
    - [null 与 undefined](#null-%E4%B8%8E-undefined)
    - [void](#void)
    - [数组的类型标注](#%E6%95%B0%E7%BB%84%E7%9A%84%E7%B1%BB%E5%9E%8B%E6%A0%87%E6%B3%A8)
    - [对象的类型标注](#%E5%AF%B9%E8%B1%A1%E7%9A%84%E7%B1%BB%E5%9E%8B%E6%A0%87%E6%B3%A8)
    - [修饰接口属性](#%E4%BF%AE%E9%A5%B0%E6%8E%A5%E5%8F%A3%E5%B1%9E%E6%80%A7)
    - [type 与 interface](#type-%E4%B8%8E-interface)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Typescript进阶

## 原始类型和对象类型

### 原始类型的注解

首先，我们来看 `JavaScript` 的内置原始类型。除了最常见的 `number` / `string` / `boolean` / `null` / `undefined`， `ECMAScript 2015`（ES6）、2020 (ES11) 又分别引入了 2 个新的原始类型：`symbol` 与 `bigint` 。在 `TypeScript` 中它们都有对应的类型注解：

```ts
const name: string = 'linbudu';
const age: number = 24;
const male: boolean = false;
const undef: undefined = undefined;
const nul: null = null;
const obj: object = { name, age, male };
const bigintVar1: bigint = 9007199254740991n;
const bigintVar2: bigint = BigInt(9007199254740991);
const symbolVar: symbol = Symbol('unique');
```

### null 与 undefined

在 `JavaScript` 中，`null` 与 `undefined` 分别表示“这里有值，但是个空值”和“这里没有值”。而在 `TypeScript` 中，`null` 与 `undefined` 类型都是有具体意义的类型

```ts
const tmp1: null = null;
const tmp2: undefined = undefined;
```

### void

`Javascript` 中有 `void`, `TypeScrip` 的原始类型标注中有 `void`，但与 `JavaScript` 中不同的是，这里的 `void` 用于描述一个内部没有 `return` 语句，或者没有显式 `return` 一个值的函数的返回值

### 数组的类型标注

数组同样是我们最常用的类型之一，在 `TypeScript` 中有两种方式来声明一个数组类型：

```ts
const arr1: string[] = [];
const arr2: Array<string> = [];
```

数组是我们在日常开发大量使用的数据结构，但在某些情况下，使用 元组（`Tuple`） 来代替数组要更加妥当，比如在越界访问时

```ts
const arr3: string[] = ['lin', 'bu', 'du'];

console.log(arr3[599]);
```

使用元组类型：

```ts
const arr4: [string, string, string] = ['lin', 'bu', 'du'];

console.log(arr4[599]); // Error: 长度为“3”的元组类型“[string, string, string]”在索引“599“处没有元素
```

在 `TypeScript` 4.0 中，有了具名元组

```ts
const arr7: [name: string, age: number, male: boolean] = ['linbudu', 599, true];
```

### 对象的类型标注

类似于数组类型，在 `TypeScript` 中我们也需要特殊的类型标注来描述对象类型，即 `interface` ，你可以理解为它代表了这个对象对外提供的接口结构

```ts
interface IDescription {
  name: string;
  age: number;
  male: boolean;
}

const obj1: IDescription = {
  name: 'linbudu',
  age: 599,
  male: true,
};
```

### 修饰接口属性

类似于上面的元组可选，在接口结构中同样通过 `?` 来标记一个属性为可选

```ts
interface IDescription {
  name: string;
  age: number;
  male?: boolean;
  func?: Function;
}

const obj2: IDescription = {
  name: 'linbudu',
  age: 599,
  male: true,
  // 无需实现 func 也是合法的
};
```

除了标记一个属性为可选以外，你还可以标记这个属性为只读：`readonly`, 它的作用是防止对象的属性被再次赋值。

```ts
interface IDescription {
  readonly name: string;
  age: number;
}

const obj3: IDescription = {
  name: 'linbudu',
  age: 599,
};

// 无法分配到 "name" ，因为它是只读属性
obj3.name = "林不渡";
```

### type 与 interface

`interface` 用来描述对象、类的结构，而类型别名用来将一个函数签名、一组联合类型、一个工具类型等等抽离成一个完整独立的类型

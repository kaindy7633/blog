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
  - [字面量类型和枚举](#%E5%AD%97%E9%9D%A2%E9%87%8F%E7%B1%BB%E5%9E%8B%E5%92%8C%E6%9E%9A%E4%B8%BE)
    - [字面量类型与联合类型](#%E5%AD%97%E9%9D%A2%E9%87%8F%E7%B1%BB%E5%9E%8B%E4%B8%8E%E8%81%94%E5%90%88%E7%B1%BB%E5%9E%8B)
    - [字面量类型](#%E5%AD%97%E9%9D%A2%E9%87%8F%E7%B1%BB%E5%9E%8B)
    - [联合类型](#%E8%81%94%E5%90%88%E7%B1%BB%E5%9E%8B)
    - [对象字面量类型](#%E5%AF%B9%E8%B1%A1%E5%AD%97%E9%9D%A2%E9%87%8F%E7%B1%BB%E5%9E%8B)
    - [枚举](#%E6%9E%9A%E4%B8%BE)
    - [常量枚举](#%E5%B8%B8%E9%87%8F%E6%9E%9A%E4%B8%BE)
  - [函数与Class类型](#%E5%87%BD%E6%95%B0%E4%B8%8Eclass%E7%B1%BB%E5%9E%8B)
    - [函数](#%E5%87%BD%E6%95%B0)
      - [函数的类型签名](#%E5%87%BD%E6%95%B0%E7%9A%84%E7%B1%BB%E5%9E%8B%E7%AD%BE%E5%90%8D)
      - [void类型](#void%E7%B1%BB%E5%9E%8B)
      - [可选参数与 rest 参数](#%E5%8F%AF%E9%80%89%E5%8F%82%E6%95%B0%E4%B8%8E-rest-%E5%8F%82%E6%95%B0)
      - [重载](#%E9%87%8D%E8%BD%BD)
      - [异步函数、Generator 函数等类型签名](#%E5%BC%82%E6%AD%A5%E5%87%BD%E6%95%B0generator-%E5%87%BD%E6%95%B0%E7%AD%89%E7%B1%BB%E5%9E%8B%E7%AD%BE%E5%90%8D)
    - [Class](#class)
      - [类与类成员的类型签名](#%E7%B1%BB%E4%B8%8E%E7%B1%BB%E6%88%90%E5%91%98%E7%9A%84%E7%B1%BB%E5%9E%8B%E7%AD%BE%E5%90%8D)
      - [修饰符](#%E4%BF%AE%E9%A5%B0%E7%AC%A6)
      - [静态成员](#%E9%9D%99%E6%80%81%E6%88%90%E5%91%98)
      - [继承、实现、抽象类](#%E7%BB%A7%E6%89%BF%E5%AE%9E%E7%8E%B0%E6%8A%BD%E8%B1%A1%E7%B1%BB)
  - [内置类型：any、unknown、never与类型断言](#%E5%86%85%E7%BD%AE%E7%B1%BB%E5%9E%8Banyunknownnever%E4%B8%8E%E7%B1%BB%E5%9E%8B%E6%96%AD%E8%A8%80)
    - [内置类型：any 、unknown 与 never](#%E5%86%85%E7%BD%AE%E7%B1%BB%E5%9E%8Bany-unknown-%E4%B8%8E-never)
    - [虚无的 never 类型](#%E8%99%9A%E6%97%A0%E7%9A%84-never-%E7%B1%BB%E5%9E%8B)
    - [类型断言：警告编译器不准报错](#%E7%B1%BB%E5%9E%8B%E6%96%AD%E8%A8%80%E8%AD%A6%E5%91%8A%E7%BC%96%E8%AF%91%E5%99%A8%E4%B8%8D%E5%87%86%E6%8A%A5%E9%94%99)
    - [双重断言](#%E5%8F%8C%E9%87%8D%E6%96%AD%E8%A8%80)
    - [非空断言](#%E9%9D%9E%E7%A9%BA%E6%96%AD%E8%A8%80)
  - [Typescript类型工具(上)](#typescript%E7%B1%BB%E5%9E%8B%E5%B7%A5%E5%85%B7%E4%B8%8A)
    - [类型别名](#%E7%B1%BB%E5%9E%8B%E5%88%AB%E5%90%8D)
    - [联合类型与交叉类型](#%E8%81%94%E5%90%88%E7%B1%BB%E5%9E%8B%E4%B8%8E%E4%BA%A4%E5%8F%89%E7%B1%BB%E5%9E%8B)
    - [索引类型](#%E7%B4%A2%E5%BC%95%E7%B1%BB%E5%9E%8B)
      - [索引签名类型](#%E7%B4%A2%E5%BC%95%E7%AD%BE%E5%90%8D%E7%B1%BB%E5%9E%8B)
      - [索引类型查询](#%E7%B4%A2%E5%BC%95%E7%B1%BB%E5%9E%8B%E6%9F%A5%E8%AF%A2)
      - [索引类型访问](#%E7%B4%A2%E5%BC%95%E7%B1%BB%E5%9E%8B%E8%AE%BF%E9%97%AE)
    - [映射类型](#%E6%98%A0%E5%B0%84%E7%B1%BB%E5%9E%8B)
  - [Typescript类型工具(下)](#typescript%E7%B1%BB%E5%9E%8B%E5%B7%A5%E5%85%B7%E4%B8%8B)
    - [类型查询操作符：typeof](#%E7%B1%BB%E5%9E%8B%E6%9F%A5%E8%AF%A2%E6%93%8D%E4%BD%9C%E7%AC%A6typeof)
    - [类型守卫](#%E7%B1%BB%E5%9E%8B%E5%AE%88%E5%8D%AB)
  - [泛型](#%E6%B3%9B%E5%9E%8B)
    - [类型别名中的泛型](#%E7%B1%BB%E5%9E%8B%E5%88%AB%E5%90%8D%E4%B8%AD%E7%9A%84%E6%B3%9B%E5%9E%8B)
    - [泛型约束与默认值](#%E6%B3%9B%E5%9E%8B%E7%BA%A6%E6%9D%9F%E4%B8%8E%E9%BB%98%E8%AE%A4%E5%80%BC)
    - [多泛型关联](#%E5%A4%9A%E6%B3%9B%E5%9E%8B%E5%85%B3%E8%81%94)
    - [对象类型中的泛型](#%E5%AF%B9%E8%B1%A1%E7%B1%BB%E5%9E%8B%E4%B8%AD%E7%9A%84%E6%B3%9B%E5%9E%8B)
    - [函数中的泛型](#%E5%87%BD%E6%95%B0%E4%B8%AD%E7%9A%84%E6%B3%9B%E5%9E%8B)
    - [Class 中的泛型](#class-%E4%B8%AD%E7%9A%84%E6%B3%9B%E5%9E%8B)
    - [内置方法中的泛型](#%E5%86%85%E7%BD%AE%E6%96%B9%E6%B3%95%E4%B8%AD%E7%9A%84%E6%B3%9B%E5%9E%8B)
  - [类型系统](#%E7%B1%BB%E5%9E%8B%E7%B3%BB%E7%BB%9F)
    - [结构化类型系统](#%E7%BB%93%E6%9E%84%E5%8C%96%E7%B1%BB%E5%9E%8B%E7%B3%BB%E7%BB%9F)
    - [标称类型系统](#%E6%A0%87%E7%A7%B0%E7%B1%BB%E5%9E%8B%E7%B3%BB%E7%BB%9F)
    - [在 TypeScript 中模拟标称类型系统](#%E5%9C%A8-typescript-%E4%B8%AD%E6%A8%A1%E6%8B%9F%E6%A0%87%E7%A7%B0%E7%B1%BB%E5%9E%8B%E7%B3%BB%E7%BB%9F)
  - [类型系统层级](#%E7%B1%BB%E5%9E%8B%E7%B3%BB%E7%BB%9F%E5%B1%82%E7%BA%A7)
    - [判断类型兼容性的方式](#%E5%88%A4%E6%96%AD%E7%B1%BB%E5%9E%8B%E5%85%BC%E5%AE%B9%E6%80%A7%E7%9A%84%E6%96%B9%E5%BC%8F)
    - [从原始类型开始](#%E4%BB%8E%E5%8E%9F%E5%A7%8B%E7%B1%BB%E5%9E%8B%E5%BC%80%E5%A7%8B)

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

## 字面量类型和枚举

看这样的接口定义：

```ts
interface IRes {
  code: number;
  status: string;
  data: any;
}
```

我们是否可以将 `code`、`status` 字段定义的更准确一些呢？

### 字面量类型与联合类型

我们可以使用联合类型加上字面量类型，把上面的例子改写成这样：

```ts
interface Res {
  code: 10000 | 10001 | 50000;
  status: "success" | "failure";
  data: any;
}
```

### 字面量类型

在 `TypeScript` 中，像上面定义的 `success`、 叫做字面量类型（Literal Types），它代表着比原始类型更精确的类型，同时也是原始类型的子类型

字面量类型主要包括字符串字面量类型、数字字面量类型、布尔字面量类型和对象字面量类型，它们可以直接作为类型标注：

```ts
const str: "linbudu" = "linbudu";
const num: 599 = 599;
const bool: true = true;
```

字面量类型通常和联合类型（即这里的 `|`）一起使用，表达一组字面量类型：

```ts
interface Tmp {
  bool: true | false;
  num: 1 | 2 | 3;
  str: "lin" | "bu" | "du"
}
```

### 联合类型

联合类型代表了一组类型的可用集合，只要最终赋值的类型属于联合类型的成员之一，就可以认为符合这个联合类型

```ts
interface Tmp {
  mixed: true | string | 599 | {} | (() => {}) | (1 | 2)
}
```

### 对象字面量类型

对象字面量类型就是一个对象类型的值

```ts
interface Tmp {
  obj: {
    name: "linbudu",
    age: 18
  }
}

const tmp: Tmp = {
  obj: {
    name: "linbudu",
    age: 18
  }
}
```

总的来说，在需要更精确类型的情况下，我们可以使用字面量类型加上联合类型的方式，将类型从 `string` 这种宽泛的原始类型直接收窄到 `"resolved" | "pending" | "rejected"` 这种精确的字面量类型集合

需要注意的是，无论是原始类型还是对象类型的字面量类型，它们的本质都是类型而不是值

### 枚举

枚举类似于 `Javascript` 中定义的常量值

```ts
enum PageUrl {
  Home_Page_Url = "url1",
  Setting_Page_Url = "url2",
  Share_Page_Url = "url3",
}

const home = PageUrl.Home_Page_Url;
```

使用枚举的好处在于首先有更好的类型提示，其次这些常量会被约束在一个命名空间下

如果你没有声明枚举的值，它会默认使用数字枚举，并且从 0 开始，以 1 递增：

```ts
enum Items {
  Foo, // 0
  Bar, // 1
  Baz  // 2
}
```

`TypeScript` 中也可以同时使用字符串枚举值和数字枚举值：

```ts
enum Mixed {
  Num = 599,
  Str = "linbudu"
}
```

枚举和对象的重要差异在于，对象是单向映射的，我们只能从键映射到键值。而枚举是双向映射的，即你可以从枚举成员映射到枚举值，也可以从枚举值映射到枚举成员：

```ts
enum Items {
  Foo,
  Bar,
  Baz
}

const fooValue = Items.Foo; // 0
const fooKey = Items[0]; // "Foo"
```

但需要注意的是，仅有值为数字的枚举成员才能够进行这样的双向枚举，字符串枚举成员仍然只会进行单次映射

### 常量枚举

常量枚举和枚举相似，只是其声明多了一个 `const`：

```ts
const enum Items {
  Foo,
  Bar,
  Baz
}

const fooValue = Items.Foo; // 0
```

对于常量枚举，你只能通过枚举成员访问枚举值

## 函数与Class类型

### 函数

#### 函数的类型签名

函数的类型就是描述了函数入参类型与函数返回值类型，它们同样使用 `:` 的语法进行类型标注

```ts
function foo(name: string): number {
  return name.length;
}
```

除了上面的函数声明方式，我们还可以通过函数表达式的方式来声明一个函数

```ts
const foo = function (name: string): number {
  return name.length
}
```

如果只是为了描述这个函数的类型结构，我们甚至可以使用 `interface` 来进行函数声明：

```ts
interface FuncFooStruct {
  (name: string): number
}
```

#### void类型

在 `TypeScript` 中，一个没有返回值（即没有调用 `return` 语句）的函数，其返回类型应当被标记为 `void` 而不是 `undefined`，即使它实际的值是 `undefined`

```ts
// 没有调用 return 语句
function foo(): void { }

// 调用了 return 语句，但没有返回值
function bar(): void {
  return;
}
```

在 `TypeScript` 中，`undefined` 类型是一个实际的、有意义的类型值，而 `void` 才代表着空的、没有意义的类型值，使用 `void` 类型能更好地说明这个函数没有进行返回操作

#### 可选参数与 rest 参数

在函数类型中我们也使用 `?` 描述一个可选参数

```ts
// 在函数逻辑中注入可选参数默认值
function foo1(name: string, age?: number): number {
  const inputAge = age || 18; // 或使用 age ?? 18
  return name.length + inputAge
}

// 直接为可选参数声明默认值
function foo2(name: string, age: number = 18): number {
  const inputAge = age;
  return name.length + inputAge
}
```

需要注意的是，可选参数必须位于必选参数之后

`rest` 参数的类型标注也比较简单，由于其实际上是一个数组，这里我们也应当使用数组类型进行标注：

```ts
function foo(arg1: string, ...rest: any[]) { }
```

你也可以使用我们前面学习的元组类型进行标注：

```ts
function foo(arg1: string, ...rest: [number, boolean]) { }

foo("linbudu", 18, true)
```

#### 重载

要想实现与入参关联的返回值类型，我们可以使用 `TypeScript` 提供的函数重载签名（`Overload Signature`）

```ts
function func(foo: number, bar: true): string;
function func(foo: number, bar?: false): number;
function func(foo: number, bar?: boolean): string | number {
  if (bar) {
    return String(foo);
  } else {
    return foo * 599;
  }
}

const res1 = func(599); // number
const res2 = func(599, true); // string
const res3 = func(599, false); // number
```

这三个 `function func` 其实具有不同的意义：

- `function func(foo: number, bar: true): string`，重载签名一，传入 `bar` 的值为 `true` 时，函数返回值为 `string` 类型。
- `function func(foo: number, bar?: false): number`，重载签名二，不传入 `bar`，或传入 `bar` 的值为 `false` 时，函数返回值为 `number` 类型。
- `function func(foo: number, bar?: boolean): string | number`，函数的实现签名，会包含重载签名的所有可能情况

基于重载签名，我们就实现了将入参类型和返回值类型的可能情况进行关联，获得了更精确的类型标注能力。

实际上，`TypeScript` 中的重载更像是伪重载，它只有一个具体实现，其重载体现在方法调用的签名上而非具体实现上

#### 异步函数、Generator 函数等类型签名

对于异步函数、`Generator` 函数、异步 `Generator` 函数的类型签名，其参数签名基本一致，而返回值类型则稍微有些区别

```ts
async function asyncFunc(): Promise<void> {}

function* genFunc(): Iterable<void> {}

async function* asyncGenFunc(): AsyncIterable<void> {}
```

### Class

#### 类与类成员的类型签名

`Class` 的主要结构只有构造函数、属性、方法和访问符（Accessor）

属性的类型标注类似于变量，而构造函数、方法、存取器的类型编标注类似于函数

```ts
class Foo {
  prop: string;

  constructor(inputProp: string) {
    this.prop = inputProp;
  }

  print(addon: string): void {
    console.log(`${this.prop} and ${addon}`)
  }

  get propA(): string {
    return `${this.prop}+A`;
  }

  set propA(value: string) {
    this.prop = `${value}+A`
  }
}
```

`setter` 方法不允许进行返回值的类型标注

就像函数可以通过函数声明与函数表达式创建一样，类也可以通过类声明和类表达式的方式创建。

```ts
const Foo = class {
  prop: string;

  constructor(inputProp: string) {
    this.prop = inputProp;
  }

  print(addon: string): void {
    console.log(`${this.prop} and ${addon}`)
  }
  
  // ...
}
```

#### 修饰符

在 `TypeScript` 中我们能够为 `Class` 成员添加这些修饰符：`public` / `private` / `protected` / `readonly`。除 `readonly` 以外，其他三位都属于访问性修饰符，而 `readonly` 属于操作性修饰符

```ts
class Foo {
  private prop: string;

  constructor(inputProp: string) {
    this.prop = inputProp;
  }

  protected print(addon: string): void {
    console.log(`${this.prop} and ${addon}`)
  }

  public get propA(): string {
    return `${this.prop}+A`;
  }

  public set propA(value: string) {
    this.propA = `${value}+A`
  }
}
```

我们可以在构造函数中对参数应用访问性修饰符

```ts
class Foo {
  constructor(public arg1: string, private arg2: boolean) { }
}

new Foo("linbudu", true)
```

#### 静态成员

在 `TypeScript` 中，你可以使用 `static` 关键字来标识一个成员为静态成员

```ts
class Foo {
  static staticHandler() { }

  public instanceHandler() { }
}
```

不同于实例成员，在类的内部静态成员无法通过 `this` 来访问，需要通过 `Foo.staticHandler` 这种形式进行访问

静态成员直接被挂载在函数体上，而实例成员挂载在原型上，这就是二者的最重要差异：静态成员不会被实例继承，它始终只属于当前定义的这个类（以及其子类）。而原型对象上的实例成员则会沿着原型链进行传递，也就是能够被继承

#### 继承、实现、抽象类

`TypeScript` 中也使用 `extends` 关键字来实现继承：

```ts
class Base { }

class Derived extends Base { }
```

对于这里的两个类，比较严谨的称呼是 基类（`Base`） 与 派生类（`Derived`），关于基类与派生类，我们需要了解的主要是派生类对基类成员的访问与覆盖操作。

派生类中可以访问到使用 `public` 或 `protected` 修饰符的基类成员。除了访问以外，基类中的方法也可以在派生类中被覆盖，但我们仍然可以通过 `super` 访问到基类中的方法

```ts
class Base {
  print() { }
}

class Derived extends Base {
  print() {
    super.print()
    // ...
  }
}
```

`TypeScript 4.3` 新增了 `override` 关键字，来确保派生类尝试覆盖的方法一定在基类中存在定义

```ts
class Base {
  printWithLove() { }
}

class Derived extends Base {
  override print() {
    // ...
  }
}

// Error: 尝试覆盖的方法并未在基类中声明
```

抽象类是对类结构与方法的抽象，简单来说，一个抽象类描述了一个类中应当有哪些成员（属性、方法等），一个抽象方法描述了这一方法在实际实现中的结构。我们知道类的方法和函数非常相似，包括结构，因此抽象方法其实描述的就是这个方法的入参类型与返回值类型

抽象类使用 `abstract` 关键字声明：

```ts
abstract class AbsFoo {
  abstract absProp: string;
  abstract get absGetter(): string;
  abstract absMethod(name: string): string
}
```

抽象类中的成员也需要使用 `abstract` 关键字才能被视为抽象类成员，如这里的抽象方法。我们可以实现（`implements`）一个抽象类：

```ts
class Foo implements AbsFoo {
  absProp: string = "linbudu"

  get absGetter() {
    return "linbudu"
  }

  absMethod(name: string) {
    return name
  }
}
```

在 `TypeScript` 中无法声明静态的抽象成员。

`interface` 不仅可以声明函数结构，也可以声明类的结构：

```ts
interface FooStruct {
  absProp: string;
  get absGetter(): string;
  absMethod(input: string): string
}

class Foo implements FooStruct {
  absProp: string = "linbudu"

  get absGetter() {
    return "linbudu"
  }

  absMethod(name: string) {
    return name
  }
}
```

## 内置类型：any、unknown、never与类型断言

我们可以使用 `TypeScript` 提供的内置类型在类型世界里获得更好的编程体验。内置的可用于标注的类型，包括 any、unknown 与 never

### 内置类型：any 、unknown 与 never

为了能够表示“任意类型”，`TypeScript` 中提供了一个内置类型 `any` ，来表示所谓的任意类型

```ts
log(message?: any, ...optionalParams: any[]): void
```

在某些情况下你的变量/参数也会被隐式地推导为 `any`。比如使用 `let` 声明一个变量但不提供初始值，以及不为函数参数提供类型标注：

```ts
// any
let foo;

// foo、bar 均为 any
function func(foo, bar){}
```

以上的函数声明在 `tsconfig` 中启用了 `noImplicitAny` 时会报错，你可以显式为这两个参数指定 `any` 类型。你可以在 `any` 类型变量上任意地进行操作，包括赋值、访问、方法调用等等，此时可以认为类型推导与检查是被完全禁用的

为了避免滥用 `any`，请记住下面的规则：

- 如果是类型不兼容报错导致你使用 `any`，考虑用类型断言替代。
- 如果是类型太复杂导致你不想全部声明而使用 `any`，考虑将这一处的类型去断言为你需要的最简类型。
- 如果你是想表达一个未知类型，更合理的方式是使用 `unknown`

`unknown` 类型和 `any` 类型有些类似，一个 `unknown` 类型的变量可以再次赋值为任意其它类型，但只能赋值给 `any` 与 `unknown` 类型的变量

`unknown` 类型区别于 `any` 之处在于， `unknown` 在未来一定会得到一个确定的类型。

内置类型 `never` 就是这么一个“什么都没有”的类型

### 虚无的 never 类型

`never` 是一个“什么都没有”的类型，它甚至不包括空的类型，严格来说，`never` 类型不携带任何的类型信息，因此会在联合类型中被直接移除

在编程语言的类型系统中，`never` 类型被称为 `Bottom Type`，是整个类型系统层级中最底层的类型。和 `null`、`undefined` 一样，它是所有类型的子类型，但只有 `never` 类型的变量能够赋值给另一个 `never` 类型变量

通常我们不会显式地声明一个 `never` 类型，它主要被类型检查所使用。但在某些情况下使用 `never` 确实是符合逻辑的，比如一个只负责抛出错误的函数：

```ts
function justThrow(): never {
  throw new Error()
}
```

### 类型断言：警告编译器不准报错

类型断言能够显式告知类型检查程序当前这个变量的类型，可以进行类型分析地修正、类型。它其实就是一个将变量的已有类型更改为新指定类型的操作，它的基本语法是 `as NewType`

```ts
let unknownVar: unknown;

(unknownVar as { foo: () => {} }).foo();
```

在联合类型中断言一个具体的分支：

```ts
function foo(union: string | number) {
  if ((union as string).includes("linbudu")) { }

  if ((union as number).toFixed() === '599') { }
}
```

### 双重断言

如果在使用类型断言时，原类型与断言类型之间差异过大，`TypeScript` 会给你一个类型报错：

```ts
const str: string = "linbudu";

// 从 X 类型 到 Y 类型的断言可能是错误的，blabla
(str as { handler: () => {} }).handler()
```

这是因为你的断言类型和原类型的差异太大，需要先断言到一个通用的类，即 `any / unknown`。这一通用类型包含了所有可能的类型，因此断言到它和从它断言到另一个类型差异不大

### 非空断言

非空断言其实是类型断言的简化，它使用 `!` 语法，即 `obj!.func()!.prop` 的形式标记前面的一个声明一定是非空的

## Typescript类型工具(上)

类型工具顾名思义，它就是对类型进行处理的工具。如果按照使用方式来划分，类型工具可以分成三类：操作符、关键字与专用语法

而按照使用目的来划分，类型工具可以分为 类型创建 与 类型安全保护 两类

### 类型别名

通过 `type` 关键字声明了一个类型别名 `A` ，同时它的类型等价于 `string` 类型。类型别名的作用主要是对一组类型或一个特定类型结构进行封装，以便于在其它地方进行复用

```ts
type A = string;
```

抽离一组联合类型：

```ts
type StatusCode = 200 | 301 | 400 | 500 | 502;
type PossibleDataTypes = string | number | (() => unknown);

const status: StatusCode = 502;
```

抽离一个函数类型：

```ts
type Handler = (e: Event) => void;

const clickHandler: Handler = (e) => { };
const moveHandler: Handler = (e) => { };
const dragHandler: Handler = (e) => { };
```

声明一个对象类型:

```ts
type ObjType = {
  name: string;
  age: number;
}
```

类型别名还能作为工具类型, 工具类同样基于类型别名，只是多了个泛型。在类型别名中，类型别名可以这么声明自己能够接受泛型（我称之为泛型坑位）。一旦接受了泛型，我们就叫它工具类型：

```ts
type Factory<T> = T | number | string;
```

声明一个简单、有实际意义的工具类型：

```ts
type MaybeNull<T> = T | null;
```

这个工具类型会接受一个类型，并返回一个包括 `null` 的联合类型。这样一来，在实际使用时就可以确保你处理了可能为空值的属性读取与方法调用：

```ts
type MaybeNull<T> = T | null;

function process(input: MaybeNull<{ handler: () => {} }>) {
  input?.handler();
}
```

```ts
type MaybeArray<T> = T | T[];

function ensureArray<T>(input: MaybeArray<T>): T[] {
  return Array.isArray(input) ? input : [input];
}
```

### 联合类型与交叉类型

联合类型还有一个和它有点像的孪生兄弟：交叉类型。它和联合类型的使用位置一样，只不过符号是 `&`，即按位与运算符

实际上，正如联合类型的符号是`|`，它代表了按位或，即只需要符合联合类型中的一个类型，既可以认为实现了这个联合类型，如`A | B`，只需要实现 `A` 或 `B` 即可

而代表着按位与的 `&` 则不同，你需要符合这里的所有类型，才可以说实现了这个交叉类型，即 `A & B`，需要同时满足 `A` 与 `B` 两个类型才行

```ts
interface NameStruct {
  name: string;
}

interface AgeStruct {
  age: number;
}

type ProfileStruct = NameStruct & AgeStruct;

const profile: ProfileStruct = {
  name: "linbudu",
  age: 18
}
```

对于对象类型的交叉类型，其内部的同名属性类型同样会按照交叉类型进行合并：

```ts
type Struct1 = {
  primitiveProp: string;
  objectProp: {
    name: string;
  }
}

type Struct2 = {
  primitiveProp: number;
  objectProp: {
    age: number;
  }
}

type Composed = Struct1 & Struct2;

type PrimitivePropType = Composed['primitiveProp']; // never
type ObjectPropType = Composed['objectProp']; // { name: string; age: number; }
```

### 索引类型

索引类型包含三个部分：索引签名类型、索引类型查询与索引类型访问，它们唯一共同点是，它们都通过索引的形式来进行类型操作，但索引签名类型是声明，后两者则是读取

#### 索引签名类型

索引签名类型主要指的是在接口或类型别名中，通过以下语法来快速声明一个键值类型一致的类型结构：

```ts
interface AllStringTypes {
  [key: string]: string;
}

type AllStringTypes = {
  [key: string]: string;
}
```

#### 索引类型查询

索引类型查询，也就是 `keyof` 操作符, 它可以将对象中的所有键转换为对应字面量类型，然后再组合成联合类型。注意，这里并不会将数字类型的键名转换为字符串类型字面量，而是仍然保持为数字类型字面量。

```ts
interface Foo {
  linbudu: 1,
  599: 2
}

type FooKeys = keyof Foo; // "linbudu" | 599
```

#### 索引类型访问

```ts
interface Foo {
  propA: number;
  propB: boolean;
}

type PropAType = Foo['propA']; // number
type PropBType = Foo['propB']; // boolean
```

### 映射类型

映射类型的主要作用即是基于键名映射到键值类型

```ts
type Stringify<T> = {
  [K in keyof T]: string;
};
```

这个工具类型会接受一个对象类型，使用 `keyof` 获得这个对象类型的键名组成字面量联合类型，然后通过映射类型（即这里的 `in` 关键字）将这个联合类型的每一个成员映射出来，并将其键值类型设置为 `string`

```ts
interface Foo {
  prop1: string;
  prop2: number;
  prop3: boolean;
  prop4: () => void;
}

type StringifiedFoo = Stringify<Foo>;

// 等价于
interface StringifiedFoo {
  prop1: string;
  prop2: string;
  prop3: string;
  prop4: string;
}
```

## Typescript类型工具(下)

上一节讲述的类型工具的作用是基于已有的类型去创建出新的类型，而除了类型的创建以外，就是两个主要用于类型安全的类型工具：类型查询操作符与类型守卫。

### 类型查询操作符：typeof

`TypeScript` 存在两种功能不同的 `typeof` 操作符。我们最常见的一种 `typeof` 操作符就是 `JavaScript` 中，用于检查变量类型的 `typeof` ，它会返回 `"string"` / `"number"` / `"object"` / `"undefined"` 等值。而除此以外， `TypeScript` 还新增了用于类型查询的 `typeof` ，即 `Type Query Operator`，这个 `typeof` 返回的是一个 `TypeScript` 类型：

```ts
const str = "linbudu";

const obj = { name: "linbudu" };

const nullVar = null;
const undefinedVar = undefined;

const func = (input: string) => {
  return input.length > 10;
}

type Str = typeof str; // "linbudu"
type Obj = typeof obj; // { name: string; }
type Null = typeof nullVar; // null
type Undefined = typeof undefined; // undefined
type Func = typeof func; // (input: string) => boolean
```

### 类型守卫

`TypeScript` 引入了 `is` 关键字来显式地提供类型信息：

```ts
function isString(input: unknown): input is string {
  return typeof input === "string";
}

function foo(input: string | number) {
  if (isString(input)) {
    // 正确了
    (input).replace("linbudu", "linbudu599")
  }
  if (typeof input === 'number') { }
  // ...
}
```

`is string`，即 `is` 关键字 + 预期类型，即如果这个函数成功返回为 `true`，那么 `is` 关键字前这个入参的类型，就会被这个类型守卫调用方后续的类型控制流分析收集到。

从这个角度来看，其实类型守卫有些类似于类型断言，但类型守卫更宽容，也更信任你一些。你指定什么类型，它就是什么类型

## 泛型

### 类型别名中的泛型

类型别名中的泛型，等价于一个接受参数的函数：

```ts
type Factory<T> = T | number | string;
```

类型别名中的泛型大多是用来进行工具类型封装:

```ts
type Stringify<T> = {
  [K in keyof T]: string;
};

type Clone<T> = {
  [K in keyof T]: T[K];
};
```

来看一个 `TypeScript` 的内置工具类型实现：

```ts
type Partial<T> = {
    [P in keyof T]?: T[P];
};
```

类型别名与泛型的结合中，还有一个是条件类型

```ts
type IsEqual<T> = T extends true ? 1 : 2;

type A = IsEqual<true>; // 1
type B = IsEqual<false>; // 2
type C = IsEqual<'linbudu'>; // 2
```

### 泛型约束与默认值

泛型也有着默认值的设定：

```ts
type Factory<T = boolean> = T | number | string;
```

泛型约束可以要求传入这个工具类型的泛型必须符合某些条件，否则你就拒绝进行后面的逻辑

```ts
function add(source: number, add: number){
  if(typeof source !== 'number' || typeof add !== 'number'){
    throw new Error("Invalid arguments!")
  }
  
  return source + add;
}
```

在泛型中，我们可以使用 `extends` 关键字来约束传入的泛型参数必须符合要求

```ts
type ResStatus<ResCode extends number> = ResCode extends 10000 | 10001 | 10002
  ? 'success'
  : 'failure';
```

### 多泛型关联

我们可以同时传入多个泛型参数，还可以让这几个泛型参数之间也存在联系

```ts
type Conditional<Type, Condition, TruthyResult, FalsyResult> =
  Type extends Condition ? TruthyResult : FalsyResult;

//  "passed!"
type Result1 = Conditional<'linbudu', string, 'passed!', 'rejected!'>;

// "rejected!"
type Result2 = Conditional<'linbudu', boolean, 'passed!', 'rejected!'>;
```

多泛型参数其实就像接受更多参数的函数，其内部的运行逻辑（类型操作）会更加抽象，表现在参数（泛型参数）需要进行的逻辑运算（类型操作）会更加复杂

### 对象类型中的泛型

下面是一个响应类型结构的泛型处理：

```ts
interface IRes<TData = unknown> {
  code: number;
  error?: string;
  data: TData;
}
```

实际例子：

```ts
interface IUserProfileRes {
  name: string;
  homepage: string;
  avatar: string;
}

function fetchUserProfile(): Promise<IRes<IUserProfileRes>> {}

type StatusSucceed = boolean;
function handleOperation(): Promise<IRes<StatusSucceed>> {}
```

泛型嵌套的场景也非常常用，比如对存在分页结构的数据，我们也可以将其分页的响应结构抽离出来：

```ts
interface IPaginationRes<TItem = unknown> {
  data: TItem[];
  page: number;
  totalCount: number;
  hasNextPage: boolean;
}

function fetchUserProfileList(): Promise<IRes<IPaginationRes<IUserProfileRes>>> {}
```

### 函数中的泛型

```ts
function handle<T>(input: T): T {}
```

我们为函数声明了一个泛型参数 `T`，并将参数的类型与返回值类型指向这个泛型参数。这样，在这个函数接收到参数时，`T` 会自动地被填充为这个参数的类型。这也就意味着你不再需要预先确定参数的可能类型了，而在返回值与参数类型关联的情况下，也可以通过泛型参数来进行运算

对于箭头函数的泛型，其书写方式是这样的：

```ts
const handle = <T>(input: T): T => {}
```

在 `tsx` 文件中，可以这样写：

```ts
const handle = <T extends any>(input: T): T => {}
```

### Class 中的泛型

`Class` 中的泛型消费方是属性、方法、乃至装饰器等

```ts
class Queue<TElementType> {
  private _list: TElementType[];

  constructor(initial: TElementType[]) {
    this._list = initial;
  }

  // 入队一个队列泛型子类型的元素
  enqueue<TType extends TElementType>(ele: TType): TElementType[] {
    this._list.push(ele);
    return this._list;
  }

  // 入队一个任意类型元素（无需为队列泛型子类型）
  enqueueWithUnknownType<TType>(element: TType): (TElementType | TType)[] {
    return [...this._list, element];
  }

  // 出队
  dequeue(): TElementType[] {
    this._list.shift();
    return this._list;
  }
}
```

### 内置方法中的泛型

`TypeScript` 中为非常多的内置对象都预留了泛型坑位，如 `Promise` 中

```ts
function p() {
  return new Promise<boolean>((resolve, reject) => {
    resolve(true);
  });
}
```

还有数组 `Array<T>` 当中，其泛型参数代表数组的元素类型

```ts
const arr: Array<number> = [1, 2, 3];
```

## 类型系统

### 结构化类型系统

首先看下面的例子：

```ts
class Cat {
  eat() { }
}

class Dog {
  eat() { }
}

function feedCat(cat: Cat) { }

feedCat(new Dog())
```

`TypeScript` 比较两个类型并非通过类型的名称，而是比较这两个类型上实际拥有的属性与方法，虽然是两个名字不同的类型，但仍然被视为结构一致，这就是结构化类型系统的特性

结构类型的别称鸭子类型（`Duck Typing`），这个名字来源于鸭子测试（`Duck Test`）。其核心理念是，如果你看到一只鸟走起来像鸭子，游泳像鸭子，叫得也像鸭子，那么这只鸟就是鸭子

严格来说，鸭子类型系统和结构化类型系统并不完全一致，结构化类型系统意味着基于完全的类型结构来判断类型兼容性，而鸭子类型则只基于运行时访问的部分来决定

除了基于类型结构进行兼容性判断的结构化类型系统以外，还有一种基于类型名进行兼容性判断的类型系统，标称类型系统。

### 标称类型系统

标称类型系统（`Nominal Typing System`）要求，两个可兼容的类型，其名称必须是完全一致的，比如以下代码：

```ts
type USD = number;
type CNY = number;

const CNYCount: CNY = 200;
const USDCount: USD = 200;

function addCNY(source: CNY, input: CNY) {
  return source + input;
}

addCNY(CNYCount, USDCount)
```

在标称类型系统中，`CNY` 与 `USD` 被认为是两个完全不同的类型

### 在 TypeScript 中模拟标称类型系统

类型的重要意义之一是限制了数据的可用操作与实际意义。这往往是通过类型附带的额外信息来实现的（类似于元数据）

## 类型系统层级

类型层级实际上指的是，`TypeScript` 中所有类型的兼容关系，从最上面一层的 `any` 类型，到最底层的 `never` 类型

### 判断类型兼容性的方式

在需要判断多个类型的层级时，条件类型更为直观，而如果只是两个类型之间的兼容性判断时，使用类型声明则更好理解一些

```ts
declare let source: string;

declare let anyType: any;
declare let neverType: never;

anyType = source;

// 不能将类型“string”分配给类型“never”。
neverType = source;
```

### 从原始类型开始

原始类型、对象类型和它们对应的字面量类型：

```ts
type Result1 = "linbudu" extends string ? 1 : 2; // 1
type Result2 = 1 extends number ? 1 : 2; // 1
type Result3 = true extends boolean ? 1 : 2; // 1
type Result4 = { name: string } extends object ? 1 : 2; // 1
type Result5 = { name: 'linbudu' } extends object ? 1 : 2; // 1
type Result6 = [] extends object ? 1 : 2; // 1
```

一个基础类型和它们对应的字面量类型必定存在父子类型关系, 字面量类型 < 对应的原始类型。

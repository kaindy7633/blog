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
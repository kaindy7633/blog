<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [TypeScript简明指南](#typescript%E7%AE%80%E6%98%8E%E6%8C%87%E5%8D%97)
  - [快速上手 Typescript](#%E5%BF%AB%E9%80%9F%E4%B8%8A%E6%89%8B-typescript)
    - [安装 Typescript](#%E5%AE%89%E8%A3%85-typescript)
    - [构建 Typescript 文件](#%E6%9E%84%E5%BB%BA-typescript-%E6%96%87%E4%BB%B6)
    - [如何编译?](#%E5%A6%82%E4%BD%95%E7%BC%96%E8%AF%91)
    - [类型注解](#%E7%B1%BB%E5%9E%8B%E6%B3%A8%E8%A7%A3)
    - [接口](#%E6%8E%A5%E5%8F%A3)
    - [类](#%E7%B1%BB)
  - [基础类型](#%E5%9F%BA%E7%A1%80%E7%B1%BB%E5%9E%8B)
    - [布尔值 Boolean](#%E5%B8%83%E5%B0%94%E5%80%BC-boolean)
    - [数字 Number](#%E6%95%B0%E5%AD%97-number)
    - [字符串 String](#%E5%AD%97%E7%AC%A6%E4%B8%B2-string)
    - [数组 Array](#%E6%95%B0%E7%BB%84-array)
    - [元组 Tuple](#%E5%85%83%E7%BB%84-tuple)
    - [枚举 Enum](#%E6%9E%9A%E4%B8%BE-enum)
    - [Any](#any)
    - [Void](#void)
    - [Null 和 Undefined](#null-%E5%92%8C-undefined)
    - [Never](#never)
    - [Object](#object)
    - [类型断言](#%E7%B1%BB%E5%9E%8B%E6%96%AD%E8%A8%80)
  - [变量声明](#%E5%8F%98%E9%87%8F%E5%A3%B0%E6%98%8E)
    - [解构](#%E8%A7%A3%E6%9E%84)
    - [扩展运算符 (...)](#%E6%89%A9%E5%B1%95%E8%BF%90%E7%AE%97%E7%AC%A6-)
  - [接口](#%E6%8E%A5%E5%8F%A3-1)
    - [定义](#%E5%AE%9A%E4%B9%89)
    - [可选属性](#%E5%8F%AF%E9%80%89%E5%B1%9E%E6%80%A7)
    - [只读属性](#%E5%8F%AA%E8%AF%BB%E5%B1%9E%E6%80%A7)
    - [额外的属性检查](#%E9%A2%9D%E5%A4%96%E7%9A%84%E5%B1%9E%E6%80%A7%E6%A3%80%E6%9F%A5)
    - [函数类型](#%E5%87%BD%E6%95%B0%E7%B1%BB%E5%9E%8B)
    - [可索引类型](#%E5%8F%AF%E7%B4%A2%E5%BC%95%E7%B1%BB%E5%9E%8B)
    - [类类型](#%E7%B1%BB%E7%B1%BB%E5%9E%8B)
    - [继承接口](#%E7%BB%A7%E6%89%BF%E6%8E%A5%E5%8F%A3)
    - [接口继承类](#%E6%8E%A5%E5%8F%A3%E7%BB%A7%E6%89%BF%E7%B1%BB)
  - [类](#%E7%B1%BB-1)
    - [定义](#%E5%AE%9A%E4%B9%89-1)
    - [继承](#%E7%BB%A7%E6%89%BF)
    - [公共、私有和受保护的修饰符](#%E5%85%AC%E5%85%B1%E7%A7%81%E6%9C%89%E5%92%8C%E5%8F%97%E4%BF%9D%E6%8A%A4%E7%9A%84%E4%BF%AE%E9%A5%B0%E7%AC%A6)
    - [readonly修饰符](#readonly%E4%BF%AE%E9%A5%B0%E7%AC%A6)
    - [存取器](#%E5%AD%98%E5%8F%96%E5%99%A8)
    - [静态属性](#%E9%9D%99%E6%80%81%E5%B1%9E%E6%80%A7)
    - [抽象类](#%E6%8A%BD%E8%B1%A1%E7%B1%BB)
  - [函数](#%E5%87%BD%E6%95%B0)
    - [函数类型](#%E5%87%BD%E6%95%B0%E7%B1%BB%E5%9E%8B-1)
    - [可选参数和默认参数](#%E5%8F%AF%E9%80%89%E5%8F%82%E6%95%B0%E5%92%8C%E9%BB%98%E8%AE%A4%E5%8F%82%E6%95%B0)
    - [剩余参数](#%E5%89%A9%E4%BD%99%E5%8F%82%E6%95%B0)
  - [泛型](#%E6%B3%9B%E5%9E%8B)
    - [泛型接口](#%E6%B3%9B%E5%9E%8B%E6%8E%A5%E5%8F%A3)
    - [泛型类](#%E6%B3%9B%E5%9E%8B%E7%B1%BB)
  - [枚举](#%E6%9E%9A%E4%B8%BE)
    - [数字枚举](#%E6%95%B0%E5%AD%97%E6%9E%9A%E4%B8%BE)
    - [字符串枚举](#%E5%AD%97%E7%AC%A6%E4%B8%B2%E6%9E%9A%E4%B8%BE)
    - [异构枚举](#%E5%BC%82%E6%9E%84%E6%9E%9A%E4%B8%BE)
  - [类型推论](#%E7%B1%BB%E5%9E%8B%E6%8E%A8%E8%AE%BA)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# TypeScript简明指南

## 快速上手 Typescript

### 安装 Typescript

```ts
> npm install -g typescript
```

### 构建 Typescript 文件

```ts
// greeter.ts
function greeter(person) {
  return "Hello" + person;
}

let user = "Kaindy Liu";

document.body.innerHTML = greeter(user);
```

### 如何编译?

```ts
> tsc greeter.ts
```

### 类型注解

类型注解就是为函数或变量添加类型约束的一种方式

```ts
// greeter.ts
function greeter(person: string) {
  return "Hello" + person;
}

// 上面的函数定义中为参数变量定义了类型注解，约束其只能定义为 String 类型

let user = [1, 2, 3];     // TypeError
```

### 接口

接口就是用来描述一个特定结构的对象，指定其所拥有的字段和字段类型

```ts
// greeter.ts
interface Person {
  firstName: string;
  lastName: string;
}

function greeter(person: Person) {
  return `Hello, ${person.firstName} ${person.lastName}`
}

let user = { firstName: 'Liu', lastName: 'Kaindy' }

document.body.innerHTML = greeter(user)
```

### 类

这个就好理解了，跟 ES6 中的类差不多

```ts
class Student {
  fullName: string;
  constructor(public firstName, public lastName) {
    this.fullName = firstName + ' ' + lastName;
  }
}

let user = new Student("Liu", "Kaindy");
```

## 基础类型

`Typescript` 中的基础类型与 `Javascript` 中的基本一致，同时也提供了其他一些类型，如：枚举

### 布尔值 Boolean

```ts
let myBool: boolean = false;
```

### 数字 Number

`Typescript` 中的数字与 `Javascript` 中的一致，都是浮点数，类型表示为 `number`，除了十进制外，同时还只支持定义十六进制、二进制和八进制。

```ts
let dec: number = 6;
let hex: number = 0xf00d;
let binary: number = 0b1010;
let oct: number = 0o744;
```

### 字符串 String

与 `Javscript` 中一样，可以使用双引号或单引号来定义字符串，也可以使用模板字符串 (` `` `)来定义多行或可引入变量的字符串。

```ts
let name: string = 'Kaindy';
let age: number = 42;
let sentence: string = `Hello, Welcome ${name}`;
```

### 数组 Array

在 `Typesciprt` 中可以有两种方式定义数组。

第一种：直接在元素类型后面加上 `[]`

```ts
let list: number[] = [1, 2, 3];
```

第二种：使用数组泛型

```ts
let list: Array<number> = [1, 2, 3];
```

### 元组 Tuple

元组表示一个已知元素数量和类型的数组，其各元素类型可不相同。

```ts
// 定义由字符串和数字组成的元组
let x: [string, number];
x = ['hello', 42];

// 或者写成一行
let x: [string, number, boolean] = ['typescript', 100, true];
console.log(x[0]);  // 'typescript'
console.log(x[1]);  // 100
console.log(x[2]);  // true
console.log(x[3]);  // 越界访问返回 undefined
```

### 枚举 Enum

枚举是 `Typescript` 新增的类型，它为一组值赋予容易理解的名字。

```ts
enum Color { Red, Green, Blue };  // 默认情况下从 0 开始索引
let c: Color = Color.Green;   // 定义变量c为Color类型，值为0
```

我们也可以显式的指定其值

```ts
enum Color { Red = 1, Green = 2, Blue };
let c: Color = Color.Green;   // c的值为2
```

利用枚举的索引值，也可以查找到对应的名字：

```ts
enum Color { Red = 1, Green, Blue };
let colorName: string = Color[2];

console.log(colorName);   // Green
```

### Any

`Any` 类型表示变量的值可以为任意类型。

```ts
let myAny: any = 4;
myAny = 'Hello Typescript';   // OK
myAny = false;    // OK
```

### Void

`Void` 与 `Any` 正好相反，表示不为任何类型。一般用于表示函数没有任何返回

```ts
function myFunc(): void {
  // ...
}
```

### Null 和 Undefined

这两个类型在 `Typescript` 并没有多大的用处。

### Never

`Never` 表示那些永远不存在的值类型。一般用于需要抛出异常的函数

```ts
function error(message: string): never {
  throw new Error(message);
}
```

### Object

`Object` 表示非原始类型

```ts
// 声明函数，指定其参数为对象或 Null
declare function create(o: object | null): void;
```

### 类型断言

我们可以明确的告诉 `Typescript`， 这个变量的类型，而不需要进行检查，有两种方式定义类型断言。

用尖括号的方式：

```ts
let value: any = 'this is a string';
let strLength: number = (<string>value).length;
```

另一种是 `as` 语法（推荐）

```ts
let value: any = 'this is a string';
let strLen: number = (value as string).length;
```

## 变量声明

与 `Javascript` 一样，推荐使用 `let` 和 `const` 来定义变量。

### 解构

数组解构：

```ts
let input = [1, 2];
let [first, second] = input;
first;   // 1
second;  // 2
```

对象解构：

```ts
let o = {
  a: 'foo',
  b: 12,
  c: 'bar'
}
let { a, b } = o;
```

### 扩展运算符 (...)

```ts
let frist = [1, 2];
let second = [3, 4];
let both = [...first, ...second, 5];  // [1, 2, 3, 4, 5]
```

## 接口

接口，就是为类型命名，和对代码及第三方库代码定义契约。定义接口使用 `interface` 关键字。

### 定义

名称解释太晦涩，下面用例子来说明接口的作用

```ts
// 定义接口
interface LabelValue {
  label: string;
}

function PrintL(paramLable: LabelValue) {
  // ...
}
```

上面函数的参数的类型被指定为接口，那么，调用函数时的参数类型就必须是一个对象，且必须包含 `label` 属性。

如果我们在调用函数时出入多余的参数，则不符合接口类型定义，将会报错。

```ts
interface LabelValue {
  label: string;
}

function PrintL(paramLable: LabelValue) {
  // ...
}

PrintL({ label: 'Hello Typescript', numb: 100 })    // Error
```

而如果定义了的属性，没有在调用时声明，则也会报错。

```ts
interface LabelValue {
  label: string;
  numb: number;
}

function PrintL(paramLable: LabelValue) {
  // ...
}

PrintL({ label: 'Hello Typescript' })    // Error
```

### 可选属性

有时接口中的属性不是必须的，我们可以使用 `?` 使其成为可选属性

```ts
interface SquareConfig {
  color?: string;
  width?: number;
}
```

### 只读属性

接口中的一些属性要求只能在刚创建的时候给其赋值，可以使用 `readonly` 来指定只读属性。

```ts
interface Point {
  readonly x: number;
  readonly y: number;
}

let p: Point = { x: 10, y: 20 };
p.x = 50;   // Error
```

### 额外的属性检查

上面提到过，如果接口中定义属性在调用它时并没有明确的声明和赋值，`Typescript` 将会报错。

```ts
interface SquareConfig {
  color?: string;
  width?: number;
}

function createSquare(config: SquareConfig) {
  color: string;
  area: number;
}

let mySquare = createSquare({ colour: 'red', width: 100 });   // Error  并不存在colour属性
```

绕过这些检查的方式可以使用类型断言：

```ts
let mySquare = createSquare({ width: 100, opactiy: 0.5 } as SquareConfig); 
```

当然，有更好的方式来处理这个问题，那就是字符串索引签名。字符串索引签名的意思就是，这个接口中还定义了任意数量的其他属性，但并未明确的指出是那些属性：

```ts
interface SquareConfig {
  color?: string;
  width?: number;
  [propName: string]: any;
}
```

字符串索引签名定义了接口中除了 `color` 和 `width` 之外，还可以有其他任意属性，且不限制类型。

### 函数类型

接口也可以定义函数类型：

```ts
interface SearchFunc {
  // 参数为待搜索字符串以及目标字符串，返回布尔类型
  (source: string, subString: string): boolean;
}

// 定义函数参数名可以与接口定义的不相同
let mySeach: SearchFunc = function (src: string, sub: string) {
  return src.search(sub) > -1;
}

console.log(mySearch("kaindy", "in"));  // true
```

### 可索引类型

可索引类型有一个 "索引签名", 它描述了对象索引的类型，以及索引返回值类型。

```ts
interface StringArray {
  // 索引是数字，返回字符串类型
  // 并给索引签名设置只读
  readonly [index: number]: string;
}

let myArray: StringArray = ["Bob", "Fred"];

let myStr: string = myArray[0]
```

另外，我们也可以使用字符串来充当索引。

### 类类型

`Typescript` 也可以像 `C#` 或 `Java` 那样，明确的强制一个类去符合某种契约。

```ts
interface ClockInterface {
  currentTime: Date;
}

class Clock implements ClockInterface {
  currentTime: Date;
  constructor(h: number, m: number) {}
}
```

同样，也可以在接口中定义方法，在类里面去实现它。

```ts
interface ClockInterface {
  currentTime: Date;
  setTime(d: Date);
}

class Clock implements ClockInterface {
  currentTime: Date;
  setTime(d: Date) {
    this.currentTime = d;
  }
  constructor(h: number, m: number) {}
}
```

### 继承接口

与类一样，接口也可以实现相互继承。

```ts
interface Shape {
  color: string;
}

interface Square extends Shape {
  slideLength: number;
}

let square = <Square>{};
square.color = 'Blue';
square.slideLength = 100;
```

一个接口也可以同时继承多个接口，实现多个接口的合成接口。

```ts
...
interface Square extends Shape, PenStroke {
  // ...
}
...
```

### 接口继承类

一个接口的定义也可以继承自一个类，如果这个类具有 `private` 或 `protected` 成员时，这个接口也会继承，所以这时这个接口只能被这个类或其子类来实现（implements）

```ts
class Control {
  private state: any;
}

interface SelectableControl extends Control {
  select(): void;
}

class Button extends Control implements SelectableControl {
  select() { }
}

class TextBox extends Control {
  select() { }
}

// 下面会发生错误
// 接口 SelectableControl 继承自类 Control，所以也拥有私有属性 state
class Image implements SelectableControl {
  select() {}
}
```

## 类

### 定义

在 `Typescript` 中，可以正常的使用 `class` 来定义类。跟在 `ES6` 中一样。

```ts
class Greeter {
  greeting: string;
  constructor(message: string) {
    this.greeting = message;
  }
  greet() {
    return `Hello, ${this.greeting}`
  }
}

let greeter = new Greeter('Typescript');
console.log(greeter.greet())
```

### 继承

继承是面向对象编程的一大特性，它可以使得我们扩展已有的类的功能范围。使用关键字 `extends` 实现继承。

```ts
class Animal {
  move(distanceInMeters: number = 0) {
    console.log(`Animal moved ${distanceInMeters}`);
  }
}

class Dog extends Animal {
  bark() {
    console.log('Woof! Woof!');
  }
}

const dog = new Dog();
dog.bark()    // 'Woof Woof'
dog.move(10);   // Animal moved 10
```

当基类中有 `constructor` 函数时，子类在继承时必须调用 `super()` 来执行基类的构造函数，这是一个惯用套路。

```ts
class Animal {
  name: string;
  constructor(theName: string) {
    this.name = theName;
  }
  move(distanceInMeters: number = 0) {
    console.log(`${this.name} moved ${distanceInMeters}`);
  }
}

// 创建蛇类
class Snake extends Animal {
  constructor(name: string) {
    // 必须在子类的构造函数中调用super方法执行基类中的构造函数
    super(name);
  }
  move(distanceInMeters = 5) {
    console.log('Slithering...');
    super.move(distanceInMeters);
  }
}

// 创建马类
class Horse extends Animal {
  constructor(name: string) {
    // 必须在子类的构造函数中调用super方法执行基类中的构造函数
    super(name);
  }
  move(distanceInMeters = 45) {
    console.log('Galloping....');
    super.move(distanceInMeters);
  }
}

// 实例化
let sam = new Snake("Sammy the Python");
let tom: Animal = new Horse("Tommy the Palomino");

sam.move();
tom.move(34);
```

### 公共、私有和受保护的修饰符

在 `Typescript` 中，如果没有显式指定其修饰符，则默认为 `public`.

```ts
class Animal {
  public name: string;
  public constructor(theName: string) {
    this.name = theName;
  }
  public move(distanceInMeters: number) {
    // ...
  }
}
```

当类成员被声明为 `private` 时，就不能再类的部分访问它。

```ts
class Animal {
  private name: string;
  ...
}

new Animal('Cat').name;   // Error
```

当成员被声明为 `protected` 时，它和被声明为 `private` 相似，不同的是这类成员仍然可以在派生类中访问。

```ts
class Person {
  protected name: string;
  constructor(name: string) {
    this.name = name;
  }
}

class Employee extends Person {
  private department: string;
  constructor(name: string, department: string) {
    super(name);
    this.department = department;
  }

  public getElevatorPitch() {
    // ....
  }
}
```

### readonly修饰符

我们可以使用 `readonly` 修饰符将属性设置为只读，必须在声明或构造函数中被初始化。

```ts
class Octopus {
  readonly name: string;
  readonly numberOfLegs: number = 8;
  constructor(theName: string) {
    this.name = theName;
  }
}

let dad = new Octopus('Man with the 8 string legs');
dad.name = 'other string';  // Error 报错，name被设置为只读
```

### 存取器

类中的成员变量保持 `public` 很方便，但也可能会带来麻烦，所以我们可以通过 `getters` 和 `setters` 来控制对类成员变量的访问和设置。

```ts
// 设置一个密匙
let passcode = "secret passcode";

class Employee {
  private _fullName: string;

  get fullName(): string {
    return this._fullName;
  }

  set fullName(newName: string) {
    if (passcode && passcode === 'secret passcode') {
      this._fullName = newName;
    } else {
      console.log('Error: Unauthorizedd update of employee!');
    }
  }
}

let employee = new Employee();
employee.fullName = 'Bob Smith';
if (employee.fullName) {
  alert(employee.fullName);
}
```

### 静态属性

我们可以使用 `static` 关键字定义静态属性成员，无需实例化，可以通过类名来访问静态成员。

```ts
class Grid {
  static origin = { x: 0, y: 0 };
  ...
}

Grid.origin;
```

### 抽象类

抽象类一般不会被实例化，它可以包含成员的实现细节，我们用 `abstract` 关键字来定义它。

```ts
abstract class Animal {
  abstract makeSound(): void;
  move(): void {
    // ...
  }
}
```

抽象类中的方法必须在其派生类中实现，抽象方法必须包含 `abstract` 关键字且可以包含访问修饰符。

```ts
abstract class Department {
  constructor(public name: string) {}
  
  printName(): void {
    console.log('Department name: ' + this.name);
  }

  abstract printMeeting(): void;  // 必须在派生类中实现
}

class AccountingDepartment extends Department {
  constructor() {
    super()
  }

  printMeeting(): void {
    console.log('The Accounting Department meets each Monday at 10am.');
  }

  generateReports(): void {
    console.log('Generating accounting reports...');
  }
}

let department = new AccountingDepartment();
department.printName();
department.printMeeting();
```

## 函数

函数在 `Javascript` 中有命名函数和匿名函数之分。`Typescript` 沿用了这个特性。

### 函数类型

我们可以在定义函数时为函数参数和返回加入类型

```ts
function add(x: number, y: number): number {
  return x + y;
}

let myAdd = function(x: number, y: number): number {
  return x + y;
}
```

### 可选参数和默认参数

我们可以在参数命名的后面使用 `?` 来标识此参数是可选的，默认参数直接在参数名后面赋默认值即可。

```ts
function buildName(firstName: string, lastName?: string) {
  // ...
}
```

```ts
function buildName(firstName: string, lastName = 'Kaindy') {
  // ...
}
```

### 剩余参数

我们可以使用扩展运算符(`...`)来处理多余参数的问题

```ts
function buildName(firstName: string, ...restName: string[]) {
  return `${firstName} ${restName.join(' ')}`;
}

let employeeName = buildName('Liu', 'Kaindy', 'aaa', 'bbb', 'ccc');
```

## 泛型

泛型从概念上讲，就是用来创建可重用的组件，这类组件支持多种数据类型。换句话说，就是我们在定义函数、接口或类的时候，不预先指定具体的类型，而是在使用的时候指定其类型的一种特性。下面用一个例子来说明：

```ts
// 创建一个返回参数的函数
function identity(arg: any): any {
  return arg;
}
```

上面的函数，可以传入一个数字类型的参数，我们希望能返回一个同类型的结果，但可能它会返回字符串类型的结果。

我们希望传入参数的类型与返回值得类型是一致的，所以，我们使用了 "类型变量"，它表示类型而不是值。

```ts
function identity<T>(arg: T): T {
  return arg;
}
```

上面改写的函数 `identity` 中，使用类型变量 `T` 捕获了参数类型，然后指定返回值得类型也是 `T`，这样就保证了参数类型和返回值类型是一致的。

改写之后的函数我们称之为"泛型函数"，调用这个函数有两种方式，一是明确指定泛型变量的类型：

```ts
let output = identity<string>("myString");
```

第二种方法更普遍，使用了"类型推论", 编译器会根据传入的参数类型自动确定 `T` 的类型：

```ts
let output = identity("myString");
```

### 泛型接口

```ts
interface GenericIdentityFn {
  <T>(arg: T): T;
}

function identity<T>(arg: T): T {
  return arg;
}

let myIdentity: GenericIdentityFn = identity;
```

### 泛型类

```ts
class GenericNumber<T> {
  zeroValue: T;
  add: (x: T, y: T) => T;
}

let myGenericNumber = new GenericNumber<number>();
myGenericNumber.zeroValue = 0;
myGenericNumber.add = function(x, y) { return x + y; }
```

## 枚举

枚举是 `Typescript` 新增的一种数据类型。它定义了一些带名字的常量，支持数字和字符串的枚举。

### 数字枚举

```ts
enum Direction {
  Up = 1,   // 赋值为1，下面的项会自动增长
  Down,
  Left,
  Right
}
```

我们可以通过枚举属性来访问枚举成员

```ts
enum Response {
  No = 0,
  Yes = 1
}

function respond(recipient: string, message: Response): void {
  // ...
}

respond("Princess", Response.Yes);
```

### 字符串枚举

字符串枚举中的每个成员都必须用字符串字面量

```ts
enum Directrion {
  Up = 'UP',
  Down = 'DOWN',
  Left = 'LEFT',
  Right = 'RIGHT'
}
```

### 异构枚举

异构枚举就是混合字符串和数字成员，但这并不被推荐。

```ts
enum Heterenums {
  No = 0,
  Yes = "Yes"
}
```

## 类型推论

类型推论在 `Typescript` 中就是由编译器去自动获取类型，而无需显式的指定其类型。

```ts
let x = 3;  // x的类型被自动推断为number
```
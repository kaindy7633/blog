<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Rust语言圣经(读书笔记)](#rust%E8%AF%AD%E8%A8%80%E5%9C%A3%E7%BB%8F%E8%AF%BB%E4%B9%A6%E7%AC%94%E8%AE%B0)
  - [基础入门](#%E5%9F%BA%E7%A1%80%E5%85%A5%E9%97%A8)
    - [变量绑定与解构](#%E5%8F%98%E9%87%8F%E7%BB%91%E5%AE%9A%E4%B8%8E%E8%A7%A3%E6%9E%84)
      - [变量命名](#%E5%8F%98%E9%87%8F%E5%91%BD%E5%90%8D)
      - [变量绑定](#%E5%8F%98%E9%87%8F%E7%BB%91%E5%AE%9A)
      - [变量可变性](#%E5%8F%98%E9%87%8F%E5%8F%AF%E5%8F%98%E6%80%A7)
      - [下划线开头的变量](#%E4%B8%8B%E5%88%92%E7%BA%BF%E5%BC%80%E5%A4%B4%E7%9A%84%E5%8F%98%E9%87%8F)
      - [变量解构](#%E5%8F%98%E9%87%8F%E8%A7%A3%E6%9E%84)
      - [常量](#%E5%B8%B8%E9%87%8F)
      - [变量遮蔽(shadowing)](#%E5%8F%98%E9%87%8F%E9%81%AE%E8%94%BDshadowing)
    - [基本类型](#%E5%9F%BA%E6%9C%AC%E7%B1%BB%E5%9E%8B)
      - [类型推导与标注](#%E7%B1%BB%E5%9E%8B%E6%8E%A8%E5%AF%BC%E4%B8%8E%E6%A0%87%E6%B3%A8)
      - [数值类型](#%E6%95%B0%E5%80%BC%E7%B1%BB%E5%9E%8B)
        - [整数类型](#%E6%95%B4%E6%95%B0%E7%B1%BB%E5%9E%8B)
        - [浮点类型](#%E6%B5%AE%E7%82%B9%E7%B1%BB%E5%9E%8B)
        - [NaN](#nan)
        - [数字运算](#%E6%95%B0%E5%AD%97%E8%BF%90%E7%AE%97)
        - [位运算](#%E4%BD%8D%E8%BF%90%E7%AE%97)
        - [序列(Range)](#%E5%BA%8F%E5%88%97range)
        - [有理数和复数](#%E6%9C%89%E7%90%86%E6%95%B0%E5%92%8C%E5%A4%8D%E6%95%B0)
      - [字符、布尔、单元类型](#%E5%AD%97%E7%AC%A6%E5%B8%83%E5%B0%94%E5%8D%95%E5%85%83%E7%B1%BB%E5%9E%8B)
        - [字符类型(char)](#%E5%AD%97%E7%AC%A6%E7%B1%BB%E5%9E%8Bchar)
        - [布尔(bool)](#%E5%B8%83%E5%B0%94bool)
        - [单元类型](#%E5%8D%95%E5%85%83%E7%B1%BB%E5%9E%8B)
      - [语句与表达式](#%E8%AF%AD%E5%8F%A5%E4%B8%8E%E8%A1%A8%E8%BE%BE%E5%BC%8F)
        - [语句](#%E8%AF%AD%E5%8F%A5)
        - [表达式](#%E8%A1%A8%E8%BE%BE%E5%BC%8F)
      - [函数](#%E5%87%BD%E6%95%B0)
        - [要点](#%E8%A6%81%E7%82%B9)
        - [函数参数](#%E5%87%BD%E6%95%B0%E5%8F%82%E6%95%B0)
        - [函数返回](#%E5%87%BD%E6%95%B0%E8%BF%94%E5%9B%9E)
        - [无返回值](#%E6%97%A0%E8%BF%94%E5%9B%9E%E5%80%BC)
        - [发散函数](#%E5%8F%91%E6%95%A3%E5%87%BD%E6%95%B0)
    - [所有权和借用](#%E6%89%80%E6%9C%89%E6%9D%83%E5%92%8C%E5%80%9F%E7%94%A8)
      - [所有权](#%E6%89%80%E6%9C%89%E6%9D%83)
        - [栈(Stack)与堆(Heap)](#%E6%A0%88stack%E4%B8%8E%E5%A0%86heap)
        - [所有权原则](#%E6%89%80%E6%9C%89%E6%9D%83%E5%8E%9F%E5%88%99)
        - [变量绑定的数据交互](#%E5%8F%98%E9%87%8F%E7%BB%91%E5%AE%9A%E7%9A%84%E6%95%B0%E6%8D%AE%E4%BA%A4%E4%BA%92)
        - [函数传值与返回](#%E5%87%BD%E6%95%B0%E4%BC%A0%E5%80%BC%E4%B8%8E%E8%BF%94%E5%9B%9E)
      - [引用和借用](#%E5%BC%95%E7%94%A8%E5%92%8C%E5%80%9F%E7%94%A8)
  - [高级进阶](#%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6)
  - [异步编程](#%E5%BC%82%E6%AD%A5%E7%BC%96%E7%A8%8B)
  - [疑难点](#%E7%96%91%E9%9A%BE%E7%82%B9)
  - [自动化测试](#%E8%87%AA%E5%8A%A8%E5%8C%96%E6%B5%8B%E8%AF%95)
  - [Cargo使用指南](#cargo%E4%BD%BF%E7%94%A8%E6%8C%87%E5%8D%97)
  - [日志监控](#%E6%97%A5%E5%BF%97%E7%9B%91%E6%8E%A7)
  - [最佳实践](#%E6%9C%80%E4%BD%B3%E5%AE%9E%E8%B7%B5)
  - [实现链表](#%E5%AE%9E%E7%8E%B0%E9%93%BE%E8%A1%A8)
  - [编译错误](#%E7%BC%96%E8%AF%91%E9%94%99%E8%AF%AF)
  - [性能优化](#%E6%80%A7%E8%83%BD%E4%BC%98%E5%8C%96)
  - [标准库](#%E6%A0%87%E5%87%86%E5%BA%93)
  - [附录](#%E9%99%84%E5%BD%95)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Rust语言圣经(读书笔记)

## 基础入门

### 变量绑定与解构

#### 变量命名

`Rust` 跟其他语言在命名上没有太大的区别，在变量命名时，需要遵循 `Rust` 命名规范，请参考最佳实践中的命名规范

#### 变量绑定

在其它语言中，我们用 `var a = "hello world"` 的方式给 `a` 赋值, 而在 `Rust` 中，我们这样写： `let a = "hello world"` ，同时给这个过程起了另一个名字：变量绑定。

#### 变量可变性

`Rust` 的变量在默认情况下是不可变的, 你可以通过 `mut` 关键字让变量变为可变的

```rs
fn main() {
    let x = 5;
    println!("The value of x is: {}", x);
    x = 6;
    println!("The value of x is: {}", x); // 报错
}
```

在 `Rust` 中，可变性很简单，只要在变量名前加一个 `mut` 即可

```rs
fn main() {
    let mut x = 5; // 变量 x 是可变的
    println!("The value of x is: {}", x);
    x = 6;
    println!("The value of x is: {}", x);
}
```

选择可变还是不可变，更多的还是取决于你的使用场景，例如不可变可以带来安全性，但是丧失了灵活性和性能（如果你要改变，就要重新创建一个新的变量，这里涉及到内存对象的再分配）。而可变变量最大的好处就是使用上的灵活性和性能上的提升

#### 下划线开头的变量

如果你创建了一个变量却不在任何地方使用它，`Rust` 通常会给你一个警告, 如果你希望 `Rust` 不要警告未使用的变量，可以用下划线作为变量名的开头

```rs
fn main() {
    let _x = 5;
    let y = 10;
}
```

#### 变量解构

`let` 表达式不仅仅用于变量的绑定，还能进行复杂变量的解构：从一个相对复杂的变量中，匹配出该变量的一部分内容：

```rs
fn main() {
    let (a, mut b): (bool,bool) = (true, false);
    // a = true,不可变; b = false，可变
    println!("a = {:?}, b = {:?}", a, b);

    b = true;
    assert_eq!(a, b);
}
```

#### 常量

常量(`constant`), 与不可变变量一样，常量也是绑定到一个常量名且不允许更改的值，但是常量和变量之间存在一些差异：

- 常量不允许使用 `mut`
- 常量使用 `const` 关键字而不是 `let` 关键字来声明，并且值的类型必须标注

#### 变量遮蔽(shadowing)

`Rust` 允许声明相同的变量名，在后面声明的变量会遮蔽掉前面声明的(相当于覆盖,或者替换)

```rs
fn main() {
    let x = 5;
    // 在main函数的作用域内对之前的x进行遮蔽
    let x = x + 1;

    {
        // 在当前的花括号作用域内，对之前的x进行遮蔽
        let x = x * 2;
        println!("The value of x in the inner scope is: {}", x);  // 12
    }

    println!("The value of x is: {}", x); // 6
}
```

**理解：** 使用 `mut` 关键字的性能更好，它不会发生内存对象再分配，而遮蔽会生成完全不同的新变量，只是变量名相同而已。

### 基本类型

`Rust` 每个值都有其确切的数据类型，总的来说可以分为两类：基本类型和复合类型, 基本类型由以下组成：

- 数值类型: 有符号整数 (`i8`, `i16`, `i32`, `i64`, `isize`)、 无符号整数 (`u8`, `u16`, `u32`, `u64`, `usize`) 、浮点数 (`f32`, `f64`)、以及有理数、复数
- 字符串：字符串字面量和字符串切片 `&str`
- 布尔类型： `true` 和 `false`
- 字符类型: 表示单个 `Unicode` 字符，存储为 4 个字节
- 单元类型: 即 `()` ，其唯一的值也是 `()`

#### 类型推导与标注

`Rust` 是一门静态类型语言，也就是编译器必须在编译期知道我们所有变量的类型，它可以根据变量的值和上下文中的使用方式来自动推导出变量的类型

#### 数值类型

`Rust` 使用一个相对传统的语法来创建整数（1，2，...）和浮点数（1.0，1.1，...）。整数、浮点数的运算和你在其它语言上见过的一致，都是通过常见的运算符来完成

##### 整数类型

整数是没有小数部分的数字。之前使用过的 `i32` 类型，表示有符号的 32 位整数（ `i` 是英文单词 `integer` 的首字母，与之相反的是 `u`，代表无符号 `unsigned` 类型）。下表显示了 `Rust` 中的内置的整数类型：

|长度|有符号类型|无符号类型|
|--|--|--|
|8位|i8|u8|
|16位|i16|u16|
|32位|i32|u32|
|64位|i64|u64|
|128位|i128|u128|
|视架构而定|isize|usize|

`Rust` 整型默认使用 `i32`，例如 `let i = 1`，那 `i` 就是 `i32` 类型，因此你可以首选它，同时该类型也往往是性能最好的

整型溢出问题，如果操作使得目标数据超出定义的整型类型范围，比如：给一个 `u8` 类型的变量绑定 256，则会发生整型溢出，在 `debug` 模式编译时，`Rust` 会检查整型溢出，若存在这些问题，则使程序在编译时 `panic`。当使用 `--release` 参数进行 `release` 模式构建时，`Rust` 不检测溢出，它会按照补码循环溢出的规则处理，比如上面的例子，则会返回 0。

要显式处理可能的溢出，可以使用标准库针对原始数字类型提供的这些方法：

- 使用 `wrapping_*` 方法在所有模式下都按照补码循环溢出规则处理，例如 `wrapping_add`
- 如果使用 `checked_*` 方法时发生溢出，则返回 `None` 值
- 使用 `overflowing_*` 方法返回该值和一个指示是否存在溢出的布尔值
- 使用 `saturating_*` 方法使值达到最小值或最大值

```rs
fn main() {
    let a : u8 = 255;
    let b = a.wrapping_add(20);
    println!("{}", b);  // 19
}
```

##### 浮点类型

浮点类型数字 是带有小数点的数字，在 `Rust` 中浮点类型数字也有两种基本类型： `f32` 和 `f64`，分别为 `32` 位和 `64` 位大小。默认浮点类型是 `f64`

```rs
fn main() {
    let x = 2.0; // f64
    let y: f32 = 3.0; // f32
}
```

浮点数根据 `IEEE-754` 标准实现。`f32`类型是单精度浮点型，`f64` 为双精度。

浮点数运算应避免测试相等性，且当结果在数学上可能存在未定义时，要格外小心。

##### NaN

对于数学上未定义的结果，例如对负数取平方根 `-42.1.sqrt()` ，会产生一个特殊的结果：`Rust` 的浮点数类型使用 `NaN` (not a number)来处理这些情况。

所有跟 `NaN` 交互的操作，都会返回一个 `NaN`，而且 `NaN` 不能用来比较

```rs
fn main() {
  let x = (-42.0_f32).sqrt();
  assert_eq!(x, x); // panic
}
```

我们可以使用 `is_nan()` 等方法，可以用来判断一个数值是否是 `NaN`

```rs
fn main() {
    let x = (-42.0_f32).sqrt();
    if x.is_nan() {
        println!("未定义的数学行为")
    }
}
```

##### 数字运算

`Rust` 支持所有数字类型的基本数学运算：加法、减法、乘法、除法和取模运算。下面代码各使用一条 `let` 语句来说明相应运算的用法：

```rs
fn main() {
    // 加法
    let sum = 5 + 10;

    // 减法
    let difference = 95.5 - 4.3;

    // 乘法
    let product = 4 * 30;

    // 除法
    let quotient = 56.7 / 32.2;

    // 求余
    let remainder = 43 % 5;
}
```

综合示例：

```rs
fn main() {
  // 编译器会进行自动推导，给予twenty i32的类型
  let twenty = 20;
  // 类型标注
  let twenty_one: i32 = 21;
  // 通过类型后缀的方式进行类型标注：22是i32类型
  let twenty_two = 22i32;

  // 只有同样类型，才能运算
  let addition = twenty + twenty_one + twenty_two;
  println!("{} + {} + {} = {}", twenty, twenty_one, twenty_two, addition);

  // 对于较长的数字，可以用_进行分割，提升可读性
  let one_million: i64 = 1_000_000;
  println!("{}", one_million.pow(2));

  // 定义一个f32数组，其中42.0会自动被推导为f32类型
  let forty_twos = [
    42.0,
    42f32,
    42.0_f32,
  ];

  // 打印数组中第一个值，并控制小数位为2位
  println!("{:.2}", forty_twos[0]);
}
```

##### 位运算

`Rust` 的运算基本上和其他语言一样

<img src="../images/Xnip2023-02-18_22-56-05.jpg" />

```rs
fn main() {
    // 二进制为00000010
    let a:i32 = 2;
    // 二进制为00000011
    let b:i32 = 3;

    println!("(a & b) value is {}", a & b);

    println!("(a | b) value is {}", a | b);

    println!("(a ^ b) value is {}", a ^ b);

    println!("(!b) value is {} ", !b);

    println!("(a << b) value is {}", a << b);

    println!("(a >> b) value is {}", a >> b);

    let mut a = a;
    // 注意这些计算符除了!之外都可以加上=进行赋值 (因为!=要用来判断不等于)
    a <<= b;
    println!("(a << b) value is {}", a);
}
```

##### 序列(Range)

`Rust` 提供了一个非常简洁的方式，用来生成连续的数值，例如 `1..5`，生成从 1 到 4 的连续数字，不包含 5 ；`1..=5`，生成从 1 到 5 的连续数字，包含 5，它的用途很简单，常常用于循环中：

```rs
for i in 1..=5 {
    println!("{}",i);
}
```

序列只允许用于数字或字符类型

```rs
for i in 'a'..='z' {
    println!("{}",i);
}
```

##### 有理数和复数

有理数和复数并未包含在标准库中，社区已开发出高质量的数值库： `num`。 在 `Cargo.toml` 中的 `[dependencies]` 下添加一行 `num = "0.4.0"`

```rs
use num::complex::Complex;

fn main() {
  let a = Complex { re: 2.1, im: -1.2 };
  let b = Complex::new(11.1, 22.2);
  let result = a + b;

  println!("{} + {}i", result.re, result.im)
}
```

#### 字符、布尔、单元类型

##### 字符类型(char)

字符，你可以把它理解为英文中的字母，中文中的汉字

```rs
fn main() {
    let c = 'z';
    let z = 'ℤ';
    let g = '国';
    let heart_eyed_cat = '😻';
}
```

`Rust` 的字符不仅仅是 `ASCII`，所有的 `Unicode` 值都可以作为 `Rust` 字符，包括单个的中文、日文、韩文、emoji 表情符号等等

由于 `Unicode` 都是 4 个字节编码，因此字符类型也是占用 4 个字节

```rs
fn main() {
    let x = '中';
    println!("字符'中'占用了{}字节的内存大小",std::mem::size_of_val(&x));
}
```

`Rust` 的字符只能用 `''` 来表示， `""` 是留给字符串的

##### 布尔(bool)

`Rust` 中的布尔类型有两个可能的值：`true` 和 `false`，布尔值占用内存的大小为 1 个字节：

```rs
fn main() {
    let t = true;

    let f: bool = false; // 使用类型标注,显式指定f的类型

    if f {
        println!("这是段毫无意义的代码");
    }
}
```

##### 单元类型

单元类型就是 `()`  ，唯一的值也是 `()`。上面经常用到的 `main` 函数就返回这个单元类型 `()`, 在 `Rust` 中，没有返回值的函数是有单独的定义的：发散函数( `diverge function` )，顾名思义，无法收敛的函数

`println!()` 的返回值也是单元类型 `()`

#### 语句与表达式

Rust 的函数体是由一系列语句组成，最后由一个表达式来返回值

```rs
fn add_with_extra(x: i32, y: i32) -> i32 {
    let x = x + 1; // 语句
    let y = y + 5; // 语句
    x + y // 表达式
}
```

##### 语句

语句完成一个具体的操作，但是并没有返回值

```rs
let a = 8;
let b: Vec<f64> = Vec::new();
let (a, c) = ("hi", false);
```

##### 表达式

表达式会进行求值，然后返回一个值。例如 `5 + 6`，在求值后，返回值 `11`，因此它就是一条表达式

调用一个函数是表达式，因为会返回一个值，调用宏也是表达式，用花括号包裹最终返回一个值的语句块也是表达式，总之，能返回值，它就是表达式:

```rs
fn main() {
    let y = {
        let x = 3;
        x + 1
    };

    println!("The value of y is: {}", y);
}
```

表达式不能包含分号。这一点非常重要，一旦你在表达式后加上分号，它就会变成一条语句，再也不会返回一个值

表达式如果不返回任何值，会隐式地返回一个 `()`

```rs
fn main() {
    assert_eq!(ret_unit_type(), ())
}

fn ret_unit_type() {
    let x = 1;
    // if 语句块也是一个表达式，因此可以用于赋值，也可以直接返回
    // 类似三元运算符，在Rust里我们可以这样写
    let y = if x % 2 == 1 {
        "odd"
    } else {
        "even"
    };
    // 或者写成一行
    let z = if x % 2 == 1 { "odd" } else { "even" };
}
```

#### 函数

先看下面的函数声明：

```rs
fn add(i: i32, j: i32) -> i32 {
   i + j
}
```

声明函数的关键字 `fn` ,函数名 `add()`，参数 `i` 和 `j`，参数类型和返回值类型都是 `i32`

##### 要点

- 函数名和变量名使用蛇形命名法(`snake case`)，例如 `fn add_two() -> {}`
- 函数的位置可以随便放，`Rust` 不关心我们在哪里定义了函数，只要有定义即可
- 每个函数参数都需要标注类型

##### 函数参数

`Rust` 是强类型语言，因此需要你为每一个函数参数都标识出它的具体类型

```rs
fn main() {
    another_function(5, 6.1);
}

fn another_function(x: i32, y: f32) {
    println!("The value of x is: {}", x);
    println!("The value of y is: {}", y);
}
```

##### 函数返回

在 `Rust` 中函数就是表达式，因此我们可以把函数的返回值直接赋给调用者。

函数的返回值就是函数体最后一条表达式的返回值，当然我们也可以使用 `return` 提前返回，下面的函数使用最后一条表达式来返回一个值：

```rs
fn plus_five(x:i32) -> i32 {
    x + 5
}

fn main() {
    let x = plus_five(5);

    println!("The value of x is: {}", x);
}
```

##### 无返回值

单元类型 `()`，是一个零长度的元组。它没啥作用，但是可以用来表达一个函数没有返回值：

- 函数没有返回值，那么返回一个 `()`
- 通过 `;` 结尾的表达式返回一个 `()`

下面的 `report` 函数会隐式返回一个 `()`：

```rs
use std::fmt::Debug;

fn report<T: Debug>(item: T) {
  println!("{:?}", item);

}
```

##### 发散函数

当用 `!` 作函数返回类型的时候，表示该函数永不返回( `diverge function` )，特别的，这种语法往往用做会导致程序崩溃的函数：

```rs
fn dead_end() -> ! {
  panic!("你已经到了穷途末路，崩溃吧！");
}
```

### 所有权和借用

#### 所有权

##### 栈(Stack)与堆(Heap)

栈和堆的核心目标就是为程序在运行时提供可供使用的内存空间

栈按照顺序存储值并以相反顺序取出值，这也被称作后进先出，增加数据叫做进栈，移出数据则叫做出栈，栈中的所有数据都必须占用已知且固定大小的内存空间

对于大小未知或者可能变化的数据，我们需要将它存储在堆上。当向堆上放入数据时，需要请求一定大小的内存空间。操作系统在堆的某处找到一块足够大的空位，把它标记为已使用，并返回一个表示该位置地址的指针, 该过程被称为在堆上分配内存。接着，该指针会被推入栈中，因为指针的大小是已知且固定的，在后续使用过程中，你将通过栈中的指针，来获取数据在堆上的实际内存位置，进而访问该数据

##### 所有权原则

关于所有权的规则，首先请谨记以下规则：

1. Rust 中每一个值都被一个变量所拥有，该变量被称为值的所有者
2. 一个值同时只能被一个变量所拥有，或者说一个值只能拥有一个所有者
3. 当所有者(变量)离开作用域范围时，这个值将被丢弃(drop)

作用域是一个变量在程序中有效的范围

```rs
{                      // s 在这里无效，它尚未声明
    let s = "hello";   // 从此处起，s 是有效的

    // 使用 s
}                      // 此作用域已结束，s不再有效
```

`String` 类型，我们通过 `let s = "Hello"` 来声明一个字符串字面值，类型为 `&str`，字符串字面值是不可变的，且并非所有字符串的值都能在编码时得知。为此，`Rust` 为我们提供动态字符串类型: `String`, 该类型被分配到堆上，因此可以动态伸缩，也就能存储在编译时大小未知的文本

用下面的方法基于字符串字面量来创建 `String` 类型:

```rs
let s = String::from("hello");
```

`::` 是一种调用操作符，这里表示调用 `String` 中的 `from` 方法。`String` 存储在堆上是动态的，你可以这样修改它：

```rs
let mut s = String::from("hello");

s.push_str(", world!"); // push_str() 在字符串后追加字面值

println!("{}", s); // 将打印 `hello, world!`
```

##### 变量绑定的数据交互

```rs
let x = 5;
let y = x;
```

上面的代码中，`Rust` 会直接在栈中拷贝一份，`x` 和 `y` 都在栈中，并且都绑定了值 `5`。在 `Rust` 中，基本数据类型都是通过自动拷贝的方式来赋值。再看下面的代码：

```rs
let s1 = String::from("hello");
let s2 = s1;
```

`String` 类型是一个复杂类型，由存储在栈中的堆指针、字符串长度、字符串容量共同组成。堆指针指向了真实存储字符串内容的堆内存，容量是堆内存分配空间的大小，长度是目前已经使用的大小。

那么问题来了，`s1` 和 `s2` 都指向了堆内存中的字符串数据，那它的所有者到底是谁呢？当变量离开作用域，它们释放的同一个堆地址上的值，会引发二次释放的错误，`Rust` 这样来解决这个问题，当 `s1` 赋予 `s2` 之后，`s1` 就会马上失效，或者说，`s1` 把 `String` 的所有权转移到了 `s2`

```rs
let s1 = String::from("hello");
let s2 = s1;

println!("{}, world!", s1); // 报错
```

如果想要在堆内存上创建值的副本，`Rust` 提供了一个 `clone` 方法

```rs
let s1 = String::from("hello");
let s2 = s1.clone();

println!("s1 = {}, s2 = {}", s1, s2);
```

`Rust` 有一个叫做 `Copy` 的特征，可以用在类似整型这样在栈中存储的类型。如果一个类型拥有 `Copy` 特征，一个旧的变量在被赋值给其他变量后仍然可用

任何基本类型的组合可以 `Copy` ，不需要分配内存或某种形式资源的类型是可以 `Copy` 的

##### 函数传值与返回

将值传递给函数，一样会发生 移动 或者 复制

```rs
fn main() {
    let s = String::from("hello");  // s 进入作用域

    takes_ownership(s);             // s 的值移动到函数里 ...
                                    // ... 所以到这里不再有效

    let x = 5;                      // x 进入作用域

    makes_copy(x);                  // x 应该移动函数里，
                                    // 但 i32 是 Copy 的，所以在后面可继续使用 x

} // 这里, x 先移出了作用域，然后是 s。但因为 s 的值已被移走，
  // 所以不会有特殊操作

fn takes_ownership(some_string: String) { // some_string 进入作用域
    println!("{}", some_string);
} // 这里，some_string 移出作用域并调用 `drop` 方法。占用的内存被释放

fn makes_copy(some_integer: i32) { // some_integer 进入作用域
    println!("{}", some_integer);
} // 这里，some_integer 移出作用域。不会有特殊操作
```

函数返回值也有所有权

```rs
fn main() {
    let s1 = gives_ownership();         // gives_ownership 将返回值
                                        // 移给 s1

    let s2 = String::from("hello");     // s2 进入作用域

    let s3 = takes_and_gives_back(s2);  // s2 被移动到
                                        // takes_and_gives_back 中,
                                        // 它也将返回值移给 s3
} // 这里, s3 移出作用域并被丢弃。s2 也移出作用域，但已被移走，
  // 所以什么也不会发生。s1 移出作用域并被丢弃

fn gives_ownership() -> String {             // gives_ownership 将返回值移动给
                                             // 调用它的函数

    let some_string = String::from("hello"); // some_string 进入作用域.

    some_string                              // 返回 some_string 并移出给调用的函数
}

// takes_and_gives_back 将传入字符串并返回该值
fn takes_and_gives_back(a_string: String) -> String { // a_string 进入作用域

    a_string  // 返回 a_string 并移出给调用的函数
}
```

#### 引用和借用

## 高级进阶

## 异步编程

## 疑难点

## 自动化测试

## Cargo使用指南

## 日志监控

## 最佳实践

## 实现链表

## 编译错误

## 性能优化

## 标准库

## 附录

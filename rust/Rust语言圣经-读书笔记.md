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

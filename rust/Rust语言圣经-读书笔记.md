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
        - [引用与解引用](#%E5%BC%95%E7%94%A8%E4%B8%8E%E8%A7%A3%E5%BC%95%E7%94%A8)
        - [不可变引用](#%E4%B8%8D%E5%8F%AF%E5%8F%98%E5%BC%95%E7%94%A8)
        - [可变引用](#%E5%8F%AF%E5%8F%98%E5%BC%95%E7%94%A8)
        - [悬垂引用(Dangling References)](#%E6%82%AC%E5%9E%82%E5%BC%95%E7%94%A8dangling-references)
      - [借用规则总结](#%E5%80%9F%E7%94%A8%E8%A7%84%E5%88%99%E6%80%BB%E7%BB%93)
    - [复合类型](#%E5%A4%8D%E5%90%88%E7%B1%BB%E5%9E%8B)
      - [字符串与切片](#%E5%AD%97%E7%AC%A6%E4%B8%B2%E4%B8%8E%E5%88%87%E7%89%87)
        - [切片(slice)](#%E5%88%87%E7%89%87slice)
        - [字符串字面量是切片](#%E5%AD%97%E7%AC%A6%E4%B8%B2%E5%AD%97%E9%9D%A2%E9%87%8F%E6%98%AF%E5%88%87%E7%89%87)
        - [什么是字符串](#%E4%BB%80%E4%B9%88%E6%98%AF%E5%AD%97%E7%AC%A6%E4%B8%B2)
        - [String 与 &str 的转换](#string-%E4%B8%8E-str-%E7%9A%84%E8%BD%AC%E6%8D%A2)
        - [字符串索引](#%E5%AD%97%E7%AC%A6%E4%B8%B2%E7%B4%A2%E5%BC%95)
        - [字符串切片](#%E5%AD%97%E7%AC%A6%E4%B8%B2%E5%88%87%E7%89%87)
        - [操作字符串](#%E6%93%8D%E4%BD%9C%E5%AD%97%E7%AC%A6%E4%B8%B2)
        - [字符串转义](#%E5%AD%97%E7%AC%A6%E4%B8%B2%E8%BD%AC%E4%B9%89)
        - [操作 UTF-8 字符串](#%E6%93%8D%E4%BD%9C-utf-8-%E5%AD%97%E7%AC%A6%E4%B8%B2)
        - [字符串深度剖析](#%E5%AD%97%E7%AC%A6%E4%B8%B2%E6%B7%B1%E5%BA%A6%E5%89%96%E6%9E%90)
      - [元组](#%E5%85%83%E7%BB%84)
        - [用模式匹配解构元组](#%E7%94%A8%E6%A8%A1%E5%BC%8F%E5%8C%B9%E9%85%8D%E8%A7%A3%E6%9E%84%E5%85%83%E7%BB%84)
        - [用 `.` 来访问元组](#%E7%94%A8--%E6%9D%A5%E8%AE%BF%E9%97%AE%E5%85%83%E7%BB%84)
        - [元组的使用示例](#%E5%85%83%E7%BB%84%E7%9A%84%E4%BD%BF%E7%94%A8%E7%A4%BA%E4%BE%8B)
      - [结构体](#%E7%BB%93%E6%9E%84%E4%BD%93)
        - [结构体语法](#%E7%BB%93%E6%9E%84%E4%BD%93%E8%AF%AD%E6%B3%95)
        - [元组结构体(Tuple Struct)](#%E5%85%83%E7%BB%84%E7%BB%93%E6%9E%84%E4%BD%93tuple-struct)
        - [单元结构体(Unit-like Struct)](#%E5%8D%95%E5%85%83%E7%BB%93%E6%9E%84%E4%BD%93unit-like-struct)
        - [结构体数据的所有权](#%E7%BB%93%E6%9E%84%E4%BD%93%E6%95%B0%E6%8D%AE%E7%9A%84%E6%89%80%E6%9C%89%E6%9D%83)
        - [使用 `#[derive(Debug)]` 来打印结构体的信息](#%E4%BD%BF%E7%94%A8-derivedebug-%E6%9D%A5%E6%89%93%E5%8D%B0%E7%BB%93%E6%9E%84%E4%BD%93%E7%9A%84%E4%BF%A1%E6%81%AF)
      - [枚举](#%E6%9E%9A%E4%B8%BE)
        - [枚举值](#%E6%9E%9A%E4%B8%BE%E5%80%BC)
        - [同一化类型](#%E5%90%8C%E4%B8%80%E5%8C%96%E7%B1%BB%E5%9E%8B)
        - [Option 枚举用于处理空值](#option-%E6%9E%9A%E4%B8%BE%E7%94%A8%E4%BA%8E%E5%A4%84%E7%90%86%E7%A9%BA%E5%80%BC)
      - [数组](#%E6%95%B0%E7%BB%84)
        - [创建数组](#%E5%88%9B%E5%BB%BA%E6%95%B0%E7%BB%84)
        - [访问数组元素](#%E8%AE%BF%E9%97%AE%E6%95%B0%E7%BB%84%E5%85%83%E7%B4%A0)
        - [数组切片](#%E6%95%B0%E7%BB%84%E5%88%87%E7%89%87)
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

在 `Rust` 中，获取变量的引用，称之为借用(`borrowing`)

##### 引用与解引用

常规引用是一个指针类型，指向了对象存储的内存地址

```rs
fn main() {
    let x = 5;
    let y = &x; // y 是 x 的一个引用

    assert_eq!(5, x);
    assert_eq!(5, *y);
}
```

如果希望对 `y` 的值做出断言，必须使用 `*y` 来解出引用所指向的值（也就是解引用）

##### 不可变引用

```rs
fn main() {
    let s1 = String::from("hello");

    let len = calculate_length(&s1); // 通过引用，不传递所有权

    println!("The length of '{}' is {}.", s1, len);
}

fn calculate_length(s: &String) -> usize {
    s.len()
}
```

这里，`&` 符号即是引用，它们允许你使用值，但是不获取所有权

![avatar](../images/v2-fc68ea4a1fe2e3fe4c5bb523a0a8247c_1440w.jpg)

上图中，通过 `&s1` 语法，我们创建了一个指向 `s1` 的引用，但是并不拥有它。因为并不拥有这个值，当引用离开作用域后，其指向的值也不会被丢弃

```rs
fn calculate_length(s: &String) -> usize { // s 是对 String 的引用
    s.len()
} // 这里，s 离开了作用域。但因为它并不拥有引用值的所有权，
  // 所以什么也不会发生
```

引用是不可变的，看下面的例子：

```rs
fn main() {
    let s = String::from("hello");
    change(&s);
}

fn change(some_string: &String) {
    some_string.push_str(", world");  // 报错
    //////////////////////////
    // cannot borrow `*some_string` as mutable, as it is behind a `&` reference
// `some_string` is a `&` reference, so the data it refers to cannot be borrowed as mutablerustcClick for full ////compiler diagnostic
//main.rs(6, 24): consider changing this to be a mutable reference: `&mut String`
}
```

##### 可变引用

如何修复上面的例子：

```rs
fn main() {
    let mut s = String::from("hello"); // 可变类型

    change(&mut s); // 参数为可变引用
}

fn change(some_string: &mut String) {  // 声明可变引用参数
    some_string.push_str(", world");
}
```

可变引用有限制：同一作用域，特定数据只能有一个可变引用，同时，可变引用与不可变引用不能同时存在

##### 悬垂引用(Dangling References)

悬垂引用也叫做悬垂指针，意思为指针指向某个值后，这个值被释放掉了，而指针仍然存在，其指向的内存可能不存在任何值或已被其它变量重新使用

#### 借用规则总结

总的来说，借用规则如下：

- 同一时刻，你只能拥有要么一个可变引用, 要么任意多个不可变引用
- 引用必须总是有效的

### 复合类型

复合类型是由其它类型组合而成的，最典型的就是结构体 `struct` 和枚举 `enum`

#### 字符串与切片

##### 切片(slice)

切片( `slice` ) 允许你引用集合中部分连续的元素序列，而不是引用整个集合，对于字符串而言，切片就是对 `String` 类型中某一部分的引用

```rs
let s = String::from("hello world");

let hello = &s[0..5];
let world = &s[6..11];
```

这就是创建切片的语法，使用方括号包括的一个序列：[开始索引..终止索引]，其中开始索引是切片中第一个元素的索引位置，而终止索引是最后一个元素后面的索引位置，也就是这是一个 右半开区间。在切片数据结构内部会保存开始的位置和切片的长度，其中长度是通过 终止索引 - 开始索引 的方式计算得来的

在使用 `Rust` 的 `.. range` 序列语法时，如果你想从索引 `0` 开始，可以省略 `0`

```rs
let s = String::from("hello");

let slice = &s[0..2];
let slice = &s[..2];  // 与上面的代码效果一样
```

同样的，如果你的切片想要包含 `String` 的最后一个字节，则可以这样使用：

```rs
let s = String::from("hello");

let len = s.len();

let slice = &s[4..len];
let slice = &s[4..];
```

你也可以截取完整的 `String` 切片：

```rs
let s = String::from("hello");

let len = s.len();

let slice = &s[0..len];
let slice = &s[..];
```

**注意：** 切片的索引必须落在字符之间的边界位置，否则可能会引起程序崩溃

因为切片是对集合的部分引用，因此不仅仅字符串有切片，其它集合类型也有，例如数组：

```rs
let a = [1, 2, 3, 4, 5];

let slice = &a[1..3];

assert_eq!(slice, &[2, 3]);
```

##### 字符串字面量是切片

字符串字面量的类型其实就是 `&str`

```rs
let s = "Hello, world!"; // s -> &str
```

该切片指向了程序可执行文件中的某个点，这也是为什么字符串字面量是不可变的，因为 `&str` 是一个不可变引用

##### 什么是字符串

字符串是由字符组成的连续集合，`Rust` 中的字符是 `Unicode` 类型，因此每个字符占据 `4` 个字节内存空间，但是在字符串中不一样，字符串是 `UTF-8` 编码，也就是字符串中的字符所占的字节数是变化的(`1` - `4`)

当 `Rust` 用户提到字符串时，往往指的就是 `String` 类型和 `&str` 字符串切片类型，这两个类型都是 `UTF-8` 编码

除了 `String` 类型的字符串，`Rust` 的标准库还提供了其他类型的字符串，例如 `OsString`， `OsStr`， `CsString` 和 `CsStr` 等，注意到这些名字都以 `String` 或者 `Str` 结尾了吗？它们分别对应的是具有所有权和被借用的变量

##### String 与 &str 的转换

从 `&str` 类型生成 `String` 类型的操作：

- `String::from("hello,world")`
- `"hello,world".to_string()`

将 `String` 类型转为 `&str` 类型，可以直接取引用

```rs
fn main() {
    let s = String::from("hello,world!");
    say_hello(&s);
    say_hello(&s[..]);
    say_hello(s.as_str());
}

fn say_hello(s: &str) {
    println!("{}",s);
}
```

##### 字符串索引

在 `Rust` 中，不能使用索引的方式访问字符串的某个字符或者子串，字符串的底层的数据存储格式实际上是 `[ u8 ]`，一个字节数组，每个英文字母在 `UTF-8` 编码中仅占用 `1` 个字节，但大部分中文占 `3` 个字节，这样的访问就会报错。

##### 字符串切片

字符串切片是非常危险的操作，因为切片的索引是通过字节来进行，遇到中文，或其他非英文字符，很容易报错导致程序 `panic`

##### 操作字符串

- 追加 (`Push`)

  在字符串尾部可以使用 `push()` 方法追加字符 `char`，也可以使用 `push_str()` 方法追加字符串字面量。这两个方法都是在原有的字符串上追加，并不会返回新的字符串。由于字符串追加操作要修改原来的字符串，则该字符串必须是可变的，即字符串变量必须由 `mut` 关键字修饰。

  ```rs
  fn main() {
      let mut s = String::from("Hello ");

      s.push_str("rust");
      println!("追加字符串 push_str() -> {}", s);

      s.push('!');
      println!("追加字符 push() -> {}", s);
  }
  ```

- 插入 (`Insert`)

  可以使用 `insert()` 方法插入单个字符 `char`，也可以使用 `insert_str()` 方法插入字符串字面量, 它们需要传入两个参数，第一个参数是字符（串）插入位置的索引，第二个参数是要插入的字符（串），索引从 `0` 开始计数。该字符串必须是可变的，即字符串变量必须由 `mut` 关键字修饰

  ```rs
  fn main() {
      let mut s = String::from("Hello rust!");
      s.insert(5, ',');
      println!("插入字符 insert() -> {}", s);
      s.insert_str(6, " I like");
      println!("插入字符串 insert_str() -> {}", s);
  }
  ```

- 替换 (`Replace`)

  把字符串中的某个字符串替换成其它的字符串，使用 `replace()` 方法，替换相关的操作有三个方法：

  - `replace`

    该方法可适用于 `String` 和 `&str` 类型。`replace()` 方法接收两个参数，第一个参数是要被替换的字符串，第二个参数是新的字符串。该方法会替换所有匹配到的字符串。该方法是返回一个新的字符串，而不是操作原来的字符串。

    ```rs
    fn main() {
        let string_replace = String::from("I like rust. Learning rust is my favorite!");
        let new_string_replace = string_replace.replace("rust", "RUST");
        dbg!(new_string_replace);
    }
    ```

  - `replacen`

      该方法可适用于 `String` 和 `&str` 类型。`replacen()` 方法接收三个参数，前两个参数与 `replace()` 方法一样，第三个参数则表示替换的个数。该方法是返回一个新的字符串，而不是操作原来的字符串

      ```rs
      fn main() {
          let string_replace = "I like rust. Learning rust is my favorite!";
          let new_string_replacen = string_replace.replacen("rust", "RUST", 1);
          dbg!(new_string_replacen);
      }
      ```

  - `replace_range`

      该方法仅适用于 `String` 类型。`replace_range` 接收两个参数，第一个参数是要替换字符串的范围（`Range`），第二个参数是新的字符串。该方法是直接操作原来的字符串，不会返回新的字符串。该方法需要使用 `mut` 关键字修饰。

      ```rs
      fn main() {
          let mut string_replace_range = String::from("I like rust!");
          string_replace_range.replace_range(7..8, "R");
          dbg!(string_replace_range);
      }
      ```

- 删除 (`Delete`)

  与字符串删除相关的方法有 `4` 个，他们分别是 `pop()`，`remove()`，`truncate()`，`clear()`。这四个方法仅适用于 `String` 类型

  - `pop` —— 删除并返回字符串的最后一个字符

    该方法是直接操作原来的字符串。但是存在返回值，其返回值是一个 `Option` 类型，如果字符串为空，则返回 `None`

    ```rs
    fn main() {
        let mut string_pop = String::from("rust pop 中文!");
        let p1 = string_pop.pop();
        let p2 = string_pop.pop();
        dbg!(p1);
        dbg!(p2);
        dbg!(string_pop);
    }
    ```

  - `remove` —— 删除并返回字符串中指定位置的字符

    该方法是直接操作原来的字符串。但是存在返回值，其返回值是删除位置的字符串，只接收一个参数，表示该字符起始索引位置。`remove()` 方法是按照字节来处理字符串的，如果参数所给的位置不是合法的字符边界，则会发生错误。

    ```rs
        fn main() {
        let mut string_remove = String::from("测试remove方法");
        println!(
            "string_remove 占 {} 个字节",
            std::mem::size_of_val(string_remove.as_str())
        );
        // 删除第一个汉字
        string_remove.remove(0);
        // 下面代码会发生错误
        // string_remove.remove(1);
        // 直接删除第二个汉字
        // string_remove.remove(3);
        dbg!(string_remove);
    }
    ```

  - `truncate` —— 删除字符串中从指定位置开始到结尾的全部字符

    该方法是直接操作原来的字符串。无返回值。 `truncate()` 方法是按照字节来处理字符串的，如果参数所给的位置不是合法的字符边界，则会发生错误。

    ```rs
    fn main() {
        let mut string_truncate = String::from("测试truncate");
        string_truncate.truncate(3);
        dbg!(string_truncate);
    }
    ```

  - `clear` —— 清空字符串

    该方法是直接操作原来的字符串。调用后，删除字符串中的所有字符，相当于 `truncate()` 方法参数为 `0` 的时候

    ```rs
    fn main() {
        let mut string_clear = String::from("string clear");
        string_clear.clear();
        dbg!(string_clear);
    }
    ```

- 连接 (`Concatenate`)

  - 使用 `+` 或者 `+=` 连接字符串

    使用 `+` 或者 `+=` 连接字符串，要求右边的参数必须为字符串的切片引用（`Slice`）类型，`+` 和 `+=` 都是返回一个新的字符串。所以变量声明可以不需要 `mut` 关键字修饰。

    ```rs
    fn main() {
        let string_append = String::from("hello ");
        let string_rust = String::from("rust");
        // &string_rust会自动解引用为&str
        let result = string_append + &string_rust;
        let mut result = result + "!";
        result += "!!!";

        println!("连接字符串 + -> {}", result);
    }
    ```

  - 使用 `format!` 连接字符串

    `format!` 这种方式适用于 `String` 和 `&str`

    ```rs
    fn main() {
        let s1 = "hello";
        let s2 = String::from("rust");
        let s = format!("{} {}!", s1, s2);
        println!("{}", s);
    }
    ```

##### 字符串转义

我们可以通过转义的方式 `\` 输出 `ASCII` 和 `Unicode` 字符

```rs
fn main() {
    // 通过 \ + 字符的十六进制表示，转义输出一个字符
    let byte_escape = "I'm writing \x52\x75\x73\x74!";
    println!("What are you doing\x3F (\\x3F means ?) {}", byte_escape);

    // \u 可以输出一个 unicode 字符
    let unicode_codepoint = "\u{211D}";
    let character_name = "\"DOUBLE-STRUCK CAPITAL R\"";

    println!(
        "Unicode character {} (U+211D) is called {}",
        unicode_codepoint, character_name
    );

    // 换行了也会保持之前的字符串格式
    let long_string = "String literals
                        can span multiple lines.
                        The linebreak and indentation here ->\
                        <- can be escaped too!";
    println!("{}", long_string);
}
```

希望保持字符串的原样，不要转义:

```rs
fn main() {
    println!("{}", "hello \\x52\\x75\\x73\\x74");
    let raw_str = r"Escapes don't work here: \x3F \u{211D}";
    println!("{}", raw_str);

    // 如果字符串包含双引号，可以在开头和结尾加 #
    let quotes = r#"And then I said: "There is no escape!""#;
    println!("{}", quotes);

    // 如果还是有歧义，可以继续增加，没有限制
    let longer_delimiter = r###"A string with "# in it. And even "##!"###;
    println!("{}", longer_delimiter);
}
```

##### 操作 UTF-8 字符串

- 字符

  如果你想要以 `Unicode` 字符的方式遍历字符串，最好的办法是使用 `chars` 方法

  ```rs
  for c in "中国人".chars() {
      println!("{}", c);
  }
  /**
    中
    国
    人
  */
  ```

- 字节

  字节返回字符串的底层字节数组表现形式

  ```rs
  for b in "中国人".bytes() {
      println!("{}", b);
  }
  /**
    228
    184
    173
    229
    155
    189
    228
    186
    186
   */

  ```

- 获取子串

  从 `UTF-8` 字符串中获取子串是较为复杂的事情，使用标准库你是做不到的。 你需要在 `crates.io` 上搜索 `utf8` 来寻找想要的功能。可以考虑尝试下这个库：`utf8_slice`。

##### 字符串深度剖析

我们来思考一下，为什么 `String` 可变，而字符串字面值 `&str` 不可变。

就字符串字面值来说，我们在编译时就知道其内容，最终字面值文本被直接硬编码进可执行文件中，这使得字符串字面值快速且高效，这主要得益于字符串字面值的不可变性。不幸的是，我们不能为了获得这种性能，而把每一个在编译时大小未知的文本都放进内存中（你也做不到！），因为有的字符串是在程序运行得过程中动态生成的。

对于 `String` 类型，为了支持一个可变、可增长的文本片段，需要在堆上分配一块在编译时未知大小的内存来存放内容，这些都是在程序运行时完成的：

- 首先向操作系统请求内存来存放 `String` 对象
- 在使用完成后，将内存释放，归还给操作系统

其中第一部分由 `String::from` 完成，它创建了一个全新的 `String`。

到了第二部分，在有垃圾回收 `GC` 的语言中，`GC` 来负责标记并清除这些不再使用的内存对象，这个过程都是自动完成，无需开发者关心；但是在无 `GC` 的语言中，需要开发者手动去释放这些内存对象，就像创建对象需要通过编写代码来完成一样，未能正确释放对象造成的后果简直不可估量。

而在 Rust 中，变量在离开作用域后，就自动释放其占用的内存：

```rs
{
    let s = String::from("hello"); // 从此处起，s 是有效的

    // 使用 s
}                                  // 此作用域已结束，
                                   // s 不再有效，调用 drop函数， 内存被释放
```

与其它系统编程语言的 `free` 函数相同，`Rust` 也提供了一个释放内存的函数： `drop`，但是不同的是，其它语言要手动调用 `free` 来释放每一个变量占用的内存，而 `Rust` 则在变量离开作用域时，自动调用 `drop` 函数: 上面代码中，`Rust` 在结尾的 `}` 处自动调用 `drop`。

#### 元组

元组是由多种类型组合到一起形成的，因此它是复合类型，元组的长度是固定的，元组中元素的顺序也是固定的。

```rs
fn main() {
    let tup: (i32, f64, u8) = (500, 6.4, 1);
}
```

##### 用模式匹配解构元组

```rs
fn main() {
    let tup = (500, 6.4, 1);

    let (x, y, z) = tup;

    println!("The value of y is: {}", y);
}
```

##### 用 `.` 来访问元组

如果只想要访问某个特定元素，`Rust` 提供了 `.` 的访问方式：

```rs
fn main() {
    let x: (i32, f64, u8) = (500, 6.4, 1);

    let five_hundred = x.0;

    let six_point_four = x.1;

    let one = x.2;
}
```

元组的索引从 `0` 开始

##### 元组的使用示例

元组在函数返回值场景很常用，可以使用元组返回多个值：

```rs
fn main() {
    let s1 = String::from("hello");

    let (s2, len) = calculate_length(s1);

    println!("The length of '{}' is {}.", s2, len);
}

fn calculate_length(s: String) -> (String, usize) {
    let length = s.len(); // len() 返回字符串的长度

    (s, length)
}
```

#### 结构体

结构体 `struct` 是一种更高级的数据结构，它由其它数据类型组合而来，帮助我们更好的抽象问题

##### 结构体语法

- 定义结构体

  一个结构体由几部分组成：
  
  - 通过关键字 `struct` 定义
  - 一个清晰明确的结构体 名称
  - 几个有名字的结构体 字段

  ```rs
  struct User {
      active: bool,
      username: String,
      email: String,
      sign_in_count: u64,
  }
  ```

- 创建结构体实例

  创建 User 结构体的实例:

  ```rs
  let user1 = User {
      email: String::from("someone@example.com"),
      username: String::from("someusername123"),
      active: true,
      sign_in_count: 1,
  };
  ```

  **注意：**

  - 初始化实例时，每个字段都需要进行初始化
  - 初始化时的字段顺序不需要和结构体定义时的顺序一致

- 访问结构体字段

  通过 `.` 操作符即可访问结构体实例内部的字段值，也可以修改它们：

  ```rs
  let mut user1 = User {
      email: String::from("someone@example.com"),
      username: String::from("someusername123"),
      active: true,
      sign_in_count: 1,
  };

  user1.email = String::from("anotheremail@example.com");
  ```

  `Rust` 不支持将某个结构体某个字段标记为可变。

- 简化结构体创建

  ```rs
  fn build_user(email: String, username: String) -> User {
      User {
          email: email,
          username: username,
          active: true,
          sign_in_count: 1,
      }
  }
  ```

  通过上面的函数我们可以简化结构体实例的创建，另外，参数也可以简化，类似于 `TypeScript`

  ```rs
  fn build_user(email: String, username: String) -> User {
      User {
          email,
          username,
          active: true,
          sign_in_count: 1,
      }
  }
  ```

- 结构体更新语法

  在实际开发场景中，我们如何通过一个结构体实例来创建另外一个实例呢?  `Rust` 为我们提供了结构体更新语法：

  ```rs
  let user2 = User {
      email: String::from("another@example.com"),
      ..user1
  };
  ```

  需要注意的是 `..user1` 必须在结构体的尾部使用。

  上面的操作会导致 `user1` 中的 `username` 无法使用，因为它已经发生了所有权转移，其他字段仍然可以使用，因为具有 `Copy` 特性而发生了值拷贝。所以，把结构体中具有所有权的字段转移出去后，将无法再访问该字段，但是可以正常访问其它的字段。

##### 元组结构体(Tuple Struct)

结构体必须要有名称，但是结构体的字段可以没有名称，这种结构体长得很像元组，因此被称为元组结构体，例如：

```rs
    struct Color(i32, i32, i32);
    struct Point(i32, i32, i32);

    let black = Color(0, 0, 0);
    let origin = Point(0, 0, 0);
```

##### 单元结构体(Unit-like Struct)

之前讲过的啥也没有用的单元类型，单元结构体就跟它很像，没有任何字段和属性

如果你定义一个类型，且并不关心该类型的内容, 只关心它的行为时，就可以使用 单元结构体：

```rs
struct AlwaysEqual;

let subject = AlwaysEqual;

// 我们不关心 AlwaysEqual 的字段数据，只关心它的行为，因此将它声明为单元结构体，然后再为它实现某个特征
impl SomeTrait for AlwaysEqual {

}
```

##### 结构体数据的所有权

上面的示例中，我们使用了自身拥有所有权的 String 类型而非基于引用的 &str 类型，当然，结构体属性可以向其他数据源借用数据，但需要标记生命周期。

##### 使用 `#[derive(Debug)]` 来打印结构体的信息

在使用 `println!()` 方法进行打印时，占位符使用 `{}` 只能打印简单类型，如果想要打印类似结构体这种类型，需要使用 `{:?}` 这样的占位符，否则就会报错，结构体没有实现 `Display` 特征，而基本类型，都默认实现了该特征。

手动实现 `Display` 特征明显不明智，而我们可以使用 `#[derive(Debug)]` 这样的派生实现

```rs
#[derive(Debug)]
struct Rectangle {
    width: u32,
    height: u32,
}

fn main() {
    let rect1 = Rectangle {
        width: 30,
        height: 50,
    };

    println!("rect1 is {:?}", rect1);
}
```

如果结构体足够复杂，我们希望有更好的输出，可以使用 `{:#?}` 来替代 `{:?}`

还有一个简单的输出 `debug` 信息的方法，那就是使用 `dbg!` 宏，它会拿走表达式的所有权，然后打印出相应的文件名、行号等 `debug` 信息，当然还有我们需要的表达式的求值结果。除此之外，它最终还会把表达式值的所有权返回！

```rs
#[derive(Debug)]
struct Rectangle {
    width: u32,
    height: u32,
}

fn main() {
    let scale = 2;
    let rect1 = Rectangle {
        width: dbg!(30 * scale),
        height: 50,
    };

    dbg!(&rect1);
}

/**
    $ cargo run
    [src/main.rs:10] 30 * scale = 60
    [src/main.rs:14] &rect1 = Rectangle {
        width: 60,
        height: 50,
    }
  */
```

#### 枚举

枚举(`enum` 或 `enumeration`)允许你通过列举可能的成员来定义一个枚举类型，枚举类型是一个类型，它会包含所有可能的枚举成员, 而枚举值是该类型中的具体某个成员的实例。

```rs
enum PokerSuit {
  Clubs,
  Spades,
  Diamonds,
  Hearts,
}
```

##### 枚举值

我们来创建枚举类型的成员实例：

```rs
let heart = PokerSuit::Hearts;
let diamond = PokerSuit::Diamonds;
```

通过 `::` 操作符来访问 `PokerSuit` 下的具体成员

```rs
fn main() {
    let heart = PokerSuit::Hearts;
    let diamond = PokerSuit::Diamonds;

    print_suit(heart);
    print_suit(diamond);
}

fn print_suit(card: PokerSuit) {
    println!("{:?}",card);
}
```

那如何为枚举添加枚举值呢？我们可以使用 struct 来表示，但 Rust 提供了更优雅的方式

```rs
enum PokerCard {
    Clubs(u8),
    Spades(u8),
    Diamonds(u8),
    Hearts(u8),
}

fn main() {
   let c1 = PokerCard::Spades(5);
   let c2 = PokerCard::Diamonds(13);
}
```

我们可以直接将数据信息关联到枚举成员上，不仅如此，同一个枚举类型下的不同成员还能持有不同的数据类型

```rs
enum PokerCard {
    Clubs(u8),
    Spades(u8),
    Diamonds(char),
    Hearts(char),
}

fn main() {
   let c1 = PokerCard::Spades(5);
   let c2 = PokerCard::Diamonds('A');
}
```

Rust 标准库中表示 IP 地址的枚举这样定义：

```rs
struct Ipv4Addr {
    // --snip--
}

struct Ipv6Addr {
    // --snip--
}

enum IpAddr {
    V4(Ipv4Addr),
    V6(Ipv6Addr),
}
```

可以看出，任何类型的数据都可以放入枚举成员中: 例如字符串、数值、结构体甚至另一个枚举。

##### 同一化类型

```rs
enum Websocket {
  Tcp(Websocket<TcpStream>),
  Tls(Websocket<native_tls::TlsStream<TcpStream>>),
}
```

使用枚举定义了两种不同的长连接方式

##### Option 枚举用于处理空值

在 `Rust` 中，没有其他语言中的 `null` 值，而改为使用 `Option` 枚举变量来表述这种结果

`Option` 枚举包含两个成员，一个成员表示含有值：`Some(T)`, 另一个表示没有值：`None`

```rs
enum Option<T> {
    Some(T),
    None,
}
```

#### 数组

在 `Rust` 中，最常用的数组有两种，第一种是速度很快但是长度固定的 `array`(数组)，第二种是可动态增长的但是有性能损耗的 `Vector`(动态数组)。

`String` 和 `Vector` 在 `Rust` 中都是高级类型：集合类型。

数组的具体定义是：将多个类型相同的元素依次组合在一起，就是一个数组

- 长度固定
- 元素必须有相同的类型
- 依次线性排列

**注意：** 这里说的数组是 `Rust` 的基本类型，是固定长度的，这点与其他编程语言不同，其它编程语言的数组往往是可变长度的，与 `Rust` 中的动态数组 `Vector` 类似。

##### 创建数组

在 `Rust` 中，数组是这样定义的：

```rs
fn main() {
    let a = [1, 2, 3, 4, 5];
}
```

数组 `Array` 元素类型大小固定，且长度也是固定，因此存储在栈上，性能也会非常优秀。动态数组 `Vector` 是存储在堆上，因此长度可以动态改变。当你不确定是使用数组还是动态数组时，那就应该使用后者

```rs
// 月份是固定的，这里使用 Array
let months = ["January", "February", "March", "April", "May", "June", "July",
              "August", "September", "October", "November", "December"];
```

为数组声明类型：

```rs
let a: [i32; 5] = [1, 2, 3, 4, 5];
```

还可以使用下面的语法初始化一个某个值重复出现 `N` 次的数组：

```rs
let a = [3; 5];
```

##### 访问数组元素

可以通过索引的方式来访问存放其中的元素：

```rs
fn main() {
    let a = [9, 8, 7, 6, 5];

    let first = a[0]; // 获取a数组第一个元素
    let second = a[1]; // 获取第二个元素
}
```

如果使用超出数组范围的索引访问数组元素, 则会访问到不存在的数组元素，最终程序会崩溃退出：

```rs
use std::io;

fn main() {
    let a = [1, 2, 3, 4, 5];

    println!("Please enter an array index.");

    let mut index = String::new();
    // 读取控制台的输出
    io::stdin()
        .read_line(&mut index)
        .expect("Failed to read line");

    let index: usize = index
        .trim()
        .parse()
        .expect("Index entered was not a number");

    let element = a[index];

    println!(
        "The value of the element at index {} is: {}",
        index, element
    );
}
```

当你尝试使用索引访问元素时，`Rust` 将检查你指定的索引是否小于数组长度。如果索引大于或等于数组长度，`Rust` 会出现 `panic`。这种检查只能在运行时进行

在实际开发中，如果数组元素是非基本类型，比如：

```rs
let array = [String::from("rust is good!"); 8];

println!("{:#?}", array);
```

此时你会得到一段错误，因为复杂类型没有实现 Copy 特征，所以在数组元素是复杂类型时，正确的写法，应该调用 `std::array::from_fn`

```rs
let array: [String; 8] = core::array::from_fn(|i| String::from("rust is good!"));

println!("{:#?}", array);
```

##### 数组切片

切片允许你引用集合中的部分连续片段，而不是整个集合，对于数组也是，数组切片允许我们引用数组的一部分

```rs
let a: [i32; 5] = [1, 2, 3, 4, 5];

let slice: &[i32] = &a[1..3];

assert_eq!(slice, &[2, 3]);
```

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

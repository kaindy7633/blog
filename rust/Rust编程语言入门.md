<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Rust 编程语言入门](#rust-%E7%BC%96%E7%A8%8B%E8%AF%AD%E8%A8%80%E5%85%A5%E9%97%A8)
  - [Rust 简介](#rust-%E7%AE%80%E4%BB%8B)
    - [为什么要使用 Rust](#%E4%B8%BA%E4%BB%80%E4%B9%88%E8%A6%81%E4%BD%BF%E7%94%A8-rust)
    - [Hello World](#hello-world)
    - [Hello Cargo](#hello-cargo)
  - [基础概念](#%E5%9F%BA%E7%A1%80%E6%A6%82%E5%BF%B5)
    - [变量与可变性](#%E5%8F%98%E9%87%8F%E4%B8%8E%E5%8F%AF%E5%8F%98%E6%80%A7)
    - [变量与常量](#%E5%8F%98%E9%87%8F%E4%B8%8E%E5%B8%B8%E9%87%8F)
    - [Shadowing(隐藏)](#shadowing%E9%9A%90%E8%97%8F)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Rust 编程语言入门

## Rust 简介

### 为什么要使用 Rust

`Rust` 是一门令人兴奋的编程语言，它可以让每个人编写可靠且高效的软件，它可以用来替换 `C/C++`，且具有同样的性能，很多常见的 `Bug` 在编译时就可以被消灭

`Rust` 是一门通用的编程语言，但它更善于以下场景：

- 需要运行时的速度
- 需要内存安全
- 更好的利用多处理器

### Hello World

按照惯例，下面是 `Rust` 版的 `Hello World`

```rust
fn main() {
    println!("Hello World!");
}
```

### Hello Cargo

`Cargo` 是 `Rust` 的构建系统和包惯例工具，构建代码、下载依赖库，构建库等等...

安装 `Rust` 时 `Cargo` 就会被自动安装，使用 `cargo --version` 命令在命令行来查看 `Cargo` 是否被正确安装

我们可以使用 Cargo 来创建项目，执行下面的命令：

```bash
cargo new hello_cargo
```

编译时可以使用 `cargo build`，运行可以使用 `cargo run`

## 基础概念

### 变量与可变性

在 `Rust` 中声明变量使用 `let` 关键字，默认情况下，变量是不可变的（`Immutable`）

```rust
let x = 5;   // 声明一个不可变变量 x
println!("The value of x is {}", x);  // {} 是占位符

x = 6;  // 编译报错
```

那如何才能让声明的变量可变呢？ 答案就是使用 `mut` 关键字

```rust
let mut x = 5;
println!("The value of x is {}", x);  // 5

x = 6;
println!("The value of x is {}", x);  // 6
```

### 变量与常量

常量（`constant`），常量在绑定值以后是不可变的，但它与不可变的变量有很多区别：

- 不可以使用 `mut` 关键字，因为常量永远都是不可变的
- 声明常量使用 `const` 关键字，它的类型必须被标注
- 常量可以在任何作用域进行声明，包括全局作用域
- 常量只可以绑定到常量表达式，无法绑定到函数的调用结果或只能在运行时才能计算出的值

在程序运行期间，常量在其声明的作用域内一直有效

`Rust` 中，常量的命名规范是使用全大写字母，每个单词之间用下划线分隔，例如：`MAX_POINTS`，下面是一个常量声明的例子：

```rust
const MAX_POINTS: u32 = 100_000;
```

### Shadowing(隐藏)

在 `Rust` 中，可以使用相同的名字来声明新的变量，新的变量就会 `shadow` (隐藏) 之前声明的同名变量，看下面的例子：

```rust
let x = 5;  // 声明不可变变量 x
x = x + 1;  // 报错

let x = x + 1;  // 编译通过，第一个x覆盖了前面声明的x， 表达式右边的x就是上面的x
```

`shadow` 和把变量标记为 `mut` 是不一样的：

- 如果不使用 `let` 关键字，那么重新给非 `mut` 的变量赋值会导致编译时错误
- 而使用 `let` 声明的同名新变量，也是不可变的
- 使用 `let` 声明的同名新变量，它的类型可以与之前不同

```rust
let spaces = "    ";  // &str类型
let spaces = spaces.len();  // usize类型
```

### 数据类型

`Rust` 的数据类型分为标量类型和符合类型，`Rust` 是静态编译语言，在编译时必须知道所有变量的类型

在通常情况下，基于使用的值，`Rust` 编译器能够推断出它的具体类型，但如果可能的类型比较多（例如把 `String` 转换为整数的 `parse` 方法），就必须添加类型的标注，否则编译就会报错

```rust
let guess: u32 = "42".parse().expect("Not a number");
// 如果不为guess变量指定变量类型 u32，程序就会报错
```

#### 标量类型

一个标量类型代表一个单个的值，`Rust` 有四个主要的标量类型：

- 整数类型
- 浮点类型
- 布尔类型
- 字符类型

##### 整数类型

整数类型没有小数部分，例如 `u32` 就是一个无符号的整数类型，占据 `32` 位的空间，无符号整数类型以 `u` 开头，有符号整数类型以 `i` 开头，`Rust` 的整数类型列表如下图：

![](../images/20210513210207.png)

每种整数类型都分 `i` 和 `u`，以及固定的位数，有符号的范围是：`-(2^n - 1)` 到 `2^n - 1`，无符号的范围是：`0` 到 `2^n - 1`

下面的 `arch` 表示系统的架构，`isize` 和 `usize` 类型的位数是由程序运行的计算机的架构所决定的，如果是 `64` 位计算机，那就是 `64` 位，分别是 `i64` 和 `u64`

这两种数据类型使用的并不多，最主要的场景是对某种集合进行索引操作

##### 整数字面量

在 `Rust` 中，整数字面量有十进制、十六进制、八进制、二进制和 `Byte`

![](../images/20210513211140.png)

在上面的整数字面量中，除了 `byte` 类型外，所有的字面值都允许使用类型后缀，如：`57u8`，它表示值是 `57`，类型是 `u8`

如果你不太清楚应该使用哪种类型，可以使用 `Rust` 提供的默认类型

整数的默认类型是 `i32`，总体来说速度很快，即使是在 `64` 位系统中

##### 整数溢出

例子：`u8` 的范围是 `0` ~ `255`，如果你把一个 `u8` 变量的值设为 `256`，那么会有两种情况发生：

- 在调式模式下编译，`Rust` 会检查整数溢出，如果发生溢出，程序会在运行时 `panic`
- 在发布模式下，（`build --release`）编译，`Rust` 不会检查可能导致 `panic` 的整数溢出

如果溢出发生，`Rust` 就会执行"环绕"操作，如 `256` 设置为 `0`，`257` 设置为 `1` ...

##### 浮点类型

`Rust` 有两种基础的浮点类型，也就是含有小数部分的类型

- `f32`， `32` 位，单精度
- `f64`， `64` 位，双精度

`Rust` 的浮点类型使用 `IEEE-754` 标准来表述，`f64` 是默认类型，在现代 `CPU` 上 `f64` 和 `f32` 的速度差不多，而且精度更高

```rust
let x = 2.0;  // 没有显式指定类型，编译器给x设置了默认的类型f64
let y: f32 = 3.0;  // 显式指定类型f32
```

##### 数值操作

Rust 支持数值的基本操作，如：加减乘除余

```rust
let sum = 5 + 10;
let difference = 95.5 - 4.3;
let product = 4 * 30;
let quotient = 56.7 / 32.2;
let reminder = 54 % 5
```

##### 布尔类型

`Rust` 的布尔类型有两个值： `true` 和 `false`，它们占据一个字节大小，符号是 `bool`

```rust
let t = true;  // 自动推断t的类型是bool
let f: bool = false;  // 显式的指定类型为bool
```

##### 字符类型

`Rust` 中 `char` 类型被用来描述语言中最基础的单个字符，字符类型的字面量使用单引号，占用 `4` 个字节大小，是 `Unicode` 标量值，可以表示比 `ASCII` 多的多的字符内容，如：拼音、中日韩文、零长度空白字符、`emoji` 表情等

```rust
let x = 'z';
let y: char = '∈'
```

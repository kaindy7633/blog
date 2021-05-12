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

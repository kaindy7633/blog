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
    - [数据类型](#%E6%95%B0%E6%8D%AE%E7%B1%BB%E5%9E%8B)
      - [标量类型](#%E6%A0%87%E9%87%8F%E7%B1%BB%E5%9E%8B)
        - [整数类型](#%E6%95%B4%E6%95%B0%E7%B1%BB%E5%9E%8B)
        - [整数字面量](#%E6%95%B4%E6%95%B0%E5%AD%97%E9%9D%A2%E9%87%8F)
        - [整数溢出](#%E6%95%B4%E6%95%B0%E6%BA%A2%E5%87%BA)
        - [浮点类型](#%E6%B5%AE%E7%82%B9%E7%B1%BB%E5%9E%8B)
        - [数值操作](#%E6%95%B0%E5%80%BC%E6%93%8D%E4%BD%9C)
        - [布尔类型](#%E5%B8%83%E5%B0%94%E7%B1%BB%E5%9E%8B)
        - [字符类型](#%E5%AD%97%E7%AC%A6%E7%B1%BB%E5%9E%8B)
      - [复合类型](#%E5%A4%8D%E5%90%88%E7%B1%BB%E5%9E%8B)
        - [Tuple](#tuple)
        - [获取 Tuple 的元素值](#%E8%8E%B7%E5%8F%96-tuple-%E7%9A%84%E5%85%83%E7%B4%A0%E5%80%BC)
        - [访问 Tuple 的元素](#%E8%AE%BF%E9%97%AE-tuple-%E7%9A%84%E5%85%83%E7%B4%A0)
        - [数组](#%E6%95%B0%E7%BB%84)
        - [声明数组](#%E5%A3%B0%E6%98%8E%E6%95%B0%E7%BB%84)
        - [数组的用处](#%E6%95%B0%E7%BB%84%E7%9A%84%E7%94%A8%E5%A4%84)
        - [数组的类型](#%E6%95%B0%E7%BB%84%E7%9A%84%E7%B1%BB%E5%9E%8B)
        - [访问数组的元素](#%E8%AE%BF%E9%97%AE%E6%95%B0%E7%BB%84%E7%9A%84%E5%85%83%E7%B4%A0)
    - [函数](#%E5%87%BD%E6%95%B0)
      - [函数的参数](#%E5%87%BD%E6%95%B0%E7%9A%84%E5%8F%82%E6%95%B0)
      - [函数体重的语句与表达式](#%E5%87%BD%E6%95%B0%E4%BD%93%E9%87%8D%E7%9A%84%E8%AF%AD%E5%8F%A5%E4%B8%8E%E8%A1%A8%E8%BE%BE%E5%BC%8F)
      - [函数的返回值](#%E5%87%BD%E6%95%B0%E7%9A%84%E8%BF%94%E5%9B%9E%E5%80%BC)
    - [注释](#%E6%B3%A8%E9%87%8A)
    - [控制流](#%E6%8E%A7%E5%88%B6%E6%B5%81)
      - [if 表达式](#if-%E8%A1%A8%E8%BE%BE%E5%BC%8F)
        - [在 let 语句中使用 if](#%E5%9C%A8-let-%E8%AF%AD%E5%8F%A5%E4%B8%AD%E4%BD%BF%E7%94%A8-if)
      - [循环](#%E5%BE%AA%E7%8E%AF)
        - [loop](#loop)
        - [while 条件循环](#while-%E6%9D%A1%E4%BB%B6%E5%BE%AA%E7%8E%AF)
        - [使用 for 循环遍历集合](#%E4%BD%BF%E7%94%A8-for-%E5%BE%AA%E7%8E%AF%E9%81%8D%E5%8E%86%E9%9B%86%E5%90%88)
        - [Range](#range)

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

#### 复合类型

复合类型可以将多个值放在一个类型里，`Rust` 提供了两种基础的复合类型：元组（`Tuple`）和数组

##### Tuple

`Tuple` 可以将多个类型的多个值放在一个类型里，它的长度是固定的，一旦声明就无法改变。创建 `Tuple`，在小括号中创建，将值用逗号分开，`Tuple` 中的每个位置都对应一个类型，`Tuple` 中个的各元素的类型不必相同

```rust
let tup: (i32, f64, u8) = (500, 6.4, 1)
```

##### 获取 Tuple 的元素值

我们可以使用模式匹配来解构(`destructure`)一个 `Tuple` 来获取元素的值

```rust
let tup: (i32, f64, u8) = (500, 6.4, 1);

let (x, y, z) = tup;

println!("{}, {}, {}", x, y, z);
```

##### 访问 Tuple 的元素

在 `tuple` 变量使用点标记法，后接元素的索引号

```rust
let tup: (i32, f64, u8) = (500, 6.4, 1)
println!("{}, {}, {}", tup.0, tup.1, tup.2)
```

##### 数组

- 数组也可以将多个值放在一个类型里
- 数组中每个元素的类型必须相同
- 数组的长度也是固定的

##### 声明数组

使用中括号将每个元素包裹，并使用逗号隔开

```rust
let a = [1, 2, 3, 4, 5];
```

##### 数组的用处

如果你想让数据存储在 `stack`（栈）上而不是 `heap`（堆）上，或者想保证有固定数量的元素，这时可以使用数组

还有一种数据结构叫 `Vector`，它与数组类似

- `Vector` 和数组类似，它由标准库提供
- `Vector` 的长度是可以改变的
- 如果你不确定应该使用数组还是 `Vector`，那么你就应该使用 `Vector`

##### 数组的类型

数组的类型可以以这种形式表示：[类型; 长度]，例如：

```rust
let a: [i32; 5] = [1, 2, 3, 4, 5];
```

另外一种声明数组的方式：如果数组的每个元素值都相同，那么可以在中括号里指定初始值，然后跟一个"; "，最后是数组的长度，如：

```rust
let a [3; 5]
// 它相同与 let a = [3, 3, 3, 3, 3]
```

##### 访问数组的元素

数组元素的访问跟其他语言是一致的，数组是 Stack 上分配的单个块的内存，可以使用索引来访问数组的元素

```rust
let colors = ["red", "blue", "yellow"];
let c1 = colors[0];
let c2 = colors[1];
```

如果访问的元素索引超出了数组的范围，那么：

- 编译会通过
- 运行会报错（`runtime` 时会 `panic`）

### 函数

声明函数使用 fn 关键字，依照惯例，针对函数和变量名，Rust 使用 snake case 命名规范：所有的字母都是小写，单词之间使用下划线分开

```rust
fn main() {
    println!("Hello World");
    another_function()
}

fn another_function() {
    // ...
}
```

#### 函数的参数

函数的参数分为两个部分，即 `parameters`（形参）和 `arguments`（实参），需要注意的是，函数的参数里，必须声明每个参数的类型

```rust
fn main() {
    another_function(5);  // arguments
}

fn another_function(x: i32) {
    println!("the value of x is: {}", x);
}
```

#### 函数体重的语句与表达式

函数体由一系列语句组成，可选的由一个表达式结束

`Rust` 是一个基于表达式的语言，语句是执行一些动作的指令，表达式会计算产生一个值

函数的定义也是语句，语句不返回值，所以不可以使用 let 将一个语句负值给一个变量

#### 函数的返回值

在 `->` 符号后边声明函数返回值的类型，但是不可以为返回值命名。

在 `Rust` 中，返回值就是函数体里面最后一个表达式的值，若想提前返回，需要使用 `return` 关键字，并指定一个值，大多数函数都是默认使用最后一个表达式作为返回值

```rust
fn five() -> i32 {
    5  // 5是一个表达式，表示 five 函数的返回值，不能加上分号
}

fn main() {
    let x = five();
    println!("The value of x is {}", x);
}
```

```rust
// 函数也可以加上参数
fn plus_five(x: i32) -> i32 {
    x + 5
}

fn main() {
    let x = five(6);
    println!("The value of x is {}", x);
}
```

### 注释

Rust 的注释和其他语言基本相同

```rust
// This is a function
fn five(x: i32) -> i32 {
    x + 5
}

/**
 * 我是多行注释中的第一行
 * 我是第二行
 */
// 也可以使用多个单行注释
// The entry point
fn main() {
    // ...
}
```

### 控制流

#### if 表达式

`if` 表达式允许你根据条件来执行不同的代码分支，这个条件必须是 `bool` 类型

`if` 表达式中，与条件相关联的代码块叫做分支（`arm`），可选的，在后边加上一个 `else` 表达式

```rust
fn main() {
    let number = 3;

    if number < 5 {
        println!("condition was true");
    } else {
        println!("condition was false");
    }
}
```

除此之外，`Rust` 里也可以使用 `else if` 语句来处理多重条件

但如果使用了多于一个 `else if`，那么最好使用 `match` 来重构代码

##### 在 let 语句中使用 if

因为 `if` 是一个表达式，所以可以将它放在 let 语句中等号的右边

```rust
let condition = true;

let number = if condition { 5 } else { 6 };

println!("The value of number is: {}", number);
```

#### 循环

`Rust` 提供了 3 种循环： `loop`、`while` 和 `for`

##### loop

`loop` 关键字告诉 `Rust` 需要反复的执行一块代码，直到你喊停为止

```rust
fn main() {
    loop {
        println!("again")
    }
}
```

上面的代码实际是一段死循环，我们可以在 `loop` 循环中使用 `break` 关键字来告诉程序何时停止

```rust
fn main() {
  let mut counter = 0;

  let result = loop {
      counter += 1;

      if counter == 10 {
          break counter * 2 // 停止循环，并将当前结果乘以2，没有加分号，直接返回结果给result
      }
  };

  println!("The result is: {}", result);
}
```

##### while 条件循环

另外一种常见的循环模式是每次执行循环体之前都判断一次条件，`while` 条件循环就是位这种模式而生的。

```rust
fn main() {
    let mut number = 3;

    while number != 0 {
        println!("{}!", number);
        number -= 1;
    };

    println!("LIFTOFF!!");
}
```

##### 使用 for 循环遍历集合

我们可以使用 `while` 或 `loop` 来遍历集合，但是易错且低效

```rust
fn main() {
    let a = [10, 20, 30, 40, 50];
    let mut index = 0;

    while index < 5 {  // 此处的索引范围容易出错，数组越界会造成panic
        println!("the value is: {}", a[index]);
        index += 1;
    }
}
```

使用 `for` 循环会更加的简洁紧凑，它可以针对集合中的每个元素来执行一些代码

```rust
fn main() {
    let a = [10, 20, 30, 40, 50];
    for element in a.iter() {
        println!("The value is: {}", element);
    }
}
```

由于 `for` 循环的安全、简洁性，所以它在 `Rust` 里用的最多

##### Range

`Range` 是由标准库提供的，它指定一个开始数字和一个结束数字，`Range` 可以生成它们之间的数字（不含结束），此外，还有一个 `rev` 方法，它可以反转 `Range`

```rust
// 使用 for 来实现上面倒计时的例子
fn main() {
    for number in (1..4).rev() {
        println!("{}!", number);
    }

    println!("LIFEOFF!!");
}
```

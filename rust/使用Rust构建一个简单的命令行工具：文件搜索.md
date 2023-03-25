<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [使用Rust构建一个简单的命令行工具：文件搜索](#%E4%BD%BF%E7%94%A8rust%E6%9E%84%E5%BB%BA%E4%B8%80%E4%B8%AA%E7%AE%80%E5%8D%95%E7%9A%84%E5%91%BD%E4%BB%A4%E8%A1%8C%E5%B7%A5%E5%85%B7%E6%96%87%E4%BB%B6%E6%90%9C%E7%B4%A2)
  - [基本功能](#%E5%9F%BA%E6%9C%AC%E5%8A%9F%E8%83%BD)
    - [接收命令行参数](#%E6%8E%A5%E6%94%B6%E5%91%BD%E4%BB%A4%E8%A1%8C%E5%8F%82%E6%95%B0)
    - [存储读取到的参数](#%E5%AD%98%E5%82%A8%E8%AF%BB%E5%8F%96%E5%88%B0%E7%9A%84%E5%8F%82%E6%95%B0)
    - [文件读取](#%E6%96%87%E4%BB%B6%E8%AF%BB%E5%8F%96)
  - [增加模块化和错误处理](#%E5%A2%9E%E5%8A%A0%E6%A8%A1%E5%9D%97%E5%8C%96%E5%92%8C%E9%94%99%E8%AF%AF%E5%A4%84%E7%90%86)
  - [测试驱动开发](#%E6%B5%8B%E8%AF%95%E9%A9%B1%E5%8A%A8%E5%BC%80%E5%8F%91)
  - [使用环境变量](#%E4%BD%BF%E7%94%A8%E7%8E%AF%E5%A2%83%E5%8F%98%E9%87%8F)
  - [重定向错误信息的输出](#%E9%87%8D%E5%AE%9A%E5%90%91%E9%94%99%E8%AF%AF%E4%BF%A1%E6%81%AF%E7%9A%84%E8%BE%93%E5%87%BA)
  - [使用迭代器来优化](#%E4%BD%BF%E7%94%A8%E8%BF%AD%E4%BB%A3%E5%99%A8%E6%9D%A5%E4%BC%98%E5%8C%96)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# 使用Rust构建一个简单的命令行工具：文件搜索

这是一个入门 Rust 的练习实战项目，构建一个简单的命令行工具，用于搜索文件，它将从命令行参数中读取指定的文件名和字符串，然后在相应的文件中找到包含该字符串的内容，最终打印出来。（类似于 `Linux` 中的 `grep` 命令）

## 基本功能

### 接收命令行参数

首先，我们需要创建一个新的项目 `minigrep`

```bash
cargo new minigrep
     Created binary (application) `minigrep` project
$ cd minigrep
```

我们执行搜索的命令大概是这个样子的：

```bash
cargo run -- searchstring example-filename.txt
```

上面的命令中，`--` 告诉 `cargo` 后面的参数是给我们的程序使用的

接下来就是在程序中读取传入的参数:

```rs
use std::env;

fn main() {
    let args: Vec<String> = env::args().collect();
    dbg!(args);
}
```

首先通过 `use` 引入标准库中的 `env` 包，然后 `env::args` 方法会读取并分析传入的命令行参数，最终通过 `collect` 方法输出一个集合类型 `Vector`。

用户的输入不可信，当传入的命令行参数包含非 `Unicode` 字符时， `std::env::args` 会直接崩溃，可以使用 `std::env::args_os`，该方法产生的数组将包含 `OsString` 类型，而不是之前的 `String` 类型，前者对于非 `Unicode` 字符会有更好的处理。

`collect` 方法其实并不是 `std::env` 包提供的，而是迭代器自带的方法(`env::args()` 会返回一个迭代器)，它会将迭代器消费后转换成我们想要的集合类型

最后使用 `dbg!` 宏来输出读取到的数组内容：

```bash
➜  minigrep git:(main) ✗ cargo run -- needle haystack
    Finished dev [unoptimized + debuginfo] target(s) in 0.00s
     Running `target/debug/minigrep needle haystack`
[src/main.rs:5] args = [
    "target/debug/minigrep",
    "needle",
    "haystack",
]
```

### 存储读取到的参数

我们需要两个变量来存储文件路径和待搜索的字符串:

```rs
use std::env;

fn main() {
    let args: Vec<String> = env::args().collect();

    let query = &args[1];
    let file_path = &args[2];

    println!("Searching for {}", query);
    println!("In file {}", file_path);
}
```

测试结果如下：

```bash
➜  minigrep git:(main) ✗ cargo run -- test sample.txt
    Finished dev [unoptimized + debuginfo] target(s) in 0.01s
     Running `target/debug/minigrep test sample.txt`
Searching for test
In file_path: sample.txt
```

### 文件读取

要读取文件，首先我们需要创建一个文件并给予一些内容:

```txt
Rust, 一门赋予每个人构建可靠且高效软件能力的语言。

为什么选择 Rust?

高性能
Rust 速度惊人且内存利用率极高。由于没有运行时和垃圾回收，它能够胜任对性能要求特别高的服务，可以在嵌入式设备上运行，还能轻松和其他语言集成。

可靠性
Rust 丰富的类型系统和所有权模型保证了内存安全和线程安全，让您在编译期就能够消除各种各样的错误。

生产力
Rust 拥有出色的文档、友好的编译器和清晰的错误提示信息， 还集成了一流的工具——包管理器和构建工具， 智能地自动补全和类型检验的多编辑器支持， 以及自动格式化代码等等。
```

在项目根目录创建 `rust_introduce.txt` 文件, 并将上面的内容写入。

接下来修改 `main.rs` 来读取文件内容：

```rs
use std::{env, fs};

fn main() {
    let args: Vec<String> = env::args().collect();

    let query = &args[1];
    let file_path = &args[2];

    let contents = fs::read_to_string(file_path)
        .expect("Should have been able to read the file");

    println!("With text:\n{contents}");
}
```

首先，通过 `use std::fs` 引入文件操作包，然后通过 `fs::read_to_string` 读取指定的文件内容，最后返回的 `contents` 是 `std::io::Result<String>` 类型。

## 增加模块化和错误处理

## 测试驱动开发

## 使用环境变量

## 重定向错误信息的输出

## 使用迭代器来优化

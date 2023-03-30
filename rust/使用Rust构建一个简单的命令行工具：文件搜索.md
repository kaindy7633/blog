<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [使用Rust构建一个简单的命令行工具：文件搜索](#%E4%BD%BF%E7%94%A8rust%E6%9E%84%E5%BB%BA%E4%B8%80%E4%B8%AA%E7%AE%80%E5%8D%95%E7%9A%84%E5%91%BD%E4%BB%A4%E8%A1%8C%E5%B7%A5%E5%85%B7%E6%96%87%E4%BB%B6%E6%90%9C%E7%B4%A2)
  - [基本功能](#%E5%9F%BA%E6%9C%AC%E5%8A%9F%E8%83%BD)
    - [接收命令行参数](#%E6%8E%A5%E6%94%B6%E5%91%BD%E4%BB%A4%E8%A1%8C%E5%8F%82%E6%95%B0)
    - [存储读取到的参数](#%E5%AD%98%E5%82%A8%E8%AF%BB%E5%8F%96%E5%88%B0%E7%9A%84%E5%8F%82%E6%95%B0)
    - [文件读取](#%E6%96%87%E4%BB%B6%E8%AF%BB%E5%8F%96)
  - [增加模块化和错误处理](#%E5%A2%9E%E5%8A%A0%E6%A8%A1%E5%9D%97%E5%8C%96%E5%92%8C%E9%94%99%E8%AF%AF%E5%A4%84%E7%90%86)
    - [分离 main 函数](#%E5%88%86%E7%A6%BB-main-%E5%87%BD%E6%95%B0)
    - [错误处理](#%E9%94%99%E8%AF%AF%E5%A4%84%E7%90%86)
    - [分离主体逻辑](#%E5%88%86%E7%A6%BB%E4%B8%BB%E4%BD%93%E9%80%BB%E8%BE%91)
    - [分离逻辑代码到库包中](#%E5%88%86%E7%A6%BB%E9%80%BB%E8%BE%91%E4%BB%A3%E7%A0%81%E5%88%B0%E5%BA%93%E5%8C%85%E4%B8%AD)
  - [测试驱动开发](#%E6%B5%8B%E8%AF%95%E9%A9%B1%E5%8A%A8%E5%BC%80%E5%8F%91)
    - [注定失败的测试用例](#%E6%B3%A8%E5%AE%9A%E5%A4%B1%E8%B4%A5%E7%9A%84%E6%B5%8B%E8%AF%95%E7%94%A8%E4%BE%8B)
    - [务必成功的测试用例](#%E5%8A%A1%E5%BF%85%E6%88%90%E5%8A%9F%E7%9A%84%E6%B5%8B%E8%AF%95%E7%94%A8%E4%BE%8B)
  - [使用环境变量](#%E4%BD%BF%E7%94%A8%E7%8E%AF%E5%A2%83%E5%8F%98%E9%87%8F)
    - [编写大小写不敏感的测试用例](#%E7%BC%96%E5%86%99%E5%A4%A7%E5%B0%8F%E5%86%99%E4%B8%8D%E6%95%8F%E6%84%9F%E7%9A%84%E6%B5%8B%E8%AF%95%E7%94%A8%E4%BE%8B)
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

### 分离 main 函数

如果 `main` 函数过于庞大，我们需要做分离处理，`Rust` 社区给出了统一的指导方案: 将程序分割为 `main.rs` 和 `lib.rs`，并将程序的逻辑代码移动到后者内

因此， `main` 函数应该包含的功能:

- 解析命令行参数
- 初始化其它配置
- 调用 `lib.rs` 中的 `run` 函数，以启动逻辑代码的运行
- 如果 `run` 返回一个错误，需要对该错误进行处理

这种分离代码的方式叫：关注点分离(`Separation of Concerns`)。简而言之，`main.rs` 负责启动程序，`lib.rs` 负责逻辑代码的运行。

这里我们暂时将这两部分都放在 `main.rs` 中，只是分离出不同的函数来执行，后续会将这部分逻辑移植到 `lib.rs` 中

```rs
// in main.rs
fn main() {
    let args: Vec<String> = env::args().collect();

    let (query, file_path) = parse_config(&args);

    // --省略--
}

fn parse_config(args: &[String]) -> (&str, &str) {
    let query = &args[1];
    let file_path = &args[2];

    (query, file_path)
}
```

配置变量并不适合分散的到处都是，因此使用一个结构体来统一存放是非常好的选择

```rs
fn main() {
    let args: Vec<String> = env::args().collect();

    let config = parse_config(&args);

    println!("Searching for {}", config.query);
    println!("In file {}", config.file_path);

    let contents = fs::read_to_string(config.file_path)
        .expect("Should have been able to read the file");

    // --snip--
}

struct Config {
    query: String,
    file_path: String,
}

fn parse_config(args: &[String]) -> Config {
    let query = args[1].clone();
    let file_path = args[2].clone();

    Config { query, file_path }
}
```

上面的代码在初始化结构体时没有使用借用，而是直接使用 `clone` 方法创建新数据，这种方法很简单，但只是在性能上有一些微小的损失。

下面我们来优化下，通过构造函数来初始化一个 `Config` 实例，而不是直接通过函数返回实例，典型的，标准库中的 `String::new` 函数就是一个范例。

```rs
fn main() {
    let args: Vec<String> = env::args().collect();

    let config = Config::new(&args);

    // --snip--
}

// --snip--

impl Config {
    fn new(args: &[String]) -> Config {
        let query = args[1].clone();
        let file_path = args[2].clone();

        Config { query, file_path }
    }
}
```

### 错误处理

在上面实现的代码中，如果执行时不输入任何参数，会因为数组访问越界而发生 `panic`，进而退出程序。 `panic` 可以主动或被动触发，显然这是被动触发的，我们可以先试试主动触发：

```rs

// in main.rs
 // --snip--
    fn new(args: &[String]) -> Config {
        if args.len() < 3 {
            panic!("not enough arguments");
        }
        // --snip--
```

主动触发后还是会有大量的 `Debug` 信息抛出，那么我们可以进一步使用 `Result` 来替代 `panic`，下面的代码将之前的 `new` 修改为了 `build`

```rs
impl Config {
    fn build(args: &[String]) -> Result<Config, &'static str> {
        if args.len() < 3 {
            return Err("not enough arguments");
        }

        let query = args[1].clone();
        let file_path = args[2].clone();

        Ok(Config { query, file_path })
    }
}
```

这里的 `Result` 可能包含一个 `Config` 实例，也可能包含一条错误信息 `&static str`，代码中的字符串字面量都是该类型，且拥有 `'static` 生命周期。

下面是这个阶段的完整代码：

```rs
use std::env;
use std::fs;
use std::process;

fn main() {
    let args: Vec<String> = env::args().collect();

    // 对 build 返回的 `Result` 进行处理
    let config = Config::build(&args).unwrap_or_else(|err| {
        println!("Problem parsing arguments: {err}");
        process::exit(1);
    });


    println!("Searching for {}", config.query);
    println!("In file {}", config.file_path);

    let contents = fs::read_to_string(config.file_path)
        .expect("Should have been able to read the file");

    println!("With text:\n{contents}");
}

struct Config {
    query: String,
    file_path: String,
}

impl Config {
    fn build(args: &[String]) -> Result<Config, &'static str> {
        if args.len() < 3 {
            return Err("not enough arguments");
        }

        let query = args[1].clone();
        let file_path = args[2].clone();

        Ok(Config { query, file_path })
    }
}
```

`unwrap_or_else` 是定义在 `Result<T,E>` 上的常用方法，如果 `Result` 是 `Ok`，那该方法就类似 `unwrap`：返回 `Ok` 内部的值；如果是 `Err`，就调用闭包中的自定义代码对错误进行进一步处理

### 分离主体逻辑

接下来我们将 main 函数中的主体逻辑分离出去，创建 run 函数，来执行读取的任务

```rs
// in main.rs
fn main() {
    let args: Vec<String> = env::args().collect();

    let config = Config::build(&args).unwrap_or_else(|err| {
        println!("Problem parsing arguments: {err}");
        process::exit(1);
    });

    println!("Searching for {}", config.query);
    println!("In file {}", config.file_path);

    run(config);
}

fn run(config: Config) {
    let contents = fs::read_to_string(config.file_path)
        .expect("Should have been able to read the file");

    println!("With text:\n{contents}");
}

// --snip--
```

上面的 `run` 函数缺少错误处理，我们可以使用 `?` 和特征对象来返回错误。

```rs
//in main.rs
use std::error::Error;

// --snip--

fn run(config: Config) -> Result<(), Box<dyn Error>> {
    let contents = fs::read_to_string(config.file_path)?;

    println!("With text:\n{contents}");

    Ok(())
}
```

`run` 函数本身不需要返回任何值，所以需要 `ok(())` 来返回个单元类型 `()`。

`Box<dyn Error>` 返回一个 `Error` 的特征对象，它表示返回一个类型，该类型实现了 `Error` 特征。

接下来我们需要在执行 run 函数时指定返回的错误，使用 `if let`

```rs
    // --snip--

    println!("Searching for {}", config.query);
    println!("In file {}", config.file_path);

    if let Err(e) = run(config) {
        println!("Application error: {e}");
        process::exit(1);
    }
}
```

### 分离逻辑代码到库包中

首先，创建一个 `src/lib.rs` 文件，然后将所有的非 `main` 函数都移动到其中。

```rs
// lib.rs
use std::error::Error;
use std::fs;

pub struct Config {
    pub query: String,
    pub file_path: String,
}

impl Config {
    pub fn build(args: &[String]) -> Result<Config, &'static str> {
        // --snip--
    }
}

pub fn run(config: Config) -> Result<(), Box<dyn Error>> {
    // --snip--
}
```

## 测试驱动开发

在进入逻辑代码编程的环节之前，我们需要先编写一些测试代码，也就是测试驱动开发模式(TDD, Test Driven Development)：

- 编写一个注定失败的测试，并且失败的原因和你指定的一样
- 编写一个成功的测试
- 编写你的逻辑代码，直到通过测试

### 注定失败的测试用例

我们先在 `lib.rs` 文件中，添加 `tests` 模块和 `test` 函数:

```rs
#[cfg(test)]
mod tests {
    use super::*;

    #[test]
    fn one_result() {
        let query = "duct";
        let contents = "\
Rust:
safe, fast, productive.
Pick three.";

        assert_eq!(vec!["safe, fast, productive."], search(query, contents));
    }
}
```

### 务必成功的测试用例

第二步：编写注定成功的测试, 实现上面的 `search` 函数。它包含以下步骤：

- 遍历迭代 `contents` 的每一行
- 检查该行内容是否包含我们的目标字符串
- 若包含，则放入返回值列表中，否则忽略
- 返回匹配到的返回值列表

`Rust` 提供了一个很便利的 `lines` 方法将目标字符串进行按行分割:

```rs
// in lib.rs
pub fn search<'a>(query: &str, contents: &'a str) -> Vec<&'a str> {
    for line in contents.lines() {
        // do something with line
    }
}
```

在每一行中查询目标字符串

```rs
// in lib.rs
pub fn search<'a>(query: &str, contents: &'a str) -> Vec<&'a str> {
    for line in contents.lines() {
        if line.contains(query) {
            // do something with line
        }
    }
}
```

`Rust` 的字符串还提供了 `contains` 方法，用于检查 `line` 是否包含待查询的 `query`。

接下来存储匹配到的结果，创建一个 `Vec` 动态数组，然后将查询到的每一个 `line` 推进数组中即可：

```rs
// in lib.rs
pub fn search<'a>(query: &str, contents: &'a str) -> Vec<&'a str> {
    let mut results = Vec::new();

    for line in contents.lines() {
        if line.contains(query) {
            results.push(line);
        }
    }

    results
}
```

最后，我们在 `run` 函数中使用 `search` 函数来替代之前的 `println!`

```rs
// in src/lib.rs
pub fn run(config: Config) -> Result<(), Box<dyn Error>> {
    let contents = fs::read_to_string(config.file_path)?;

    for line in search(&config.query, &contents) {
        println!("{line}");
    }

    Ok(())
}
```

## 使用环境变量

我们可以使用环境变量来控制大小写敏感，例如:

```bash
IGNORE_CASE=1 cargo run -- to poem.txt
```

### 编写大小写不敏感的测试用例

我们来创建一个新的大小写不敏感函数进行测试 `search_case_insensitive`, 首先编写一个注定失败的用例:

```rs
// in src/lib.rs
#[cfg(test)]
mod tests {
    use super::*;

    #[test]
    fn case_sensitive() {
        let query = "duct";
        let contents = "\
Rust:
safe, fast, productive.
Pick three.
Duct tape.";

        assert_eq!(vec!["safe, fast, productive."], search(query, contents));
    }

    #[test]
    fn case_insensitive() {
        let query = "rUsT";
        let contents = "\
Rust:
safe, fast, productive.
Pick three.
Trust me.";

        assert_eq!(
            vec!["Rust:", "Trust me."],
            search_case_insensitive(query, contents)
        );
    }
}
```

接着来实现这个大小写不敏感的搜索函数:

```rs
pub fn search_case_insensitive<'a>(
    query: &str,
    contents: &'a str,
) -> Vec<&'a str> {
    let query = query.to_lowercase();
    let mut results = Vec::new();

    for line in contents.lines() {
        if line.to_lowercase().contains(&query) {
            results.push(line);
        }
    }

    results
}
```

上面的代码中引入了一个新的方法 `to_lowercase`，它会将 `line` 转换成全小写的字符串

接下来就是最后一步，在 `run` 中调用新的搜索函数。但是在此之前，要新增一个配置项，用于控制是否开启大小写敏感。

```rs
// in lib.rs
pub struct Config {
    pub query: String,
    pub file_path: String,
    pub ignore_case: bool,
}
```

检查该字段，来判断是否启动大小写敏感：

```rs
pub fn run(config: Config) -> Result<(), Box<dyn Error>> {
    let contents = fs::read_to_string(config.file_path)?;

    let results = if config.ignore_case {
        search_case_insensitive(&config.query, &contents)
    } else {
        search(&config.query, &contents)
    };

    for line in results {
        println!("{line}");
    }

    Ok(())
}
```

我们可以借助 Rust 提供的 env 包提供的方法来控制这个环境变量

```rs
use std::env;
// --snip--

impl Config {
    pub fn build(args: &[String]) -> Result<Config, &'static str> {
        if args.len() < 3 {
            return Err("not enough arguments");
        }

        let query = args[1].clone();
        let file_path = args[2].clone();

        let ignore_case = env::var("IGNORE_CASE").is_ok();

        Ok(Config {
            query,
            file_path,
            ignore_case,
        })
    }
}
```

上面的 `is_ok` 方法是 `Result` 提供的，用于检查是否有值，有就返回 `true`，没有则返回 `false`

## 重定向错误信息的输出

到目前为止，无论 `debug` 还是 `error` 类型信息，都是通过 `println!` 宏输出到终端的标准输出( `stdout` )，但是对于程序来说，错误信息更适合输出到标准错误输出(`stderr`)

将错误信息重定向到 `stderr` 很简单，只需在打印错误的地方，将 `println!` 宏替换为 `eprintln!`即可。

```rs
fn main() {
    let args: Vec<String> = env::args().collect();

    let config = Config::build(&args).unwrap_or_else(|err| {
        eprintln!("Problem parsing arguments: {err}");
        process::exit(1);
    });

    if let Err(e) = minigrep::run(config) {
        eprintln!("Application error: {e}");
        process::exit(1);
    }
}
```

## 使用迭代器来优化

在 `build` 方法中，我们使用了 `clone`，其实这里我们可以直接获取迭代器的所有权，而不是去借用一个数组

```rs
fn main() {
    let config = Config::build(env::args()).unwrap_or_else(|err| {
        eprintln!("Problem parsing arguments: {err}");
        process::exit(1);
    });

    // --snip--
}
```

`env::args` 可以直接返回一个迭代器，再作为 `Config::build` 的参数传入，下面再来改写 `build` 方法。

```rs
impl Config {
    pub fn build(
        mut args: impl Iterator<Item = String>,
    ) -> Result<Config, &'static str> {
        // --snip--
```

`args` 类型并没有使用本身的 `std::env::Args` ，而是使用了特征约束的方式来描述 `impl Iterator<Item = String>`，这样意味着 `arg` 可以是任何实现了 `String` 迭代器的类型。

数组索引会越界，为了安全性和简洁性，使用 `Iterator` 特征自带的 `next` 方法是一个更好的选择:

```rs
impl Config {
    pub fn build(
        mut args: impl Iterator<Item = String>,
    ) -> Result<Config, &'static str> {
        // 第一个参数是程序名，由于无需使用，因此这里直接空调用一次
        args.next();

        let query = match args.next() {
            Some(arg) => arg,
            None => return Err("Didn't get a query string"),
        };

        let file_path = match args.next() {
            Some(arg) => arg,
            None => return Err("Didn't get a file path"),
        };

        let ignore_case = env::var("IGNORE_CASE").is_ok();

        Ok(Config {
            query,
            file_path,
            ignore_case,
        })
    }
}
```

最后，使用迭代器来改造 `search` 函数

```rs
pub fn search<'a>(query: &str, contents: &'a str) -> Vec<&'a str> {
    contents
        .lines()
        .filter(|line| line.contains(query))
        .collect()
}
```

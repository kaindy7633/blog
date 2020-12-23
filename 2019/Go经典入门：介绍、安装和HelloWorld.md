# Go经典入门：介绍、安装和HelloWorld

## Golang 是什么

`Go` 亦称为 `Golang` (译注：按照 `Rob Pike` 说法，语言叫做 `Go`，`Golang` 只是官方网站的网址)，是由谷歌开发的一个开源的编译型的静态语言。

`Golang` 的主要关注点是使得高可用性和可扩展性的 `Web` 应用的开发变得简便容易。（译注：`Go` 的定位是系统编程语言，只是对 `Web` 开发支持较好）

## 为何选择 Golang

既然有很多其他编程语言可以做同样的工作，如 `Python`，`Ruby`，`Nodejs` 等，为什么要选择 `Golang` 作为服务端编程语言？

以下是我使用 `Go` 语言时发现的一些优点：

- 并发是语言的一部分（译注：并非通过标准库实现），所以编写多线程程序会是一件很容易的事。后续教程将会讨论到，并发是通过 `Goroutines` 和 `channels` 机制实现的。

- `Golang` 是一种编译型语言。源代码会编译为二进制机器码。而在解释型语言中没有这个过程，如 `Nodejs` 中的 `JavaScript`。

- 语言规范十分简洁。所有规范都在一个页面展示，你甚至都可以用它来编写你自己的编译器呢 :)

- `Go` 编译器支持静态链接。所有 `Go` 代码都可以静态链接为一个大的二进制文件（译注：相对现在的磁盘空间，其实根本不大），并可以轻松部署到云服务器，而不必担心各种依赖性。

## 安装

`Golang` 支持三个平台：`Mac`，`Windows` 和 `Linux`（译注：不只是这三个，也支持其他主流平台）。你可以在 <a href="https://golang.org/dl/" target="_blank">https://golang.org/dl/</a> 中下载相应平台的二进制文件。（译注：因为众所周知的原因，如果下载不了，请到 <a href="https://studygolang.com/dl" target="_blank">https://studygolang.com/dl</a> ）

### Mac OS

在 <a href="https://golang.org/dl/" target="_blank">https://golang.org/dl/</a> 下载安装程序。双击开始安装并且遵循安装提示，会将 `Golang` 安装到 `/usr/local/go` 目录下，同时 `/usr/local/go/bin` 文件夹也会被添加到 `PATH` 环境变量中。

### Windows

在 <a href="https://golang.org/dl/" target="_blank">https://golang.org/dl/</a> 下载 MSI 安装程序。双击开始安装并且遵循安装提示，会将 `Golang` 安装到 `C:\Go` 目录下，同时 `c:\Go\bin` 目录也会被添加到你的 `PATH` 环境变量中。

### Linux

在 <a href="https://golang.org/dl/" target="_blank">https://golang.org/dl/</a> 下载 `tar` 文件，并解压到 `/usr/local`。
请添加 `/usr/local/go/bin` 到 `PATH` 环境变量中。`Go` 就已经成功安装在 `Linux` 上了。

## 第一个 Go 程序

现在已经 `Go1.15.x` 了，自然使用 `Go` 模块，而不是之前的 `GOPATH`。

在你的系统任意目录下创建一个目录 `hello`

接着创建 `helloworld.go` 文件，在里面保存下面的程序。

```go
package main

import "fmt"

func main() {
    fmt.Println("Hello World")
}
```

### 运行 Go 程序

运行 Go 程序有多种方式，我们下面依次介绍。

- 使用 `go run` 命令 - 在命令提示符旁，输入 `go run helloworld.go`。在控制台上会看见 `Hello World` 的输出。

- 使用 `go install` 命令 - 运行 `go install hello`，接着可以用 `$GOPATH/bin/hello` 来运行该程序。

- 使用 `go playground`。尽管它有自身的限制，但该方法对于运行简单的程序非常方便

### 简述 hello world 程序

下面就是我们刚写下的 `hello world` 程序。

```go
package main //1

import "fmt" //2

func main() { //3
 fmt.Println("Hello World") //4
}
```

现在简单介绍每一行大概都做了些什么，在以后的教程中还会深入探讨每个部分。

- `package main` - 每一个 `Go` 文件都应该在开头进行 `package name` 的声明（译注：只有可执行程序的包名应当为 `main`）。包（`Packages`）用于代码的封装与重用，这里的包名称是 `main`。

- `import "fmt"` - 我们引入了 `fmt` 包，用于在 `main` 函数里面打印文本到标准输出。

- `func main()` - `main` 是一个特殊的函数。整个程序就是从 `main` 函数开始运行的。`main` 函数必须放置在 `main` 包中。`{` 和 `}` 分别表示 `main` 函数的开始和结束部分。

- `fmt.Println("Hello World")` - `fmt` 包中的 `Println` 函数用于把文本写入标准输出。
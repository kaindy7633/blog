# Golang经典入门

## 介绍、安装和 Hello World

### Golang 是什么

`Go` 亦称为 `Golang` (译注：按照 `Rob Pike` 说法，语言叫做 `Go`，`Golang` 只是官方网站的网址)，是由谷歌开发的一个开源的编译型的静态语言。

`Golang` 的主要关注点是使得高可用性和可扩展性的 `Web` 应用的开发变得简便容易。（译注：`Go` 的定位是系统编程语言，只是对 `Web` 开发支持较好）

### 为何选择 Golang

既然有很多其他编程语言可以做同样的工作，如 `Python`，`Ruby`，`Nodejs` 等，为什么要选择 `Golang` 作为服务端编程语言？

以下是我使用 `Go` 语言时发现的一些优点：

- 并发是语言的一部分（译注：并非通过标准库实现），所以编写多线程程序会是一件很容易的事。后续教程将会讨论到，并发是通过 `Goroutines` 和 `channels` 机制实现的。

- `Golang` 是一种编译型语言。源代码会编译为二进制机器码。而在解释型语言中没有这个过程，如 `Nodejs` 中的 `JavaScript`。

- 语言规范十分简洁。所有规范都在一个页面展示，你甚至都可以用它来编写你自己的编译器呢 :)

- `Go` 编译器支持静态链接。所有 `Go` 代码都可以静态链接为一个大的二进制文件（译注：相对现在的磁盘空间，其实根本不大），并可以轻松部署到云服务器，而不必担心各种依赖性。

### 安装

`Golang` 支持三个平台：`Mac`，`Windows` 和 `Linux`（译注：不只是这三个，也支持其他主流平台）。你可以在 <a href="https://golang.org/dl/" target="_blank">https://golang.org/dl/</a> 中下载相应平台的二进制文件。（译注：因为众所周知的原因，如果下载不了，请到 <a href="https://studygolang.com/dl" target="_blank">https://studygolang.com/dl</a> ）

#### Mac OS

在 <a href="https://golang.org/dl/" target="_blank">https://golang.org/dl/</a> 下载安装程序。双击开始安装并且遵循安装提示，会将 `Golang` 安装到 `/usr/local/go` 目录下，同时 `/usr/local/go/bin` 文件夹也会被添加到 `PATH` 环境变量中。

#### Windows

在 <a href="https://golang.org/dl/" target="_blank">https://golang.org/dl/</a> 下载 MSI 安装程序。双击开始安装并且遵循安装提示，会将 `Golang` 安装到 `C:\Go` 目录下，同时 `c:\Go\bin` 目录也会被添加到你的 `PATH` 环境变量中。

#### Linux

在 <a href="https://golang.org/dl/" target="_blank">https://golang.org/dl/</a> 下载 `tar` 文件，并解压到 `/usr/local`。
请添加 `/usr/local/go/bin` 到 `PATH` 环境变量中。`Go` 就已经成功安装在 `Linux` 上了。

### 第一个 Go 程序

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

#### 运行 Go 程序

运行 Go 程序有多种方式，我们下面依次介绍。

- 使用 `go run` 命令 - 在命令提示符旁，输入 `go run helloworld.go`。在控制台上会看见 `Hello World` 的输出。

- 使用 `go install` 命令 - 运行 `go install hello`，接着可以用 `$GOPATH/bin/hello` 来运行该程序。

- 使用 `go playground`。尽管它有自身的限制，但该方法对于运行简单的程序非常方便

#### 简述 hello world 程序

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

## 变量

### 变量是什么

变量指定了某存储单元（`Memory Location`）的名称，该存储单元会存储特定类型的值。在 `Go` 中，有多种语法用于声明变量。

### 声明单个变量

`var name type` 是声明单个变量的语法。

```go
package main

import "fmt"

func main() {
    var age int // 变量声明
    fmt.Println("my age is", age)
}
```

语句 `var age int` 声明了一个 `int` 类型的变量，名字为 `age`。我们还没有给该变量赋值。如果变量未被赋值，`Go` 会自动地将其初始化，赋值该变量类型的零值（`Zero Value`）。本例中 `age` 就被赋值为 0。如果你运行该程序，你会看到如下输出：

```go
my age is 0
```

变量可以赋值为本类型的任何值。上一程序中的 `age` 可以赋值为任何整型值（`Integer Value`）。

```go
package main

import "fmt"

func main() {
    var age int // 变量声明
    fmt.Println("my age is", age)
    age = 29 // 赋值
    fmt.Println("my age is", age)
    age = 54 // 赋值
    fmt.Println("my new age is", age)
}
```

上面的程序会有如下输出：

```go
// my age is  0
// my age is 29
// my new age is 54
```

### 声明变量并初始化

声明变量的同时可以给定初始值。

`var name type = initialvalue` 的语法用于声明变量并初始化。

```go
package main

import "fmt"

func main() {
    var age int = 29 // 声明变量并初始化

    fmt.Println("my age is", age)
}
```

在上面的程序中，`age` 是具有初始值 29 的 `int` 类型变量。如果你运行上面的程序，你可以看见下面的输出，证实 `age` 已经被初始化为 29。

```go
my age is 29
```

### 类型推断（Type Inference）

如果变量有初始值，那么 `Go` 能够自动推断具有初始值的变量的类型。因此，如果变量有初始值，就可以在变量声明中省略 `type`。

如果变量声明的语法是 `var name = initialvalue`，`Go` 能够根据初始值自动推断变量的类型。

在下面的例子中，你可以看到在第 6 行，我们省略了变量 `age` 的 `int` 类型，`Go` 依然推断出了它是 `int` 类型。

```go
package main

import "fmt"

func main() {
    var age = 29 // 可以推断类型

    fmt.Println("my age is", age)
}
```

### 声明多个变量

`Go` 能够通过一条语句声明多个变量。

声明多个变量的语法是 `var name1, name2 type = initialvalue1, initialvalue2`。

```go
package main

import "fmt"

func main() {
    var width, height int = 100, 50 // 声明多个变量

    fmt.Println("width is", width, "height is", heigh)
}
```

上述程序将在标准输出打印 `width is 100 height is 50`。

你可能已经想到，如果 `width` 和 `height` 省略了初始化，它们的初始值将赋值为 0。

```go
package main

import "fmt"

func main() {
    var width, height int
    fmt.Println("width is", width, "height is", height)
    width = 100
    height = 50
    fmt.Println("new width is", width, "new height is ", height)
}
```

上面的程序将会打印：

```go
// width is 0 height is 0
// new width is 100 new height is  50
```

在有些情况下，我们可能会想要在一个语句中声明不同类型的变量。其语法如下：

```go
var (
    name1 = initialvalue1,
    name2 = initialvalue2
)
```

使用上述语法，下面的程序声明不同类型的变量。

```go
package main

import "fmt"

func main() {
    var (
        name   = "naveen"
        age    = 29
        height int
    )
    fmt.Println("my name is", name, ", age is", age, "and height is", height)
}
```

这里我们声明了 `string` 类型的 `name`、`int` 类型的 `age` 和 `height`（我们将会在下一教程中讨论 `golang` 所支持的变量类型）。运行上面的程序会产生输出 `my name is naveen , age is 29 and height is 0`。

### 简短声明

`Go` 也支持一种声明变量的简洁形式，称为简短声明（`Short Hand Declaration`），该声明使用了 `:=` 操作符。

声明变量的简短语法是 `name := initialvalue`。

```go
package main

import "fmt"

func main() {
    name, age := "naveen", 29 // 简短声明

    fmt.Println("my name is", name, "age is", age)
}
```

运行上面的程序，可以看到输出为 `my name is naveen age is 29`。

简短声明要求 `:=` 操作符左边的所有变量都有初始值。下面程序将会抛出错误 `cannot assign 1 values to 2 variables`，这是因为 `age` 没有被赋值。

```go
package main

import "fmt"

func main() {
    name, age := "naveen" //error

    fmt.Println("my name is", name, "age is", age)
}
```

简短声明的语法要求 `:=` 操作符的左边至少有一个变量是尚未声明的。考虑下面的程序：

```go
package main

import "fmt"

func main() {
    a, b := 20, 30 // 声明变量a和b
    fmt.Println("a is", a, "b is", b)
    b, c := 40, 50 // b已经声明，但c尚未声明
    fmt.Println("b is", b, "c is", c)
    b, c = 80, 90 // 给已经声明的变量b和c赋新值
    fmt.Println("changed b is", b, "c is", c)
}
```

在上面程序中的第 8 行，由于 `b` 已经被声明，而 `c` 尚未声明，因此运行成功并且输出：

```go
// a is 20 b is 30
// b is 40 c is 50
// changed b is 80 c is 90
```

但是如果我们运行下面的程序:

```go
package main

import "fmt"

func main() {
    a, b := 20, 30 // 声明a和b
    fmt.Println("a is", a, "b is", b)
    a, b := 40, 50 // 错误，没有尚未声明的变量
}
```

上面运行后会抛出 `no new variables on left side of :=` 的错误，这是因为 `a` 和 `b` 的变量已经声明过了，`:=` 的左边并没有尚未声明的变量。

变量也可以在运行时进行赋值。考虑下面的程序：

```go
package main

import (
    "fmt"
    "math"
)

func main() {
    a, b := 145.8, 543.8
    c := math.Min(a, b)
    fmt.Println("minimum value is ", c)
}
```

在上面的程序中，`c` 的值是运行过程中计算得到的，即 `a` 和 `b` 的最小值。上述程序会打印：

```go
// minimum value is  145.8
```

由于 `Go` 是强类型（`Strongly Typed`）语言，因此不允许某一类型的变量赋值为其他类型的值。下面的程序会抛出错误 `cannot use "naveen" (type string) as type int in assignment`，这是因为 `age` 本来声明为 `int` 类型，而我们却尝试给它赋字符串类型的值。

```go
package main

func main() {
    age := 29      // age是int类型
    age = "naveen" // 错误，尝试赋值一个字符串给int类型变量
}
```

## 常量

### 定义

在 `Go` 语言中，术语"常量"用于表示固定的值。比如 `5` 、`-89`、 `I love Go`、`67.89` 等等。

看看下面的代码:

```go
var a int = 50
var b string = "I love Go"
```

在上面的代码中，变量 `a` 和 `b` 分别被赋值为常量 `50` 和 `I love GO`。关键字 `const` 被用于表示常量，比如 `50` 和 `I love Go`。即使在上面的代码中我们没有明确的使用关键字 `const`，但是在 `Go` 的内部，它们是常量。

顾名思义，常量不能再重新赋值为其他的值。因此下面的程序将不能正常工作，它将出现一个编译错误: `cannot assign to a.`。

```go
package main

func main() {
    const a = 55 // 允许
    a = 89       // 不允许重新赋值
}
```

常量的值会在编译的时候确定。因为函数调用发生在运行时，所以不能将函数的返回值赋值给常量。

```go
package main

import (
    "fmt"
    "math"
)

func main() {
    fmt.Println("Hello, playground")
    var a = math.Sqrt(4)   // 允许
    const b = math.Sqrt(4) // 不允许
}
```

在上面的程序中，因为 `a` 是变量，因此我们可以将函数 `math.Sqrt(4)` 的返回值赋值给它（我们将在单独的地方详细讨论函数）。

`b` 是一个常量，它的值需要在编译的时候就确定。函数 `math.Sqrt(4)` 只会在运行的时候计算，因此 `const b = math.Sqrt(4)` 将会抛出错误 `error main.go:11: const initializer math.Sqrt(4) is not a constant)`

### 字符串常量

双引号中的任何值都是 `Go` 中的字符串常量。例如像 `Hello World` 或 `Sam` 等字符串在 `Go` 中都是常量。

什么类型的字符串属于常量？答案是他们是无类型的。

像 `Hello World` 这样的字符串常量没有任何类型。

```go
const hello = "Hello World"
```

上面的例子，我们把 `Hello World` 分配给常量 `hello`。现在常量 `hello` 有类型吗？答案是没有。常量仍然没有类型。

`Go` 是一门强类型语言，所有的变量必须有明确的类型。那么, 下面的程序是如何将无类型的常量 `Sam` 赋值给变量 `name` 的呢？

```go
package main

import (
    "fmt"
)

func main() {
    var name = "Sam"
    fmt.Printf("type %T value %v", name, name)

}
```

答案是无类型的常量有一个与它们相关联的默认类型，并且当且仅当一行代码需要时才提供它。在声明中 `var name = "Sam"` ， `name` 需要一个类型，它从字符串常量 `Sam` 的默认类型中获取。

有没有办法创建一个带类型的常量？答案是可以的。以下代码创建一个有类型常量。

```go
const typedhello string = "Hello World"
```

上面代码中， `typedhello` 就是一个 `string` 类型的常量。

`Go` 是一个强类型的语言，在分配过程中混合类型是不允许的。让我们通过以下程序看看这句话是什么意思。

```go
package main

func main() {
    var defaultName = "Sam" // 允许
    type myString string
    var customName myString = "Sam" // 允许
    customName = defaultName // 不允许
}
```

在上面的代码中，我们首先创建一个变量 `defaultName` 并分配一个常量 `Sam` 。常量 `Sam` 的默认类型是 `string` ，所以在赋值后 `defaultName` 是 `string` 类型的。

下一行，我们将创建一个新类型 `myString`，它是 `string` 的别名。

然后我们创建一个 `myString` 的变量 `customName` 并且给他赋值一个常量 `Sam` 。因为常量 `Sam` 是无类型的，它可以分配给任何字符串变量。因此这个赋值是允许的，`customName` 的类型是 `myString`。

现在，我们有一个类型为 `string` 的变量 `defaultName` 和另一个类型为 `myString` 的变量 `customName`。即使我们知道这个 `myString` 是 `string` 类型的别名。`Go` 的类型策略不允许将一种类型的变量赋值给另一种类型的变量。因此将 `defaultName` 赋值给 `customName` 是不允许的，编译器会抛出一个错误 `main.go:7:20: cannot use defaultName (type string) as type myString in assignmen`。

### 布尔常量

布尔常量和字符串常量没有什么不同。他们是两个无类型的常量 `true` 和 `false`。字符串常量的规则适用于布尔常量，所以在这里我们不再重复。以下是解释布尔常量的简单程序。

```go
package main

func main() {
    const trueConst = true
    type myBool bool
    var defaultBool = trueConst // 允许
    var customBool myBool = trueConst // 允许
    defaultBool = customBool // 不允许
}
```

### 数字常量

数字常量包含整数、浮点数和复数的常量。数字常量中有一些微妙之处。

让我们看一些例子来说清楚。

```go
package main

import (
    "fmt"
)

func main() {
    const a = 5
    var intVar int = a
    var int32Var int32 = a
    var float64Var float64 = a
    var complex64Var complex64 = a
    fmt.Println("intVar",intVar, "\nint32Var", int32Var, "\nfloat64Var", float64Var, "\ncomplex64Var",complex64Var)
}
```

上面的程序，常量 `a` 是没有类型的，它的值是 5 。您可能想知道 `a` 的默认类型是什么，如果它确实有一个的话, 那么我们如何将它分配给不同类型的变量。答案在于 `a` 的语法。下面的程序将使事情更加清晰。

```go
package main

import (
    "fmt"
)

func main() {
    var i = 5
    var f = 5.6
    var c = 5 + 6i
    fmt.Printf("i's type %T, f's type %T, c's type %T", i, f, c)

}
```

在上面的程序中，每个变量的类型由数字常量的语法决定。`5` 在语法中是整数， `5.6` 是浮点数，`5+6i` 的语法是复数。当我们运行上面的程序，它会打印出 `i's type int, f's type float64, c's type complex128`。

现在我希望下面的程序能够正确的工作。

```go
package main

import (
    "fmt"
)

func main() {
    const a = 5
    var intVar int = a
    var int32Var int32 = a
    var float64Var float64 = a
    var complex64Var complex64 = a
    fmt.Println("intVar",intVar, "\nint32Var", int32Var, "\nfloat64Var", float64Var, "\ncomplex64Var",complex64Var)
}
```

在这个程序中， `a` 的值是 `5` ，`a` 的语法是通用的（它可以代表一个浮点数、整数甚至是一个没有虚部的复数），因此可以将其分配给任何兼容的类型。这些常量的默认类型可以被认为是根据上下文在运行中生成的。`var intVar int = a` 要求 `a` 是 `int`，所以它变成一个 `int` 常量。`var complex64Var complex64 = a` 要求 `a` 是 `complex64`，因此它变成一个复数类型。很简单的:)。

### 数字表达式

数字常量可以在表达式中自由混合和匹配，只有当它们被分配给变量或者在需要类型的代码中的任何地方使用时，才需要类型。

```go
package main

import (
    "fmt"
)

func main() {
    var a = 5.9/8
    fmt.Printf("a's type %T value %v",a, a)
}
```

在上面的程序中， `5.9` 在语法中是浮点型，`8` 是整型，`5.9/8` 是允许的，因为两个都是数字常量。除法的结果是 `0.7375` 是一个浮点型，所以 `a` 的类型是浮点型。这个程序的输出结果是: `a's type float64 value 0.7375`。

## 类型

下面是 `Go` 支持的基本类型：

- `bool`
- 数字类型
  - `int8`, `int16`, `int32`, `int64`, `int`
  - `uint8`, `uint16`, `uint32`, `uint64`, `uint`
  - `float32`, `float64`
  - `complex64`, `complex128`
  - `byte`
  - `rune`
- string

### bool

`bool` 类型表示一个布尔值，值为 `true` 或者 `false`。

```go
package main

import "fmt"

func main() {
    a := true
    b := false
    fmt.Println("a:", a, "b:", b)
    c := a && b
    fmt.Println("c:", c)
    d := a || b
    fmt.Println("d:", d)
}
```

在上面的程序中，`a` 赋值为 `true`，`b` 赋值为 `false`。

`c` 赋值为 `a && b`。仅当 `a` 和 `b` 都为 `true` 时，操作符 `&&` 才返回 `true`。因此，在这里 `c` 为 `false`。

当 `a` 或者 `b` 为 `true` 时，操作符 `||` 返回 `true`。在这里，由于 `a` 为 `true`，因此 `d` 也为 `true`。我们将得到程序的输出如下。

```go
a: true b: false
c: false
d: true
```

### 有符号整型

- `int8`：表示 8 位有符号整型大小：8 位范围：-128 ～ 127

- `int16`：表示 16 位有符号整型大小：16 位范围：-32768 ～ 32767

- `int32`：表示 32 位有符号整型大小：32 位范围：-2147483648 ～ 2147483647

- `int64`：表示 64 位有符号整型大小：64 位范围：-9223372036854775808 ～ 9223372036854775807

- `int`：根据不同的底层平台（`Underlying Platform`），表示 32 或 64 位整型。除非对整型的大小有特定的需求，否则你通常应该使用 `int` 表示整型。大小：在 32 位系统下是 32 位，而在 64 位系统下是 64 位。范围：在 32 位系统下是 -2147483648 ～ 2147483647，而在 64 位系统是 -9223372036854775808 ～ 9223372036854775807。

```go
package main

import "fmt"

func main() {
    var a int = 89
    b := 95
    fmt.Println("value of a is", a, "and b is", b)
}
```

上面程序会输出 `value of a is 89 and b is 95`。

在上述程序中，`a` 是 `int` 类型，而 `b` 的类型通过赋值（95）推断得出。上面我们提到，`int` 类型的大小在 32 位系统下是 32 位，而在 64 位系统下是 64 位。接下来我们会证实这种说法。

在 `Printf` 方法中，使用 `%T` 格式说明符（`Format Specifier`），可以打印出变量的类型。`Go` 的 `unsafe` 包提供了一个 `Sizeof` 函数，该函数接收变量并返回它的字节大小。`unsafe` 包应该小心使用，因为使用 `unsafe` 包可能会带来可移植性问题。不过出于本教程的目的，我们是可以使用的。

下面程序会输出变量 `a` 和 `b` 的类型和大小。格式说明符 `%T` 用于打印类型，而 `%d` 用于打印字节大小。

```go
package main

import (
    "fmt"
    "unsafe"
)

func main() {
    var a int = 89
    b := 95
    fmt.Println("value of a is", a, "and b is", b)
    fmt.Printf("type of a is %T, size of a is %d", a, unsafe.Sizeof(a)) // a 的类型和大小
    fmt.Printf("\ntype of b is %T, size of b is %d", b, unsafe.Sizeof(b)) // b 的类型和大小
}
```

以上程序会输出：

```go
// value of a is 89 and b is 95
// type of a is int, size of a is 4
// type of b is int, size of b is 4
```

从上面的输出，我们可以推断出 `a` 和 `b` 为 `int` 类型，且大小都是 32 位（4 字节）。如果你在 64 位系统上运行上面的代码，会有不同的输出。在 64 位系统下，`a` 和 `b` 会占用 64 位（8 字节）的大小。

### 无符号整型

- `uint8`：表示 8 位无符号整型大小：8 位范围：0 ～ 255

- `uint16`：表示 16 位无符号整型大小：16 位范围：0 ～ 65535

- `uint32`：表示 32 位无符号整型大小：32 位范围：0 ～ 4294967295

- `uint64`：表示 64 位无符号整型大小：64 位范围：0 ～ 18446744073709551615

- `uint`：根据不同的底层平台，表示 32 或 64 位无符号整型。大小：在 32 位系统下是 32 位，而在 64 位系统下是 64 位。范围：在 32 位系统下是 0 ～ 4294967295，而在 64 位系统是 0 ～ 18446744073709551615。

### 浮点型

- `float32`：32 位浮点数

- `float64`：64 位浮点数

下面一个简单程序演示了整型和浮点型的运用。

```go
package main

import (
    "fmt"
)

func main() {
    a, b := 5.67, 8.97
    fmt.Printf("type of a %T b %T\n", a, b)
    sum := a + b
    diff := a - b
    fmt.Println("sum", sum, "diff", diff)

    no1, no2 := 56, 89
    fmt.Println("sum", no1+no2, "diff", no1-no2)
}
```

`a` 和 `b` 的类型根据赋值推断得出。在这里，`a` 和 `b` 的类型为 `float64`（`float64` 是浮点数的默认类型）。我们把 `a` 和 `b` 的和赋值给变量 `sum`，把 `b` 和 `a` 的差赋值给 `diff`，接下来打印 `sum` 和 `diff`。`no1` 和 `no2` 也进行了相同的计算。上述程序将会输出：

```go
// type of a float64 b float64
// sum 14.64 diff -3.3000000000000007
// sum 145 diff -33
```

### 复数类型

- `complex64`：实部和虚部都是 `float32` 类型的的复数。

- `complex128`：实部和虚部都是 `float64` 类型的的复数。

内建函数 `complex` 用于创建一个包含实部和虚部的复数。`complex` 函数的定义如下：

```go
func complex(r, i FloatType) ComplexType
```

该函数的参数分别是实部和虚部，并返回一个复数类型。实部和虚部应该是相同类型，也就是 `float32` 或 `float64`。如果实部和虚部都是 `float32` 类型，则函数会返回一个 `complex64` 类型的复数。如果实部和虚部都是 `float64` 类型，则函数会返回一个 `complex128` 类型的复数。

还可以使用简短语法来创建复数：

```go
c := 6 + 7i
```

下面我们编写一个简单的程序来理解复数。

```go
package main

import (
    "fmt"
)

func main() {
    c1 := complex(5, 7)
    c2 := 8 + 27i
    cadd := c1 + c2
    fmt.Println("sum:", cadd)
    cmul := c1 * c2
    fmt.Println("product:", cmul)
}
```

在上面的程序里，`c1` 和 `c2` 是两个复数。`c1` 的实部为 5，虚部为 7。`c2` 的实部为 8，虚部为 27。`c1` 和 `c2` 的和赋值给 `cadd` ，而 `c1` 和 `c2` 的乘积赋值给 `cmul`。该程序将输出：

```go
// sum: (13+34i)
// product: (-149+191i)
```

### 其他数字类型

`byte` 是 `uint8` 的别名。`rune` 是 `int32` 的别名。

在学习字符串的时候，我们会详细讨论 `byte` 和 `rune`。

### string 类型

在 `Golang` 中，字符串是字节的集合。如果你现在还不理解这个定义，也没有关系。我们可以暂且认为一个字符串就是由很多字符组成的。我们后面会在一个教程中深入学习字符串。

下面编写一个使用字符串的程序。

```go
package main

import (
    "fmt"
)

func main() {
    first := "Naveen"
    last := "Ramanathan"
    name := first +" "+ last
    fmt.Println("My name is",name)
}
```

上面程序中，`first` 赋值为字符串 `"Naveen"`，`last` 赋值为字符串 `"Ramanathan"`。`+` 操作符可以用于拼接字符串。我们拼接了 `first`、空格和 `last`，并将其赋值给 `name`。上述程序将打印输出 `My name is Naveen Ramanathan`。

还有许多应用于字符串上面的操作，我们将会在一个单独的教程里看见它们。

### 类型转换

`Go` 有着非常严格的强类型特征。`Go` 没有自动类型提升或类型转换。我们通过一个例子说明这意味着什么。

```go
package main

import (
    "fmt"
)

func main() {
    i := 55      //int
    j := 67.8    //float64
    sum := i + j //不允许 int + float64
    fmt.Println(sum)
}
```

上面的代码在 `C` 语言中是完全合法的，然而在 `Go` 中，却是行不通的。`i` 的类型是 `int` ，而 `j` 的类型是 `float64` ，我们正试图把两个不同类型的数相加，`Go` 不允许这样的操作。如果运行程序，你会得到 `main.go:10: invalid operation: i + j (mismatched types int and float64)`

要修复这个错误，`i` 和 `j` 应该是相同的类型。在这里，我们把 `j` 转换为 `int` 类型。把 `v` 转换为 `T` 类型的语法是 `T(v)`。

```go
package main

import (
    "fmt"
)

func main() {
    i := 55      //int
    j := 67.8    //float64
    sum := i + int(j) //j is converted to int
    fmt.Println(sum)
}
```

现在，当你运行上面的程序时，会看见输出 122。

赋值的情况也是如此。把一个变量赋值给另一个不同类型的变量，需要显式的类型转换。下面程序说明了这一点。

```go
package main

import (
    "fmt"
)

func main() {
    i := 10
    var j float64 = float64(i) // 若没有显式转换，该语句会报错
    fmt.Println("j", j)
}
```

在第 9 行，`i` 转换为 `float64` 类型，接下来赋值给 `j`。如果不进行类型转换，当你试图把 `i` 赋值给 `j` 时，编译器会抛出错误。

## 函数

### 函数是什么？

函数是一块执行特定任务的代码。一个函数是在输入源基础上，通过执行一系列的算法，生成预期的输出。

### 函数的声明

在 `Go` 语言中，函数声明通用语法如下：

```go
func functionname(parametername type) returntype {
    // 函数体（具体实现的功能）
}
```

函数的声明以关键词 `func` 开始，后面紧跟自定义的函数名 `functionname` (函数名)。函数的参数列表定义在 `(` 和 `)` 之间，返回值的类型则定义在之后的 `returntype` (返回值类型)处。声明一个参数的语法采用 参数名 参数类型 的方式，任意多个参数采用类似 (`parameter1 type, parameter2 type`) 即(`参数1 参数1的类型, 参数2 参数2的类型`)的形式指定。之后包含在 `{` 和 `}` 之间的代码，就是函数体。

函数中的参数列表和返回值并非是必须的，所以下面这个函数的声明也是有效的

```go
func functionname() {
 // 译注: 表示这个函数不需要输入参数，且没有返回值
}
```

### 示例函数

我们以写一个计算商品价格的函数为例，输入参数是单件商品的价格和商品的个数，两者的乘积为商品总价，作为函数的输出值。

```go
func calculateBill(price int, no int) int {
    var totalPrice = price * no // 商品总价 = 商品单价 * 数量
    return totalPrice // 返回总价
}
```

上述函数有两个整型的输入 `price` 和 `no`，返回值 `totalPrice` 为 `price` 和 `no` 的乘积，也是整数类型。

如果有连续若干个参数，它们的类型一致，那么我们无须一一罗列，只需在最后一个参数后添加该类型。 例如，`price int, no int` 可以简写为 `price, no int`，所以示例函数也可写成

```go
func calculateBill(price, no int) int {
    var totalPrice = price * no
    return totalPrice
}
```

现在我们已经定义了一个函数，我们要在代码中尝试着调用它。调用函数的语法为 `functionname(parameters)`。调用示例函数的方法如下：

```go
calculateBill(10, 5)
```

完成了示例函数声明和调用后，我们就能写出一个完整的程序，并把商品总价打印在控制台上：

```go
package main

import (
    "fmt"
)

func calculateBill(price, no int) int {
    var totalPrice = price * no
    return totalPrice
}
func main() {
    price, no := 90, 6 // 定义 price 和 no,默认类型为 int
    totalPrice := calculateBill(price, no)
    fmt.Println("Total price is", totalPrice) // 打印到控制台上
}
```

该程序在控制台上打印的结果为

```go
// Total price is 540
```

### 多返回值

`Go` 语言支持一个函数可以有多个返回值。我们来写个以矩形的长和宽为输入参数，计算并返回矩形面积和周长的函数 `rectProps`。矩形的面积是长度和宽度的乘积, 周长是长度和宽度之和的两倍。即：

面积 = 长 _宽
周长 = 2_ ( 长 + 宽 )

```go
package main

import (
    "fmt"
)

func rectProps(length, width float64)(float64, float64) {
    var area = length * width
    var perimeter = (length + width) * 2
    return area, perimeter
}

func main() {
    area, perimeter := rectProps(10.8, 5.6)
    fmt.Printf("Area %f Perimeter %f", area, perimeter)
}
```

如果一个函数有多个返回值，那么这些返回值必须用 ( 和 ) 括起来。`func rectProps(length, width float64)(float64, float64)` 示例函数有两个 `float64` 类型的输入参数 `length` 和 `width`，并返回两个 `float64` 类型的值。该程序在控制台上打印结果为

```go
// Area 60.480000 Perimeter 32.800000
```

### 命名返回值

从函数中可以返回一个命名值。一旦命名了返回值，可以认为这些值在函数第一行就被声明为变量了。

上面的 `rectProps` 函数也可用这个方式写成：

```go
func rectProps(length, width float64)(area, perimeter float64) {
    area = length * width
    perimeter = (length + width) * 2
    return // 不需要明确指定返回值，默认返回 area, perimeter 的值
}
```

请注意, 函数中的 `return` 语句没有显式返回任何值。由于 `area` 和 `perimeter` 在函数声明中指定为返回值, 因此当遇到 `return` 语句时, 它们将自动从函数返回。

### 空白符

`_` 在 `Go` 中被用作空白符，可以用作表示任何类型的任何值。

我们继续以 `rectProps` 函数为例，该函数计算的是面积和周长。假使我们只需要计算面积，而并不关心周长的计算结果，该怎么调用这个函数呢？这时，空白符 `_` 就上场了。

下面的程序我们只用到了函数 `rectProps` 的一个返回值 `area`

```go
package main

import (
    "fmt"
)

func rectProps(length, width float64) (float64, float64) {
    var area = length * width
    var perimeter = (length + width) * 2
    return area, perimeter
}

func main() {
    area, _ := rectProps(10.8, 5.6) // 返回值周长被丢弃
    fmt.Printf("Area %f ", area)
}
```

在程序的 `area, _ := rectProps(10.8, 5.6)` 这一行，我们看到空白符 `_` 用来跳过不要的计算结果。

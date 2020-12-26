# Go语言中的编码规范

每个语言都有自己特色的编码规范，学习该语言的命名规范，能让你写出来的代码更加易读，更加不容易出现一些低级错误。

## 文件命名

- 由于 `Windows` 平台文件名不区分大小写，所以文件名应一律使用小写

- 不同单词之间用下划线分词，不要使用驼峰式命名

- 如果是测试文件，可以以 `_test.go` 结尾

- 文件若具有平台特性，应以 `文件名_平台.go` 命名，比如 `utils_windows.go`，`utils_linux.go`，可用的平台有：`windows`, `unix`, `posix`, `plan9`, `darwin`, `bsd`, `linux`, `freebsd`, `nacl`, `netbsd`, `openbsd`, `solaris`, `dragonfly`, `bsd`, `notbsd`， `android`，`stubs`

- 一般情况下应用的主入口应为 `main.go`，或者以应用的全小写形式命名。比如 `MyBlog` 的入口可以为 `myblog.go`

## 常量命名

目前在网络上可以看到主要有两种风格的写法

- 第一种是驼峰命名法，比如 `appVersion`

- 第二种使用全大写且用下划线分词，比如 `APP_VERSION`

这两种风格，没有孰好孰弱，可自由选取，我个人更倾向于使用第二种，主要是能一眼与变量区分开来。

如果要定义多个变量，请使用括号来组织。

```go
const (
  APP_VERSION = "0.1.0"
  CONF_PATH = "/etc/xx.conf"
)
```

## 变量命名

和常量不同，变量的命名，开发者们的喜好就比较一致了，统一使用驼峰命名法

- 在相对简单的环境（对象数量少、针对性强）中，可以将完整单词简写为单个字母，例如：`user`写为 `u`

- 若该变量为 `bool` 类型，则名称应以 `Has`, `Is`, `Can` 或 `Allow` 开头。例如：`isExist` ，`hasConflict` 。

- 其他一般情况下首单词全小写，其后各单词首字母大写。例如：`numShips` 和 `startDate` 。

- 若变量中有特有名词（以下列出），且变量为私有，则首单词还是使用全小写，如 `apiClient`。

- 若变量中有特有名词（以下列出），但变量不是私有，那首单词就要变成全大写。例如：`APIClient`，`URLString`

这里列举了一些常见的特有名词：

```go
// A GonicMapper that contains a list of common initialisms taken from golang/lint
var LintGonicMapper = GonicMapper{
    "API":   true,
    "ASCII": true,
    "CPU":   true,
    "CSS":   true,
    "DNS":   true,
    "EOF":   true,
    "GUID":  true,
    "HTML":  true,
    "HTTP":  true,
    "HTTPS": true,
    "ID":    true,
    "IP":    true,
    "JSON":  true,
    "LHS":   true,
    "QPS":   true,
    "RAM":   true,
    "RHS":   true,
    "RPC":   true,
    "SLA":   true,
    "SMTP":  true,
    "SSH":   true,
    "TLS":   true,
    "TTL":   true,
    "UI":    true,
    "UID":   true,
    "UUID":  true,
    "URI":   true,
    "URL":   true,
    "UTF8":  true,
    "VM":    true,
    "XML":   true,
    "XSRF":  true,
    "XSS":   true,
}
```

## 函数命名

- 函数名还是使用驼峰命名法

- 但是有一点需要注意，在 `Golang` 中是用大小写来控制函数的可见性，因此当你需要在包外访问，请使用大写字母开头

- 当你不需要在包外访问，请使用小写字母开头

另外，函数内部的参数的排列顺序也有几点原则

- 参数的重要程度越高，应排在越前面

- 简单的类型应优先复杂类型

- 尽可能将同种类型的参数放在相邻位置，则只需写一次类型

## 接口命名

使用驼峰命名法，可以用 `type alias` 来定义大写开头的 `type`  给包外访问。

```go
type helloWorld interface {
    func Hello();
}

type SayHello helloWorld
```

当你的接口只有一个函数时，接口名通常会以 `er` 为后缀

```go
type Reader interface {
    Read(p []byte) (n int, err error)
}
```

## 注释规范

注释分为

### 包注释

位于 `package` 之前，如果一个包有多个文件，只需要在一个文件中编写即可

如果你想在每个文件中的头部加上注释，需要在版权注释和 `Package` 前面加一个空行，否则版权注释会作为 `Package` 的注释。

```go
// Copyright 2009 The Go Authors. All rights reserved.
// Use of this source code is governed by a BSD-style
// license that can be found in the LICENSE file.
package net
```

如果是特别复杂的包，可单独创建 `doc.go` 文件说明

### 代码注释

用于解释代码逻辑，可以有两种写法

单行注释使用 `//` ，多行注释使用 `/* comment */`

```go
// 单行注释

/*
多
行
注
释
*/
```

另外，对于代码注释还有一些更加苛刻的要求，这个看个人了，摘自网络：

- 所有导出对象都需要注释说明其用途；非导出对象根据情况进行注释。

- 如果对象可数且无明确指定数量的情况下，一律使用单数形式和一般进行时描述；否则使用复数形式。

- 包、函数、方法和类型的注释说明都是一个完整的句子。

- 句子类型的注释首字母均需大写；短语类型的注释首字母需小写。

- 注释的单行长度不能超过 80 个字符。

- 类型的定义一般都以单数形式描述：

```go
// Request represents a request to run a command.  type Request struct { ...
```

- 如果为接口，则一般以以下形式描述：

```go
// FileInfo is the interface that describes a file and is returned by Stat and Lstat.
type FileInfo interface { ...
```

- 函数与方法的注释需以函数或方法的名称作为开头：

```go
// Post returns *BeegoHttpRequest with POST method.
```

- 如果一句话不足以说明全部问题，则可换行继续进行更加细致的描述：

```go
// Copy copies file from source to target path.
// It returns false and error when error occurs in underlying function calls.
```

- 若函数或方法为判断类型（返回值主要为 `bool` 类型），则以 `<name> returns true if` 开头：

```go
// HasPrefix returns true if name has any string in given slice as prefix.
func HasPrefix(name string, prefixes []string) bool { ...
```

### 特别注释

- `TODO` ：提醒维护人员此部分代码待完成

- `FIXME` ：提醒维护人员此处有BUG待修复

- `NOTE` ：维护人员要关注的一些问题说明

## 包的导入

单行的包导入

```go
import "fmt"
```

多个包导入，请使用 `()` 来组织

```go
import (
  "fmt"
  "os"
)
```

另外根据包的来源，对排版还有一定的要求

- 标准库排最前面，第三方包次之、项目内的其它包和当前包的子包排最后，每种分类以一空行分隔。

- 尽量不要使用相对路径来导入包。

```go
import (
    "fmt"
    "html/template"
    "net/http"
    "os"

    "github.com/codegangsta/cli"
    "gopkg.in/macaron.v1"

    "github.com/gogits/git"
    "github.com/gogits/gfm"

    "github.com/gogits/gogs/routers"
    "github.com/gogits/gogs/routers/repo"
    "github.com/gogits/gogs/routers/user"
)
```

## 善用 gofmt

除了命名规范外，Go 还有很多格式上的规范，比如

- 使用 tab 进行缩进

- 一行最长不要超过 80 个字符

因此在格式上的问题，你大部分都可以放心交由 `gofmt` 帮你调整。
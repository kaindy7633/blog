<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [GoLang极速入门](#golang%E6%9E%81%E9%80%9F%E5%85%A5%E9%97%A8)
  - [变量定义](#%E5%8F%98%E9%87%8F%E5%AE%9A%E4%B9%89)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## GoLang极速入门

### 变量定义

`go`语言中使用 `var` 关键字来定义变量

```go
func variable() {
  var a int
  var s string
}
```

`go` 语言中，变量名写在前面，变量类型写在后面，这与其他高级语言不一样

上面的示例定义中，没有赋初值，这种情况下，`int` 类型的初始值是 `0`， `string` 类型是空字符串

```go
func veriableZerovalue() {
  var a int
  var s string
  fmt.Printf("%d %q\n", a, s)  // 0 ""
}
```

当然变量定义也可以赋初始值，也可以同时给多个同类型的变量赋值

```go
func variableInitialValue() {
  var a int = 3
  var s string = "Hello"

  var b, c int = 4, 5
  var s1, s2 string = "s1", "s2"
}
```

在确定值的情况下，类型定义可以被省略，`go` 会自动判断变量类型

```go
var a = 3
var b, c = 4, 5

var s = "World"
var s1, s2 = "s1", "s2"
```

`var` 关键字是可以省略的，使用 `:=` 来定义， 在函数定义中，尽可能省略，但在包中定义（也就是在函数之外定义），则不能省略 `var`

```go
func variableShorter() {
  a, b, c := 3, "string", true
}
```
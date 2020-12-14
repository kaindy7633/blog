# GoLang极速入门
## 变量定义

如果你是`Python`、`PHP` 或 `Ruby` 等动态语言开发者，也许会不太理解声明这个过程，在动态语言中，基本是直接拿来就用，也不用声明类型啥的。但 `Go` 语言是和 `C` 一样的静态类型语言，编译时会检查变量的类型，所以变量必须有具体的类型。

变量在使用前，需要先声明。声明会有类型或推导出类型，这就约定了该变量只能赋该类型的值。（接口是另外一种形式）

声明或定义一般有以下六种方法，其中前面两种也可用于常量，只要替换关键字 `var -> const` 即可。

### 第一种 ：一行一个变量，静态语言最基本常用的方式

```go
var <name> <type>
```

其中 `var` 是关键字（固定不变），`name` 是变量名，`type` 是类型。`Node/JS` 开发者，对于 `type` 外，其他应该挺熟悉的。

使用 `var` ，虽然只指定了类型，但是 `Go` 会所有类型都有默认值，比如 `string` 类型会初始化为空字符串，`int` 类型会初始化为 `0`，`float` 会初始化为 `0.0`，`bool` 会初始化为 `false`，引用和指针类型就初始化为 `nil` 等。

若要在声明时，顺便也初始化，可以这样写

```go
var name sting = "Go编程时光发布在Go语言中文网"
```

以上例子的完整代码如下（为了不写重复性的代码，后续不再贴完整代码，只贴关键代码）

```go
package main

import "fmt"

func main()  {
    var name string = "Go编程时光发布在Go语言中文网"
    fmt.Println(name)
}
```

从右值（等号右边的值，`rvalue`）来看，明显是个 `string` 类型。因此也可以将其简化为

```go
var name = "Go编程时光发布在Go语言中文网"
```

这叫做**类型推导**。

若你的右值带有小数点，在不指定类型的情况下，编译器会将你的这个变量声明为 `float64`。如果你不需要这么高的精度可以指定类型：

```go
var rate float32 0.89
```

### 第二种：多个变量一起声明，声明组

声明多个变量，除了可以按照上面写成多行之外，还可以写成下面这样

```go
var (
    name string
    age int
    gender string
)
```

### 第三种：短声明，只能在函数内

使用 `:=` （推导声明写法或短类型声明法：编译器会自动根据右值类型推断出左值的对应类型。），可以声明一个变量，并对其进行（显式）初始化。

```go
name := "Go编程时光发布在Go语言中文网"

// 等价于
var name string = "Go编程时光发布在Go语言中文网"

// 等价于
var name = "Go编程时光发布在Go语言中文网"
```

但这种方法有个限制就是，只能用于函数内部

### 第四种：一行声明和初始化多个变量

```go
name, age := "Go编程时光发布在Go语言中文网", 28
```

这种方法，也经常用于变量的交换。之前常见的面试题，如何不用中间变量交换两个整数变量，在 `Go` 中直接搞定。

```go
var a int = 100
var b int = 200
b, a = a, b
```

### 第五种：通过 new 创建指针变量

先简单介绍下指针的相关内容。

一般变量分为两种 普通变量 和 指针变量

普通变量，存放的是数据本身，而指针变量存放的是数据的地址。

如下代码，`age` 是一个普通变量，存放的内容是 `28`，而 `ptr` 是 存放变量 `age` 值的内存地址：`0xc000010098`

```go
package main

import "fmt"

func main()  {
    var age int = 28
    var ptr = &age  // &后面接变量名，表示取出该变量的内存地址
    fmt.Println("age: ", age)
    fmt.Println("ptr: ", ptr)
}

// age:  28
// ptr:  0xc000010098
```

而这里要说的 `new` 函数，是 `Go` 里的一个内建函数。

使用表达式 `new(Type)` 将创建一个 `Type` 类型的匿名变量，初始化为 `Type` 类型的零值，然后返回变量地址，返回的指针类型为 `*Type`。

```go
package main

import "fmt"

func main()  {
    ptr := new(int)
    fmt.Println("ptr address: ", ptr)
    fmt.Println("ptr value: ", *ptr)  // * 后面接指针变量，表示从内存地址中取出值
}

// ptr address:  0xc000010098
// ptr value:  0
```

用 `new` 创建变量和普通变量声明语句方式创建变量没有什么区别，除了不需要声明一个临时变量的名字外，我们还可以在表达式中使用 `new(Type)` 。换言之，`new` 函数类似是一种语法糖，而不是一个新的基础概念。

如下两种写法，可以说是等价的

```go
// 使用 new
func newInt() *int {
    return new(int)
}

// 使用传统的方式
func newInt() *int {
    var dummy int
    return &dummy
}
```

### 第六种：make 函数创建 slice、map 或 chan 类型变量

```go
var slice = make([]int, 8)
var m = make(map[string]int)
var c = make(chan int)
```

`slice`、`map` 和 `chan` 是 `Go` 中的引用类型，它们的创建和初始化，一般使用 `make`。特别的，`chan` 只能用 `make`。`slice` 和 `map` 还可以简单的方式：

```go
slice := []int{0, 0}
m := map[string]int{}
```


以上不管哪种方法，变量/常量都只能声明一次，声明多次，编译就会报错。

但也有例外，这就要说到一个特殊变量：匿名变量，也称作占位符，或者空白标识符，用下划线表示。

匿名变量，优点有三：

- 不分配内存，不占用内存空间

- 不需要你为命名无用的变量名而纠结

- 多次声明不会有任何问题

通常我们用匿名接收 必须接收，但是又不会用到的值，可以理解为垃圾桶。

```go
func GetData() (int, int) {
    return 100, 200
}
func main(){
    a, _ := GetData()
    _, b := GetData()
    fmt.Println(a, b)
}
```
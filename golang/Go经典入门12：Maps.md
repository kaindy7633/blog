# Go 经典入门 13：Maps

## 什么是 map ？

`map` 是在 `Go` 中将值（`value`）与键（`key`）关联的内置类型。通过相应的键可以获取到值。

## 如何创建 map ？

通过向 `make` 函数传入键和值的类型，可以创建 `map`。`make(map[type of key]type of value)` 是创建 `map` 的语法。

```go
personSalary := make(map[string]int)
```

上面的代码创建了一个名为 `personSalary` 的 `map`，其中键是 `string` 类型，而值是 `int` 类型。

`map` 的零值是 `nil`。如果你想添加元素到 `nil map` 中，会触发运行时 `panic`。因此 `map` 必须使用 `make` 函数初始化。

```go
package main

import (
    "fmt"
)

func main() {
    var personSalary map[string]int
    if personSalary == nil {
        fmt.Println("map is nil. Going to make one.")
        personSalary = make(map[string]int)
    }
}
```

上面的程序中，`personSalary` 是 `nil`，因此需要使用 `make` 方法初始化，程序将输出 `map is nil. Going to make one.`。

## 给 map 添加元素

给 `map` 添加新元素的语法和数组相同。下面的程序给 `personSalary map` 添加了几个新元素。

```go
package main

import (
    "fmt"
)

func main() {
    personSalary := make(map[string]int)
    personSalary["steve"] = 12000
    personSalary["jamie"] = 15000
    personSalary["mike"] = 9000
    fmt.Println("personSalary map contents:", personSalary)
}
```

上面的程序输出：`personSalary map contents: map[steve:12000 jamie:15000 mike:9000]`

你也可以在声明的时候初始化 `map`。

```go
package main

import (
    "fmt"
)

func main() {
    personSalary := map[string]int {
        "steve": 12000,
        "jamie": 15000,
    }

    personSalary["mike"] = 9000
    fmt.Println("personSalary map contents:", personSalary)
}
```

上面的程序声明了 `personSalary`，并在声明的同时添加两个元素。之后又添加了键 `mike`。程序输出：

```go
// personSalary map contents: map[steve:12000 jamie:15000 mike:9000]
```

键不一定只能是 `string` 类型。所有可比较的类型，如 `boolean`，`interger`，`float`，`complex`，`string` 等，都可以作为键。关于可比较的类型，如果你想了解更多，请访问 http://golang.org/ref/spec#Comparison_operators[4]。

## 获取 map 中的元素

目前我们已经给 `map` 添加了几个元素，现在学习下如何获取它们。获取 `map` 元素的语法是 `map[key]` 。

```go
package main

import (
    "fmt"
)

func main() {
    personSalary := map[string]int{
        "steve": 12000,
        "jamie": 15000,
    }

    personSalary["mike"] = 9000
    employee := "jamie"
    fmt.Println("Salary of", employee, "is", personSalary[employee])
}
```

上面的程序很简单。获取并打印员工 `jamie` 的薪资。程序输出 `Salary of jamie is 15000`。

如果获取一个不存在的元素，会发生什么呢？`map` 会返回该元素类型的零值。在 `personSalary` 这个 `map` 里，如果我们获取一个不存在的元素，会返回 `int` 类型的零值 0。

```go
package main

import (
    "fmt"
)

func main() {
    personSalary := map[string]int{
        "steve": 12000,
        "jamie": 15000,
    }

    personSalary["mike"] = 9000
    employee := "jamie"

    fmt.Println("Salary of", employee, "is", personSalary[employee])
    fmt.Println("Salary of joe is", personSalary["joe"])
}
```

上面程序输出：

```go
// Salary of jamie is 15000
// Salary of joe is 0
```

上面程序返回 `joe` 的薪资是 0。`personSalary` 中不包含 `joe` 的情况下我们不会获取到任何运行时错误。

如果我们想知道 `map` 中到底是不是存在这个 `key`，该怎么做：

```go
value, ok := map[key]
```

上面就是获取 `map` 中某个 `key` 是否存在的语法。如果 `ok` 是 `true`，表示 `key` 存在，`key` 对应的值就是 `value` ，反之表示 `key` 不存在。

```go
package main

import (
    "fmt"
)

func main() {
    personSalary := map[string]int{
        "steve": 12000,
        "jamie": 15000,
    }

    personSalary["mike"] = 9000
    newEmp := "joe"
    value, ok := personSalary[newEmp]
    if ok == true {
        fmt.Println("Salary of", newEmp, "is", value)
    } else {
        fmt.Println(newEmp,"not found")
    }
}
```

上面的程序中，第 15 行，`joe` 不存在，所以 `ok` 是 `false`。程序将输出：

```go
// joe not found
```

遍历 `map` 中所有的元素需要用 `for range` 循环。

```go
package main

import (
    "fmt"
)

func main() {
    personSalary := map[string]int{
        "steve": 12000,
        "jamie": 15000,
    }

    personSalary["mike"] = 9000
    fmt.Println("All items of a map")
    for key, value := range personSalary {
        fmt.Printf("personSalary[%s] = %d\n", key, value)
    }
}
```

上面程序输出：

```go
// All items of a map
// personSalary[mike] = 9000
// personSalary[steve] = 12000
// personSalary[jamie] = 15000
```

有一点很重要，当使用 `for range` 遍历 `map` 时，不保证每次执行程序获取的元素顺序相同。

## 删除 map 中的元素

删除 `map` 中 `key` 的语法是 `_delete(map, key)`。这个函数没有返回值。

```go
package main

import (
    "fmt"
)

func main() {
    personSalary := map[string]int{
        "steve": 12000,
        "jamie": 15000,
    }

    personSalary["mike"] = 9000
    fmt.Println("map before deletion", personSalary)
    delete(personSalary, "steve")
    fmt.Println("map after deletion", personSalary)

}
```

上述程序删除了键 "steve"，输出：

```go
// map before deletion map[steve:12000 jamie:15000 mike:9000]
// map after deletion map[mike:9000 jamie:15000]
```

## 获取 map 的长度

获取 `map` 的长度使用 `len` 函数。

```go
package main

import (
    "fmt"
)

func main() {
    personSalary := map[string]int{
        "steve": 12000,
        "jamie": 15000,
    }

    personSalary["mike"] = 9000
    fmt.Println("length is", len(personSalary))
}
```

上述程序中的 `len(personSalary)` 函数获取了 `map` 的长度。程序输出 `length is 3`。

## Map 是引用类型

和 `slices` 类似，`map` 也是引用类型。当 `map` 被赋值为一个新变量的时候，它们指向同一个内部数据结构。因此，改变其中一个变量，就会影响到另一变量。

```go
package main

import (
    "fmt"
)

func main() {
    personSalary := map[string]int{
        "steve": 12000,
        "jamie": 15000,
    }

    personSalary["mike"] = 9000
    fmt.Println("Original person salary", personSalary)
    newPersonSalary := personSalary
    newPersonSalary["mike"] = 18000
    fmt.Println("Person salary changed", personSalary)
}
```

上面程序中的第 14 行，`personSalary` 被赋值给 `newPersonSalary`。下一行 ，`newPersonSalary` 中 `mike` 的薪资变成了 `18000` 。`personSalary` 中 `Mike` 的薪资也会变成 18000。程序输出：

```go
// Original person salary map[steve:12000 jamie:15000 mike:9000]
// Person salary changed map[steve:12000 jamie:15000 mike:18000]
```

当 `map` 作为函数参数传递时也会发生同样的情况。函数中对 `map` 的任何修改，对于外部的调用都是可见的。

## Map 的相等性

`map` 之间不能使用 `==` 操作符判断，`==` 只能用来检查 `map` 是否为 `nil`。

```go
package main

func main() {
    map1 := map[string]int{
        "one": 1,
        "two": 2,
    }

    map2 := map1

    if map1 == map2 {
    }
}
```

上面程序抛出编译错误 `invalid operation: map1 == map2 (map can only be compared to nil)`。

判断两个 `map` 是否相等的方法是遍历比较两个 `map` 中的每个元素

---

下一节：[Go 经典入门 13：字符串](https://github.com/kaindy7633/blog/blob/main/golang/Go%E7%BB%8F%E5%85%B8%E5%85%A5%E9%97%A813%EF%BC%9A%E5%AD%97%E7%AC%A6%E4%B8%B2.md)

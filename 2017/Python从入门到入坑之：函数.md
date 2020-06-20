<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [前言](#%E5%89%8D%E8%A8%80)
- [调用函数](#%E8%B0%83%E7%94%A8%E5%87%BD%E6%95%B0)
  - [内置函数](#%E5%86%85%E7%BD%AE%E5%87%BD%E6%95%B0)
  - [数据类型转换](#%E6%95%B0%E6%8D%AE%E7%B1%BB%E5%9E%8B%E8%BD%AC%E6%8D%A2)
- [定义函数](#%E5%AE%9A%E4%B9%89%E5%87%BD%E6%95%B0)
  - [定义](#%E5%AE%9A%E4%B9%89)
  - [空函数](#%E7%A9%BA%E5%87%BD%E6%95%B0)
  - [参数检查](#%E5%8F%82%E6%95%B0%E6%A3%80%E6%9F%A5)
  - [返回多个值](#%E8%BF%94%E5%9B%9E%E5%A4%9A%E4%B8%AA%E5%80%BC)
- [函数的参数](#%E5%87%BD%E6%95%B0%E7%9A%84%E5%8F%82%E6%95%B0)
  - [位置参数](#%E4%BD%8D%E7%BD%AE%E5%8F%82%E6%95%B0)
  - [默认参数](#%E9%BB%98%E8%AE%A4%E5%8F%82%E6%95%B0)
  - [可变参数](#%E5%8F%AF%E5%8F%98%E5%8F%82%E6%95%B0)
  - [关键字参数](#%E5%85%B3%E9%94%AE%E5%AD%97%E5%8F%82%E6%95%B0)
  - [命名关键字参数](#%E5%91%BD%E5%90%8D%E5%85%B3%E9%94%AE%E5%AD%97%E5%8F%82%E6%95%B0)
  - [参数组合](#%E5%8F%82%E6%95%B0%E7%BB%84%E5%90%88)
- [递归函数](#%E9%80%92%E5%BD%92%E5%87%BD%E6%95%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# 前言

<p style="height:20px"></p>

当我们写代码的时候，发现有规律的重复的逻辑，我们自然就会想到把这部分功能封装成一个函数，基本上所有的高级语言都支持函数，Python也不例外。Python不但能非常灵活地定义函数，而且本身内置了很多有用的函数，可以直接调用。

抽象是数学中非常常见的概念。举个例子：

计算数列的和，比如：`1 + 2 + 3 + ... + 100`，写起来十分不方便，于是数学家发明了求和符号`∑`，可以把 `1 + 2 + 3 + ... + 100` 记作：

100  
∑n  
n=1

这种抽象记法非常强大，因为我们看到 `∑` 就可以理解成求和，而不是还原成低级的加法运算。

而且，这种抽象记法是可扩展的，比如：

100  
∑(n2+1)  
n=1

还原成加法运算就变成了：

(1 x 1 + 1) + (2 x 2 + 1) + (3 x 3 + 1) + ... + (100 x 100 + 1)

可见，借助抽象，我们才能不关心底层的具体计算过程，而直接在更高的层次上思考问题。

写计算机程序也是一样，函数就是最基本的一种代码抽象的方式。

# 调用函数

## 内置函数

Python内置了很多有用的函数，我们可以直接调用。

要调用一个函数，需要知道函数的名称和参数，比如求绝对值的函数 `abs` ，只有一个参数。可以直接从Python的官方网站查看文档：http://docs.python.org/3/library/functions.html#abs

也可以在交互式命令行通过 `help(abs)` 查看 `abs` 函数的帮助信息。

```python
abs(100)
100
abs(-20)
20
abs(12.34)
12.34
```

调用函数的时候，如果传入的参数数量不对，会报TypeError的错误，并且Python会明确地告诉你：`abs()` 有且仅有1个参数，但给出了两个：

```python
abs(1, 2)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: abs() takes exactly one argument (2 given)
```

如果传入的参数数量是对的，但参数类型不能被函数所接受，也会报TypeError的错误，并且给出错误信息：str是错误的参数类型：

```python
abs('a')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: bad operand type for abs(): 'str'
```

函数 `max()` 则可以接收任意多个参数，并返回最大的那个：

```python
max(1, 2)
2
max(2, 3, 1, -5)
3
```

## 数据类型转换

Python内置的常用函数还包括数据类型转换函数，比如 `int()` 函数可以把其他数据类型转换为整数：

```python
int('123')
123
int(12.34)
12
float('12.34')
12.34
str(1.23)
'1.23'
str(100)
'100'
bool(1)
True
bool('')
False
bool(None)
False
```

函数名其实就是指向一个函数对象的引用，完全可以把函数名赋给一个变量，相当于给这个函数起了一个“别名”：

```python
a = abs # 变量a指向abs函数
a(-1) # 所以也可以通过a调用abs函数
1
```

# 定义函数

## 定义

在Python中，定义一个函数要使用 `def` 语句，依次写出函数名、括号、括号中的参数和冒号 `:`，然后，在缩进块中编写函数体，函数的返回值用 `return` 语句返回。

我们以自定义一个求绝对值的 `my_abs` 函数为例：

```python
def my_abs(x):
    if x > 0:
        return x
    else:
        return -x
```

请注意，函数体内部的语句在执行时，一旦执行到 `return` 时，函数就执行完毕，并将结果返回。因此，函数内部通过条件判断和循环可以实现非常复杂的逻辑。

如果没有 `return` 语句，函数执行完毕后也会返回结果，只是结果为 `None`。`return None` 可以简写为`return`。

## 空函数

如果想定义一个什么事也不做的空函数，可以用 `pass` 语句：

```python
def nop():
    pass
```

`pass` 语句什么都不做，那有什么用？实际上 `pass` 可以用来作为占位符，比如现在还没想好怎么写函数的代码，就可以先放一个 `pass`，让代码能运行起来。

`pass` 还可以用在其他语句里，比如：

```python
if age >= 18:
    pass # 如果缺少pass，运行就会报错
```

## 参数检查

调用函数时，如果参数个数不对，Python解释器会自动检查出来，并抛出TypeError：

```python
my_abs(1, 2)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: my_abs() takes 1 positional argument but 2 were given
```

但是如果参数类型不对，Python解释器就无法帮我们检查，我们可以观察一下刚才我们定义的 `my_abs` 和Python内置的 `abs` 函数之间的差别：

```python
my_abs('A')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "<stdin>", line 2, in my_abs
TypeError: unorderable types: str() >= int()

abs('A')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: bad operand type for abs(): 'str'
```

当传入了不恰当的参数时，内置函数 `abs` 会检查出参数错误，而我们定义的 `my_abs` 没有参数检查，会导致 `if`语句出错，出错信息和 `abs` 不一样。所以，这个函数定义不够完善。

让我们修改一下 `my_abs` 的定义，对参数类型做检查，只允许整数和浮点数类型的参数。数据类型检查可以用内置函数`isinstance()` 实现：

```python
def my_abs(x):
    if not isinstance(x, (int, float)):
        raise TypeError('bad operand type')
    if x >= 0:
        return x
    else:
        return -x
```

添加了参数检查后，如果传入错误的参数类型，函数就可以抛出一个错误：

```python
my_abs('A')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "<stdin>", line 3, in my_abs
TypeError: bad operand type
```

## 返回多个值

函数可以返回多个值吗？答案是肯定的。

比如在游戏中经常需要从一个点移动到另一个点，给出坐标、位移和角度，就可以计算出新的新的坐标：

```python
import math

def move(x, y, step, angle=0):
    nx = x + step * math.cos(angle)
    ny = y - step * math.sin(angle)
    return nx, ny
```

`import math` 语句表示导入 `math` 包，并允许后续代码引用 `math` 包里的``sin` 、`cos` 等函数。

然后，我们就可以同时获得返回值：

```python
x, y = move(100, 100, 60, math.pi / 6)
print(x, y)
151.96152422706632 70.0
```

但其实这只是一种假象，Python函数返回的仍然是单一值：

```python
r = move(100, 100, 60, math.pi / 6)
print(r)
(151.96152422706632, 70.0)
```

原来返回值是一个 `tuple` ！但是，在语法上，返回一个 `tuple` 可以省略括号，而多个变量可以同时接收一个`tuple`，按位置赋给对应的值，所以，Python的函数返回多值其实就是返回一个 `tuple`，但写起来更方便。

# 函数的参数

定义函数的时候，我们把参数的名字和位置确定下来，函数的接口定义就完成了。对于函数的调用者来说，只需要知道如何传递正确的参数，以及函数将返回什么样的值就够了，函数内部的复杂逻辑被封装起来，调用者无需了解。

Python的函数定义非常简单，但灵活度却非常大。除了正常定义的必选参数外，还可以使用默认参数、可变参数和关键字参数，使得函数定义出来的接口，不但能处理复杂的参数，还可以简化调用者的代码。

## 位置参数

我们先写一个计算x<sup>2</sup>的函数：

```python
def power(x):
    return x * x
```

当我们调用power函数时，必须传入有且仅有的一个参数x：

```python
power(5)
25
power(15)
225
```

现在，如果我们要计算x<sup>3</sup>怎么办？可以再定义一个power<sup>3</sup>函数，但是如果要计算x<sup>4</sup>、x<sup>5</sup>……怎么办？我们不可能定义无限多个函数。

我们可以把 `power(x)` 修改为 `power(x, n)` ，用来计算x<sup>n</sup>

```python
def power(x, n):
    s = 1
    while n > 0:
        n = n - 1
        s = s * x
    return s
```

对于这个修改后的 `power(x, n)` 函数，可以计算任意n次方：

```python
power(5, 2)
25
power(5, 3)
125
```

修改后的 `power(x, n)` 函数有两个参数：`x` 和 `n`，这两个参数都是位置参数，调用函数时，传入的两个值按照位置顺序依次赋给参数 `x` 和 `n`。

## 默认参数

默认参数就是在定义函数时，给参数设定一个初始值：

```python
def power(x, n=2):
    s = 1
    while n > 0:
        n = n - 1
        s = s * x
    return s
```

这样，当我们调用 `power(5)` 时，相当于调用 `power(5, 2)`：

```python
power(5)
25
power(5, 2)
25
```

默认参数可以简化函数的调用。设置默认参数时，有几点要注意：

1. 是必选参数在前，默认参数在后，否则Python的解释器会报错（思考一下为什么默认参数不能放在必选参数前面）；

2. 如何设置默认参数。

当函数有多个参数时，把变化大的参数放前面，变化小的参数放后面。变化小的参数就可以作为默认参数。

使用默认参数有什么好处？最大的好处是能降低调用函数的难度。

举个例子，我们写个一年级小学生注册的函数，需要传入 `name` 和 `gender` 两个参数：

```python
def enroll(name, gender):
    print('name:', name)
    print('gender:', gender)
```

这样，调用 `enroll()` 函数只需要传入两个参数：

```python
enroll('Sarah', 'F')
name: Sarah
gender: F
```

如果要继续传入年龄、城市等信息怎么办？这样会使得调用函数的复杂度大大增加。

我们可以把年龄和城市设为默认参数：

```python
def enroll(name, gender, age=6, city='Beijing'):
    print('name:', name)
    print('gender:', gender)
    print('age:', age)
    print('city:', city)
```

这样，大多数学生注册时不需要提供年龄和城市，只提供必须的两个参数：

```python
enroll('Sarah', 'F')
name: Sarah
gender: F
age: 6
city: Beijing
```

只有与默认参数不符的学生才需要提供额外的信息：

```python
enroll('Bob', 'M', 7)
enroll('Adam', 'M', city='Tianjin')
```

默认参数降低了函数调用的难度，而一旦需要更复杂的调用时，又可以传递更多的参数来实现。无论是简单调用还是复杂调用，函数只需要定义一个

有多个默认参数时，调用的时候，既可以按顺序提供默认参数，比如调用 `enroll('Bob', 'M', 7)`，意思是，除了`name`，`gender` 这两个参数外，最后1个参数应用在参数 `age` 上，`city` 参数由于没有提供，仍然使用默认值。

也可以不按顺序提供部分默认参数。当不按顺序提供部分默认参数时，需要把参数名写上。比如调用 `enroll('Adam', 'M', city='Tianjin')`，意思是，`city` 参数用传进去的值，其他默认参数继续使用默认值。

默认参数很有用，但使用不当，也会掉坑里。默认参数有个最大的坑

先定义一个函数，传入一个 `list`，添加一个 `END` 再返回：

```python
def add_end(L=[]):
    L.append('END')
    return L
```

当你正常调用时，结果似乎不错：

```python
add_end([1, 2, 3])
[1, 2, 3, 'END']
add_end(['x', 'y', 'z'])
['x', 'y', 'z', 'END']
```

当你使用默认参数调用时，一开始结果也是对的：

```python
add_end()
['END']
```

但是，再次调用 `add_end()` 时，结果就不对了：

```python
add_end()
['END', 'END']
add_end()
['END', 'END', 'END']
```

出现这种情况的原因是：Python函数在定义的时候，默认参数L的值就被计算出来了，即 `[]`，因为默认参数L也是一个变量，它指向对象 `[]`，每次调用该函数，如果改变了L的内容，则下次调用时，默认参数的内容就变了，不再是函数定义时的 `[]` 了。

<p style="background:#fff1f0;color:#d85030;border-color:gba(216,80,48,0.3);border-radius:4px;text-shadow:0 1px 0 #fff;padding: 10px;">定义默认参数要牢记一点：默认参数必须指向不变对象！</p>

要修改上面的例子，我们可以用None这个不变对象来实现：

```python
def add_end(L=None):
    if L is None:
        L = []
    L.append('END')
    return L
```

现在，无论调用多少次，都不会有问题：

```python
add_end()
['END']
add_end()
['END']
```

为什么要设计 `str`、`None` 这样的不变对象呢？因为不变对象一旦创建，对象内部的数据就不能修改，这样就减少了由于修改数据导致的错误。此外，由于对象不变，多任务环境下同时读取对象不需要加锁，同时读一点问题都没有。我们在编写程序时，如果可以设计一个不变对象，那就尽量设计成不变对象。

## 可变参数

在Python函数中，还可以定义可变参数。顾名思义，可变参数就是传入的参数个数是可变的，可以是1个、2个到任意个，还可以是0个。

我们以数学题为例子，给定一组数字a，b，c……，请计算a<sup>2</sup> + b<sup>2</sup> + c<sup>2</sup> + ……

要定义出这个函数，我们必须确定输入的参数。由于参数个数不确定，我们首先想到可以把a，b，c……作为一个`list` 或 `tuple` 传进来，这样，函数可以定义如下：

```python
def calc(numbers):
    sum = 0
    for n in numbers:
        sum = sum + n * n
    return sum
```

但是调用的时候，需要先组装出一个 `list` 或 `tuple`：

```python
calc([1, 2, 3])
14
calc((1, 3, 5, 7))
84
```

现在，我们利用可变参数，修改这个函数：

```python
def calc(*numbers):
    sum = 0
    for n in numbers:
        sum = sum + n * n
    return sum
```

然后就可以这样调用函数：

```python
calc(1, 2, 3)
14
calc(1, 3, 5, 7)
84
```

定义可变参数和定义一个 `list` 或 `tuple` 参数相比，仅仅在参数前面加了一个 `*` 号。在函数内部，参数numbers接收到的是一个 `tuple` ，因此，函数代码完全不变。但是，调用该函数时，可以传入任意个参数，包括0个参数：

```python
calc(1, 2)
5
calc()
0
```

但如果我就想传一个 `list` 或 `tuple` 进去，怎么办呢？ Python允许你在 `list` 或 `tuple` 前面加一个 `*` 号，把 `list` 或 `tuple` 的元素变成可变参数传进去：

```python
ums = [1, 2, 3]
calc(*nums)
14
```

## 关键字参数

可变参数允许你传入0个或任意个参数，这些可变参数在函数调用时自动组装为一个 `tuple`。

而关键字参数允许你传入0个或任意个含参数名的参数，这些关键字参数在函数内部自动组装为一个 `dict`

```python
def person(name, age, **kw):
    print('name:', name, 'age:', age, 'other:', kw)
```

函数 `person` 除了必选参数 `name` 和 `age` 外，还接受关键字参数 `kw`。在调用该函数时，可以只传入必选参数：

```python
person('Michael', 30)
name: Michael age: 30 other: {}
```

也可以传入任意个数的关键字参数：

```python
person('Bob', 35, city='Beijing')
name: Bob age: 35 other: {'city': 'Beijing'}
person('Adam', 45, gender='M', job='Engineer')
name: Adam age: 45 other: {'gender': 'M', 'job': 'Engineer'}
```

关键字参数可以扩展函数的功能。比如，在 `person` 函数里，我们保证能接收到 `name` 和 `age` 这两个参数，但是，如果调用者愿意提供更多的参数，我们也能收到。试想你正在做一个用户注册的功能，除了用户名和年龄是必填项外，其他都是可选项，利用关键字参数来定义这个函数就能满足注册的需求。

和可变参数类似，也可以先组装出一个 `dict`，然后，把该 `dict` 转换为关键字参数传进去：

```python
extra = {'city': 'Beijing', 'job': 'Engineer'}
person('Jack', 24, city=extra['city'], job=extra['job'])
name: Jack age: 24 other: {'city': 'Beijing', 'job': 'Engineer'}
```

上面的调用也可以简化：

```python
extra = {'city': 'Beijing', 'job': 'Engineer'}
person('Jack', 24, **extra)
name: Jack age: 24 other: {'city': 'Beijing', 'job': 'Engineer'}
```

`**extra` 表示把 `extra` 这个 `dict` 的所有 `key-value` 用关键字参数传入到函数的 `**kw` 参数，kw将获得一个 `dict`，注意kw获得的 `dict` 是 `extra` 的一份拷贝，对kw的改动不会影响到函数外的 `extra`。

## 命名关键字参数

对于关键字参数，函数的调用者可以传入任意不受限制的关键字参数。至于到底传入了哪些，就需要在函数内部通过kw检查。

仍以 `person()` 函数为例，我们希望检查是否有 `city` 和 `job` 参数：

```python
def person(name, age, **kw):
    if 'city' in kw:
        # 有city参数
        pass
    if 'job' in kw:
        # 有job参数
        pass
    print('name:', name, 'age:', age, 'other:', kw)
```

但是调用者仍可以传入不受限制的关键字参数：

```python
person('Jack', 24, city='Beijing', addr='Chaoyang', zipcode=123456)
```

如果要限制关键字参数的名字，就可以用命名关键字参数，例如，只接收 `city` 和 `job` 作为关键字参数。这种方式定义的函数如下：

```python
def person(name, age, *, city, job):
    print(name, age, city, job)
```

和关键字参数 `**kw` 不同，命名关键字参数需要一个特殊分隔符 `*`，`*` 后面的参数被视为命名关键字参数。

```python
person('Jack', 24, city='Beijing', job='Engineer')
Jack 24 Beijing Engineer
```

如果函数定义中已经有了一个可变参数，后面跟着的命名关键字参数就不再需要一个特殊分隔符 `*` 了：

```python
def person(name, age, *args, city, job):
    print(name, age, args, city, job)
```

命名关键字参数必须传入参数名，这和位置参数不同。如果没有传入参数名，调用将报错：

```python
person('Jack', 24, 'Beijing', 'Engineer')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: person() takes 2 positional arguments but 4 were given
```

由于调用时缺少参数名 `city` 和` job`，Python解释器把这4个参数均视为位置参数，但 `person()` 函数仅接受2个位置参数。

命名关键字参数可以有缺省值，从而简化调用：

```python
def person(name, age, *, city='Beijing', job):
    print(name, age, city, job)
```

由于命名关键字参数 `city` 具有默认值，调用时，可不传入 `city` 参数：

```python
person('Jack', 24, job='Engineer')
Jack 24 Beijing Engineer
```

使用命名关键字参数时，要特别注意，如果没有可变参数，就必须加一个 `*` 作为特殊分隔符。如果缺少 `*`，Python解释器将无法识别位置参数和命名关键字

```python
def person(name, age, city, job):
    # 缺少 *，city和job被视为位置参数
    pass
```

## 参数组合

在Python中定义函数，可以用必选参数、默认参数、可变参数、关键字参数和命名关键字参数，这5种参数都可以组合使用。但是请注意，参数定义的顺序必须是：必选参数、默认参数、可变参数、命名关键字参数和关键字参数。

```python
def f1(a, b, c=0, *args, **kw):
    print('a =', a, 'b =', b, 'c =', c, 'args =', args, 'kw =', kw)

def f2(a, b, c=0, *, d, **kw):
    print('a =', a, 'b =', b, 'c =', c, 'd =', d, 'kw =', kw)
```

在函数调用的时候，Python解释器自动按照参数位置和参数名把对应的参数传进去。

```python
f1(1, 2)
a = 1 b = 2 c = 0 args = () kw = {}
f1(1, 2, c=3)
a = 1 b = 2 c = 3 args = () kw = {}
f1(1, 2, 3, 'a', 'b')
a = 1 b = 2 c = 3 args = ('a', 'b') kw = {}
f1(1, 2, 3, 'a', 'b', x=99)
a = 1 b = 2 c = 3 args = ('a', 'b') kw = {'x': 99}
f2(1, 2, d=99, ext=None)
a = 1 b = 2 c = 0 d = 99 kw = {'ext': None}
```

通过一个 `tuple` 和 `dict` ，你也可以调用上述函数：

```python
args = (1, 2, 3, 4)
kw = {'d': 99, 'x': '#'}
f1(*args, **kw)
a = 1 b = 2 c = 3 args = (4,) kw = {'d': 99, 'x': '#'}
args = (1, 2, 3)
kw = {'d': 88, 'x': '#'}
f2(*args, **kw)
a = 1 b = 2 c = 3 d = 88 kw = {'x': '#'}
```

所以，对于任意函数，都可以通过类似 `func(*args, **kw)` 的形式调用它，无论它的参数是如何定义的。

<p style="background:#ebf7fd;color:#2d7091;border:1px solid rgba(45,112,145,0.3);border-radius:4px;text-shadow: 0 1px 0 #fff;padding:10px">虽然可以组合多达5种参数，但不要同时使用太多的组合，否则函数接口的可理解性很差。</p>

本节概念较多，下面来总结一下：

Python的函数具有非常灵活的参数形态，既可以实现简单的调用，又可以传入非常复杂的参数。

默认参数一定要用不可变对象，如果是可变对象，程序运行时会有逻辑错误！

要注意定义可变参数和关键字参数的语法：

`*args` 是可变参数，`args` 接收的是一个`tuple`；

`**kw` 是关键字参数，`kw` 接收的是一个 `dict`。

以及调用函数时如何传入可变参数和关键字参数的语法：

可变参数既可以直接传入：`func(1, 2, 3)`，又可以先组装 `list` 或 `tuple`，再通过`*args` 传入：`func(*(1, 2, 3))`；

关键字参数既可以直接传入：`func(a=1, b=2)`，又可以先组装 `dict`，再通过 `**kw` 传入：`func(**{'a': 1, 'b': 2})`。

使用 `*args` 和 `**kw` 是Python的习惯写法，当然也可以用其他参数名，但最好使用习惯用法。

命名的关键字参数是为了限制调用者可以传入的参数名，同时可以提供默认值。

定义命名的关键字参数在没有可变参数的情况下不要忘了写分隔符*，否则定义的将是位置参数。

# 递归函数

在函数内部，可以调用其他函数。如果一个函数在内部调用自身本身，这个函数就是递归函数。

我们来计算阶乘 `n! = 1 x 2 x 3 x ... x n`，用函数 `fact(n)` 表示，可以看出：

```
fact(n) = n! = 1 x 2 x 3 x ... x (n-1) x n = (n-1)! x n = fact(n-1) x n
```

所以，`fact(n)` 可以表示为 `n x fact(n-1)`，只有 `n=1` 时需要特殊处理。

于是，`fact(n)` 用递归的方式写出来就是：

```python
def fact(n):
    if n==1:
        return 1
    return n * fact(n - 1)
```

调用：

```python
fact(1)
1
fact(5)
120
fact(100)
93326215443944152681699238856266700490715968264381621468592963895217599993229915608941463976156518286253697920827223758251185210916864000000000000000000000000
```

如果我们计算fact(5)，可以根据函数定义看到计算过程如下：

```python
===> fact(5)
===> 5 * fact(4)
===> 5 * (4 * fact(3))
===> 5 * (4 * (3 * fact(2)))
===> 5 * (4 * (3 * (2 * fact(1))))
===> 5 * (4 * (3 * (2 * 1)))
===> 5 * (4 * (3 * 2))
===> 5 * (4 * 6)
===> 5 * 24
===> 120
```

递归函数的优点是定义简单，逻辑清晰。理论上，所有的递归函数都可以写成循环的方式，但循环的逻辑不如递归清晰

使用递归函数需要注意防止栈溢出。在计算机中，函数调用是通过栈（stack）这种数据结构实现的，每当进入一个函数调用，栈就会加一层栈帧，每当函数返回，栈就会减一层栈帧。由于栈的大小不是无限的，所以，递归调用的次数过多，会导致栈溢出。可以试试fact(1000)：

```python
fact(1000)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "<stdin>", line 4, in fact
  ...
  File "<stdin>", line 4, in fact
RuntimeError: maximum recursion depth exceeded in comparison
```

解决递归调用栈溢出的方法是通过尾递归优化，事实上尾递归和循环的效果是一样的，所以，把循环看成是一种特殊的尾递归函数也是可以的

> 尾递归是指，在函数返回的时候，调用自身本身，并且，return语句不能包含表达式。这样，编译器或者解释器就可以把尾递归做优化，使递归本身无论调用多少次，都只占用一个栈帧，不会出现栈溢出的情况。

上面的 `fact(n)` 函数由于 `return n * fact(n - 1)` 引入了乘法表达式，所以就不是尾递归了。要改成尾递归方式，需要多一点代码，主要是要把每一步的乘积传入到递归函数中：

```python
def fact(n):
    return fact_iter(n, 1)

def fact_iter(num, product):
    if num == 1:
        return product
    return fact_iter(num - 1, num * product)
```

可以看到，`return fact_iter(num - 1, num * product)` 仅返回递归函数本身，`num - 1` 和 `num * product` 在函数调用前就会被计算，不影响函数调用。

fact(5)对应的fact_iter(5, 1)的调用如下：

```python
===> fact_iter(5, 1)
===> fact_iter(4, 5)
===> fact_iter(3, 20)
===> fact_iter(2, 60)
===> fact_iter(1, 120)
===> 120
```

尾递归调用时，如果做了优化，栈不会增长，因此，无论多少次调用也不会导致栈溢出。

遗憾的是，大多数编程语言没有针对尾递归做优化，Python解释器也没有做优化，所以，即使把上面的 `fact(n)` 函数改成尾递归方式，也会导致栈溢出。

本节完毕.





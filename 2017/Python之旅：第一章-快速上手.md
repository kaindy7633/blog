<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Python之旅：第一章 快速上手](#python%E4%B9%8B%E6%97%85%E7%AC%AC%E4%B8%80%E7%AB%A0-%E5%BF%AB%E9%80%9F%E4%B8%8A%E6%89%8B)
  - [交互式解释器](#%E4%BA%A4%E4%BA%92%E5%BC%8F%E8%A7%A3%E9%87%8A%E5%99%A8)
  - [算法是什么](#%E7%AE%97%E6%B3%95%E6%98%AF%E4%BB%80%E4%B9%88)
  - [数和表达式](#%E6%95%B0%E5%92%8C%E8%A1%A8%E8%BE%BE%E5%BC%8F)
  - [变量](#%E5%8F%98%E9%87%8F)
  - [语句](#%E8%AF%AD%E5%8F%A5)
  - [获取用户输入](#%E8%8E%B7%E5%8F%96%E7%94%A8%E6%88%B7%E8%BE%93%E5%85%A5)
  - [函数](#%E5%87%BD%E6%95%B0)
  - [模块](#%E6%A8%A1%E5%9D%97)
    - [cmath和复数](#cmath%E5%92%8C%E5%A4%8D%E6%95%B0)
    - [回到未来](#%E5%9B%9E%E5%88%B0%E6%9C%AA%E6%9D%A5)
  - [保存并执行程序](#%E4%BF%9D%E5%AD%98%E5%B9%B6%E6%89%A7%E8%A1%8C%E7%A8%8B%E5%BA%8F)
    - [从命令提示符运行Python脚本](#%E4%BB%8E%E5%91%BD%E4%BB%A4%E6%8F%90%E7%A4%BA%E7%AC%A6%E8%BF%90%E8%A1%8Cpython%E8%84%9A%E6%9C%AC)
    - [让脚本像普通程序一样](#%E8%AE%A9%E8%84%9A%E6%9C%AC%E5%83%8F%E6%99%AE%E9%80%9A%E7%A8%8B%E5%BA%8F%E4%B8%80%E6%A0%B7)
    - [注释](#%E6%B3%A8%E9%87%8A)
  - [字符串](#%E5%AD%97%E7%AC%A6%E4%B8%B2)
    - [单引号字符串以及对引号转义](#%E5%8D%95%E5%BC%95%E5%8F%B7%E5%AD%97%E7%AC%A6%E4%B8%B2%E4%BB%A5%E5%8F%8A%E5%AF%B9%E5%BC%95%E5%8F%B7%E8%BD%AC%E4%B9%89)
    - [拼接字符串](#%E6%8B%BC%E6%8E%A5%E5%AD%97%E7%AC%A6%E4%B8%B2)
    - [字符串表示str和repr](#%E5%AD%97%E7%AC%A6%E4%B8%B2%E8%A1%A8%E7%A4%BAstr%E5%92%8Crepr)
    - [长字符串、原始字符串和字节](#%E9%95%BF%E5%AD%97%E7%AC%A6%E4%B8%B2%E5%8E%9F%E5%A7%8B%E5%AD%97%E7%AC%A6%E4%B8%B2%E5%92%8C%E5%AD%97%E8%8A%82)
      - [长字符串](#%E9%95%BF%E5%AD%97%E7%AC%A6%E4%B8%B2)
      - [原始字符串](#%E5%8E%9F%E5%A7%8B%E5%AD%97%E7%AC%A6%E4%B8%B2)
    - [Unicode、bytes和bytearray](#unicodebytes%E5%92%8Cbytearray)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Python之旅：第一章 快速上手

Python是一种面向对象的解释性高级编程语言，它拥有动态类型系统和垃圾回收功能，能够自动管理内存使用，并且支持多种编程范式，包括面向对象、命令式、函数式和过程式编程，其本身拥有一个巨大而广泛的标准库

Python需要安装，请访问其官方网站：https://python.org，根据你的系统下载并安装相应版本，安装部分这里就不再赘述了。

## 交互式解释器

在Python安装完成后，你可以在命令行窗口中输入`python`，即可启动Python的交互解释器，如果有多个版本共存，比如版本2和版本3，则输入`python3`，本书以Python3.6为标准进行撰写。

在解释器中，`>>>`代表可输入，我们来试试：

```python
print('hello Python!') # 语句后面无需加入分号
```

回车之后，解释器会打印出：

```python
hello Python!
>>>
```

## 算法是什么

算法详尽的描述了如何完成某项任务的流程或方法。

## 数和表达式

Python具有强大的数学运算功能，能执行常见的加减乘除运算，其他的还有求模(求余)、幂运算等。

在Python中，执行除法运算的结果始终为浮点数(Float)

```python
>>> 1 / 2
0.5
>>> 1 / 1
1.0
```

你可以使用双斜杠`//`来执行整除运算，即丢弃小数部分，注意，执行此运算时Python总是向下取整

```python
>>> 1 // 2
0
>>> 1 // 1
1
>>> 5.0 // 2.4
2.0
>>> 10 // 3
3
```

在Python中执行求余(求模)运算使用 `%` ，跟大多数语言一样。

```python
>>> 10 % 3
1
>>> 9 % 3
0
>>> 2.75 % 0.5
0.25
```

一些带有负数的整除和求余运算，取整运算(`//`)会始终取不大于当前结果的整数，也就是向下取整

```python
>>> 10 // 3
3
>>> 10 // -3
-4
>>> -10 // 3
-4
>>> -10 // -3
3
>>> 10 % -3
-2
>>> -10 % 3
2
>>> -10 % -3
-1
```

扩展阅读：大家看到上面的`10 % -3`的结果是-2，可能会感到很奇怪，不应该是-1吗？这里要特别说明一下，Python在求余运算时采用的floored division算法，它的运算规则由除法规则决定，所以，被除数、除数、商和余数的关系应该要满足下面的等式：

```
被除数 = 除数 * 商 + 模
```

由上面的等式得出：

```
模 = 被除数 - 除数 * 商
```

我们看到，`10 // -3`得到的结果是-4，因为Python在做整除运算时始终遵循向下取整的规则，所以`10 / -3`的结果`-3.33333...`向下取整就是-4，按照上面的公式，可以得出：`10 % -3`的结果应该是： `10 - -3 * -4 = -2`

接下来看看乘方(求幂)运算：

```python
>>> 2 ** 3
8
>>> -3 ** 2
-9
>>> (-3) ** 2
9
```

注意，乘方运算符的优先级比求负(单目减)高，所以`-3 ** 2`相当于-(3 ** 2),而如果要计算的是`(-3) ** 2`，就需要加上括号，明确的指出先进行单目运算。

在Python中，我们可以如下表示十六进制、八进制和二进制：

```python
>>> 0xAF
175
>>> 0o5
5
>>> 0b1011010010
722
```

## 变量

变量是表示(或指向)特定值的名称，比如你可以使用名称 `x` 来表示3:

```python
x = 3
```

这个过程称为赋值(assignment)，或者也可以这样理解，我们将变量`x`与值(或对象)3关联起来，给变量赋值后，就可以在表达式中使用：

```python
>>> x * 2
6
```

注意，使用变量之前必须给他赋值，在Python中变量没有默认值。上面的名称(标识符)只能由字母、数字和下划线(`_`)构成，且不能以数字打头。这个大多数编程语言一致。

## 语句

前面已经介绍的几乎是表达式，但又不完全是，也可以说它们是语句，比如`print`语句和赋值语句。

```python
print('hello world') # print语句
x = 3 # 赋值语句
```

表达式和语句有什么不同呢？表达式是一些东西，而语句做一些事情，它们的行为很相似，因此它们之间的界限并不是那么明确。

注意：`print`实际上是一个函数，因此`print`语句也就是函数调用。

## 获取用户输入

在Python中，使用函数`input`来获取用户输入：

```python
>>> input('The meaning of life:')
The meaning of life: 42
42
```

在命令行输入后回车，屏幕打印出需要用户输入的提示，输入值后回车，解释器再次打印出用户的输入，被输入的值以字符串的类型返回，我们可以使用`int`函数将其转换为数值

```python
>>> x = input('x: ')
x: 34
>>> y = input('y: ')
y: 42
>>> print(int(x) * int(y))
1428
```

## 函数

上面我们介绍了求幂运算，`2 ** 3`，求2的3次方，其实我们也可以使用函数`pow`来完成这个任务：

```python
>>> 2 ** 3
8
>>> pow(2, 3)
8
```

函数就是一个小型程序，用来执行特定的操作，Python也允许开发者自定义函数，因此我们将`pow`等标准函数称为**内置函数**

使用函数称为函数调用，向它提供实参，它返回一个值，函数调用会返回一个值，因此它们也是表达式，我们可以结合使用函数调用和运算符来编写更复杂的表达式：

```python
>>> 10 + pow(2, 3 * 5) / 3.0
10932.666666666666
```

内置函数`abs`计算绝对值，`round`函数将浮点数取值为与之最接近的整数

```python
>>> abs(-10)
10
>>> 2 // 3
0
>>> round(2 / 3)
1.0
```

Python还提供了`floor`函数，但我们不能直接使用它，它是被包含在模块中的。

## 模块

我们可以将模块看做是扩展，可以将其导入以扩展Python的功能。在Python中，导入模块使用`import`命令，上面提到的`floor`函数包含在模块`math`中

```python
>>> import math
>>> math.floor(32.9)
32
```

Python中有一些类似于函数的东西，诸如：`str`和`float`，它们用于类型转换，但它们并不是函数，而是类。

模块`math`还包含了`ceil`函数，它正好与`floor`相反，它返回大于或等于给定数的最小整数

```python
>>> math.ceil(32.3)
33
>>> math.ceil(32)
32
```

如果我们不想导入整个模块，也可以像下面那样从某个模块导入特定的函数：

```python
>>> from math import sqrt
>>> sqrt(9)
3
```

我们还可以使用变量来引用函数，比如，执行赋值语句`foo = math.sqrt`，我们就可以使用`foo`来计算平方根：

```python
>>> from math import sqrt
>>> foo = math.sqrt
>>> foo(4)
2.0
```

### cmath和复数

如果我们向函数`sqrt`提供了一个负数的参数，那么它将报错：

```python
>>> sqrt(-1)
Traceback (most recent call last):
  File "<pyshell#76>", line 1, in <module>
    sqrt(-1)
ValueError: math domain error
>>> 
```

如果我们坚持将值域限定为实数，并使用其近似的浮点数实现，那将无法计算负数的平方根，负数的平方根为虚数，而由实数部分和虚数部分组成的数为**复数**，Python提供了专门用于处理复数的模块：

```python
>>> import cmath
>>> cmath.sqrt(-1)
1j
```

### 回到未来

Python提供了一个`__future__`模块，这个模块里提供了Python当前不支持，但未来将成为标准的一些功能，如果你想使用，可以从这个模块中导入。

## 保存并执行程序

到目前为止，我们都在Python提供的交互式解释器中运行代码，如果你退出交互式解释器，那么你编写的代码将丢失。

如果你想保存你编写的代码，那么选择一个你所了解并擅长的代码编辑器吧，比如：vscode

这部分比较简单也很好理解，就不再赘述。

### 从命令提示符运行Python脚本

使用你所熟悉的代码编辑器编写完Python代码，并保存为`.py`结尾的文件，在命令行窗口，进入此文件所在目录，执行`python xxx.py`，就可以运行此Python脚本。

### 让脚本像普通程序一样

有时候我们希望运行Python脚本跟运行其他程序一样，比如浏览器或是文本编辑器。在Unix系统中提供了实现这个目的的标准方法：让脚本的第一行以字符序列 `#!` 开始，并在它后面指定用于对脚本进行解释的程序的绝对路径：

```python
#!/usr/bin/env python
```

然后给你即将要运行的Python脚本一个可执行权限：

```bash
$ chmod a+x xxx.py
```

现在就可以直接在命令行运行它了：

```bash
$ xxx.py
```

### 注释

在Python中，我们使用`#`来作为注释符号，`#`后面到行尾的所有内容将被忽略。注意：为统一注释风格，一般`#`和注释内容之间会有一个空格

```python
# 打印圆的周长
print(2 * PI * radius)
```

## 字符串

### 单引号字符串以及对引号转义

与数值一样，字符串也是值:

```python
>>> "hello world"
'hello world'
```

在定义字符串时，使用单引号和双引号没有任何差别，同时支持两者是因为有时候定义的字符串会相互包含：

```python
>>> "Let's go!"
"Let's go!"

# 如果这里使用单引号就会报错
>>> 'Let's go!'
SyntaxError: invalid syntax
```

其实在Python中，可以使用`\`来对引号进行转义，比如上面报错的部分可以这样写：

```python
>>> 'Let\'s go!'
"Let's go!"
```

### 拼接字符串

Python中，可以像做加法运算那样，使用`+`号将两个字符串拼接起来：

```python
>>> "hello " + "world!"
"hello world!"
>>> x = 'hello '
>>> y = 'Python!'
>>> x + y
"hello Python!"
```

### 字符串表示str和repr

Python通过`str`和`repr`两种不同的机制将值转换成了字符串。

```python
>>> print(repr("Hello,\nworld!"))
'Hello,\nworld!'
>>> print(str("Hello,\nworld!"))
Hello,
world!
```

### 长字符串、原始字符串和字节

在Python3.x中，所有的字符串都是Unicode编码的字符串。

#### 长字符串

要表示很长的字符串(跨越多行的字符串),可以使用三引号(不是普通引号)

```python
>>> print('''This is a very long string. It continues here.
And it's not over yet. "Hello world!"
Still here. ''')

This is a very long string. It continues here.
And it's not over yet. "Hello world!"
Still here. 
```

还可以使用三个双引号，比如：`"""Like This"""`，解释器能够识别表示字符串开始和结束的引号，因此字符串本身可包含单引号和双引号，无需使用反斜杠来转义。

#### 原始字符串

原始字符串不以特殊方式处理反斜杠，在常规字符串中，反斜杠扮演者特殊的角色：它对字符进行转义，能让你在字符串中包含原本无法包含的字符。比如`\n`表示换行：

```python
>>> print('Hello,\nworld!')
Hello,
world!
```

但如果我们希望输出的字符串中包含`\n`呢？比如：

```python
>>> path = 'C:\nowhere'
>>> print(path)
C:
owhere
```

这样就不对了，不是我们想要的结果，其实我们可以直接对反斜杠进行转义：

```python
>>> print('C:\\nowhere')
C:\nowhere
```

但如果字符串是很长的，而且包含了很多的需要转义的反斜杠，是不是写起来很繁琐？Python为我们提供了`r`标识符，来表示这是原始字符串：

```python
print(r'C:\Program Files\fnord\foo\bar\baz\frozz\bozz')
C:\Program Files\fnord\foo\bar\baz\frozz\bozz
```

原始字符串中可以包含任意字符，但有一个例外，引号是需要被转义的，所以，用于转义的反斜杠会被包含在结果字符串中：

```python
>>> print(r'Let\'s go!')
Let\'s go!
```

还有就是原始字符串不能以单个反斜杠结尾，除非你对其进行转义，但如果需要以反斜杠结尾，该怎么办呢？？下面的例子可以解决这个问题：

```python
>>> print(r'C:\Program Files\foo\bar' '\\')
C:\Program Files\foo\bar\
```

注意，指定原始字符串时，可使用单引号或双引号将其括起来，还可以使用三引号将其括起来。

### Unicode、bytes和bytearray

Python字符串使用Unicode编码来表示文本。

本章节完毕

本系列目录：

- [Python之旅：第一章 快速上手](https://www.todever.com/2018/03/31/Python%E4%B9%8B%E6%97%85%EF%BC%9A%E7%AC%AC%E4%B8%80%E7%AB%A0-%E5%BF%AB%E9%80%9F%E4%B8%8A%E6%89%8B/)
- [Python之旅：第二章 列表和元组](https://www.todever.com/2018/04/01/Python%E4%B9%8B%E6%97%85%EF%BC%9A%E7%AC%AC%E4%BA%8C%E7%AB%A0-%E5%88%97%E8%A1%A8%E5%92%8C%E5%85%83%E7%BB%84/)
- [Python之旅：第三章 使用字符串](https://www.todever.com/2018/04/02/Python%E4%B9%8B%E6%97%85%EF%BC%9A%E7%AC%AC%E4%B8%89%E7%AB%A0-%E4%BD%BF%E7%94%A8%E5%AD%97%E7%AC%A6%E4%B8%B2/)
- [Python之旅：第四章 当索引行不通时：使用字典](https://www.todever.com/2018/04/04/Python%E4%B9%8B%E6%97%85%EF%BC%9A%E7%AC%AC%E5%9B%9B%E7%AB%A0-%E5%BD%93%E7%B4%A2%E5%BC%95%E8%A1%8C%E4%B8%8D%E9%80%9A%E6%97%B6%EF%BC%9A%E4%BD%BF%E7%94%A8%E5%AD%97%E5%85%B8/)
- [Python之旅：第五章 条件、循环及其他语句](https://www.todever.com/2018/04/08/Python%E4%B9%8B%E6%97%85%EF%BC%9A%E7%AC%AC%E4%BA%94%E7%AB%A0-%E6%9D%A1%E4%BB%B6%E3%80%81%E5%BE%AA%E7%8E%AF%E5%8F%8A%E5%85%B6%E4%BB%96%E8%AF%AD%E5%8F%A5/)
- [Python之旅：第六章 抽象](https://www.todever.com/2018/04/11/Python%E4%B9%8B%E6%97%85%EF%BC%9A%E7%AC%AC%E5%85%AD%E7%AB%A0-%E6%8A%BD%E8%B1%A1/)
- [Python之旅：第七章 再谈抽象-面向对象编程](https://www.todever.com/2018/04/14/Python%E4%B9%8B%E6%97%85%EF%BC%9A%E7%AC%AC%E4%B8%83%E7%AB%A0-%E5%86%8D%E8%B0%88%E6%8A%BD%E8%B1%A1-%E9%9D%A2%E5%90%91%E5%AF%B9%E8%B1%A1%E7%BC%96%E7%A8%8B/)
- [Python之旅：第八章 异常](https://www.todever.com/2018/04/15/Python%E4%B9%8B%E6%97%85%EF%BC%9A%E7%AC%AC%E5%85%AB%E7%AB%A0-%E5%BC%82%E5%B8%B8/)
- [Python之旅：第九章 魔法方法、特性和迭代器](https://www.todever.com/2018/04/16/Python%E4%B9%8B%E6%97%85%EF%BC%9A%E7%AC%AC%E4%B9%9D%E7%AB%A0-%E9%AD%94%E6%B3%95%E6%96%B9%E6%B3%95%E3%80%81%E7%89%B9%E6%80%A7%E5%92%8C%E8%BF%AD%E4%BB%A3%E5%99%A8/)
- [Python之旅：第十章 开箱即用-标准库模块](https://www.todever.com/2018/04/21/Python%E4%B9%8B%E6%97%85%EF%BC%9A%E7%AC%AC%E5%8D%81%E7%AB%A0-%E5%BC%80%E7%AE%B1%E5%8D%B3%E7%94%A8-%E6%A0%87%E5%87%86%E5%BA%93%E6%A8%A1%E5%9D%97/)
- [Python之旅：第十一章 文件](https://www.todever.com/2018/04/23/Python%E4%B9%8B%E6%97%85%EF%BC%9A%E7%AC%AC%E5%8D%81%E4%B8%80%E7%AB%A0-%E6%96%87%E4%BB%B6/)
- [Python之旅：第十二章 图形用户界面](https://www.todever.com/2018/04/24/Python%E4%B9%8B%E6%97%85%EF%BC%9A%E7%AC%AC%E5%8D%81%E4%BA%8C%E7%AB%A0-%E5%9B%BE%E5%BD%A2%E7%94%A8%E6%88%B7%E7%95%8C%E9%9D%A2/)
- [Python之旅：第十三章 数据库支持](https://www.todever.com/2018/04/25/Python%E4%B9%8B%E6%97%85%EF%BC%9A%E7%AC%AC%E5%8D%81%E4%B8%89%E7%AB%A0-%E6%95%B0%E6%8D%AE%E5%BA%93%E6%94%AF%E6%8C%81/)
- [Python之旅：第十四章 网络编程](https://www.todever.com/2018/04/26/Python%E4%B9%8B%E6%97%85%EF%BC%9A%E7%AC%AC%E5%8D%81%E5%9B%9B%E7%AB%A0-%E7%BD%91%E7%BB%9C%E7%BC%96%E7%A8%8B/)
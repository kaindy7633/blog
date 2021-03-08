<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Python之旅：第三章 使用字符串](#python%E4%B9%8B%E6%97%85%E7%AC%AC%E4%B8%89%E7%AB%A0-%E4%BD%BF%E7%94%A8%E5%AD%97%E7%AC%A6%E4%B8%B2)
  - [字符串基本操作](#%E5%AD%97%E7%AC%A6%E4%B8%B2%E5%9F%BA%E6%9C%AC%E6%93%8D%E4%BD%9C)
  - [设置字符串格式：精简版](#%E8%AE%BE%E7%BD%AE%E5%AD%97%E7%AC%A6%E4%B8%B2%E6%A0%BC%E5%BC%8F%E7%B2%BE%E7%AE%80%E7%89%88)
  - [设置字符串格式：完整版](#%E8%AE%BE%E7%BD%AE%E5%AD%97%E7%AC%A6%E4%B8%B2%E6%A0%BC%E5%BC%8F%E5%AE%8C%E6%95%B4%E7%89%88)
    - [替换字段名](#%E6%9B%BF%E6%8D%A2%E5%AD%97%E6%AE%B5%E5%90%8D)
    - [基本转换](#%E5%9F%BA%E6%9C%AC%E8%BD%AC%E6%8D%A2)
    - [宽度、精度和千位分隔符](#%E5%AE%BD%E5%BA%A6%E7%B2%BE%E5%BA%A6%E5%92%8C%E5%8D%83%E4%BD%8D%E5%88%86%E9%9A%94%E7%AC%A6)
    - [符号、对齐和用0填充](#%E7%AC%A6%E5%8F%B7%E5%AF%B9%E9%BD%90%E5%92%8C%E7%94%A80%E5%A1%AB%E5%85%85)
  - [字符串的方法](#%E5%AD%97%E7%AC%A6%E4%B8%B2%E7%9A%84%E6%96%B9%E6%B3%95)
    - [center](#center)
    - [find](#find)
    - [join](#join)
    - [lower](#lower)
    - [replace](#replace)
    - [split](#split)
    - [strip](#strip)
    - [translate](#translate)
    - [判断字符串是否满足特定的条件](#%E5%88%A4%E6%96%AD%E5%AD%97%E7%AC%A6%E4%B8%B2%E6%98%AF%E5%90%A6%E6%BB%A1%E8%B6%B3%E7%89%B9%E5%AE%9A%E7%9A%84%E6%9D%A1%E4%BB%B6)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Python之旅：第三章 使用字符串

## 字符串基本操作

前面我们讲过所有的标准序列操作，比如：索引、切片、乘法、成员资格检查、长度、最小值和最大值，都适用于字符串，但字符串是不可变的，所以字符串的元素赋值和切片赋值都是非法的：

```python
>>> website = 'www.pythor.org'
>>> website[-3:] = 'com'
Traceback (most recent call last):
  File "<pyshell#55>", line 1, in <module>
    website[-3:] = 'com'
TypeError: 'str' object does not support item assignment
```

## 设置字符串格式：精简版

Python提供了多种字符串格式设置方法。以前，主要的解决方案是使用字符串格式设置运算符：百分号(`%`)。在`%`的左边指定一个字符串(格式字符串),并在右边指定要设置其格式的值。指定要设置其格式的值时，可使用单个值，比如字符串或数字，也可以使用元组或字典，其中最常见的是元组

```python
>>> format = 'Hello, %s. %s enough for ya?'
>>> values = ('world', 'Hot')
>>> format % values # 左边是格式字符串，右边是要设置的值，这里是一个元组
'Hello, world. Hot enough for ya?'
```

上面的示例代码中，`%s`称为转换说明符，它指出了要将值插入到什么地方。`s`意味着将值视为字符串进行格式设置，如果给定的值不是字符串，则会使用`str`进行转换，比如，如果使用`%.3f`，则是将给定的浮点数保留其小数点后3位进行输出，若不是浮点数，则会进行类型转换。

上述的方式在现在的版本中依然有效，另一种方案是所谓的模板字符串：

```python
>>> from string import Template
>>> tmpl = Template('Hello, $who! $what enough for ya?')
>>> tmpl.substitute(who="Mars", what="Dusty")
'Hello, Mars! Dusty enough for ya?'
```

包含等号的参数称为关键字参数，在字符串格式设置中，可将关键字参数视为一种向命名替换字段提供值的方式。

现在，我们应该选择使用字符串方法`format`来格式化字符串。

```python
>>> "{}, {} and {}".format("first", "second", "third")
'first, second and third'
>>> "{0}, {1} and {2}".format("first", "second", "third")
'first, second and third'
```

索引是不需要按上面那样顺序排列的：

```python
>>> "{3} {0} {2} {1} {3} {0}".format("be", "not", "or", "to")
'to be or not to be'
```

```python
>>> from math import pi
>>> "{name} is approximately {value:.2f}".format(value=pi, name="PI")
'PI is approximately 3.14'
```

关键字参数的排列顺序无关紧要。

在Python3.6中，如果变量与替换字段同名，还可以使用一种简写，在这种情况下，使用`f`字符串(在字符串前面加上`f`)

```python
>>> from math import e
>>> f"Euler's constant is roughly {e}"
"Euler's constant is roughly 2.718281828459045"
```

## 设置字符串格式：完整版

格式字符串的基本思想就是调用方法`format`，并提供要设置其格式的值。

在格式字符串中，最关键的是替换字段，替换字段由如下部分组成：

- **字段名**： 索引或标识符，指出要设置那个值的格式并使用结果来替换该字段
- **转换标志**： 跟在叹号后面的单个字符，当前支持的字符包括`r`(表示`repr`)、`s`(表示`str`)和`a`(表示`ascii`)。
- **格式说明符**: 跟在冒号后面的表达式。

### 替换字段名

通常情况下，我们只需向`format`提供要设置其格式的未命名参数，并在格式字符串中使用未命名字段。此时，将按顺序将字段和参数配对。你还可以给参数指定名称，这种参数将被用于相应的替换字段中，并且可以混用这两种方法：

```python
>>> "{foo} {} {bar} {}".format(1, 2, bar=4, foo=3)
'3 1 4 2'
```

还可以通过索引来指定要在那个字段中使用相应的未命名参数，这样就可以不按顺序使用未命名参数：

```python
>>> "{foo} {1} {bar} {0}".format(1, 2, bar=4, foo=3)
'3 2 4 1'
```

### 基本转换

指定了要在字段中包含的值后，就可以添加有关如何设置其格式的指令了。

```python
>>> print("{pi!s} {pi!r} {pi!a}".format(pi=" π "))
 π  ' π ' ' \u03c0 '
```

上述三个标志(`s`、`r`和`a`)指定分别使用`str`、`repr`和`ascii`进行转换。

你还可以指定要转换的值是那种类型，更准确的说，是要将其视为那种类型：

```python
>>> "The number is {num}".format(num=42)
'The number is 42'
>>> "The number is {num:f}".format(num=42)
'The number is 42.000000'
>>> "The number is {num:b}".format(num=42) # 还可以将其视为二进制
'The number is 101010'
```

下面是字符串格式设置中的类型说明符：

| 类型 | 含义 |
| --- | --- |
| `b` | 将整数表示为二进制数 |
| `c` | 将整数解读为Unicode码点 |
| `d` | 将整数视为十进制数进行处理，这是整数默认使用的说明符 |
| `e` | 使用科学表示法来表示小数(用e来表示指数) |
| `E` | 与`e`相同，但使用`E`来表示指数 |
| `f` | 将小数表示为定点数 |
| `F` | 与`f`相同，但对于特殊值(nan和inf)，使用大写表示 |
| `g` | 自动在定点表示法和科学表示法之间做出选择。这是默认用于小数的说明符，但在默认情况下至少有1位小数 |
| `G` | 与`g`相同，但使用大写来表示指数和特殊值 |
| `n` | 与`g`相同，但插入随区域而异的数字分隔符 |
| `o` | 将整数表示为八进制数 |
| `s` | 保持字符串的格式不变，这是默认用于字符串的说明符 |
| `x` | 将整数表示为十六进制并使用小写字母 |
| `X` | 与x相同，但使用大写字母 |
| `%` | 将数字表示为百分比值 |

### 宽度、精度和千位分隔符

设置浮点数的格式时，默认在小数点后面显示6位小数，这种默认设置可能不是你想要的，在这种情况下，你可以根据需要在格式说明中指定宽度和精度。

```python
>>> "{num:10}".format(num=3)
'         3'
>>> "{name:10}".format(name="Bob")
'Bob       '
```

可以看出，数字和字符串的对齐方式不同。

精度也是使用整数指定的，但需要在它前面加上一个表示小数点的句点。

```python
>>> "PI day is {pi:.2f}".format(pi=pi)
'PI day is 3.14'
```

当然，也可以同时指定宽度和精度：

```python
>>> "{pi:10.2f}".format(pi=pi)
'      3.14'
```

可使用逗号来指出你要添加千位分隔符

```python
>>> "One googol is {:,}".format(10**100)
'One googol is 10,000,000,000,000,000,000,000,000,000,000,000,000,000,000,000,000,000,000,000,000,000,000,000,000,000,000,000,000,000,000,000,000,000'
```

### 符号、对齐和用0填充

在指定宽度和精度的数前面，可添加一个标志，这个标志可以是零、加号、减号或空格，其中零表示使用0来填充数字：

```python
>>> '{:010.2f}'.format(pi)
'0000003.14'
```

要指定左对齐、右对齐或居中对齐，可分别使用`<`、`>`和`^`

```python
>>> print('{0:<10.2f}\n{0:^10.2f}\n{0:>10.2f}'.format(pi))
3.14      
   3.14   
      3.14
```

可以使用填充字符来扩充对齐说明符，这样将使用指定的字符而不是默认的空格来填充

```python
>>> '{:$^15}'.format(' WIN BIG ')
'$$$ WIN BIG $$$'
```

## 字符串的方法

### center

方法`center`通过在字符串的两边添加填充字符(默认为空格),让字符串居中

```python
>>> 'The Middle by Jimmy Eat World'.center(39)
'     The Middle by Jimmy Eat World     '
>>> 'The Middle by Jimmy Eat World'.center(39, '*')
'*****The Middle by Jimmy Eat World*****'
```

### find

方法`find`在字符串中查找子串，如果找到，返回子串的第一个字符的索引，否则返回`-1`

```python
>>> 'With a moo-moo here, and a moo-moo there'.find('moo')
7
>>> title = 'Monty Python\'s Flying circus'
>>> title.find('Monty')
0
>>> title.find('Python')
6
>>> title.find('Flying')
15
>>> title.find('Zirquss')
-1
```

**注意**：字符串方法`find`返回的并非布尔值，如果它返回的是0，说明它在索引0的位置找到了指定的子串

你可以指定搜索的起点和终点(它们是可选的)

```python
>>> subject = '$$$ Get rich now!!! $$$'
>>> subject.find('$$$')
0
>>> subject.find('$$$', 1) # 只指定了起点
20
>>> subject.find('!!!')
16
>>> subject.find('!!!', 0, 16) # 指定了查找起点和终点
-1
```

请注意，起点和终点值(第二个和第三个参数)指定的搜索范围包含起点，但不包含终点，这个切片的规则有点类似。

### join

`join`是一个非常重要的字符串方法，其作用域`split`相反，用于合并序列的元素

```python
>>> seq = [1, 2, 3, 4, 5]
>>> sep = '+'
>>> sep.join(seq)
Traceback (most recent call last):
  File "<pyshell#103>", line 1, in <module>
    sep.join(seq)
TypeError: sequence item 0: expected str instance, int found
>>> seq = ['1', '2', '3', '4', '5']
>>> sep.join(seq)
'1+2+3+4+5'
>>> dirs = '', 'usr', 'bin', 'env'
>>> '/'.join(dirs)
'/usr/bin/env'
>>> print('C:' + '\\'.join(dirs))
C:\usr\bin\env
```

如上面的例子，所合并序列的元素必须都是字符串。

### lower

方法`lower`范湖字符串的小写版本：

```python
>>> 'Trondheim Hammer Dance'.lower()
'trondheim hammer dance'
```

### replace

方法`replace`将指定子串替换为另一个字符串，并返回替换后的结果

```python
>>> 'This is a test'.replace('is', 'eez')
'Theez eez a test'
```

### split

`split`方法的作用与`join`相反，永不将字符串拆分为序列

```python
>>> '1+2+3+4+5'.split('+')
['1', '2', '3', '4', '5']
>>> '/usr/bin/env'.split('/')
['', 'usr', 'bin', 'env']
>>> 'Using the default'.split()
['Using', 'the', 'default']
```

注意：如果没有指定分隔符，将默认在单个或多个连续的空白字符(空格、制表符、换行符等)处进行拆分.

### strip

方法`strip`将字符串开头和末尾的空白(但不包含中间的空白)删除，并返回删除后的结果。

```python
>>> '  internal whitespace is kept  '.strip()
'internal whitespace is kept'
```

你也可以在一个字符串参数中指定要删除那些字符

```python
>>> '*** SPAM * for * everyone!!! ***'.strip(' *!') # 这个方法只删除开头和末尾的指定的字符
'SPAM * for * everyone'
```

### translate

方法`translate`与`replace`一样替换字符串的特定部分。但不同的是，`translate`只能对单个字符进行替换，相对于`replace`，它的优势在于它可以同时替换多个字符，因此效率比较高。

再使用`translate`进行替换之前，我们必须创建一个转换表，这个转换表指出了不同Unicode码点之间的转换关系。我们可以使用`str`调用方法`maketrans`，这个方法接受两个参数：两个长度相同的字符串：

```python
>>> table = str.maketrans('cs', 'kz')
>>> 'this is an incredible test'.translate(table)
'thiz iz an inkredible tezt'
```

### 判断字符串是否满足特定的条件

很多字符串方法都是以`is`打头，如`isspace`、`isdigit`和`isupper`等，它们判断字符串是否具有特定的性质，如果字符串具备特定的性质，就返回`True`，否则返回`False`

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
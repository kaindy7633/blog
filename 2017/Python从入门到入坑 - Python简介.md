# Python简介

## Python是什么

Python是著名的“龟叔”Guido van Rossum在1989年圣诞节期间，为了打发无聊的圣诞节而编写的一个编程语言。

Python就为我们提供了非常完善的基础代码库，覆盖了网络、文件、GUI、数据库、文本等大量内容，被形象地称作“内置电池（batteries included）”。

那Python适合开发哪些类型的应用呢？

首选是网络应用，包括网站、后台服务等等；

其次是许多日常需要的小工具，包括系统管理员需要的脚本任务等等；

另外就是把其他语言开发的程序再包装起来，方便使用。

## 安装Python

Python是跨平台的，它可以运行在Windows、Mac和各种Linux/Unix系统上。要开始学习Python编程，首先就得把Python安装到你的电脑里

### 安装Python 3.6

目前，Python有两个版本，一个是2.x版，一个是3.x版，这两个版本是不兼容的。由于3.x版越来越普及，我们的教程将以最新的Python 3.6版本为基础。请确保你的电脑上安装的Python版本是最新的3.6.x

#### 在Mac上安装Python

如果你正在使用Mac，系统是OS X 10.8~10.10，那么系统自带的Python版本是2.7。要安装最新的Python 3.6，有两个方法：

方法一：从Python官网下载Python 3.6的安装程序（网速慢的同学请移步国内镜像），双击运行并安装；

方法二：如果安装了Homebrew，直接通过命令brew install python3安装即可。

#### 在Linux上安装Python

如果你正在使用Linux，那我可以假定你有Linux系统管理经验，自行安装Python 3应该没有问题，否则，请换回Windows系统。

#### 在Windows上安装Python

首先，根据你的Windows版本（64位还是32位）从Python的官方网站下载Python 3.6对应的64位安装程序或32位安装程序（网速慢的同学请移步国内镜像），然后，运行下载的EXE安装包

特别要注意勾上`Add Python 3.6 to PATH`，然后点“Install Now”即可完成安装。

# 语法基础

Python的语法比较简单，采用缩进方式:

```python
# print absolute value of an integer:

a = 100
if a >= 0:
    print(a)
else:
    print(-a)
```

以`#`开头的语句是注释，注释是给人看的，可以是任意内容，解释器会忽略掉注释。

其他每一行都是一个语句，当语句以冒号`:`结尾时，缩进的语句视为代码块

没有规定缩进是几个空格还是Tab。按照约定俗成的管理，应该始终坚持使用**4个空格**的缩进

> 注意，Python程序是大小写敏感的

## 数据类型和变量

### 数据类型

#### 整数

Python可以处理任意大小的整数，当然包括负整数

#### 浮点数

浮点数也就是小数，之所以称为浮点数，是因为按照科学记数法表示时，一个浮点数的小数点位置是可变的。对于很大的浮点数，一般用科学计数法，如：`1.23e9`，或者`12.3e8`

#### 字符串

字符串是以单引号`'`或双引号`"`括起来的任意文本，比如'abc'，"xyz"等等。如果字符串中包含单引号或双引号，可以用转义字符`\`来表示，比如：`'I\'m \"OK\"!'`表示的字符串就是`I'm "OK"!`

转义字符`\`可以转义很多字符，比如`\n`表示换行，`\t`表示制表符

为了简化，Python还允许用`r''`表示`''`内部的字符串默认不转义

```python
>>> print(r'\\\t\\')
\\\t\\
```

如果字符串内部有很多换行，Python允许用`'''...'''`的格式表示多行内容

```python
>>> print('''line1
... line2
... line3''')
line1
line2
line3
```

#### 布尔值

在Python中，可以直接用`True`、`False`表示布尔值（请注意大小写，其他语言中是`true`和`false`）

```python
>>> True
True
>>> False
False
>>> 3 > 2
True
>>> 3 > 5
False
```

布尔值可以用`and`、`or`和`not`运算。

`and`运算是与运算，只有所有都为`True`，`and`运算结果才是`True`：

```python
>>> True and True
True
>>> True and False
False
>>> False and False
False
>>> 5 > 3 and 3 > 1
True
```

`or`运算是或运算，只要其中有一个为`True`，`or`运算结果就是`True`：

```python
>>> True or True
True
>>> True or False
True
>>> False or False
False
>>> 5 > 3 or 1 > 3
True
```

`not`运算是非运算，它是一个单目运算符，把`True`变成`False`，`False`变成`True`：

```python
>>> not True
False
>>> not False
True
>>> not 1 > 2
True
```

#### 空值

空值是Python里一个特殊的值，用`None`表示。`None`不能理解为0，因为0是有意义的，而`None`是一个特殊的空值。

此外，Python还提供了列表、字典等多种数据类型，还允许创建自定义数据类型

### 变量

在计算机程序中，变量不仅可以是数字，还可以是任意数据类型。变量在程序中就是用一个变量名表示了，变量名必须是大小写英文、数字和_的组合，且不能用数字开头

```python
# 变量a是一个整数。
a = 1

# 变量t_007是一个字符串。
t_007 = 'T007'

# 变量Answer是一个布尔值True。
Answer = True
```

在Python中，等号=是赋值语句，可以把任意数据类型赋值给变量，同一个变量可以反复赋值，而且可以是不同类型的变量

这种变量本身类型不固定的语言称之为动态语言，与之对应的是静态语言。静态语言在定义变量时必须指定变量类型，如果赋值的时候类型不匹配，就会报错，如Java

### 常量

所谓常量就是不能变的变量，比如常用的数学常数π就是一个常量。在Python中，通常用全部大写的变量名表示常量：

```python
PI = 3.14159265359
```

但事实上PI仍然是一个变量，Python根本没有任何机制保证PI不会被改变

在Python中，有两种除法，一种除法是`/`：

```python
>>> 10 / 3
3.3333333333333335
```

`/`除法计算结果是浮点数，即使是两个整数恰好整除，结果也是浮点数：

```python
>>> 9 / 3
3.0
```

还有一种除法是`//`，称为地板除，两个整数的除法仍然是整数：

```python
>>> 10 // 3
3
```

因为`//除法只取结果的整数部分，所以Python还提供一个余数运算，可以得到两个整数相除的余数：

```python
>>> 10 % 3
1
```

## 字符串和编码

### Python的字符串

在最新的Python 3版本中，字符串是以Unicode编码的，也就是说，Python的字符串支持多语言

```python
>>> print('包含中文的str')
包含中文的str
```

对于单个字符的编码，Python提供了`ord()`函数获取字符的整数表示，`chr()`函数把编码转换为对应的字符

```python
>>> ord('A')
65
>>> ord('中')
20013
>>> chr(66)
'B'
>>> chr(25991)
'文'
```

如果知道字符的整数编码，还可以用十六进制这么写`str`：

```python
>>> '\u4e2d\u6587'
'中文'
```

由于Python的字符串类型在内存中以Unicode表示,一个字符对应若干个字节,如果要在网络上传输，或者保存到磁盘上，就需要将其转换为以字节为单位的`bytes`。

Python对`bytes`类型的数据用带b前缀的单引号或双引号表示：

```python
x = b'ABC'
```

以Unicode表示的字符串通过`encode()`方法可以编码为指定的`bytes`

```python
>>> 'ABC'.encode('ascii')
b'ABC'
>>> '中文'.encode('utf-8')
b'\xe4\xb8\xad\xe6\x96\x87'
>>> '中文'.encode('ascii')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
UnicodeEncodeError: 'ascii' codec can't encode characters in position 0-1: ordinal not in range(128)
```

反过来，如果我们从网络或磁盘上读取了字节流，那么读到的数据就是`bytes`。要把`bytes`变为字符串，就需要用`decode()`方法：

```python
>>> b'ABC'.decode('ascii')
'ABC'
>>> b'\xe4\xb8\xad\xe6\x96\x87'.decode('utf-8')
'中文'
```

要计算字符串包含多少个字符，可以用`len()`函数：

```python
>>> len('ABC')
3
>>> len('中文')
2
```

`len()`函数计算的是str的字符数，如果换成`bytes`，`len()`函数就计算字节数：

```python
>>> len(b'ABC')
3
>>> len(b'\xe4\xb8\xad\xe6\x96\x87')
6
>>> len('中文'.encode('utf-8'))
6
```

在操作字符串时，我们经常遇到str和bytes的互相转换。为了避免乱码问题，应当始终坚持使用UTF-8编码对str和bytes进行转换

由于Python源代码也是一个文本文件，所以，当你的源代码中包含中文的时候，在保存源代码时，就需要务必指定保存为UTF-8编码。当Python解释器读取源代码时，为了让它按UTF-8编码读取，我们通常在文件开头写上这两行：

```python
#!/usr/bin/env python3
# -*- coding: utf-8 -*-
```

### 格式化

在Python中，采用的格式化方式和C语言是一致的，用`%`实现

```python
>>> 'Hello, %s' % 'world'
'Hello, world'
>>> 'Hi, %s, you have $%d.' % ('Michael', 1000000)
'Hi, Michael, you have $1000000.'
```

`%`运算符就是用来格式化字符串的。在字符串内部，`%s`表示用字符串替换，`%d`表示用整数替换，有几个`%?`占位符，后面就跟几个变量或者值，顺序要对应好。如果只有一个`%?`，括号可以省略。

常见的占位符有：

|占位符|替换内容|
|---|---|
|%d|整数|
|%f|浮点数|
|%s|字符串|
|%x|十六进制整数|

其中，格式化整数和浮点数还可以指定是否补0和整数与小数的位数：

```python
>>> '%02d-%02d' % (3,1)
'03-01'

>>> '%.2f' % 3.1415926
'3.14'
```

如果你不太确定应该用什么，`%s`永远起作用，它会把任何数据类型转换为字符串：

```python
>>> 'Age: %s. Gender: %s' % (25, True)
'Age: 25. Gender: True'
```

字符串里面的`%`是一个普通字符怎么办？这个时候就需要转义，用`%%`来表示一个`%`：

```python
>>> 'growth rate: %d %%' % 7
'growth rate: 7 %'
```

### format()

另一种格式化字符串的方法是使用字符串的`format()`方法，它会用传入的参数依次替换字符串内的占位符{0}、{1}……

```python
>>> 'Hello, {0}, 成绩提升了 {1:.1f}%'.format('小明', 17.125)
'Hello, 小明, 成绩提升了 17.1%'
```

## 列表(list)和元组(tuple)

### 列表(list)

Python内置的一种数据类型是列表：list。list是一种有序的集合，可以随时添加和删除其中的元素。

```python
>>> classmates = ['Michael', 'Bob', 'Tracy']
>>> classmates
['Michael', 'Bob', 'Tracy']
```

用`len()`函数可以获得list元素的个数：

```python
>>> len(classmates)
3
```

我们可以用索引来访问list中每一个位置的元素，索引是从0开始的：

```python
>>> classmates[0]
'Michael'
>>> classmates[1]
'Bob'
>>> classmates[2]
'Tracy'
>>> classmates[3]
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
IndexError: list index out of range
```

要确保索引不要越界，记得最后一个元素的索引是`len(classmates) - 1`

如果要取最后一个元素，除了计算索引位置外，还可以用-1做索引，直接获取最后一个元素：

```python
>>> classmates[-1]
'Tracy'
```

```python
# 获取倒数第2个，第3个...

>>> classmates[-2]
'Bob'
>>> classmates[-3]
'Michael'
>>> classmates[-4]
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
IndexError: list index out of range
```

我们可以往list中追加元素到末尾，使用`append()`方法，类似JavaScript中的数组函数`push()`

```python
>>> classmates.append('Adam')
>>> classmates
['Michael', 'Bob', 'Tracy', 'Adam']
```

也可以使用`insert()`方法把元素插入到指定的位置

```python
>>> classmates.insert(1, 'Jack')
>>> classmates
['Michael', 'Jack', 'Bob', 'Tracy', 'Adam']
```

使用`pop()`方法来删除list中末尾的元素

```python
>>> classmates.pop()
'Adam'
>>> classmates
['Michael', 'Jack', 'Bob', 'Tracy']
```

要删除指定位置的元素，用`pop(i)`方法，其中i是索引位置：

```python
>>> classmates.pop(1)
'Jack'
>>> classmates
['Michael', 'Bob', 'Tracy']
```

要把某个元素替换成别的元素，可以直接赋值给对应的索引位置：

```python
>>> classmates[1] = 'Sarah'
>>> classmates
['Michael', 'Sarah', 'Tracy']
```

list里面的元素的数据类型也可以不同，比如：

```python
>>> L = ['Apple', 123, True]
```

list元素也可以是另一个list，比如：

```python
>>> s = ['python', 'java', ['asp', 'php'], 'scheme']
>>> len(s)
4
```

如果一个list中一个元素也没有，就是一个空的list，它的长度为0：

```python
>>> L = []
>>> len(L)
0
```

### 元组(tuple)

Python中还有另外一种有序列表叫元组：tuple。tuple和list非常类似，但是tuple一旦初始化就不能修改

```python
>>> classmates = ('Michael', 'Bob', 'Tracy')
```

classmates这个tuple不能变了，它也没有`append()`，`insert()`这样的方法。其他获取元素的方法和list是一样的，你可以正常地使用`classmates[0]`，`classmates[-1]`，但不能赋值成另外的元素。

那不可变的元组有什么意义呢？ 其实不可变就代表着代码更安全，如果可能，请尽量使用tuple

一个tuple的坑：Python规定，当你定义一个tuple时，在定义的时候，tuple的元素就必须被确定下来

```python
>>> t = (1, 2)
>>> t
(1, 2)
```

如果要定义一个空的tuple，可以写成()：

```python
>>> t = ()
>>> t
()
```

但是，如果你想定义只有一个元素的tuple，就会出现歧义：

```python
>>> t = (1)
>>> t
1
```

所以，Python规定，如果定义一个只有一个元素的tuple时，必须在此元素后面加上一个`,`

```python
>>> t = (1,)
>>> t
(1,)
```

下面我们再来看一个例子，一个可变的tuple：

```python
>>> t = ('a', 'b', ['A', 'B'])
>>> t[2][0] = 'X'
>>> t[2][1] = 'Y'
>>> t
('a', 'b', ['X', 'Y'])
```

不是说tuple一旦定义就不能被改变了吗？？我们来理解一下tuple的不可变，实际上，tuple的不可变，指的是元素的指向不可变，上面的例子中，元组t的第三个元素是一个list，它指向的是这个list对象，但这并不能说这个list对象里的值不能变，而是第三个元素所指向的list对象不能变。

所以，要确保一个tuple不可变，就要保证这个tuple里的所有元素都是不可变的。

## 条件判断

在Python程序中，我们使用if语句来实现条件判断，这跟大多数高级程序语言一致

```python
age = 20
if age >= 18:
    print('your age is', age)
    print('adult')
```

Python中没有类似`{...}`这样的代码块，来标识这些是要来运行的代码，在Python中使用缩进来判断，如果条件成立，则需要运行的程序都会缩进编写，如上面的例子，如果条件成立，会执行下面的两句print代码

**特别注意：在Python中，判断语句后面都会加上`:`**

如果是多个条件的判断，我们可以使用`elif`,注意，不是`else if`

```python
age = 3
if age >= 18:
    print('adult')
elif age >= 6:
    print('teenager')
else:
    print('kid')
```

`if`也可以简写：

```python
if x:
    print('True')
```

只要x是非零数值、非空字符串、非空list等，就判断为`True`，否则为`False`。

注意：在Python中没有`switch...case`

### `input()`方法中的坑

在控制台，我们可以使用`input()`方法来获取用户的输入：

```python
birth = input('birth: ')
if birth < 2000:
    print('00前')
else:
    print('00后')
```

上面这段程序却报错了？为什么？ 这是因为在`input()`方法中返回的数据类型是字符串类型，在Python中，字符串类型是不能和数值类型做比较的(想想还是JavaScript方便啊，有自动类型转换).所以，我们可以使用`int()`方法将用户输入的值转换为数值类型

```python
s = input('birth: ')
birth = int(s)
if birth < 2000:
    print('00前')
else:
    print('00后')
```

但是问题又来了，如果输入的不是数值，而是其他类型，如字符串，也会报错。因为`int()`方法不能处理非数值类型的数据，这里我们放到后面的异常捕获和错误处理来讲。

## 循环

在Python中，循环有两种，一种是 `for...in` 循环，还有一种是 `while`

### `for...in`

`for...in` 可以依次将列表或元组中的值打印出来：

```python
names = ['Michael', 'Bob', 'Tracy']
for name in names:
    print(name)

Mickael
Bob
Tracy
```

如果想要计算一个列表中所有值的和，可以用一个变量sum来做累加：

```python
sum = 0
for x in [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]:
    sum = sum + x
print(sum)
```

但如果是100个元素或者更多呢？ Python提供一个 `range()` 函数，可以生成一个整数序列，再通过 `list()` 函数可以转换为list, 比如 `range(5)`可以生成一个从0开始且小于5的list

```python
list(range(5))
[0, 1, 2, 3, 4]
```

这样，我们就可以用 `range(101)` 来计算100以内的数的和:

```python
sum = 0
for x in range(101)
    sum += x

print(sum)
5050
```

### `while`

第二种循环是 `while` 循环，满足条件则不断循环，不满足则退出循环。我们可以用 `while` 来计算100以内奇数的和：

```python
sum = 0
n = 99

while n > 0:
    sum += n
    n = n - 2

print(sum)
2500
```

在循环内部变量n不断自减，直到变为-1时，不再满足 `while` 条件，循环退出

下面的例子使用 `while` 依次打印出名字

```python
N = ['Bret', 'Mick', 'Zroe']
i = 0
while i < len(N):
    print(N[i])
    i += 1
```

### `break`

在Python的循环中，如果满足条件，`break` 可以提前退出循环

```python
# 当n大于10时，使用break退出循环
n = 1
while n < 100:
    if n > 10:
        break 
    print(n)
    n += 1
print('END')
```

`break` 的作用是提前结束循环

### `continue`

在循环过程中，也可以通过 `continue` 语句，跳过当前的这次循环，直接开始下一次循环

```python
# 循环打印10以内的奇数

n = 0
while n < 10:
    n += 1
    if n % 2 == 0:  # 如果当前的n是偶数
        continue    # 退出当前这次循环，继续下一次循环
    print(n)
```

`continue` 的作用是提前结束本轮循环，并直接开始下一轮循环

## 字典(dict)和set

### 字典(dict)

Python具有字典(dict)这种数据类型，在其他的编程语言中，它称作 map , 它使用键值对(key-value)存储数据，具有极快的查找速度。

```python
# 定义一个dict
d = {'Mick': 98, 'Bote': 79, 'Kaindy': 59}
d['Kaindy']
59
```

把数据放入dict的方法，除了初始化时指定外，还可以通过key放入：

```python
d['Adm'] = 65
d['Adm']
65
```

一个key只能对应一个value，所以，多次对一个key放入value，后面的值会把前面的值替换掉

```python
d['Jack'] = 99
d['Jack']
99

d['Jack'] = 90
d['Jack']
90
```

如果查找的key不存在，Python就会报错，所以我们可以有两种方法来判断可要查找的key是否存在于dict中

一是通过 `in`来判断：

```python
'Those' in d
Flase
```

二是通过dict提供的 `get()` 方法，如果key不存在，则返回 `None`，注意，在Python交互环境中，`None`是不显示的

```python
d.get('Those')
d.get('Kaindy')
58
```

要删除一个key，可以使用 `pop(key)` 方法，对应的value也会从dict中删除

```python
d.pop('Kaindy')
58

d
{'Mick': 98, 'Bor': 78, 'Adm': 65}
```

可以看出，list和dict很相似，我们来看下他们的区别：

dict：
1. 查找和插入的速度极快，不会随着key的增加而变慢；
2. 需要占用大量的内存，内存浪费多。

而list相反：

1. 查找和插入的时间随着元素的增加而增加；
2. 占用空间小，浪费内存很少。

dict是用空间来换取时间的一种方法。

dict可以用在需要高速查找的很多地方，在Python代码中几乎无处不在，正确使用dict非常重要，需要牢记的第一条就是dict的key必须是不可变对象。

这是因为dict根据key来计算value的存储位置，如果每次计算相同的key得出的结果不同，那dict内部就完全混乱了。这个通过key计算位置的算法称为哈希算法（Hash）。

要保证hash的正确性，作为key的对象就不能变。在Python中，字符串、整数等都是不可变的，因此，可以放心地作为key。而list是可变的，就不能作为key：

```python
key = [1, 2, 3]
d[key] = 'a list'
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: unhashable type: 'list'
```

### set

set和dict类似，也是一组key的集合，但不存储value。由于key不能重复，所以，在set中，没有重复的key

要创建一个set，需要提供一个list作为输入集合：

```python
s = set([1, 2, 3])
s
{1, 2, 3}
```

重复元素在set中自动被过滤：

```python
s = set([1, 2, 2, 3, 4, 4, 5])
s
{1, 2, 3, 4, 5}
```

可以通过 `add(key)` 方法可以添加元素到set中

```python
s.add(6)
s
{1, 2, 3, 4, 5, 6}

# 添加重复的key不会有任何效果
s.add(1)
s
{1, 2, 3, 4, 5, 6}
```

通过 `remove(key)` 方法可以删除set中的元素：

```python
s.remove(1)
s
{2, 3, 4, 5, 6}
```

set可以看成数学意义上的无序和无重复元素的集合，因此，两个set可以做数学意义上的交集、并集等操作：

```python
s1 = set([1, 2, 3])
s2 = set([2, 3, 4])

s1 & s2
{2, 3}

s1 | s2
{1, 2, 3, 4}
```

set和dict的唯一区别仅在于没有存储对应的value，但是，set的原理和dict一样，所以，同样不可以放入可变对象，因为无法判断两个可变对象是否相等，也就无法保证set内部“不会有重复元素”

### 不可变对象

str是不变对象，而list是可变对象。

对于可变对象，比如list，对list进行操作，list内部的内容是会变化的

```python
a = ['c', 'b', 'a']
a.sort()
a
['a', 'b', 'c']
```

而对于不可变对象，比如str：

```python
a = 'abc'
a.replace('a', 'A')
'Abc'
a
'abc'
```

我们使用 `replace()` 方法将字符串中的a替换为大写的A，可为什么a的值还是`abc`呢？

我们把上面的例子换一下，看看：

```python
a = 'abc'
b = a.replace('a', 'A')
b
'Abc'
a
'abc'
```

a是变量，'abc'是字符串对象，`a = 'abc'`这句可以理解为变量a指向了一个字符串对象，这个字符串对象的值是`abc`，上面的 `replace()` 方法实际上是创建了一个新的字符串对象 `Abc` ，并将其返回，而变量a仍然指向原来的字符串对象'abc'

对于不变对象来说，调用对象自身的任意方法，也不会改变该对象自身的内容。相反，这些方法会创建新的对象并返回，这样，就保证了不可变对象本身永远是不可变的。

## 结束语

本章结束，本章主要讲述了 `Python` 的一些基础语法，后续我会深入讨论`Python`的其他特性。此篇系列文章不太全面，但对于入门来讲已经足够，后期我会制作一些比较完整的Python教程，敬请期待.
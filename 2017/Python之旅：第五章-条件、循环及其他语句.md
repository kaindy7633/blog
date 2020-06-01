# Python之旅：第五章 条件、循环及其他语句

## 再谈print和import

`print`和`import`有几个隐藏的特性，虽然`print`现在是一个函数，但以前它却是一个语句。对于很多应用程序来说，使用模块`logging`来写入日志比使用`print`更合适。

### 使用print打印多个参数

`print`可用于打印一个表达式，这个表达式要么是字符串，要么将自动转换为字符串，并且，我们也可以同时打印多个表达式，条件是用逗号分隔它们：

```python
>>> print('Age: ', 42)
Age: 42
```

如果你要合并文本和变量值，而又不想使用字符串格式设置功能时，这很有用：

```python
>>> name = 'Gumby'
>>> salutation = 'Mr.'
>>> greeting = 'Hello, '
>>> print(greeting, salutation, name)
Hello,  Mr. Gumby
```

如果有需要，我们还可以自定义分隔符：

```python
>>> print('I', 'wish', 'to', 'register', 'a', 'complaint', sep='_')
I_wish_to_register_a_complaint
```

我们还可以自定义结束字符串，以替代默认的换行符

```python
# 在交互式环境中无法运行

print('Hello,', end='')
print('world!')
```

### 使用import导入模块时重命名

我们从模块导入时，通常使用：

```python
import somemodule
```

或者：

```python
from somemodule import somefunction
```

又或者：

```python
from somemodule import somfunction, anotherfunction, yetanotherfunction
```

又或者：

```python
from somemodule import *
```

只有当你了解所导入模块中的一切细节时，可以采用最后一种方式。为了避免不同模块包含同名方法时导入的问题，我们可以在语句末尾添加`as`子句并指定别名：

```python
>>> import math as foobar
>>> foobar.sqrt(4)
2.0
```

导入特定函数并给它指定别名：

```python
>>> from math import sqrt as foobar
>>> foobar(4)
2.0
```

## 赋值魔法

下面介绍一些在赋值语句中使用的技巧

### 序列解包

前面介绍的赋值语句有很多，如给变量赋值，或给某种数据结构的某个元素赋值，我们也可以同时(并行)给多个变量赋值：

```python
>>> x, y, z = 1, 2, 3
>>> print(x, y, z)
1 2 3
```

可以使用这种方式来交换两个变量的值，只需要一行代码：

```python
>>> x, y = y, x
>>> print(x, y ,z)
2 1 3
```

上面的操作我们叫做**序列解包**(或可迭代对象解包)：将一个序列(或任何可迭代对象)解包，并将得到的值存储到一系列变量中。

```python
>>> values = 1, 2, 3
>>> values
(1, 2, 3)
>>> x, y, z = values
>>> x
1
```

我们使用方法`popitem`从一个字典中任意获取一个键值对，并以元组的方式返回，接下来就可以直接将返回的元组解包到两个变量中。

```python
>>> scoundrel = {'name': 'Robin', 'girlfriend': 'Marion'}
>>> key, value = scoundrel.popitem()
>>> key
'girlfriend'
>>> value
'Marion'
```

要解包的序列包含的元素个数必须与左边列出的目标个数相同，否则Python将引发异常

```python
>>> x, y ,z = 1, 2
Traceback (most recent call last):
  File "<pyshell#22>", line 1, in <module>
    x, y ,z = 1, 2
ValueError: not enough values to unpack (expected 3, got 2)
>>> x, y, z = 1, 2, 3, 4
Traceback (most recent call last):
  File "<pyshell#23>", line 1, in <module>
    x, y, z = 1, 2, 3, 4
ValueError: too many values to unpack (expected 3)
```

不过我们可以使用星号运算符(`*`)来收集多余的值，这样无需确保值和变量的个数相同。

```python
>>> a, b, *rest = [1, 2, 3, 4]
>>> rest
[3, 4]
```

还可以将带星号的变量放在其他位置：

```python
>>> name = 'Albus Percival Wulfric Brian Dumbledore'
>>> first, *middle, last = name.split()
>>> middle
['Percival', 'Wulfric', 'Brian']
```

赋值语句的右边可以是任何类型的序列，但带星号的变量最终包含的总是一个列表，即使变量和值的个数相同亦是如此：

```python
>>> a, *b, c = 'abc'
>>> a, b, c
('a', ['b'], 'c')
```

### 链式赋值

链式赋值是一种快捷方式，用于将多个变量关联到同一个值。

```python
x = y = somefunction()
```

### 增强赋值

当我们要执行一个运算表达式时，如：`x = x + 1`，可以将右边表达式中的运算符移到赋值运算符的的前面，从而写成`x += 1`，这种方式称为增强赋值，它适用于所有标准运算符，如`*`、`/`和`%`等。

```python
>>> x = 2
>>> x += 1
>>> x *= 2
>>> x
6
```

增强赋值也可用于其他数据类型：

```python
>>> fnord = 'foo'
>>> fnord += 'bar'
>>> fnord *= 2
>>> fnord
'foobarfoobar'
```

## 代码块：缩进的乐趣

代码块是一组语句，可在满足条件时执行(if语句)，可执行多次(循环),代码块是通过缩进代码来创建的。

**注意：** 也可以使用制表符来缩进代码块，但标准的做法是只使用空格来缩进，且每级缩进4个空格。

在Python中，使用冒号(`:`)指出接下来是一个代码块，并将该代码块中的每行代码都缩进相同的程度，发现缩进量与之前相同时，就知道当前代码块结束。

## 条件和条件语句

### 这正是布尔值的用武之地

条件判断语句中经常会用到的是真值和假值，它们都是布尔值类型。用作布尔表达式时，下面的值都被解释器视为假：

- 标准值：`False`
- 值类型：`None`
- 各种类型(包括浮点数、复数)的数值 `0`
- 空字符串、空元组`()`和空列表`[]`
- 空字典 `{}`

其他的值都被视为真值，包括特殊值`True`

标准真值为0(表示假)和1(表示真)。实际上`True`和`False`不过是1和0的别名，其作用都是相同的。

```python
>>> True
True
>>> False
False
>>> True == 1
True
>>> False == 0
True
>>> True + False + 42
43
```

布尔值`True`和`False都属于类型`bool`，它与`list`、`str`和`tuple`一样，可用来转换其他的值。

```python
>>> bool('I think, therefore I am')
True
>>> bool(42)
True
>>> bool('')
False
>>> bool(0)
False
```

### 有条件的执行和if语句

`if`语句让你能够有条件的执行代码，如果条件为真，则执行后续的代码块，否则就不执行。

```python
name = input('What is your name? ')
if name.endswith('Gumby'):
  print('Hello, Mr. Gumby')
```

### else子句

`else`子句是可以增加的一种选择，当条件不成立时，将执行`else`之后的语句块

```python
name = input('What is your name? ')

if name.endswith('Gumby'):
    print('Hello, Mr.Gumby')
else:
    print('Hello, stranger')
```

在Python中还有一个跟`if`很相似的条件表达式，也就是其他语言中的三目运算：

```python
# 如果中间的if表达式为真，则取第一个值friend，否则取else后面的stranger
status = 'friend' if name.endswith('Gumby') else 'stranger'
```

### elif子句

要检查多个条件，可以使用`elif`，`elif`是`else if`的缩写。

```python
num = int(input('Enter a number: '))

if num > 0:
    print('The number is positive')
elif num < 0:
    print('The number is negative')
else:
    print('The number is zero')
```

### 代码块嵌套

我们也可以将`if`语句放在其他`if`语句块中：

```python
name = input('What is your name? ')

if name.endswith('Kaindy'):
    if name.startswith('Mr.'):
        print('Hello, Mr. Kaindy')
    elif name.startswith('Mrs.'):
        print('Hello, Mrs. Kaindy')
    else:
        print('Hello, Kaindy')
else:
    print('Hello, stranger')
```

### 更复杂的条件

#### 比较运算符

在条件表达式中，最基本的运算符可能是比较运算符，它们用于执行比较：

| 表达式 | 描述 |
| ----- | --- |
| `x == y` | x等于y |
| `x < y` | x小于y |
| `x > y` | x大于y |
| `x >= y` | x大于等于y |
| `x <= y` | x小于等于y |
| `x != y` | x不等于y |
| `x is y` | x和y是同一对象 |
| `x is not y` | x和y不是同一对象 |
| `x in y` | x是容器(如序列)y的成员 |
| `x not in y` | x不是容器(如序列)y的成员 |

Python也支持链式比较：可同时使用多个比较运算符，如：`0 < age < 100`

需要特别注意的运算符：

##### 相等运算符

要确定两个对象是否相等，可使用比较运算符 `==`， 但不是`=`，`=`仅用于赋值。

##### 相同运算符

`is`是相同运算符，看上去与`==`很相似，但它们却完全不同：

```python
>>> x = y = [1, 2, 3]
>>> z = [1, 2, 3]
>>> x == y
True
>>> x == z
True
>>> x is y
True
>>> x is z
False
```

`x`和`y`指向同一对象列表，而`z`指向另一个列表对象，虽然它们的值都是一样的，但存储的地址不同，所以，`==`比较的是它们的值，而`is`却是比较它们是否指向同一对象。再看下面的例子：

```python
>>> x = [1, 2, 3]
>>> y = [2, 4]
>>> x is not y
True
>>> del x[2]
>>> y[1] = 1
>>> y.reverse()
>>> x == y
True
>>> x is y
False
```

很显然，`x`和`y`相等但不相同。一般，我们使用`==`来检查两个对象是否相等，而`is`用来检查两个对象是否相同(是同一个对象)

##### `in`：成员资格运算符

`in`与其他运算符一样，也可以用于条件表达式中：

```python
name = input('What is your name? ')
if 's' in name:
    print('Your name contains the letter "s".')
else:
    print('Your name does not contain the letter "s".')
```

##### 字符串和序列的比较

字符串是根据字符的字母排列顺序进行比较的，但字母都是Unicode字符，它们是按码点排列的。

```python
>>> 'alpha' < 'beta'
True
```

我们可以使用函数`ord`来获取码点，它与`chr`函数正好相反。

再排序比较时遇到大小写字母，可能结果就和预期的不一致了，我们可以使用字符串方法`lower`来忽略大小写。

```python
>>> 'a' < 'B'
False
>>> 'a'.lower() < 'B'.lower()
True
>>> 'FnOrD'.lower() == 'Fnord'.lower()
True
```

#### 布尔运算符

运算符`and`是一个布尔运算符，它接受两个真值，并在这两个值都为真时返回真，否则返回假

```python
number = int(input('Enter a number between 1 and 10: '))
if number <= 10 and number >= 1:
    print('Great!')
else:
    print('Wrong!')
```

另外还有两个布尔运算符：`or`和`not`

```python
if ((cash > price) or customer_has_good_credit) and not out_of_stock:
    give_goods()
```

在`x and y`这样的布尔运算中，如果`x`为假，则表达式直接返回假，而不会去对y求值，这种行为称为短路逻辑(或延迟求值):布尔运算符常被称为逻辑运算符。

### 断言

我们可以在表达式中使用关键字：`assert`，来断言输出是否满足条件，如果必须满足特定条件，程序才能正确执行，那就可添加`assert`语句充当检查点

```python
>>> age = 10
>>> assert 0 < age < 100
>>> age = -1
>>> assert 0 < age < 100
Traceback (most recent call last):
  File "<pyshell#22>", line 1, in <module>
    assert 0 < age < 100
AssertionError
```

还可以在条件后面添加一个字符串，对断言做出说明：

```python
>>> age = -1
>>> assert 0 < age < 100, 'The age must be relaistic'
Traceback (most recent call last):
  File "<pyshell#24>", line 1, in <module>
    assert 0 < age < 100, 'The age must be relaistic'
AssertionError: The age must be relaistic
```

## 循环

### while循环

Python使用`while`关键字实现循环操作:

```python
>>> x = 1
>>> while x <= 100:
	print(x)
	x += 1
```

下面的例子用来确保用户一定会输入名字：

```python
yourname = ''
while not yourname:
    yourname = raw_input('Please enter your name: ')
print('Hello, {}!'.format(yourname))
```

思考一下上面的例子，如果输入一个空格呢？在Python中，一个空格也是字符，所以这个空格就作为你输入的名字了，这显然不合理，我们可以稍微改动一下代码：

```python
yourname = ''
while not yourname or yourname.isspace():
    yourname = raw_input('Please enter your name: ')
print('Hello, {}!'.format(yourname))
```

又或者可以将`while not yourname or yourname.isspace()`改为`while not yourname.strip()`

### for循环

`while`循环可用于在条件为真时反复执行代码块，但有时我们想要定制这样的循环次数，比如迭代序列，为此可使用`for`语句：

```python
>>> words = ['this', 'is', 'an', 'ex', 'parrot']
>>> for word in words:
	print(word)

this
is
an
ex
parrot
```

鉴于迭代(遍历)特定范围内的数是一种常见的操作任务，Python提供了一个创建范围的内置函数`range`

```python
>>> range(0, 10)
range(0, 10)
>>> list(range(0, 10))
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

如果提供给函数`range`的参数只有一个数字，那么这个数字将被视为结束位置，且起始位置为0。

```python
>>> range(10)
range(0, 10)
```

```python
>>> for number in range(1, 101):
	print(number)
```

提示：只要能使用`for`循环，就不要使用`while`循环。

### 迭代字典

要遍历字典的所有关键字，可像遍历序列那样使用普通的`for`语句：

```python
>>> d = {'x': 1, 'y': 2, 'z': 3}
>>> for key in d:
	print(key, 'corresponds to', d[key])

x corresponds to 1
y corresponds to 2
z corresponds to 3
```

我们可以使用`keys`方法来获取所有的键，`items()`方法以元组的方式返回所有的键值对，在使用`for`遍历字典时，还可以使用序列解包

```python
>>> for key, value in d.items():
	print(key, ' - ', value)

x  -  1
y  -  2
z  -  3
```

### 一些迭代工具

Python提供了多个可帮助迭代序列(或其他科迭代对象)的函数。

#### 并行迭代

有时候，我们可能想要同时迭代两个序列。下面有两个列表：

```python
>>> names = ['anne', 'beth', 'george', 'damon']
>>> ages = [12, 45, 32, 102]
```

如果要打印名字和对应的年龄，我们可以这样做：

```python
>>> for i in range(len(names)):
	print(names[i], 'is', ages[i], 'years old')
```

Python为我们提供了并行迭代工具函数是`zip`，它将两个序列"缝合"起来，并返回一个由元组组成的序列，返回值是一个可迭代对象。

```python
>>> list(zip(names, ages))
[('anne', 12), ('beth', 45), ('george', 32), ('damon', 102)]
```

再使用`zip`之后，可在循环中将元组解包：

```python
>>> for name, age in zip(names, ages):
	print(name, 'is', age, 'years old')
```

函数`zip`可用于"缝合"任意数量的序列，当序列的长度不同时，它将在最短的序列用完后停止"缝合".

```python
>>> list(zip(range(5), range(1000)))
[(0, 0), (1, 1), (2, 2), (3, 3), (4, 4)]
```

#### 迭代时获取索引

我们在迭代对象序列时可能想获取当前对象的索引，比如，我们想替换字符串列表中的某些子串，可以像这样做：

```python
>>> strings = ['abc', '123', 'xxx2', 'kaindy']
>>> for string in strings:
	if 'xxx' in string:
		index = strings.index(string)
		strings[index] = 'censored'
```

这样的方案可行，但前面的搜索好像有点多余，我么还可以像下面这样做：

```python
>>> index = 0
>>> for string in strings:
	if 'xxx' in string:
		strings[index] = 'censored'
	index += 1
```

上面的方法虽然可以接受，但太笨拙，另一种解决方案是使用Python的内置函数：`enumerate`

```python
>>> for index, string in enumerate(strings):
	if 'xxx' in string:
		strings[index] = 'censored'
```

函数`enumerate`能让你迭代索引值对，其中的索引是自动提供的。

#### 反向迭代和排序后再迭代

函数`reversed`和`sorted`，类似于列表方法`reverse`和`sort`，它们可用于任何序列或可迭代对象，且不会就地修改对象，而是返回反转和排序后的版本。

```python
>>> sorted([4, 3, 6, 8, 3])
[3, 3, 4, 6, 8]
>>> sorted('Hello, world!')
[' ', '!', ',', 'H', 'd', 'e', 'l', 'l', 'l', 'o', 'o', 'r', 'w']
>>> list(reversed('Hello, world!'))
['!', 'd', 'l', 'r', 'o', 'w', ' ', ',', 'o', 'l', 'l', 'e', 'H']
>>> ''.join(reversed('Hello, world!'))
'!dlrow ,olleH'
```

### 跳出循环

在某些情况下，你可能想要中断正在执行的循环，开始新迭代，或直接结束循环

#### break

要结束(跳出)循环，可以使用`break`关键字。假设你要找出小于100的最大平方值，可以从100开始向下迭代，当找到一个值后，则无需再迭代，而直接跳出循环。

```python
>>> from math import sqrt
>>> for n in range(99, 0, -1):
	root = sqrt(n)
	if root == int(root):
		print(n)
		break
```

#### continue

`continue`可结束当前迭代，并跳到下一次迭代的开始。

```python
for x in seq:
    if condition1: continue
    if condition2: continue
    if condition3: continue

    do_something()
    do_something_else()
    do_another_thing()
    etc()
```

#### while True/break成例

当我们希望在用户没有根据提示输入内容时就跳出循环时，使用`while True/break`是非常方便的：

```python
>> while True:
	word = input('Please enter a word: ')
	if not word: break
	print('The word was ', word)
```

当我们输入某些字符后，程序会自动打印，并继续要求用户输入，而如果没有输入直接回车，则循环结束。

### 循环中的else语句

如果想在循环没有结果时做一些事，可使用`else`，比如上面的找最大平方值的例子，我们把范围改为99-81，则找不到最后结果：

```python
>>> for n in range(99, 81, -1):
	root = sqrt(n)
	if root == int(root):
		print(n)
		break
else:
	print('Didn\'t find it!')
```

## 简单推导

列表推导是一种从其他列表创建列表的方式，类似于数学中的集合推导，列表推导的原理有点像`for`循环

```python
>>> [x * x for x in range(10)]
[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```

如果我们只想要那些能被3整除的平方值，可以加上`if`语句

```python
>>> [x * x for x in range(10) if x % 3 == 0]
[0, 9, 36, 81]
```

## 三人行：pass、del和exec

### 什么都不做

在Python中使用`pass`表示什么都不做，比如像下面的示例：

```python
if name == 'Ralph Auldus Melish':
    print('Welcome')
elif name == 'Enid':
    # 还未完成
elif name == 'Bill Gates':
    print('Access Denied')
```

上面的代码是不能运行的，因为在Python中代码块不能为空，要修复这个问题，只需加入`pass`即可：

```python
if name == 'Ralph Auldus Melish':
    print('Welcome')
elif name == 'Enid':
    # 还未完成
    pass
elif name == 'Bill Gates':
    print('Access Denied')
```

### 使用del删除

在Python中，对于没有任何变量与之关联的对象，将会被解释器直接删除，这称为垃圾收集。另一个是使用`del`语句，它会删除当前变量名称

```python
>>> x = 1
>>> del x
>>> x
Traceback (most recent call last):
  File "<pyshell#96>", line 1, in <module>
    x
NameError: name 'x' is not defined
```

对于多个变量都指向同一对象的情况，当删除其中一个变量时，只删除了其名称，而对应的对象还是存在的。

```python
>>> x = ['Hello', 'world']
>>> y = x
>>> del x
>>> y
['Hello', 'world']
```

对于内存中不再使用的值，我们大可不必关心，因为Python解释器会自动帮我们删除它们。

### 使用exec和eval执行字符串及计算其结果

#### exec

函数`exec`可以将字符串当做代码来执行：

```python
>>> exec('print("Hello, world!")')
Hello, world!
```

然后调用函数`exec`时只给它提供一个字符串参数是不安全的，在大多数情况下，我们应该为它传递一个命名空间，即用于放置变量的地方，否则代码将污染你的命名空间：

```python
>>> from math import sqrt
>>> exec('sqrt = 1')
>>> sqrt(4)
Traceback (most recent call last):
  File "<pyshell#100>", line 1, in <module>
    sqrt(4)
TypeError: 'int' object is not callable
```

函数`exec`主要用于动态的创建代码字符串，如果这个代码字符串来自用户，则无法确定它包含什么内容，因此为了安全，需要提供一个字典以充当命名空间。

```python
>>> from math import sqrt
>>> scope = {}
>>> exec('sqrt = 1', scope)
>>> sqrt(4)
2.0
>>> scope['sqrt']
1
```

#### eval

`eval`也是Python内置函数，`exec`执行一系列的Python语句，而`eval`计算用字符串表示的Python表达式的值，并返回结果(`exec`什么都不返回):

```python
>>> eval(input('Enter an arithmetic expression: '))
Enter an arithmetic expression: 6 + 18 * 2
42
```

与`exec`一样，我们也可以给`eval`提供一个命名空间

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
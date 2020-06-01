# Python之旅：第六章 抽象

## 懒惰是一种美德

当我们需要编写大型程序时，通常会将重复使用的部分抽象出来，比如，如果我们需要计算斐波那契数列(一种数列，其中每个数都是前面两个数的和),可以像下面这样：

```python
>>> fibs = [0, 1]
>>> for i in range(8):
	fibs.append(fibs[-2] + fibs[-1])

>>> fibs
[0, 1, 1, 2, 3, 5, 8, 13, 21, 34]
```

其实一般我们会将计算抽象成一个函数，比如`fibs`，这样我们就可以在程序任意地方进行调用：

```python
num = input('How many numbers do you want?' )
print(fibs(num))
```

## 抽象和结构

抽象是程序能被人理解的关键所在，无论是编写程序还是阅读程序。组织计算机程序时，我们采取的方式应该是非常抽象的。比如下载网页，计算使用频率，打印每个单词的使用频率，可以用下面的伪代码表示：

```python
page = download_page()
freqs = compute_frequencies(page)
for word, freq in freqs:
    print(word, freq)
```

## 自定义函数

函数执行特定的操作并返回一个值(有些函数并不会返回任何值),你可以调用它，并可能会提供一些参数。一般而言，要判断某个对象是否可调用，可以使用内置函数`callable`

```python
>>> import math
>>> x = 1
>>> y = math.sqrt
>>> callable(x)
False
>>> callable(y)
True
```

函数是结构化编程的核心，在Python中，使用`def`关键字来定义函数

```python
def hello(name):
    return 'Hello, ' + name + '!'
```

自定义函数生成后，返回一个字符串，我们可以像使用内置函数一样使用它们

```python
>>> print(hello('world'))
Hello, world!
>>> print(hello('Gumby'))
Hello, Gumby
```

现在我们来自定义函数计算斐波那契数列：

```python
>>> def fibs(num):
	  result = [0, 1]
	  for i in range(num - 2):
		    result.append(result[-2] + result[-1])
	  return result
```

参数`num`由用户的输入决定：

```python
>>> fibs(10)
[0, 1, 1, 2, 3, 5, 8, 13, 21, 34]
>>> fibs(15)
[0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, 233, 377]
```

### 给函数编写文档

一般我们可以添加注释(以`#`打头的内容),来为函数编写说明文档。另外还有一种编写注释的方式，就是添加独立的字符串。放在函数开头的字符串称为**文档字符串**，它将作为函数的一部分被存储起来。

```python
>>> def square(x):
	  'Calculates the square of the number x.'
	  return x * x
```

我们可以像下面这样访问文档字符串：

```python
>>> square.__doc__
'Calculates the square of the number x.'
```

我们也可以使用内置函数`help`，在交互式解释器中，可使用它来获取函数有关的信息，其中包含函数的文档字符串。

```python
>>> help(square)
Help on function square in module __main__:

square(x)
    Calculates the square of the number x.
```

### 其实并不是函数的函数

在Python中，有些函数什么都不会返回，这些函数不包含`return`语句，或者包含`return`语句，只是`return`后面没有任何值，这类`return`的作用就是为了结束函数。

```python
def test():
    print('This is printed')
    return
    print('This is not')
```

执行`test`并赋值给变量`x`

```python
>>> x = test()
This is printed
```

函数`test`什么都不返回，那么`x`的值是什么呢？什么都没有，或者说是`None`

```python
>>> x
>>>

>>> print(x)
None
```

由此可见，所有的函数都会返回值，如果没有指定返回值，那么它就返回`None`

## 参数魔法

### 值从哪里来

编写函数的目的是为当前程序或其他程序提供服务，我们只要确保它在提供的参数正确时完成任务，并在参数不对时显式的提供失败(通常使用断言或异常)。

在`def`语句中，位于函数名后面的变量通常称为形参，而调用函数时提供的值称为实参。

### 我能修改参数吗

如果在函数内部修改参数，这对外部没有任何影响。

```python
>>> def try_to_change(n):
	      n = 'Mr. Gumby'

>>> name = 'Mrs.ENtity'
>>> try_to_change(name)
>>> name
'Mrs.ENtity'
```

字符串(以及数和元组)是不可变的(immutable)，这意味着你不能修改它们(只能替换为新值)。但如果参数是一个可变的数据结构呢？

```python
def change(n):
    n[0] = 'Mr.Gumby'

>>> names = ['Mrs.Entity', 'Mrs.Thing']
>>> change(names)
names
['Mr.Gumby', 'Mrs.Thing']
```

可以看到，原来的列表被修改了，为了原始数据不被修改，我们可以使用切片来产生一个参数的副本，对副本对象进行操作不会影响原参数

```python
>>> change(names[:])
>>> names
['Mrs.Entity', 'Mrs.Thing']
```

#### 为何要修改参数

抽象的关键在于隐藏所有的更新细节，在编写大型程序时尤为重要，我们可以使用函数将细节隐藏起来，仅返回结果。比如我们要编写一个存储人名的程序：

首先，我们写一个`init`函数，来初始化一个字典，这个字典将存储人名

```python
>> def init(data):
	  data['first'] = {}
	  data['middle'] = {}
  	data['last'] = {}

>>> storage = {}
>>> init(storage)
>>> sotrage
{'first': {}, 'middle': {}, 'last': {}}
```

下面我们来编写获取人员姓名的函数`lookup`

```python
def lookup(data, label, name):
    return data[label].get(name)
```

显然，如果`storage`中已存储了人员姓名，我们可以像这样调用函数`lookup`获取：

```python
>>> lookup(storage, 'middle', 'Lie')
['Magnus Lie Hetland']
```

下面我们来编写存储人名的函数：

```python
def store(data, full_name):
    names = full_name.split()
    if len(names) == 2: names.insert(1, '')
    labels = 'first', 'middle', 'last'

    for label, name in zip(labels, names):
        people = lookup(data, label, name)
        if people:
            people.append(full_name)
        else:
            data[label][name] = [full_name]
```

#### 如果参数是不可变的

在Python中，是无法修改参数的值，而影响函数外部的变量。更清晰的做法是返回修改后的值。

### 关键字参数和默认值

前面讲的参数都是**位置参数**，它们的位置是固定的，为了简化调用，我们可以为参数指定名称。

```python
# 定义函数
def hello_1(greeting, name):
    print('{}, {}!'.format(greeting, name))

# 调用并为参数指定名称
>>> hello_1(greeting='Hello', name='world')
Hello, world!
```

参数的顺序就无关紧要了，但名称很重要：

```python
>>> hello_1(name='world', greeting='Hello')
Hello, world!
```

像这样使用名称指定的参数称为**关键字参数**，它主要的优点是有助于澄清各个参数的作用，还有就是你可以为参数指定默认值：

```python
>>> def hello_1(greeting='Hello', name='world'):
	print('{}, {}!'.format(greeting, name))

>>> hello_1()
Hello, world!
```

像这样给参数指定默认值后，调用函数就可以不提供它，也可以根据需要，提供部分参数。

我们也可以结合使用位置参数和关键字参数，但必须先指定所有的位置参数，否则解释器不知道它们是哪个参数。

通常而言，我们不应该结合使用位置参数和关键字参数，例如下面的例子，函数`hello`可能要求必须指定姓名，而问候语和标点是可选的。

```python
>>> def hello(name, greeting='Hello', punctuation='!'):
	      print('{}, {}{}'.format(greeting, name, punctuation))
```

可以像下面这样调用：

```python
>>> hello('Mars')
Hello, Mars!
>>> hello('Mars', 'Howdy')
Howdy, Mars!
```

### 收集参数

我们可以在定义函数时，在某个形参的前面加上星号`*`，表示收集多余的实参

```python
def print_parmas(*params):
    print(params)

# 调用
>>> print_params('Testing')
('Testing',)
```

如果形参前面加上了星号，则参数会以元组的方式返回。

```python
>>> print_params(1, 2, 3)
(1, 2, 3)
```

参数前面的星号将提供的所有值都放在一个元组中，也就是将这些值收集起来，那如果有多余的参数呢？

```python
def print_params(title, *params):
    print(title)
    print(params)

>>> print_params('Params:', 1, 2, 3)
Params:
(1, 2, 3)
```

如上面的例子看出，星号意味着收集余下的位置参数，如果没有可供收集的参数，params将是一个空元组

带星号的参数也可以放在其他位置，而不是最后，但不同的是，必须使用名称来指定后续参数

```python
def in_the_middle(x, *y, z):
    print(x, y, z)

>>> in_the_middle(1, 2, 3, 4, 5, z=7)
1 (2, 3, 4, 5), 7
```

星号(`*`)不会收集关键字参数，要想收集关键字参数，可以使用两个星号(`**`)

```python
def print_params(**params):
    print(params)

>>> print_params(x=1, y=2, z=3)
{'x': 1, 'y': 2, 'z': 3}
```

如上，最后得到的参数是一个字典，而不是元组

### 分配参数

前面介绍的是使用两个运算符(`*`和`**`),来收集参数到元组和字典中，我们也可以使用它们来做相反的操作，这个相反的操作就是**分配参数**，通过在调用函数时(而不是定义函数时)使用运算符`*`来实现：

```python
def add(x, y):
    return x + y

>>> params = (1, 2)
>>> add(*params)
3
```

通过运算符`**`，可将字典中的值分配个关键字参数：

```python
>> def hello(greeting='Hello', name='world'):
	      print('{}, {}!'.format(greeting, name))
  
>>> params = {'name': 'Sir Robin', 'greeting': 'Well met'}	      
>>> hello(**params)
Well met, Sir Robin!
```

### 练习使用参数

下面我们来做一些实例，定义一些函数并使用它们：

```python
def story(**kwds):
    return 'Once upon a time, there was a ' \
           '{job} called {name}.'.format_map(kwds)

def power(x, y, *others):
    if others:
        print('Received redundant parameters:', others)
    return pow(x, y)

def interval(start, stop=None, step=1):
    'Imitates range() for step > 0'
    if stop is None:                    # 如果没有给参数stop指定值
        start, stop = 0, start          # 就调整参数start和stop的值
    result = []

    i = start                           # 从start开始往上数
    while i < stop:                     # 数到stop的位置
        result.append(i)                # 将当前数加入到result的末尾
        i += step
    return result
```

```python
>>> print(story(job='king', name='Gumby'))
Once upon a time, there was a king called Gumby.
>>> print(story(name='Sir Robin', job='brave knight'))
Once upon a time, there was a brave knight called Sir Robin.
>>> params = {'job': 'language', 'name': 'Python'}
>>> print(story(**params))
Once upon a time, there was a language called Python.
>>> del params['job']
>>> print(story(job='stroke of genius', **params))
Once upon a time, there was a stroke of genius called Python.
>>> power(2, 3)
8
>>> power(3, 2)
9
>>> power(y=3, x=2)
8
>>> params = (5,) * 2
>>> power(*params)
3125
>>> power(3, 3, 'Hello, world')
Received redundant parameters: ('Hello, world',)
27
>> interval(10)
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
>>> interval(1, 5)
[1, 2, 3, 4]
>>> interval(3, 12, 4)
[3, 7, 11]
>>> power(*interval(3, 7))
Received redundant parameters: (5, 6)
81
```

## 作用域

我们可以将变量视为指向值的名称，例如执行`x = 1`，则名称`x`指向值`1`,这与字典很相似。我们可以使用内置函数`vars()`来返回这个看不见的字典。

```python
>>> x = 1
>>> scope = vars()
>>> scope['x']
1
>>> scope['x'] += 1
>>> x
2
```

在Python中，不应该修改内置函数`vars()`返回的字典，这可能带来意想不到的结果。

这种'看不见的字典'称为**命名空间**或**作用域**，除全局作用域外，每个函数调用都会创建一个。

```python
>>> def foo(): x = 42
...
>>> x = 1
>>> foo()
>>> x
1
```

从上面的例子可以看出，函数`foo`的调用会创建一个局部空间，`foo`函数中的变量`x`只在这个局部空间有效，而不会影响全局空间中的`x`。这种在函数内部使用的变量称为**局部变量**，参数类似于局部变量。

```python
>>> def output(x): print(x)
...
>>> x = 1
>>> y = 2
>>> output(y)
2
```

但如果我们要访问全局变量呢？如果仅仅是访问，而不是重新关联它，通常是不会有问题的：

```python
>>> def combine(parameter): print(parameter + external)
...
>>> external = 'berry'
>>> combine('Shrub')
Shrubberry
```

这样访问全局变量其实并不是好的做法，通常会导致许多未知的BUG。

下面我们来讨论两个关于作用域的问题：遮盖和作用域嵌套。

### "遮盖"的问题

当我们在函数内部读取全局变量时，恰好函数内部变量与此全局变量同名，就会出现全局变量被局部变量"遮盖"的问题。所以，如果需要在函数内部访问全局变量，请使用函数`globals`，它类似于`vars`，返回一个包含全局变量的字典。(`local`返回一个包含局部变量的字典)

```python
>>> def combine(parameter):
        print(parameter + globals()['parameter'])
...
>>> parameter = 'berry'
>>> combine('Shrub')
Shrubberry
```

另外，如果我们需要在函数内部修改全局变量，可以使用`global`关键字来告诉Python，我调用的是全局变量：

```python
>>> x = 1
>>> def change_global():
...     global x
...     x = x + 1
...
>>> change_global()
>>> x
2
```

### 作用域嵌套

Python函数可以嵌套，即可将一个函数放在另一个函数内。

```python
>>> def foo():
...     def bar():
...         print('Hello, world!')
...     bar()
```

嵌套的作用就是使用一个函数来创建另一个函数,下面的例子就是返回一个函数

```python
>>> def multiplier(factor):
...     def multiplyByFactor(number):
...         return number * factor
...     return multiplyByFactor
```

在上面的例子中，一个函数位于另一个函数中，且外面的函数返回里面的函数，也就是返回一个函数，而不是调用它。且返回的函数能访问其所在的作用域，也就是它会携带自己所在的上下文环境。这样的存储其所在作用域的函数称为**闭包**

在闭包中，内部函数通常不能给外部作用域中的变量赋值，如果一定要做，可以使用关键字`nonlocal`。

## 递归

函数可以调用其他的函数，当然它也可以调用自己，我们称这为**递归**，递归意味着函数引用了自身。

### 两个经典案例：阶乘和幂

我们来讨论下两个经典的递归应用场景，首先是阶乘，假设我们要计算`n`的阶乘，那么就是`n x (n - 1) x (n - 2) x ... x 1`,我们可以使用循环来实现：

```python
>>> def factorial(n):
	  result = n
	  for i in range(1, n):
		    result *= i
	  return result
```

在数学中，如何来定义阶乘的概念呢？

- 1的阶乘为1
- 对于大于1的数字`n`,其阶乘为`n - 1`的阶乘再乘以`n`.

OK，有了定义，我们就可以使用递归来解决这个问题：

```python
>>> def factorial(n):
	      if n == 1:
		        return 1
	      else:
		        return n * factorial(n - 1)
```

下面我们再来看下幂运算，它的一个简单定义是：`power(x, n)`(`x`的`n`次幂)是将数字`x`自乘`n - 1`次的结果，我们先用循环来解决：

```python
>>> def power(x, n):
	      result = 1
	      for i in range(n):
		        result *= x
	      return result
```

我们来将它修改为递归式的：

- 对于任何数字`x`，`power(x, 0)`都为1
- 当`n > 0`时，`power(x, n)`为`power(x, n - 1)`与`x`的乘积

```python
>>> def power(x, n):
	      if n == 0:
		        return 1
	      else:
		        return x * power(x, n - 1)
```

那么递归有什么作用呢？我们可以看到，使用循环同样能完成需求，且使用循环的效率会更高，但大多数情况下，使用递归的可读性更高，特别是对于复杂的算法。

### 另一个经典案例：二分查找

下面我们来讨论一个递归实例：**二分查找算法**

假如，我们玩猜数字的游戏，对方心里想一个1 ~ 100之间的数，让我们去猜。当然，猜100次肯定能对，但问题是我们最少需要多少次呢？

实际上我们只需要7次，首先问："这个数字大于50吗？",如果答案是肯定，接着问："这个数大于75吗？"，就这样不断的将数字区间减半，直到猜对为止。

如果我们使用递归的方式来解决这个问题，首先要明确解决的定义：

- 如果上限和下限相同，就说明他们都指向数字所在的位置，因此可将这个数字直接返回
- 否则，找出区间的中间位置(上限和下限的平均值)，再确定数字在左边部分还是右半部分，然后再继续在数字所在的那部分查找。

```python
def search(sequence, number, lower, upper):
	  if lower == upper:
		    assert number == sequence[upper]
		    return upper
	  else:
		    middle = (lower + upper) // 2
		    if number > sequence[middle]:
			      return search(sequence, number, middle + 1, upper)
		    else:
			      return search(sequence, number, lower, middle)
```

我们还可以将`lower`和`upper`参数设置为可选：

```python
def search(sequence, number, lower=0, upper=None):
    ...
```

其实使用`index`内置函数一样能做到，而且更简单，但如果我们遇到很大的列表需要查找，上面的递归方式的效率就会更高。

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
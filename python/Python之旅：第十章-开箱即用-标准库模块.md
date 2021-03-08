<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Python之旅：第十章 开箱即用-标准库模块](#python%E4%B9%8B%E6%97%85%E7%AC%AC%E5%8D%81%E7%AB%A0-%E5%BC%80%E7%AE%B1%E5%8D%B3%E7%94%A8-%E6%A0%87%E5%87%86%E5%BA%93%E6%A8%A1%E5%9D%97)
  - [模块](#%E6%A8%A1%E5%9D%97)
    - [模块就是程序](#%E6%A8%A1%E5%9D%97%E5%B0%B1%E6%98%AF%E7%A8%8B%E5%BA%8F)
    - [模块是用来下定义的](#%E6%A8%A1%E5%9D%97%E6%98%AF%E7%94%A8%E6%9D%A5%E4%B8%8B%E5%AE%9A%E4%B9%89%E7%9A%84)
      - [在模块中定义函数](#%E5%9C%A8%E6%A8%A1%E5%9D%97%E4%B8%AD%E5%AE%9A%E4%B9%89%E5%87%BD%E6%95%B0)
      - [在模块中添加测试代码](#%E5%9C%A8%E6%A8%A1%E5%9D%97%E4%B8%AD%E6%B7%BB%E5%8A%A0%E6%B5%8B%E8%AF%95%E4%BB%A3%E7%A0%81)
    - [让模块可用](#%E8%AE%A9%E6%A8%A1%E5%9D%97%E5%8F%AF%E7%94%A8)
      - [将模块放在正确的位置](#%E5%B0%86%E6%A8%A1%E5%9D%97%E6%94%BE%E5%9C%A8%E6%AD%A3%E7%A1%AE%E7%9A%84%E4%BD%8D%E7%BD%AE)
      - [告诉解释器到哪里去查找](#%E5%91%8A%E8%AF%89%E8%A7%A3%E9%87%8A%E5%99%A8%E5%88%B0%E5%93%AA%E9%87%8C%E5%8E%BB%E6%9F%A5%E6%89%BE)
    - [包](#%E5%8C%85)
  - [探索模块](#%E6%8E%A2%E7%B4%A2%E6%A8%A1%E5%9D%97)
    - [模块包含什么](#%E6%A8%A1%E5%9D%97%E5%8C%85%E5%90%AB%E4%BB%80%E4%B9%88)
        - [使用`dir`](#%E4%BD%BF%E7%94%A8dir)
      - [变量`__all__`](#%E5%8F%98%E9%87%8F__all__)
    - [使用`help`获取帮助](#%E4%BD%BF%E7%94%A8help%E8%8E%B7%E5%8F%96%E5%B8%AE%E5%8A%A9)
    - [文档](#%E6%96%87%E6%A1%A3)
    - [使用源代码](#%E4%BD%BF%E7%94%A8%E6%BA%90%E4%BB%A3%E7%A0%81)
  - [标准库：一些深受欢迎的模块](#%E6%A0%87%E5%87%86%E5%BA%93%E4%B8%80%E4%BA%9B%E6%B7%B1%E5%8F%97%E6%AC%A2%E8%BF%8E%E7%9A%84%E6%A8%A1%E5%9D%97)
    - [sys](#sys)
    - [os](#os)
    - [fileinput](#fileinput)
    - [集合、堆和双端队列](#%E9%9B%86%E5%90%88%E5%A0%86%E5%92%8C%E5%8F%8C%E7%AB%AF%E9%98%9F%E5%88%97)
      - [集合](#%E9%9B%86%E5%90%88)
      - [堆](#%E5%A0%86)
      - [双端队列](#%E5%8F%8C%E7%AB%AF%E9%98%9F%E5%88%97)
    - [time](#time)
    - [random](#random)
    - [shelve和json](#shelve%E5%92%8Cjson)
    - [re](#re)
      - [正则表达式是什么](#%E6%AD%A3%E5%88%99%E8%A1%A8%E8%BE%BE%E5%BC%8F%E6%98%AF%E4%BB%80%E4%B9%88)
        - [通配符](#%E9%80%9A%E9%85%8D%E7%AC%A6)
        - [对特殊字符进行转义](#%E5%AF%B9%E7%89%B9%E6%AE%8A%E5%AD%97%E7%AC%A6%E8%BF%9B%E8%A1%8C%E8%BD%AC%E4%B9%89)
        - [字符集](#%E5%AD%97%E7%AC%A6%E9%9B%86)
        - [二选一和子模式](#%E4%BA%8C%E9%80%89%E4%B8%80%E5%92%8C%E5%AD%90%E6%A8%A1%E5%BC%8F)
        - [可选模式和重复模式](#%E5%8F%AF%E9%80%89%E6%A8%A1%E5%BC%8F%E5%92%8C%E9%87%8D%E5%A4%8D%E6%A8%A1%E5%BC%8F)
        - [字符串的开头和末尾](#%E5%AD%97%E7%AC%A6%E4%B8%B2%E7%9A%84%E5%BC%80%E5%A4%B4%E5%92%8C%E6%9C%AB%E5%B0%BE)
      - [模块re的内容](#%E6%A8%A1%E5%9D%97re%E7%9A%84%E5%86%85%E5%AE%B9)
      - [匹配对象和编组](#%E5%8C%B9%E9%85%8D%E5%AF%B9%E8%B1%A1%E5%92%8C%E7%BC%96%E7%BB%84)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Python之旅：第十章 开箱即用-标准库模块

> Python的语言核心非常强大，同时它还提供了其他工具，标准安装时会包含一组称为**标准库**(Standard Library)的模块，比如`math`或`cmath`。

## 模块

在前面的章节中，我们已介绍过，如果使用`import`将函数从外部模块导入到程序中，比如：

```python
>>> import math
>>> math.sin(0)
0.0
```

下面我们来看看如何编写自己的模块。

### 模块就是程序

任何Python程序都可作为模块被导入。假设你编写了如下一段代码，并保存在`hello.py`中，那么`hello`将称为这个模块的名称。

```python
# hello.py
print('Hello, world!')
```

文件的存储位置也很重要，这里假设文件存储在目录`C:\python`(Windows)或`~/python`(UNIX/macOS)中。我们必须要告诉解释器到哪里去查找这个模块：

```python
>>> import sys
>>> sys.path.append('C:/python')
```

上面的代码告诉解释器，除了通常将查找的位置外，还应到目录`C:\python`中去查找这个模块，这样，我们就可以导入这个模块了：

```python
>>> import hello
hello world!
```

我这里是MacOS，所以导入过程如下：

```python
>>> import sys
>>> sys.path.append('/Users/liuzhen/python')
>>> import hello
Hello python!
```

如果我们再次导入整个模块，会发现什么都没有，这是因为模块并不是用来执行操作的，而是用于定义变量、函数或类，鉴于定义只需做一次，所以导入模块多次和导入一次的效果是相同的。

如果想要重新加载模块，可使用模块`importlib`中的`reload`函数，它接受一个参数，即要重新加载的模块，并返回它。这种操作在修改了模块后想要立即反映到程序中非常有用。

```python
>>> import importlib
>>> hello = importlib.reload(hello)
Hello, python!
```

### 模块是用来下定义的

让模块值得被创建的原因在于它们像类一样，有自己的作用域，这意味着在模块中定义的类和函数以及对其进行赋值的变量都将成为模块的属性。

#### 在模块中定义函数

我们将上面的`hello.py`改动一下：

```python
# hello2.py
def hello():
    print('Hello, Python!')
```

像这样导入并调用其函数：

```python
>>> import hello2
>>> hello2.hello()
Hello, Python
```

在模块的全局作用域内定义的名称都可以像上面那样访问。这样做的原因主要是为了**代码重用**，通过将代码放在模块中，就可以在多个程序中使用它们。要让代码可重用，请务必将其模块化，这也与抽象密切相关。

#### 在模块中添加测试代码

模块用于定义函数和类，但有些情况下，也可以添加一些测试代码来检查情况是否符合预期。

```python
# hello3.py
def hello():
    print('Hello, Python!')

# 一个测试
hello()
```

使用上面的例子，如果作为普通程序运行，是很正常的，但如果作为模块导入，也将执行测试代码，这可能不是我们想要的。因此，我们可以使用变量`__name__`来判断是否模块是作为程序运行还是被导入了另一个程序：

```python
# hello4.py

def hello():
    print('Hello, Python!')

def test():
    hello()

if __name__ == '__main__': test()
```

这样，如果模块作为程序运行，将执行函数`hello()`，而作为模块导入，会像普通模块一样。

```python
>>> import hello4
>>> hello4.hello()
Hello, Python!
```

我们可以调用`test`方法来进行测试：

```python
>>> hello4.test()
Hello, Python!
```

**注意**：如果要编写更详尽的测试代码，应将其放在一个独立的测试程序中，而不是主程序中。

### 让模块可用

在前面的例子中，我们将编写好的模块放在一个目录中，并向`sys.path`添加了这个目录，这样Python解释器就会去这里查找，通常，最理想的解决方案是，`sys.path`一开始就包含正确的目录，为此，有两个解决方法：

- 将模块放在正确的位置
- 告诉解释器到哪里去查找

#### 将模块放在正确的位置

这个方案很简单，只需找出Python解释器会到哪里去查找模块，然后再将文件放在这个地方即可。但有时会有权限问题，如果Python是管理员安装，那么其他用户则不能使用这些目录。我们来查找一下Python解释器会到那些地方查找模块：

```python
>>> import sys, pprint
>>> pprint.pprint(sys.path)
['',
 '/Users/liuzhen/Documents',
 '/Library/Frameworks/Python.framework/Versions/3.6/lib/python36.zip',
 '/Library/Frameworks/Python.framework/Versions/3.6/lib/python3.6',
 '/Library/Frameworks/Python.framework/Versions/3.6/lib/python3.6/lib-dynload',
 '/Library/Frameworks/Python.framework/Versions/3.6/lib/python3.6/site-packages',
 '/home/liuzhen/python',
 '~/python',
 '/Users/liuzhen/python']
```

其中，`site-packages`目录是最佳的选择，如果你有使用权限，请将模块放在这里，因为它本身的作用就是用来放在模块的。

#### 告诉解释器到哪里去查找

上面的方案可能不是最佳的，原因在于：

- 不希望Python解释器的目录中充斥着自定义编写的模块
- 没有必要的权限，将无法把文件保存到Python解释器的目录中的。
- 想将模块放在其他地方。

如果要告诉解释器到哪里去查找模块，办法之一就是直接修改`sys.path`，但这种做法不常见，标准做法是将模块所在目录包含在环境变量`PYTHONPATH`中。

环境变量并不是Python解释器的一部分，而是操作系统的一部分，它类似于Python变量，但需要在Python解释器外部设置，如果你使用的是`bash shell`(大多数类UNIX系统、macOS系统或较新的Windows系统)，你就可以使用如下命令将`~/python`添加到环境变量`PYTHONPATH`的末尾：

```bash
export PYTHONPATH=$PYTHONPATH:~/python
```

可以将上面的命令包含在主目录的`.bashrc`文件中以在所有启动的shell中起作用。

### 包

为了组织模块，我们可将多个模块编组为**包**(package)。模块存储在扩展名为`.py`的文件中，而包则是一个目录。要被Python视为包，目录必须包含文件`__init__.py`。

要将模块加入包中，只需将模块文件放在包目录中即可，我们还可以在包中嵌套其他的包。例如，我们要创建一个名为`drawing`的包，其中包含模块`shapes`和`colors`：

| 文件/目录 | 描述 |
| -------- | --- |
| `~/python/` | PYTHONPATH中的目录 |
| `~/python/drawing/` | 包目录(包`drawing`) |
| `~/python/drawing/__init__.py` | 包代码(模块drawing) |
| `~/python/drawing/colors.py` | 模块`colors` |
| `~/python/drawing/shapes.py` | 模块`shapes` |

下面的导入方式都是合法的：

```python
import drawing    # 导入drawing包
import drawing.colors   # 导入drawing包中的模块colors
from drawing import shapes   # 从包drawing中导入模块shapes
```

## 探索模块

下面介绍一些查看模块的技巧。

### 模块包含什么

前面很多例子中都使用过`import`来导入模块，我们可以在Python解释器中使用它，如果没有报错，则说明模块是存在的。

```python
import copy
```

没有引发异常，`copy`模块是存在的。下面我们来看看如何探究这个模块是干什么的，里面包含了什么。

##### 使用`dir`

要查明模块包含哪些东西，可以使用函数`dir`,它列出对象的所有属性(对于模块，则列出所有的函数、类、变量等)

```python
>>> import copy
>>> dir(copy)
['Error', '__all__', '__builtins__', '__cached__', '__doc__', '__file__', '__loader__', '__name__', '__package__', '__spec__', '_copy_dispatch', '_copy_immutable', '_deepcopy_atomic', '_deepcopy_dict', '_deepcopy_dispatch', '_deepcopy_list', '_deepcopy_method', '_deepcopy_tuple', '_keep_alive', '_reconstruct', 'copy', 'deepcopy', 'dispatch_table', 'error']
```

我们看到，所有的属性都被罗列出来，有一些是下划线开头的，它们并非供外部使用，所以我们使用列表推导过滤掉它们：

```python
>>> [n for n in dir(copy) if not n.startswith('_')]
['Error', 'copy', 'deepcopy', 'dispatch_table', 'error']
```

#### 变量`__all__`

前面我们使用列表推导获取了模块`copy`对外公布的可调用的方法名称，其实可以调用其`__all__`变量来获取可调用方法列表：

```python
>>> copy.__all__
['Error', 'copy', 'deepcopy']
```

那么这个`__all__`有什么作用呢？其实它就是为了定义此模块的公有接口，如果你像下面这样导入模块，就只能获取到`__all__`对象里定义的3个方法接口：

```python
>>> from copy import *
```

但如果我们想要导入`dispatch_table`，就必须显式的指定需要导入的接口名称：

```python
>>> from copy import dispatch_table 
```

编写模块时，像这样设置`__all__`很有用，因为模块可能包含大量我们不需要的变量、函数和类，比较周全的方法就是把它们都过滤掉。

### 使用`help`获取帮助

通常，我们可以使用函数`help`来获取所有我们所需要的信息。

```python
>>> help(copy.copy)
Help on function copy in module copy:

copy(x)
    Shallow copy operation on arbitrary Python objects.
    
    See the module's __doc__ string for more info.
```

从上述信息可以看出，函数`copy`只接受一个参数，且执行的是浅复制。

上面的信息中提到了`__doc__`，文档字符串是在函数开头用来说明函数作用的。实际上，上面的信息就是从`copy`函数的文档字符串中提取的：

```python
>>> print(copy.copy.__doc__)
Shallow copy operation on arbitrary Python objects.

    See the module's __doc__ string for more info.
```

### 文档

如果在开发时想要知道某个函数的用法信息，最直接快捷的方式就是使用它的文档字符串：

```python
>>> print(range.__doc__)
range(stop) -> range object
range(start, stop[, step]) -> range object

Return an object that produces a sequence of integers from start (inclusive)
to stop (exclusive) by step.  range(i, j) produces i, i+1, i+2, ..., j-1.
start defaults to 0, and stop is omitted!  range(4) produces 0, 1, 2, 3.
These are exactly the valid indices for a list of 4 elements.
When step is given, it specifies the increment (or decrement).
```

### 使用源代码

学习编程除了要动手敲代码之外，阅读源代码就是最快捷的方式了。假设我们要阅读标准模块`copy`的代码，一种方法是像解释器那样通过`sys.path`来查找其位置，更快捷的方式是查看模块的特性`__file__`

```python
>>> print(copy.__file__)
/Library/Frameworks/Python.framework/Versions/3.6/lib/python3.6/copy.py
```

接下来我们就可以在自己的编辑器中打开它并阅读和理解。(切记不能修改它)

## 标准库：一些深受欢迎的模块

### sys

模块`sys`让你能够访问与Python解释器紧密相关的变量和函数：

| 函数/变量 | 描述 |
| ------- | ---- |
| `argv` | 命令行参数，包括脚本名 |
| `exit([arg])` | 退出当前程序，可通过可选参数指定返回值或错误信息 |
| `modules` | 一个字典，将模块名映射到加载的模块 |
| `path` | 一个列表，包含要在其中查找模块的目录的名称 |
| `platform` | 一个平台标识符，如`sunos5`或`win32` |
| `stdin` | 标准输入流：一个类似于文件的对象 |
| `stdout` | 标准输出流：一个类似于文件的对象 |
| `stderr` | 标准错误流：一个类似于文件的对象 |

```python
# 反转并打印命令行参数
# reverseargs.py

import sys
args = sys.argv[1:]
args.reverse()
print(' '.join(args))
```

运行如下：

```python
$ python reverseargs.py this is a test
test a is this
```

### os

模块`os`让你能够访问多个操作系统服务。`os`及其子模块`os.path`还包含多个查看、创建和删除目录及文件的函数，以及一些操作路径的函数。

| 函数/变量 | 描述 |
| ------- | ---- |
| `environ` | 包含环境变量的映射 |
| `system(command)` | 在子shell中执行操作系统命令 |
| `sep` | 路径中使用的分隔符 |
| `pathsep` | 分隔不同路径的分隔符 |
| `linesep` | 行分隔符('\n'、'\r'或'\r\n') |
| `urandom(n)` | 返回n个字符串的强加密随机数据 |

### fileinput

模块`fileinput`让你能迭代一系列文本文件中的所有行，如：

```python
$ python some_script.py file1.txt file2.txt file3.txt
```

| 函数 | 描述 |
| --- | --- |
| `input([files[, inplace[, backup]]])` | 帮助迭代多个输入流中的行 |
| `filename()` | 返回当前文件的名称 |
| `lineno()` | 返回当前行号(累计的) |
| `filelineno()` | 返回在当前文件中的行号 |
| `isfirstline()` | 检查当前行是否是文件中的第一行 |
| `isstdin()` | 检查最后一行是否来自`sys.stdin` |
| `nextfile()` | 关闭当前文件并移动到下一个文件 |
| `close()` | 关闭序列 |

### 集合、堆和双端队列

Python支持一些常用的数据结构，比如其中的字典(散列表)和列表(动态数组)。有一些就不那么重要了，不过也有其应用场景。

#### 集合

在老版本的Python中，集合是由模块`sets`中的`Set`类实现的，新版本中，集合是由内置类`set`实现的，这意味着我们可以直接创建集合，而无需导入模块`sets`

```python
>>> set(range(10))
{0, 1, 2, 3, 4, 5, 6, 7, 8, 9}
```

可以使用序列或其他可迭代对象来创建集合，也可以使用花括号显式的指定，但不能仅使用花括号来创建集合，因为那将创建一个空字典。

```python
>>> type({})
<class 'dict'>
```

调用`set`不能提供任何参数，集合主要用于成员资格检查，因此它将忽略重复的元素。

```python
>>> {0, 1, 2, 3, 0, 1, 2, 3, 4, 5}
{0, 1, 2, 3, 4, 5}
```

与字典一样，集合中元素的排列顺序是不确定的。

```python
>>> {'fee', 'fie', 'foe'}
{'foe', 'fee', 'fie'}
```

除了成员资格检查外，还可执行各种标准集合操作，如并集和交集，要计算两个集合的并集，可对其中一个集合调用方法`union`，也可以使用按位或运算符`|`

```python
>>> a = {1, 2, 3}
>>> b = {2, 3, 4}
>>> a.union(b)
{1, 2, 3, 4}
>>> a | b
{1, 2, 3, 4}
```

还有其他的一些运算：

```python
>>> c = a & b
>>> c.issubset(a)
True
>>> c <= a
True
>>> c.issuperset(a)
False
>>> c >= a
False
>>> a.intersection(b)
{2, 3}
>>> a & b
{2, 3}
>>> a.difference(b)
{1}
>>> a - b
{1}
>>> a.symmetric_difference(b)
{1, 4}
>>> a ^ b
{1, 4}
>>> a.copy()
{1, 2, 3}
>>> a.copy() is a
False
```

集合是可变的，因此不能用作字典中的键。集合只能包含不可变的值，因此不能包含其他集合。另外，`frozenset`类型表示不可变的集合。

```python
>>> a = set()
>>> b = set()
>>> a.add(b)
Traceback (most recent call last):
  File "<pyshell#45>", line 1, in <module>
    a.add(b)
TypeError: unhashable type: 'set'
>>> a.add(frozenset(b))  # 将集合b转换为不可变集合
```

#### 堆

另一种我们要介绍的数据结构是**堆**(heap)，它是一种优先队列。优先队列让你能够以任意顺序添加对象，并随时找出(并删除)最小的元素。

实际上，Python并没有独立的堆类型，而只有一个包含一些堆操作函数的模块：`heapq`,它包含6个函数：

| 函数 | 描述 |
| --- | --- |
| `heappush(heap, x)` | 将x压入堆中 |
| `heappop(heap)` | 从堆中弹出最小的元素 |
| `heapify(heap)` | 让列表具备堆特征 |
| `heapreplace(heap, x)` | 弹出最小元素，并将x压入堆中 |
| `nlargest(n, iter)` | 返回iter中那个最大的元素 |
| `nsmallest(n, iter)` | 返回iter中n个最小的元素 |

函数`heappush`用于向堆中添加一个元素。它不能用于普通列表，而只能用于使用各种堆函数创建的列表。

```python
>>> from heapq import *
>>> from random import shuffle
>>> data = list(range(10))
>>> shuffle(data)
>>> heap = []
>>> for n in data:
	      heappush(heap, n)

>>> heap
[0, 1, 4, 3, 2, 7, 5, 9, 8, 6]
>>> heappush(heap, 0.5)
>>> heap
[0, 0.5, 4, 3, 1, 7, 5, 9, 8, 6, 2]
```

堆中的元素看起来并不是那么的随意，它也具有一些基本特征，即：位置`i`处的元素总是大于位置`i // 2`处的元素，这是底层堆算法的基础，我们称之为**堆特征**(heap property)

函数`heappop`弹出最小元素(最小元素总是位于索引0处),并确保剩余元素中最小的那个位于索引0处，以保持堆特征。

```python
>>> heap
[0, 0.5, 4, 3, 1, 7, 5, 9, 8, 6, 2]
>>> heappop(heap)
0
>>> heappop(heap)
0.5
>>> heappop(heap)
1
>>> heap
[2, 3, 4, 8, 6, 7, 5, 9]
```

函数`heapify`通过执行尽可能少的位移操作将列表变成合法的堆，如果你的堆并不是使用`heappush`创建的，应在使用`heappush`和`heappop`之前使用这个函数

```python
>>> heap2 = [5, 8, 0, 3, 6, 7, 9, 1, 4, 2]
>>> heapify(heap2)
>>> heap2
[0, 1, 5, 3, 2, 7, 9, 8, 4, 6]
```

函数`heapreplace`用的比较少，它从堆中弹出最小元素，再压入一个新元素，相比依次执行`heappush`和`heappop`，它的效率会更高。

```python
>> heap
[0, 3, 1, 4, 8, 7, 2, 6, 5, 9]
>>> heapreplace(heap, 0.5)
0
>>> heap
[0.5, 3, 1, 4, 8, 7, 2, 6, 5, 9]
>>> heapreplace(heap, 10)
0.5
>>> heap
[1, 3, 2, 4, 8, 7, 10, 6, 5, 9]
```

我们再来看看模块`heapq`中的最后两个函数`nlargest(n, iter)`和`nsmallest(n, iter)`，它们部分用于找出可迭代对象`iter`中最大和最小的n个元素，这种需求也可以通过先排序再切片来完成，但堆算法的速度更快，使用的内存更少。

#### 双端队列

如果需要按添加元素的顺序进行删除时，可使用双端队列。在模块`collections`中，包含类型`deque`以及其他几个集合类型。与集合`set`一样，双端队列也是从可迭代对象创建而来的。

```python
>>> from collections import deque
>>> q = deque(range(5))
>>> q
deque([0, 1, 2, 3, 4])
>>> q.append(5)
>>> q.appendleft(6)
>>> q
deque([6, 0, 1, 2, 3, 4, 5])
>>> q.pop()
5
>>> q.popleft()
6
>>> q.rotate(3)
>>> q
deque([2, 3, 4, 0, 1])
>>> q.rotate(-1)
>>> q
deque([3, 4, 0, 1, 2])
```

双端队列支持在队首(左端)高效的附加和弹出元素，而列表无法这样做。另外，它还可以高效的旋转元素(即将元素向右或向左移动，并在达到一端时绕到另一端)。双端队列对象还包含`extend`和`extendleft`方法。

### time

模块`time`包含用于获取当前时间、操作时间和日期、从字符串中读取日期、将日期格式化为字符串的函数。日期可以表示为实数(在UNIX中为从1970年1月1日0时其到现在的秒数)，也可以表示为包含9个整数的元组，比如，元组(2008, 1, 21, 12, 2, 56, 0, 21, 0)表示2008年1月21日12时2分56秒，星期一，2008年的第21天

| 索引 | 字段 | 值 |
| --- | ---- | --- |
| 0 | 年 | 如2000、2001等 |
| 1 | 月 | 范围1~12 |
| 2 | 日 | 范围1~31 |
| 3 | 时 | 范围0~23 |
| 4 | 分 | 范围0~59 |
| 5 | 秒 | 范围0~61 |
| 6 | 星期 | 范围0~6，其中0表示星期一 |
| 7 | 儒略日 | 范围1~366 |
| 8 | 夏令时 | 0、1或-1 |

下面的表格描述了`time`的一些重要函数

| 函数 | 描述 |
| --- | --- |
| `asctime([tuple])` | 将时间元组转换为字符串 |
| `localtime([secs])` | 将秒数转换为表示当地时间的日期元组 |
| `mktime(tuple)` | 将时间元组转换为当地时间 |
| `sleep(secs)` | 休眠secs秒 |
| `strptime(string[, format])` | 将字符串转换为时间元组 |
| `time()` | 当前时间 |

另外还有两个较新的与时间相关的模块：`datetime`和`timeit`，前者提供了日期和时间算术支持，后者可以帮助我们计算代码的执行时间。

### random

模块`random`包含生成伪随机数的函数，请注意，这里生成的数字在系统背后是可以被预测的，如果想要完全随机且不可预测的结果，应考虑使用模块`os`中的函数`urandom`，模块`random`中的`SystemRandom`类基于的功能与`urandom`类似，可提供接近于真正随机的数据。

| 函数 | 描述 |
| --- | ---- |
| `random()` | 返回一个0~1(含)的随机实数 |
| `getrandbits(n)` | 以长整数方式返回n个随机的二进制位 |
| `uniform(a, b)` | 返回一个a~b(含)的随机实数 |
| `randrange([start], stop, [step])` | 从`range(start, stop, step)`中随机选择一个数 |
| `choice(seq)` | 从序列seq中随机选择一个元素 |
| `shuffle(seq[, random])` | 就地打乱序列seq |
| `sample(seq, n)` | 从序列seq中随机选择n个值不同的元素 |

下面我们来看一些实例：

首先我们需要在2016年到2017年之间选择一个随机的日期时间并转换为本地日期时间：

```python
#!/usr/bin/env python

# 随机选择2016年~2017年之间的一个日期时间
from random import *
from time import *
data1 = (2016, 1, 1, 0, 0, 0, -1, -1, -1)
time1 = mktime(data1)
data2 = (2017, 1, 1, 0, 0, 0, -1, -1, -1)
time2 = mktime(data2)

# 获取一个随机的时间戳
random_time = uniform(time1, time2)

# 转换并打印
print(asctime(localtime(random_time)))
```

下面的示例使用`randrange`和`for`循环来实现用户定制的掷筛子：

```python
#!/usr/bin/env python

# 询问用户要掷多少个筛子和每个筛子有多少面

from random import randrange
num = int(input('How many dice? '))
sides = int(input('How many sides per die? '))

sum = 0
for i in range(num):
    sum += randrange(sides) + 1

print('The result is ', sum)
```

### shelve和json

在Python中，我们可以使用模块`shelve`来实现一个简单的数据存储。使用`shelve`中的`open`函数，将一个文件名作为参数，并返回一个`Shelf`对象，就可以用来存储数据，这个对象的操作类似于操作字典，但键必须是字符串，操作完毕后，可调用`close`关闭并保存修改。

我们来看下面一段简单的示例：

```python
>>> import shelve
>>> s = shelve.open('test.data')
>>> s
<shelve.DbfilenameShelf object at 0x112434ef0>
>>> s['x'] = ['a', 'b', 'c']
>>> s['x'] .append('d')
>>> s['x']
['a', 'b', 'c']
```

你会发现，返回的对象`s`中的`x`键下，并没有`d`这个值。这是因为`append('d')`这个操作结果并没有被存储，那如何解决呢？我们可以创建一个临时副本来存储：

```python
>>> temp = s['x']
>>> temp.append('d')
>>> s['x'] = temp
>>> s['x']
['a', 'b', 'c', 'd']
```

还有一种方法来解决这个问题，将函数`open`的参数`writeback`设置为`True`，这样，从`Shelf`对象读取或赋值给它的所有数据结构都将保存在内存中，并等待你关闭`shelf`对象时才将它们写入磁盘中。在这种情况下，你必须确保在处理完毕后将`shelf`对象关闭。

下面来看一个模拟简单数据库的例子：

```python
#!/usr/bin/env python
# database.py

import sys, shelve

def store_person(db):
    '''
    让用户输入数据并将其存储到shelf对象中
    '''
    pid = input('Enter unique ID number: ')
    person = {}
    person['name'] = input('Enter name: ')
    person['age'] = input('Eneter age: ')
    person['phone'] = input('Enter phone number: ')
    db[pid] = person

def lookup_person(db):
    '''
    让用户输入ID和所需的字段，并从shelf对象中获取相应的数据
    '''
    pid = input('Enter ID number: ')
    field = input('What would you like to know? (name, age, phone) ')
    filed = field.strip().lower()

    print(filed.capitalize() + ':', db[pid][filed])

def print_help():
    print('The availabel commands are: ')
    print('store : Stores information about a person')
    print('lookup : Looks up a person from ID number')
    print('quit : Save changes and exit')
    print('? : Prints this message')

def enter_command():
    cmd = input('Enter command (? for help): ')
    cmd = cmd.strip().lower()
    return cmd

def main():
    database = shelve.open('./database.dat')
    try:
        while True:
            cmd = enter_command()
            if cmd == 'store':
                store_person(database)
            elif cmd == 'lookup':
                lookup_person(database)
            elif cmd == '?':
                print_help()
            elif cmd == 'quit':
                return
    finally:
        database.close()

    if name == '__main__': main()
```

### re

模块`re`提供了对正则表达式的支持。

#### 正则表达式是什么

正则表达式是可匹配文本片段的模式。最简单的正则表达式为普通字符串，与它自己匹配。

##### 通配符

正则表达式可与多个字符串匹配，你可使用特殊字符来创建这种正则表达式。例如：句点`.`与除换行符的其他字符都匹配，且只能匹配1个字符，因此正则表达式`'.ython'`与字符串`'python'`和`'jython'`都匹配。所以，句点`.`被称之为**通配符**

##### 对特殊字符进行转义

有时候我们可能想要匹配特殊字符，比如，`'python.org'`可直接使用模式`'python.org'`来匹配，但它也可以匹配`'pythonzorg'`，因为`.`可以匹配除换行符之外的所有字符，所以，我们需要对句点`.`进行转义，在需要转义的字符前面加上反斜杠即可。因此这个列子可以这样：`'python\\.org'匹配'python.org'`。这里使用了两个反斜杠，我们也可以使用原始字符串，如：`r'python\.org`

##### 字符集

我们可以用方括号将一个子串括起来，创建一个字符集，这样的字符集与其包含的字符都匹配。比如`'[pj]ython'`与`'python'`和`'jython'`都匹配，还可以使用范围，比如`'[a-z]'`与`a~z`的任何字母都匹配，也可以是多个组合，比如，`[a-zA-Z0-9]`可以匹配大写字母、小写祖母和数字。请注意，字符集只能匹配一个字符。

要指定要排除的字符集，可以在开头添加`^`字符，例如：`[^abc]`与除`a`、`b`和`c`之外的其他字符都匹配

##### 二选一和子模式

有时候，如果我们只想匹配字符串`python`和`perl`，就可以使用表示二选一的特殊字符：管道字符(`|`)，那么这个模式就为`python|perl`。然后，我们并不想把二选一用于整个模式，那么可以将这部分放在圆括号内，前面示例可以写作：`p(ython|erl)`。注意，单个字符也可以称为子模式。

##### 可选模式和重复模式

通过在子模式后面加上问号，可将其指定为可选的，即可包含可不包含。比如这个： `r'(http://)?(www\.)?python\.org`，对于这个示例，需要注意的是：

- 对句点`.`进行了转义，以防止它称为通配符
- 使用原始字符串减少反斜杠的出现
- 每个可选的子模式都放在圆括号内
- 每个可选的子模式都可以出现，也可以不出现

问号`?`表示可选的子模式可出现一次，也可不出现，下面还有几个运算符：

- `(pattern)*`：可重复0、1或多次
- `(pattern)+`：可重复1次或多次
- `(pattern){m,n}`：模式可重复m~n次

##### 字符串的开头和末尾

我们可以使用脱字符(`^`)来确定某个模式与字符串相匹配，要指定字符串末尾，可使用美元符号(`$`)

#### 模块re的内容

模块`re`包含多个使用正则表达式的函数。

| 函数 | 描述 |
| --- | ---- |
| `compile(pattern[, flags])` | 根据包含正则表达式的字符串创建模式对象 |
| `search(pattern, string[, flags])` | 在字符串中查找模式 |
| `match(pattern, string[, flags])` | 在字符串开头匹配模式 |
| `split(pattern, string[, maxsplit=0])` | 根据模式来分割字符串 |
| `findall(pattern, string)` | 返回一个列表，其中包含字符串中所有与模式匹配的子串 |
| `sub(pat, repl, string[, count=0])` | 将字符串中与模式`pat`匹配的子串都替换为`repl` |
| `escape(string)` | 对字符串中所有的正则表达式特殊字符都进行转义 |

函数`re.compile`将用字符串表示的正则表达式转换为模式对象，以提高匹配效率。调用`search`、`match`等函数时，如果提供的是用字符串表示的正则表达式，都必须在内部将它们转换为模式对象。

函数`re.search`在给定字符串中查找第一个与指定正则表达式匹配的子串。如果找到，将返回`MatchObject`(结果为真),否则返回`None`(结果为假)

```python
if re.search(pat, string):
    print('Found it!')
```

函数`re.match`尝试在给定字符串开头查找与正则表达式匹配的子串，因此`re.match('p', 'python')`返回真(`MatchObject`),而`re.match('p', 'www.python.org')`返回假(`None`)

函数`re.split`根据与模式匹配的子串来分割字符串。这个方法类似于字符串方法`split`，但这个函数能使用更多的字符来进行分割

```python
>>> some_text = 'alpha, beta,,,,gamma     dalta'
>>> re.split('[, ]+', some_text)
['alpha', 'beta', 'gamma', 'dalta']
```

它的返回值为子串列表，参数`maxsplit`则指定最多分割多少次

```python
>>> re.split('[, ]+', some_text, maxsplit=2)
['alpha', 'beta', 'gamma     dalta']
>>> re.split('[, ]+', some_text, maxsplit=1)
['alpha', 'beta,,,,gamma     dalta']
```

函数`re.findall`返回一个列表，其中包含所有与给定模式匹配的子串

```python
>>> pat = '[a-zA-Z]+'
>>> text = '"Hm... Err -- are you sure?" he said, sounding insecure.'
>>> re.findall(pat, text)
['Hm', 'Err', 'are', 'you', 'sure', 'he', 'said', 'sounding', 'insecure']
```

如果要查找所有的标点符号，可以像这样：

```python
>>> pat = r'[.?\-",]+'
>>> re.findall(pat, text)
['"', '...', '--', '?"', ',', '.']
```

函数`re.sub`从左往右将于模式匹配的子串替换为指定内容

```python
>>> pat = '{name}'
>>> text = 'Dear {name}...'
>>> re.sub(pat, 'Mr.Gumby', text)
'Dear Mr.Gumby...'
```

函数`re.escape`是一个工具函数，永不对字符串中所有可能被视为正则表达式运算符的字符进行转义。

#### 匹配对象和编组

在模块`re`中，查找与模式匹配的子串的函数都在找到时返回`MatchObject`对象。这种对象包含于模式匹配的子串的信息，还包含模式的那部分与子串的那部分匹配的信息，这些子串部分称为编组(`group`)

下面是`re`匹配对象的一些重要方法：

| 方法 | 描述 |
| --- | --- |
| `group([group1, ...])` | 获取与给定子模式(编组)匹配的子串 |
| `start([group])` | 返回与给定编组匹配的子串的起始位置 |
| `end([group])` | 返回与给定编组匹配的子串的终止位置 |
| `span([group])` | 返回与给定编组匹配的子串的起始和终止位置 |

方法`group`返回与模式中给定编组匹配的子串。如果没有指定编组号，则默认为0，如果只指定了一个编组号，将只返回一个字符串；否则返回一个元组，其中包含与给定编组匹配的子串

方法`start`返回与给定编组匹配的子串的起始索引

方法`end`类似于`start`，但返回终止索引加1

方法`span`返回一个元组，其中包含与给定编组匹配的子串的起始索引和终止索引。

```python
>>> m = re.match(r'www\.(.*)\..{3}', 'www.python.org')
>>> m.group(1)
'python'
>>> m.start(1)
4
>>> m.end(1)
10
>>> m.span(1)
(4, 10)
```

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
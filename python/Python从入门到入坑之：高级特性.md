<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [切片](#%E5%88%87%E7%89%87)
- [迭代](#%E8%BF%AD%E4%BB%A3)
- [列表生成式](#%E5%88%97%E8%A1%A8%E7%94%9F%E6%88%90%E5%BC%8F)
- [生成器](#%E7%94%9F%E6%88%90%E5%99%A8)
- [迭代器](#%E8%BF%AD%E4%BB%A3%E5%99%A8)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# 切片

在Python中，取一个 `list` 或 `tuple` 的部分元素是非常常见的操作。比如，一个 `list` 如下：

```python
>>> L = ['Michael', 'Sarah', 'Tracy', 'Bob', 'Jack']
```

取前3个元素，应该怎么做？最快想到这样做：

```python
>>> [L[0], L[1], L[2]]
['Michael', 'Sarah', 'Tracy']
```

但如果要取前4个，或者前5个呢？ 也就是取前N个元素，索引为0-(N-1)的元素，可以用循环：

```python
>>> r = []
>>> n = 3
>>> for i in range(n):
...     r.append(L[i])
... 
>>> r
['Michael', 'Sarah', 'Tracy']
```

用循环来处理指定索引范围的操作，是很繁琐的，Python提供了切片（ `Slice` ）操作符，能大大简化这种操作

对应上面的问题，取前3个元素，用一行代码就可以完成切片：

```python
>>> L[0:3]
['Michael', 'Sarah', 'Tracy']
```

`L[0:3]` 表示，从索引0开始取，直到索引3为止，但不包括索引3。即索引0，1，2，正好是3个元素。

如果第一个索引是0，还可以省略：

```python
>>> L[:3]
['Michael', 'Sarah', 'Tracy']
```

也可以从索引1开始，取出2个元素出来：

```python
>>> L[1:3]
['Sarah', 'Tracy']
```

类似的，既然Python支持 `L[-1]` 取倒数第一个元素，那么它同样支持倒数切片，试试：

```python
>>> L[-2:]
['Bob', 'Jack']
>>> L[-2:-1]
['Bob']
```

记住倒数第一个元素的索引是-1。

切片操作十分有用。我们先创建一个0-99的数列：

```python
>>> L = list(range(100))
>>> L
[0, 1, 2, 3, ..., 99]
```

可以通过切片轻松取出某一段数列。比如前10个数：

```python
>>> L[:10]
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

后10个数：

```python
>>> L[-10:]
[90, 91, 92, 93, 94, 95, 96, 97, 98, 99]
```

前11-20个数：

```python
>>> L[10:20]
[10, 11, 12, 13, 14, 15, 16, 17, 18, 19]
```

前10个数，每两个取一个：

```python
>>> L[:10:2]
[0, 2, 4, 6, 8]
```

所有数，每5个取一个：

```python
>>> L[::5]
[0, 5, 10, 15, 20, 25, 30, 35, 40, 45, 50, 55, 60, 65, 70, 75, 80, 85, 90, 95]
```

甚至什么都不写，只写[:]就可以原样复制一个list：

```python
>>> L[:]
[0, 1, 2, 3, ..., 99]
```

`tuple` 也是一种 `list`，唯一区别是 `tuple` 不可变。因此，`tuple` 也可以用切片操作，只是操作的结果仍是`tuple`：

```python
>>> (0, 1, 2, 3, 4, 5)[:3]
(0, 1, 2)
```

符串'xxx'也可以看成是一种 `list` ，每个元素就是一个字符。因此，字符串也可以用切片操作，只是操作结果仍是字符串：

```python
>>> 'ABCDEFG'[:3]
'ABC'
>>> 'ABCDEFG'[::2]
'ACEG'
```

# 迭代

如果给定一个 `list` 或 `tuple`，我们可以通过 `for` 循环来遍历这个 `list` 或 `tuple` ，这种遍历我们称为迭代（Iteration）。

在Python中，迭代是通过 `for ... in` 来完成的

Python的 `for` 循环抽象程度要高于C的 `for` 循环，因为Python的 `for` 循环不仅可以用在 `list` 或`tuple` 上，还可以作用在其他可迭代对象上

只要是可迭代对象，无论有无下标，都可以迭代，比如 `dict` 就可以迭代：

```python
>>> d = {'a': 1, 'b': 2, 'c': 3}
>>> for key in d:
...     print(key)
...
a
c
b
```

因为 `dict` 的存储不是按照 `list` 的方式顺序排列，所以，迭代出的结果顺序很可能不一样。

默认情况下，`dict` 迭代的是 `key`。如果要迭代 `value`，可以用 `for value in d.values()`，如果要同时迭代 `key` 和 `value`，可以用 `for k, v in d.items()`。

由于字符串也是可迭代对象，因此，也可以作用于 `for` 循环：

```python
>>> for ch in 'ABC':
...     print(ch)
...
A
B
C
```

所以，当我们使用 `for` 循环时，只要作用于一个可迭代对象，`for` 循环就可以正常运行，而我们不太关心该对象究竟是 `list` 还是其他数据类型。

那么，如何判断一个对象是可迭代对象呢？方法是通过 `collections` 模块的 `Iterable` 类型判断：

```python
>>> from collections import Iterable
>>> isinstance('abc', Iterable) # str是否可迭代
True
>>> isinstance([1,2,3], Iterable) # list是否可迭代
True
>>> isinstance(123, Iterable) # 整数是否可迭代
False
```

另外，Python内置的 `enumerate` 函数可以把一个 `list` 变成索引-元素对，这样就可以在 `for` 循环中同时迭代索引和元素本身：

```python
>>> for i, value in enumerate(['A', 'B', 'C']):
...     print(i, value)
...
0 A
1 B
2 C
```

上面的 `for` 循环里，同时引用了两个变量，在Python里是很常见的，比如下面的代码：

```python
>>> for x, y in [(1, 1), (2, 4), (3, 9)]:
...     print(x, y)
...
1 1
2 4
3 9
```

# 列表生成式

列表生成式即 `List Comprehensions`，是Python内置的非常简单却强大的可以用来创建 `list` 的生成式。

比如：要生成list `[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]` 可以用 `list(range(1, 11))`：

```python
>>> list(range(1, 11))
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```

但如果要生成 `[1x1, 2x2, 3x3, ..., 10x10]` 怎么做？方法一是循环：

```python
>>> L = []
>>> for x in range(1, 11):
...    L.append(x * x)
...
>>> L
[1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
```

但是循环太繁琐，而列表生成式则可以用一行语句代替循环生成上面的 `list`：

```python
>>> [x * x for x in range(1, 11)]
[1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
```

写列表生成式时，把要生成的元素 `x * x` 放到前面，后面跟 `for` 循环，就可以把 `list` 创建出来

for循环后面还可以加上if判断，这样我们就可以筛选出仅偶数的平方：

```python
>>> [x * x for x in range(1, 11) if x % 2 == 0]
[4, 16, 36, 64, 100]
```

还可以使用两层循环，可以生成全排列：

```python
>>> [m + n for m in 'ABC' for n in 'XYZ']
['AX', 'AY', 'AZ', 'BX', 'BY', 'BZ', 'CX', 'CY', 'CZ']
```

运用列表生成式，可以写出非常简洁的代码。例如，列出当前目录下的所有文件和目录名，可以通过一行代码实现：

```python
>>> import os # 导入os模块
>>> [d for d in os.listdir('.')] # os.listdir可以列出文件和目录
['.emacs.d', '.ssh', '.Trash', 'Adlm', 'Applications', 'Desktop', 'Documents', 'Downloads', 'Library', 'Movies', 'Music', 'Pictures', 'Public', 'VirtualBox VMs', 'Workspace', 'XCode']
```

`for` 循环其实可以同时使用两个甚至多个变量，比如 `dict` 的 `items()` 可以同时迭代 `key` 和 `value`：

```python
>>> d = {'x': 'A', 'y': 'B', 'z': 'C' }
>>> for k, v in d.items():
...     print(k, '=', v)
...
y = B
x = A
z = C
```

因此，列表生成式也可以使用两个变量来生成list：

```python
>>> d = {'x': 'A', 'y': 'B', 'z': 'C' }
>>> [k + '=' + v for k, v in d.items()]
['y=B', 'x=A', 'z=C']
```

最后把一个list中所有的字符串变成小写：

```python
>>> L = ['Hello', 'World', 'IBM', 'Apple']
>>> [s.lower() for s in L]
['hello', 'world', 'ibm', 'apple']
```

# 生成器

通过列表生成式，我们可以直接创建一个列表。但是，受到内存限制，列表容量肯定是有限的。而且，创建一个包含100万个元素的列表，不仅占用很大的存储空间，如果我们仅仅需要访问前面几个元素，那后面绝大多数元素占用的空间都白白浪费了。

所以，如果列表元素可以按照某种算法推算出来，那我们是否可以在循环的过程中不断推算出后续的元素呢？这样就不必创建完整的 `list` ，从而节省大量的空间。在Python中，这种一边循环一边计算的机制，称为生成器：`Generator`。

要创建一个 `generator`，有很多种方法。第一种方法很简单，只要把一个列表生成式的`[]`改成`()`，就创建了一个`generator`：

```python
>>> L = [x * x for x in range(10)]
>>> L
[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
>>> g = (x * x for x in range(10))
>>> g
<generator object <genexpr> at 0x1022ef630>
```

创建L和g的区别仅在于最外层的`[]`和`()`，L是一个`list`，而g是一个`generator`。

我们可以直接打印出`list`的每一个元素，但我们怎么打印出`generator`的每一个元素呢？

如果要一个一个打印出来，可以通过`next()`函数获得`generator`的下一个返回值：

```python
>>> next(g)
0
>>> next(g)
1
>>> next(g)
4
>>> next(g)
9
>>> next(g)
16
>>> next(g)
25
>>> next(g)
36
>>> next(g)
49
>>> next(g)
64
>>> next(g)
81
>>> next(g)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
StopIteration
```

`generator`保存的是算法，每次调用`next(g)`，就计算出g的下一个元素的值，直到计算到最后一个元素，没有更多的元素时，抛出`StopIteration`的错误。

当然，上面这种不断调用`next(g)`实在是太变态了，正确的方法是使用`for`循环，因为`generator`也是可迭代对象：

```python
>>> g = (x * x for x in range(10))
>>> for n in g:
...     print(n)
... 
0
1
4
9
16
25
36
49
64
81
```

我们创建了一个`generator`后，基本上永远不会调用`next()`，而是通过`for`循环来迭代它，并且不需要关心`StopIteration`的错误。

`generator`非常强大。如果推算的算法比较复杂，用类似列表生成式的`for`循环无法实现的时候，还可以用函数来实现。

比如，著名的斐波拉契数列（Fibonacci），除第一个和第二个数外，任意一个数都可由前两个数相加得到：

```
1, 1, 2, 3, 5, 8, 13, 21, 34, ...
```

斐波拉契数列用列表生成式写不出来，但是，用函数把它打印出来却很容易：

```python
def fib(max):
    n, a, b = 0, 0, 1
    while n < max:
        print(b)
        a, b = b, a + b
        n = n + 1
    return 'done'
```

上面的函数可以输出斐波那契数列的前N个数：

```python
>>> fib(6)
1
1
2
3
5
8
'done'
```

仔细观察，可以看出，`fib`函数实际上是定义了斐波拉契数列的推算规则，可以从第一个元素开始，推算出后续任意的元素，这种逻辑其实非常类似`generator`。

也就是说，上面的函数和`generator`仅一步之遥。要把`fib`函数变成`generator`，只需要把`print(b)`改为`yield b`就可以了：

```python
def fib(max):
    n, a, b = 0, 0, 1
    while n < max:
        yield b
        a, b = b, a + b
        n = n + 1
    return 'done'
```

这就是定义`generator`的另一种方法。如果一个函数定义中包含`yield`关键字，那么这个函数就不再是一个普通函数，而是一个`generator`：

```python
>>> f = fib(6)
>>> f
<generator object fib at 0x104feaaa0>
```

这里，最难理解的就是`generator`和函数的执行流程不一样。函数是顺序执行，遇到`return`语句或者最后一行函数语句就返回。而变成`generator`的函数，在每次调用`next()`的时候执行，遇到`yield`语句返回，再次执行时从上次返回的`yield`语句处继续执行。

举个简单的例子，定义一个`generator`，依次返回数字`1，3，5`：

```python
def odd():
    print('step 1')
    yield 1
    print('step 2')
    yield(3)
    print('step 3')
    yield(5)
```

调用该`generator`时，首先要生成一个`generator`对象，然后用`next()`函数不断获得下一个返回值：

```python
>>> o = odd()
>>> next(o)
step 1
1
>>> next(o)
step 2
3
>>> next(o)
step 3
5
>>> next(o)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
StopIteration
```

可以看到，`odd`不是普通函数，而是`generator`，在执行过程中，遇到`yield`就中断，下次又继续执行。执行3次`yield`后，已经没有`yield`可以执行了，所以，第4次调用`next(o)`就报错。

回到fib的例子，我们在循环过程中不断调用`yield`，就会不断中断。当然要给循环设置一个条件来退出循环，不然就会产生一个无限数列出来。

同样的，把函数改成`generator`后，我们基本上从来不会用`next()`来获取下一个返回值，而是直接使用`for`循环来迭代：

```python
>>> for n in fib(6):
...     print(n)
...
1
1
2
3
5
8
```

但是用`for`循环调用`generator`时，发现拿不到`generator`的`return`语句的返回值。如果想要拿到返回值，必须捕获`StopIteration`错误，返回值包含在`StopIteration`的`value`中：

```python
>>> g = fib(6)
>>> while True:
...     try:
...         x = next(g)
...         print('g:', x)
...     except StopIteration as e:
...         print('Generator return value:', e.value)
...         break
...
g: 1
g: 1
g: 2
g: 3
g: 5
g: 8
Generator return value: done
```

`generator`是非常强大的工具，在Python中，可以简单地把列表生成式改成`generator`，也可以通过函数实现复杂逻辑的`generator`。

要理解`generator`的工作原理，它是在`for`循环的过程中不断计算出下一个元素，并在适当的条件结束`for`循环。对于函数改成的`generator`来说，遇到`return`语句或者执行到函数体最后一行语句，就是结束`generator`的指令，`for`循环随之结束。

# 迭代器

我们已经知道，可以直接作用于for循环的数据类型有以下几种：

1. 一类是集合数据类型，如`list`、`tuple`、`dict`、`set`、`str`等；

2. 一类是`generator`，包括生成器和带`yield`的`generator function`。

这些可以直接作用于`for`循环的对象统称为可迭代对象：`Iterable`。

可以使用`isinstance()`判断一个对象是否是`Iterable`对象：

```python
>>> from collections import Iterable
>>> isinstance([], Iterable)
True
>>> isinstance({}, Iterable)
True
>>> isinstance('abc', Iterable)
True
>>> isinstance((x for x in range(10)), Iterable)
True
>>> isinstance(100, Iterable)
False
```

而生成器不但可以作用于`for`循环，还可以被`next()`函数不断调用并返回下一个值，直到最后抛出`StopIteration`错误表示无法继续返回下一个值了。

可以被`next()`函数调用并不断返回下一个值的对象称为迭代器：`Iterator`。

可以使用`isinstance()`判断一个对象是否是`Iterator`对象：

```python
>>> from collections import Iterator
>>> isinstance((x for x in range(10)), Iterator)
True
>>> isinstance([], Iterator)
False
>>> isinstance({}, Iterator)
False
>>> isinstance('abc', Iterator)
False
```

生成器都是`Iterator`对象，但`list`、`dict`、`str`虽然是`Iterable`，却不是`Iterator`。

把`list`、`dict`、`str`等`Iterable`变成`Iterator`可以使用`iter()`函数：

```python
>>> isinstance(iter([]), Iterator)
True
>>> isinstance(iter('abc'), Iterator)
True
```

为什么`list`、`dict`、`str`等数据类型不是`Iterator`？

这是因为Python的`Iterator`对象表示的是一个数据流，`Iterator`对象可以被`next()`函数调用并不断返回下一个数据，直到没有数据时抛出`StopIteration`错误。可以把这个数据流看做是一个有序序列，但我们却不能提前知道序列的长度，只能不断通过`next()`函数实现按需计算下一个数据，所以`Iterator`的计算是惰性的，只有在需要返回下一个数据时它才会计算。

`Iterator`甚至可以表示一个无限大的数据流，例如全体自然数。而使用`list`是永远不可能存储全体自然数的。

总结一下：

- 凡是可作用于`for`循环的对象都是`Iterable`类型；

- 凡是可作用于`next()`函数的对象都是`Iterator`类型，它们表示一个惰性计算的序列；

- 集合数据类型如`list`、`dict`、`str`等是`Iterable`但不是`Iterator`，不过可以通过`iter()`函数获得一个`Iterator`对象。

本节完毕。
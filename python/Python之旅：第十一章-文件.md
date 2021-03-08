<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Python之旅：第十一章 文件](#python%E4%B9%8B%E6%97%85%E7%AC%AC%E5%8D%81%E4%B8%80%E7%AB%A0-%E6%96%87%E4%BB%B6)
  - [打开文件](#%E6%89%93%E5%BC%80%E6%96%87%E4%BB%B6)
  - [文件的基本方法](#%E6%96%87%E4%BB%B6%E7%9A%84%E5%9F%BA%E6%9C%AC%E6%96%B9%E6%B3%95)
    - [读取和写入](#%E8%AF%BB%E5%8F%96%E5%92%8C%E5%86%99%E5%85%A5)
    - [使用管道重定向输出](#%E4%BD%BF%E7%94%A8%E7%AE%A1%E9%81%93%E9%87%8D%E5%AE%9A%E5%90%91%E8%BE%93%E5%87%BA)
    - [随机存取](#%E9%9A%8F%E6%9C%BA%E5%AD%98%E5%8F%96)
    - [读取和写入行](#%E8%AF%BB%E5%8F%96%E5%92%8C%E5%86%99%E5%85%A5%E8%A1%8C)
    - [关闭文件](#%E5%85%B3%E9%97%AD%E6%96%87%E4%BB%B6)
      - [上下文管理器](#%E4%B8%8A%E4%B8%8B%E6%96%87%E7%AE%A1%E7%90%86%E5%99%A8)
    - [使用文件的基本方法](#%E4%BD%BF%E7%94%A8%E6%96%87%E4%BB%B6%E7%9A%84%E5%9F%BA%E6%9C%AC%E6%96%B9%E6%B3%95)
  - [迭代文件的内容](#%E8%BF%AD%E4%BB%A3%E6%96%87%E4%BB%B6%E7%9A%84%E5%86%85%E5%AE%B9)
    - [每次一个字符(或字节)](#%E6%AF%8F%E6%AC%A1%E4%B8%80%E4%B8%AA%E5%AD%97%E7%AC%A6%E6%88%96%E5%AD%97%E8%8A%82)
    - [每次一行](#%E6%AF%8F%E6%AC%A1%E4%B8%80%E8%A1%8C)
    - [读取所有内容](#%E8%AF%BB%E5%8F%96%E6%89%80%E6%9C%89%E5%86%85%E5%AE%B9)
    - [使用fileinput实现延迟行迭代](#%E4%BD%BF%E7%94%A8fileinput%E5%AE%9E%E7%8E%B0%E5%BB%B6%E8%BF%9F%E8%A1%8C%E8%BF%AD%E4%BB%A3)
    - [文件迭代器](#%E6%96%87%E4%BB%B6%E8%BF%AD%E4%BB%A3%E5%99%A8)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Python之旅：第十一章 文件

## 打开文件

要打开文件，可使用函数`open`，它位于自动导入的模块`io`中，函数`open`将文件名作为唯一必不可少的参数，并返回一个文件对象。

```python
>>> f = open('somefile.txt')
```

如果要通过写入文本来创建文件，这种调用函数`open`的方法并不能满足要求，为此可以使用`open`的第二个参数。

调用函数`open`时，如果只指定文件名，将获得一个可读取的文件对象，如果要写入文件，必须通过指定模式来显式地指出这一点，函数`open`的参数`mode`可取值有多个：

| 值 | 描述 |
| -- | --- |
| `r` | 读取模式(默认值) |
| `w` | 写入模式 |
| `x` | 独占写入模式 |
| `a` | 附加模式 |
| `b` | 二进制模式(与其他模式结合使用) |
| `t` | 文本模式(默认值，与其他模式结合使用) |
| `+` | 读写模式(与其他模式结合使用) |

显式的指定读取模式与不指定模式相同。写入模式让你能够写入文件，并在文件不存在时创建它。独占写入模式在文件已存在时引发`FileExistsError`异常。在写入模式下打开文件，原有内容将被删除(截断),并从文件开头处开始写入，如果要在既有文件末尾继续写入，可使用附加模式。

`+`可与其他任何模式结合起来使用，表示即可读取也可写入。例如要打开一个文本文件进行读写，可以使用`r+`。

默认模式为`rt`，这意味着将把文件视为经过编码的Unicode文本。因此将自动执行解码和编码，且默认使用UTF-8编码。

如果文件包含非文本的二进制数据，如声音剪辑或图像，只需使用二进制模式`rb`来禁用与文本相关的功能即可。

## 文件的基本方法

### 读取和写入

文件最重要的功能是提供和接收数据。如果有一个名为`f`的文件对象，可使用`f.write`来写入数据，还可使用`f.read`来读取数据。

每当调用`f.write(string)`时，字符串都将写入到文件既有内容的后面。

```python
>>> f = open('somfile.txt', 'w')
>>> f.write('Hello, ')
7
>>> f.write('World!')
6
>>> f.close
```

读取也一样，只需告诉方法你需要读取多少个字符(二进制模式下是多少个字节)

```python
>>> f = open('somfile.txt', 'r')
>>> f.read(4)
'Hell'
>>> f.read()
'o, World!'
```

### 使用管道重定向输出

在`bash`等`shell`中，可以依次输入多条命令，并使用管道将它们链接起来

```bash
cat somefile.txt | python somescript.py | sort
```

管道将一条命令的标准输出链接到下一个命令的标准输入。下面是一个计算包含多少个单词的脚本：

```python
# somescript.py
import sys
text = sys.stdin.read()
words = text.split()
wordcount = len(words)
print('Wordcount: ', wordcount)
```

读取下面这个文本，并计算有多少个单词

```python
'''
Your mother was a hamster and your
father smelled of elderberries.
'''

cat somefile.txt | python somescript.py
```

结果如下：

```python
Wordcount: 11
```

### 随机存取

前面介绍的读写都是将文件视为流，只能按顺序从头到尾读取，实际上，可在文件中移动读取，这称为随机存取。为此，可使用文件对象的两个方法：`seek`和`tell`.

方法`seek(offset[, whence])`将当前位置移动到`offset`和`whence`指定的地方。参数`offset`指定了字节(字符)数,而参数`whence`默认为`io.SEEK_SET(0)`,这意味着偏移量是相对于文件开头的。参数`whence`还可以设置为`io.SEEK_CUR(1)`或`io.SEEK_END(2)`,前者表示相对于当前位置进行移动，而后者表示相对于文件末尾进行移动。

```python
>>> f = open(r'/Users/liuzhen/python/somefile.txt', 'w')
>>> f.write('01234567890123456789')
20
>>> f.seek(5)
5
>>> f.write('Hello, World!')
13
>>> f.close()
>>> f = open(r'/Users/liuzhen/python/somefile.txt')
>>> f.read()
'01234Hello, World!89'
```

方法`tell()`返回当前位于文件的什么位置

```python
>>> f = open(r'/Users/liuzhen/python/somefile.txt')
>>> f.read(3)
'012'
>>> f.read(2)
'34'
>>> f.tell()
5
```

### 读取和写入行

要读取文本中的一行(从当前位置到下一个换行符的文本)，可以使用方法`readline`，滴啊用这个方法可以不提供任何参数，在这种情况下，将读取一行并返回它。也可以提供一个非负整数，指定`readline`最多读取多少个字符。要读取文件中的所有行，并以列表的方式返回，可以使用方法`readlines`

方法`writelines`与`readlines`相反，它接收一个字符串列表参数，也可以是任何可迭代对象，并将这些字符串写入到文件或流中。请注意，写入时不会添加换行符，因此你必须自行添加。另外，没有方法`writeline`

### 关闭文件

在读取文件后，并忘了调用方法`close`关闭文件。通常，程序退出时将自动关闭文件对象，但手动调用方法关闭文件总是对的，因为这样可以避免在某些系统中出现问题。

对于写入过的文件，一定要将其关闭，因为Python可能缓冲你写入的数据。如果程序崩溃，数据可能根本不会写入到文件中。如果想重置缓冲并将修改反映到磁盘文件中，但又不想关闭文件，可以使用`flush`。

要确保文件关闭，可以使用一条`try/finally`语句，并在`finally`子句中调用`close`

```python
# 在这里打开文件
try:
    # 将数据写入到文件中
finally:
    file.close()
```

实际上，Python还提供了一条专门为此设计的语句，那就是`with`语句：

```python
with open("somefile.txt") as somefile:
    do_something(somefile)
```

`with`语句让你能够打开文件并将其赋值给一个变量`somefile`，你可以将数据写入文件，到达语句末尾时，将自动关闭文件。

#### 上下文管理器

`with`语句实际上是一个非常通用的结构，它允许你使用上下文管理器。上下文管理器支持两个方法的对象：`__enter__`和`__exit__`(魔法方法，自动调用)。

方法`__enter__`不接受任何参数，在进入`with`时被调用，其返回值被赋值给关键字`as`后面的变量。

方法`__exit__`接收三个参数：异常类型、异常对象那个和异常跟踪。

文件也可用作上下文管理器，它的方法`__enter__`返回文件对象本身，而方法`__exit__`将关闭文件。

### 使用文件的基本方法

这里有一个简单的文本文件，内容如下：

```python
'''
Welcome to this file
There is nothing here except
This stupid haiku
'''
```

我们来试试前面介绍过的方法，首先是`read(n)`

```python
>>> f = open(r'/Users/liuzhen/python/somefile.txt')
>>> f.read(7)
'Welcome'
>>> f.read(4)
' to '
>>> f.close()
```

接下来是`read()`

```python
>>> f = open(r'/Users/liuzhen/python/somefile.txt')
>>> print(f.read())
Welcome to this file
There is nothing here except
This stupid haiku
>>> f.close()
```

下面是`readline()`

```python
>>> f = open(r'/Users/liuzhen/python/somefile.txt')
>>> for i in range(3):
	      print(str(i) + ': ' + f.readline(), end='')

0: Welcome to this file
1: There is nothing here except
2: This stupid haiku
>>> f.close()
```

最后是`readlines()`

```python
>>> import pprint
>>> pprint.pprint(open(r'/Users/liuzhen/python/somefile.txt').readlines())
['Welcome to this file\n',
 'There is nothing here except\n',
 'This stupid haiku']
```

上面的例子中文件对象会被自动关闭。

下面我们来尝试写入操作，首先是`write(string)`

```python
>>> f = open(r'/Users/liuzhen/python/somefile.txt', 'w')
>>> f.write('this\nis no\nhaiku')
16
>>> f.close()
```

然后是`writelines(list)`

```python
>>> f = open(r'/Users/liuzhen/python/somefile.txt')
>>> lines = f.readlines()
>>> f.close()
>>> lines[1] = "isn't a\n"
>>> f = open(r'/Users/liuzhen/python/somefile.txt', 'w')
>>> f.writelines(lines)
>>> f.close()
```

## 迭代文件的内容

有一种比较常见的文件操作是迭代其内容，并在迭代过程中做一些事。看下面的`process`函数，它将打印每次迭代的字符或行

```python
def process(string):
    print('Processing: ', string)
```

下面的示例会使用这个函数来模拟一些常见的操作。`filename`参数表示一些文件。

### 每次一个字符(或字节)

一种很简单但却不常见的操作是在`while`循环中使用方法`read`，来读取文件中每个字符(或二进制模式下的每个字节):

```python
with open(filename) as f:
    char = f.read(1)
    while char:
        process(char)
        char = f.read(1)
```

上面的示例虽然可以成功运行，但同样的代码出现了两次，所以，我们做了如下优化：

```python
with open(filename) as f:
    while True:
        char = f.read(1)
        if not char: break
        process(char)
```

### 每次一行

处理文本文件时，我们通常想做的是迭代行，而不是每个字符，迭代行可以使用方法`readline`：

```python
with open(filename) as f:
    while True:
        line = f.readline()
        if not line: break
        process(line)
```

### 读取所有内容

如果要一次读取整个文件，可以使用方法`read`且不提供任何参数，也就是将整个文件读取到一个字符串中。也可以使用方法`readlines`，将整个文件读取到一个字符串列表中，每个字符串是一行。

```python
# 使用read迭代
with open(filename) as f:
    for char in f.read():
        process(char)

# 使用readlines迭代行
with open(filename) as f:
    for line in f.radlines():
        process(line)
```

### 使用fileinput实现延迟行迭代

如果文件过大，使用`readlines`会占用过多的内存，当然你可以使用`while`循环和`readline`，但在Python中，应首选`for`循环，我们可以使用一种名为延迟行迭代的方法，只读取实际需要的文本部分。这里使用了`fileinput`，模块`fileinput`会负责打开文件，只需给它提供一个文件名即可：

```python
import fileinput
for line in fileinput.input(filename):
    process(line)
```

### 文件迭代器

在Python中最常见的就是文件迭代器了。实际上文件是可迭代的，这意味着可在`for`循环中直接使用它们来迭代行：

```python
with open(filename) as f:
    for line in f:
        process(line)
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
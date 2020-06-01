# Python之旅：第二章 列表和元组

我们先来说说数据结构，数据结构是以某种方式组合起来的数据元素集合。在Python中，最基本的数据结构为**序列**(Sequence)。序列中的每个元素都有编号，即其位置或索引，其中第一个元素的索引为0，第二个元素的索引为1，依次类推...，同时可回绕到序列末尾，用负索引表示序列末尾元素的位置。

## 序列概述

Python内置了多种序列，最常用的是列表和元组，另一种重要的序列是字符串。

列表和元组的主要不同在于，列表是可以修改的，而元组不可以，这就意味着列表适用于需要中途添加元素的情景，而元组适用于出于某种考虑而需要禁止修改序列的情景。

在需要处理一系列值时，序列是很有用的。比如在数据库中表示一个人，我们可以使用列表，列表中的每个元素表示人的特征，这些元素放在方括号中，并使用逗号隔开：

```python
>>> edward = ['Edward Gumby', 42] # 包含名字和年龄
```

一个序列中可以包含其他的序列，因此可以创建一个由序列组成的列表：

```python
>>> edward = ['Edward Gumby', 42]
>>> john = ['John Smith', 50]
>>> database = [edward, john]
>>> database
[['Edward Gumby', 42], ['John Smith', 50]]
```

**注意：** Python支持一种数据结构的基本概念，叫做**容器**(Container)，容器就是可以包含其他对象的对象。Python中有两种主要的容器，一种是序列(如列表和元组),另一种是映射(如字典),在序列中，每个元素都是编号，而在映射中，每个元素都有名称(也叫键),除此之外，还有一种既不是序列也不是映射的容器，它就是集合(Set)。

![](https://todever-images.oss-cn-beijing.aliyuncs.com/201804011801.png)

## 通用的序列操作

在Python中，对序列的操作包括索引、切片、相加、相乘和成员资格检查，另外，还有一些内置函数，用于确定序列的长度以及找出序列中的最大和最小元素。迭代功能将在后续章节中介绍

### 索引

序列中的所有元素都有编号，从0开始递增：

```python
>>> greeting = 'Hello'
>>> greeting[0]
'H'
```

字符串就是由字符组成的序列，索引0指向第一个元素，在Python中没有专门表示字符的类型，因此一个字符就是指包含一个元素的字符串。

我们可以使用索引来获取元素，这种索引方式适用于所有序列，当你使用负数索引时，Python将从右开始往左数，也就是从最后一个元素开始，因此-1是最后一个元素的位置：

```python
>>> greeting[-1]
'o'
```

我们也可以直接将索引应用到字符串字面量上：

```python
>>> 'Hello'[-1]
'o'
```

如果函数调用返回一个序列，可直接对其执行索引操作：

```python
>>> fourth = input('Year: ')[3]
Year: 2018
>>> fourth
'8'
```

下面我们来做一个实例：要求输入年、月、日，再使用相应的月份名将日期打印出来

```python
# 将指定的年、月、日打印出来
months = [
  'January',
  'February',
  'March',
  'April',
  'May',
  'June',
  'August',
  'September',
  'October',
  'November',
  'December'
]

# 一个列表，其中包含数1~31对应的结尾
endings = ['st', 'nd', 'rd'] + 17 * ['th'] \
        + ['st', 'nd', 'rd'] + 7 * ['th'] \
        + ['st']

year = input('Year: ')
month = input('Month (1-12): ')
day = input('Day (1-31): ')

# 类型转换
month_number = int(month)
day_number = int(day)

# 月和日需要-1，这样才能获取正确的索引
month_name = months[month_number - 1]
ordinal = day + endings[day_number - 1]

print(month_name + ' ' + ordinal + ', ' + year)
```

运行结果如下：

```python
Year: 2018
Month (1-12): 4
Day (1-31): 1
April 1st, 2018
```

### 切片

在Python中可以使用切片(slicing)来访问特定范围内的元素，你可以使用两个索引，并用冒号分隔：

```python
>>> tag = '<a href="http://www.python.org">Python web site</a>'
>>> tag[9:30]
'http://www.python.org'
>>> tag[32:-4]
'Python web site'
```

切片适用于提取序列的一部分，其中编号很重要，第一个索引是包含的第一个元素的编号，但第二个索引是切片后余下的第一个元素的编号

```python
>>> numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
>>> numbers[3:6] 
[4, 5, 6]
>>> numbers[0:1]
[1]
```

如上的列子可以看出，你需要提供两个索引来指定切片的边界，其中第一个索引指定的元素包含在切片内，但第二个索引指定的元素不包含在切片内。

#### 切片的简写

如果切片结束于序列的末尾，可以省略第二个索引：

```python
>>> numbers[-3:]
[8, 9, 10]
```

同样的，如果切片始于序列开头，则可以省略第一个索引

```python
>>> numbers[:3]
[1, 2, 3]
```

所以，如果要复制整个序列，可以将两个索引都省略掉：

```python
>>> numbers[:]
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```

让我们用切片来做个小示例：

```python
# 从用户输入的url中获取域名
url = input('Please enter the URL: ')
domain = url[11:-4]

print('Domain name: ' + domain)
```

运行结果如下：

```python
Please enter the URL: http://www.python.org
Domain name: python
```

#### 更大的步长

前面切片操作都省略了一个参数，即步长，在普通切片中，步长为1，这意味着普通切片操作包含了起点和终点之间的所有元素：

```python
>>> numbers[0:10:1]
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```

下面我们来显式的指定步长为2，那么将从起点开始，每隔一个元素提取一个元素

```python
>>> numbers[0:10:2]
[1, 3, 5, 7, 9]
```

显式的指定步长，也可以使用上面的简写，比如要从序列中每隔3个元素提取1个，只需提供步长即可：

```python
>>> numbers[::4]
[1, 5, 9]
```

步长是不能为0的，否则无法向前移动，但可以为负数，即从右向左提取元素

```python
>>> numbers[8:3:-1]
[9, 8, 7, 6, 5]
>>> numbers[10:0:-2]
[10, 8, 6, 4, 2]
>>> numbers[0:10:-2]
[]
```

步长为负数时，第一个索引必须比第二个大。

### 序列相加

在Python中可以使用加法运算来拼接序列

```python
>>> [1, 2, 3] + [4, 5]
[1, 2, 3, 4, 5]
>>> 'Hello ' + 'world!'
'Hello world!'
>>> [1, 2, 3] + 'world!'
Traceback (most recent call last):
  File "<pyshell#12>", line 1, in <module>
    [1, 2, 3] + 'world!'
TypeError: can only concatenate list (not "str") to list
```

不能拼接列表和字符串，虽然它们都是序列，一般而言，不能拼接不同类型的序列。

### 乘法

如果将序列与数x相乘，将重复这个序列x次来创建一个新的序列：

```python
>>> 'python' * 5
'pythonpythonpythonpythonpython'
>>> [42] * 10
[42, 42, 42, 42, 42, 42, 42, 42, 42, 42]
```

空列表是使用不包含任何内容的两个方括号(`[]`)表示的。在Python中，使用`None`表示什么都没有，因此要将列表的长度初始化为10，可以这样做：

```python
>>> sequence = [None] * 10
>>> sequence
[None, None, None, None, None, None, None, None, None, None]
```

下面我们来看一个例子，使用序列的乘法运行，在屏幕中央打印一个方框

```python
# 在位于屏幕中央且宽度何时的方框内打印一个句子
sentence = input('Sentence: ')

screen_width = 80
text_width = len(sentence)
box_width = text_width + 4
left_margin = (screen_width - box_width) // 2

print()
print(' ' * left_margin + '+' + '-' * (box_width-2) + '+')
print(' ' * left_margin + '| ' + ' ' * text_width + ' |')
print(' ' * left_margin + '| ' + sentence + ' |')
print(' ' * left_margin + '| ' + ' ' * text_width + ' |')
print(' ' * left_margin + '+' + '-' * (box_width-2) + '+')
print()
```

### 成员资格

如果我们要检查特定的值是否包含在序列中，可以使用运算符`in`，它检查是否满足指定的条件，并返回相应的值：满足时返回`True`，否则返回`Flase`，这样的运算称为布尔运算

```python
>>> permissions = 'rw'
>>> 'w' in permissions
True
>>> 'x' in permissions
False
>>> users = ['mlh', 'foo', 'bar']
>>> 'mlh' in users
True
```

下面的示例定义了一个数据列表，需要用户输入后，检查用户输入的是否在列表中

```python
# 检查用户名和PIN码

database = [
    ['albert', '1234'],
    ['dilbert', '4242'],
    ['smith', '7524'],
    ['jones', '9843']
]

username = input('User name: ')
pin = input('PIN code: ')

if [username, pin] in database:
    print('Access granted')
```

Python内置的函数`len`、`min`和`max`很有用，`len`函数返回序列包含的元素个数，而`min`和`max`分别返回序列中的最小和最大的元素

```python
>>> numbers = [100, 34, 678]
>>> len(numbers)
3
>>> max(numbers)
678
>>> min(numbers)
34
>>> max(2, 3)
3
>>> min(9, 3, 2, 5)
2
```

在后面的两个示例中，调用`max`和`min`时指定的实参并不是序列，而直接将数值作为实参。

## 列表：Python的主力

列表是不同于元组和字符串的，列表是可变的，即可以修改其内容，另外，列表也有很多特有的方法

### 函数list

列表是可修改的，不同于字符串不可修改，使用字符串来创建列表是很有帮助的，因此，可以使用函数`list`：(实际上`list`是一个类，而不是一个函数)

```python
>>> list('Hello')
['H', 'e', 'l', 'l', 'o']
```

注意：可以将任何序列，不仅仅是字符串，作为`list`的参数。另外，还可以使用`join`来做反向操作，也就是把列表转换成一个字符串输出

```python
>>> ''.join(['H', 'e', 'l', 'l', 'o']) # 前面的''可以是任意字符，作为分隔符使用的
'Hello'
```

### 基本的列表操作

除了可以对列表执行标准操作外，如索引、切片、拼接和相乘，还可以给元素赋值、删除元素、给切片赋值以及使用列表方法。

#### 修改列表：给元素赋值

我们可以使用索引表示法给特定位置的元素赋值，如：`x[1] = 2`

```python
>>> x = [1, 1, 1]
>>> x[1] = 2
>>> x
[1, 2, 1]
```

#### 删除元素

从列表中删除元素使用`del`语句即可

```python
>>> names = ['Alice', 'Beth', 'Cecil', 'Dee-Dee', 'Earl']
>>> del names[2]
>>> names
['Alice', 'Beth', 'Dee-Dee', 'Earl']
```

列表长度从5变成了4，`del`除了用于删除列表元素外，还可以用于字典，乃至变量。

#### 给切片赋值

```python
>>> name = list('Perl')
>>> name
['P', 'e', 'r', 'l']
>>> name[2:] = list('ar')
>>> name
['P', 'e', 'a', 'r']
```

通过切片赋值，还可以将切片替换为长度与其不同的序列：

```python
>> name = list('Perl')
>>> name
['P', 'e', 'r', 'l']
>>> name[1:] = list('ython')
>>> name
['P', 'y', 't', 'h', 'o', 'n']
```

使用切片赋值还可以在不替换原有元素的情况下插入新元素

```python
>>> numbers = [1, 5]
>>> numbers[1:1] = [2, 3, 4]
>>> numbers
[1, 2, 3, 4, 5]
```

### 列表方法

方法是与对象(列表、数值、字符串等)联系紧密的函数。通常我们可以像这样调用方法：

```python
object.method(arguments)
```

#### append

方法`append`用于将一个对象附加到列表末尾

```python
>>> lst = [1, 2, 3]
>>> lst.append(4)
>>> lst
[1, 2, 3, 4]
```

请注意：跟后面的几个方法相似，`append`方法就地修改列表，意思就是说它不会返回修改后的新列表，而是直接修改旧的列表

#### clear

方法`clear`就地清空列表的内容

```python
>>> lst = [1, 2, 3]
>>> lst.clear()
>>> lst
[]
```

这就类似于切片语句：`lst[:] = []`

#### copy

方法`copy`复制列表，一般常规的赋值语句只是将另一个名称关联到当前列表

```python
>>> a = [1, 2, 3]
>>> b = a
>>> b[1] = 4
>>> a
[1, 4, 3]
```

在我们将`a`赋值给`b`，修改了`b`，`a`的值也改变了，说明`a`和`b`都是指向的同一个列表，要让`a`和`b`指向不同的列表，就必须将`b`关联到`a`的副本

```python
>>> a = [1, 2, 3]
>>> b = a.copy()
>>> b[1] = 4
>>> a
[1, 2, 3]
>>> b
[1, 4, 3]
```

#### count

方法`count`计算指定的元素在列表中出现了多少次

```python
>>> ['to', 'be', 'or', 'not', 'to', 'be'].count('to')
2
>>> x = [[1, 2], 1, 1, [2, 1, [1, 2]]]
>>> x.count(1)
2
>>> x.count([1, 2])
1
```

#### extend

方法`extend`能够让你将多个值附加到一个列表的末尾，可以将这些值组成的序列作为参数提供给方法`extend`，换言之，你可以使用一个列表来扩展另一个列表

```python
>>> a = [1, 2, 3]
>>> b = [4, 5, 6]
>>> a.extend(b)
>>> a
[1, 2, 3, 4, 5, 6]
```

这种情况看起来很像是两个序列的拼接，但与拼接有一定的区别，拼接是返回了一个新的列表，而原列表是不变的，但`extend`会修改原列表，上面的例子中是`a`

#### index

方法`index`在列表中查找指定值第一次出现的索引。

```python
>>> knights = ['We', 'are', 'the', 'knights', 'who', 'say', 'ni']
>>> knights.index('who')
4
>>> knights.index('herring')
Traceback (most recent call last):
  File "<pyshell#7>", line 1, in <module>
    knights.index('herring')
ValueError: 'herring' is not in list
```

### insert

方法`insert`用于将一个对象插入到列表中，其中第一个参数是要将对象插入到那个索引位置，第二个参数是即将要插入的对象。

```python
>>> numbers = [1, 2, 3, 5, 6, 7]
>>> numbers.insert(3, 'four')
>>> numbers
[1, 2, 3, 'four', 5, 6, 7]
```

#### pop

方法`pop`从列表中删除一个元素(末尾为最后一个元素)，并返回这个元素，如果没有给`pop`提供参数，则删除最后一个。

```python
>>> x = [1, 2, 3]
>>> x.pop()
3
>>> x
[1, 2]
>>> x.pop(0)
1
>>> x
[2]
```

注意：`pop`是唯一既修改列表又返回一个非None值的列表方法

使用`pop`可实现一种常见的数据结构 - 栈(stack)，栈就像一叠盘子，你可以在上面添加盘子，还可以从上面取走盘子，最后加入的盘子最后取出，这被称为**后进先出(LIFO)**。类似的弹夹也是这样的原理。

`push`和`pop`是实现栈操作的两个关键方法，但Python中没有`push`方法，不过我们可以使用`append`来替代。

> 还有一种与栈相似的数据结构 - 队列，它的规则是**先进先出(FIFO)**，可以使用`insert(0, ...)`替代`append`，然后使用`pop(0)`。但最佳的解决方案是使用模块`collections`中的`deque`

#### remove

`remove`用于删除第一个为指定值的元素.

```python
>>> x = ['to', 'be', 'or', 'not', 'to', 'be']
>>> x.remove('be')
>>> x
['to', 'or', 'not', 'to', 'be']
>>> x.remove('bee')
Traceback (most recent call last):
  File "<pyshell#23>", line 1, in <module>
    x.remove('bee')
ValueError: list.remove(x): x not in list
```

`remove`方法就地修改且不返回值。

#### reverse

方法`reverse`按相反的顺序排列列表中的元素

```python
>>> x = [1, 2, 3]
>>> x.reverse()
>>> x
[3, 2, 1]
```

注意：`reverse`修改列表但不返回任何值。

#### sort

方法`sort`用于对列表就地排序，就地排序意味着对原来的列表进行修改，使其元素按顺序排列，而不是返回排列后的列表副本。

```python
>>> x = [4, 6, 2, 1, 7, 9]
>>> x.sort()
>>> x
[1, 2, 4, 6, 7, 9]
```

可以看出，`sort`方法跟上面很多方法一样，都修改了原列表，且不会返回任何值。如果我们像要对列表排序且不能修改原列表，我们就要对原列表的副本进行排序，但下面的例子是错误的：

```python
>>> x = [4, 6, 2, 1, 7, 9]
>>> y = x.sort() # 不要这样做
>>> print(y)
None
```

正确的做法是：

```python
>>> x = [4, 6, 2, 1, 7, 9]
>>> y = x.copy() # 创建x的副本，并赋值给y
>>> y.sort()
>>> x
[4, 6, 2, 1, 7, 9]
>>> y
[1, 2, 4, 6, 7, 9]
```

除了上面的方法外，我们还可以使用`sorted`方法：

```python
[4, 6, 2, 1, 7, 9]
>>> y = sorted(x)
>>> x
[4, 6, 2, 1, 7, 9]
>>> y
[1, 2, 4, 6, 7, 9]
```

`sorted`方法可以用于任何序列，它总是返回一个列表。

```python
>>> sorted('python')
['h', 'n', 'o', 'p', 't', 'y']
```

#### 高级排序

方法`sort`接受两个可选参数：`key`和`reverse`。这两个参数通常是按名称指定的，称为关键字参数。我们可以将`key`设置为一个用于排序的函数，然后并不会直接使用这个函数来判断一个元素是否比另一个小，而是使用它来为每个元素创建一个键，再根据这些键对元素进行排序，如：把`key`设置为`len`，即根据元素长度进行排序：

```python
>>> x = ['aardvark', 'abalone', 'acme', 'add', 'aerate']
>>> x.sort(key=len)
>>> x
['add', 'acme', 'aerate', 'abalone', 'aardvark']
```

对于另一个关键字参数`reverse`，只需为其指定一个布尔值(`True`或`False`)，以指出是否要按相反的顺序对列表进行排序

```python
>>> x = [4, 6, 2, 1, 7, 9]
>>> x.sort(reverse=True)
>>> x
[9, 7, 6, 4, 2, 1]
```

## 元组：不可修改的序列

与列表一样，元组也是序列，它与列表唯一的差别在于**元组不能被修改**(字符串也不能被修改),创建元组的方法很简单，只需要用逗号将一些值隔开就能自动创建

```python
>>> 1, 2, 3
(1, 2, 3)
```

但通常来讲，我们创建元素都会加上一对括号：

```python
>>> (1, 2, 3)
(1, 2, 3)
```

空元组用两个不包含任何元素的圆括号表示：

```python
>>> ()
()
```

如果元组里只有一个元素，请务必要给这个元素后面加上一个逗号：

```python
>>> 42,
(42,)
>>> (42,)
(42,)
```

创建元组还可以使用`tuple`函数，它跟`list`和相似，将一个序列作为参数，并将其转换为一种，如果参数已经是元组，则原封不动的返回它。

```python
>>> tuple([1, 2, 3])
(1, 2, 3)
>>> tuple('abc')
('a', 'b', 'c')
>>> tuple((1, 2, 3))
(1, 2, 3)
```

元组的创建及其元素的访问方式与其他序列相同。

```python
>>> x = (1, 2, 3)
>>> x[1]
2
>>> x[0:2]
(1, 2)
```

元组的切片也是元组，就像列表的切片也是列表一样。

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
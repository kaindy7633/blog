<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Python之旅：第四章 当索引行不通时：使用字典](#python%E4%B9%8B%E6%97%85%E7%AC%AC%E5%9B%9B%E7%AB%A0-%E5%BD%93%E7%B4%A2%E5%BC%95%E8%A1%8C%E4%B8%8D%E9%80%9A%E6%97%B6%E4%BD%BF%E7%94%A8%E5%AD%97%E5%85%B8)
  - [字典的用途](#%E5%AD%97%E5%85%B8%E7%9A%84%E7%94%A8%E9%80%94)
  - [创建和使用字典](#%E5%88%9B%E5%BB%BA%E5%92%8C%E4%BD%BF%E7%94%A8%E5%AD%97%E5%85%B8)
    - [函数dict](#%E5%87%BD%E6%95%B0dict)
    - [基本的字典操作](#%E5%9F%BA%E6%9C%AC%E7%9A%84%E5%AD%97%E5%85%B8%E6%93%8D%E4%BD%9C)
    - [将字符串格式设置功能用于字典](#%E5%B0%86%E5%AD%97%E7%AC%A6%E4%B8%B2%E6%A0%BC%E5%BC%8F%E8%AE%BE%E7%BD%AE%E5%8A%9F%E8%83%BD%E7%94%A8%E4%BA%8E%E5%AD%97%E5%85%B8)
    - [字典方法](#%E5%AD%97%E5%85%B8%E6%96%B9%E6%B3%95)
      - [clear](#clear)
      - [copy](#copy)
      - [fromkeys](#fromkeys)
      - [get](#get)
      - [itmes](#itmes)
      - [keys](#keys)
      - [pop](#pop)
      - [popitem](#popitem)
      - [setdefault](#setdefault)
      - [update](#update)
      - [values](#values)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Python之旅：第四章 当索引行不通时：使用字典

前面几个章节介绍的序列是一种通过索引(编号)来访问各个元素的数据结构。通过名称来访问其各个元素值的数据结构，叫做**映射(mapping)**，而字典则是Python中唯一的内置映射类型。字典中的值是没有顺序的，而是存储在键下，键可以是数字、字符串或元组。

## 字典的用途

字典的名称指出了这种数据结构的用途。字典旨在让你能轻松的找到特定的单词(键),以获得其定义的(值)

例如：如果我们要创建一个人的序列，但需要根据人来找到其电话号码，则必须创建两个list，然后一一对应的找到其值，使用列表是可行的，但使用字典是最佳方式，且效率更高。

## 创建和使用字典

创建字典类似下面的这种表示方式：

```python
phonebook = {'Alice': '2341', 'Beth': '9102', 'Cecil': '3258'}
```

字典由键及其相应的值组成，这种键-值对称为**项**(item)，每个键与其值之间都用冒号(`:`)分隔，项之间用逗号分隔，而整个字典放在花括号内。空字典直接使用两个花括号表示：`{}`。特别注意：在字典中的键必须是唯一的，而值则无需如此。

### 函数dict

可使用函数`dict`从其他映射(如其他字典)或键-值对序列创建字典

```python
>>> items = [('name', 'Gumby'), ('age', 42)]
>>> d = dict(items)
>>> d
{'name': 'Gumby', 'age': 42}
```

还可以使用关键字实参来调用这个函数：

```python
>>> d = dict(name='Gumby', age=42)
>>> d
{'name': 'Gumby', 'age': 42}
```

就像函数`list`、`tuple`和`str`一样，如果调用`dict`函数时没有提供任何实参，将返回一个空字典。

### 基本的字典操作

字典的基本行为在很多方面都类似于序列

- `len(d)`: 返回字典`d`包含的项(键值对)的数量
- `d[k]`: 返回与键`k`相关联的值。
- `d[k] = v`: 将值`v`关联到键`k`
- `del d[k]`: 删除键为`k`的项
- `k in d`: 检查字典d是否包含键为k的项

字典与序列的不同之处：

- 键的类型：序列中只有索引，类似于字典中的键，但它只能为整数，而字典中的键可以是整数，也可以是任何不可变的类型，比如浮点数、字符串或元组
- 自动添加：即便是字典中原本没有的键，也可以给它赋值，这将在字典中创建一个新项，然后，我们不能给列表中没有的元素赋值
- 成员资格：在字典中，表达式`k in d`(`d`是一个字典),查找的是键，而不是值，在序列中，表达式`v in l`(`l`是一个列表)，查找的是值而不是索引。

字典中的键可以是任何不可变的类型，这一点是字典的主要优点，看下面的示例：

```python
>>> x = []
>>> x[42] = 'Foobar'
Traceback (most recent call last):
  File "<pyshell#130>", line 1, in <module>
    x[42] = 'Foobar'
IndexError: list assignment index out of range
>>> x = {}
>>> x[42] = 'Foobar'
>>> x
{42: 'Foobar'}
```

如果要给空的列表添加新的项，上面的操作是不可行的，然而，字典却可以。

看下面的例子：

```python
# 一个简单的数据库

# 一个将人名用作键的字典，每个人都用一个字典表示
# 字典包含键'phone'和'addr'，它们分别与电话号码和地址相关联

people = {
  'Alice': {
    'phone': '2341',
    'addr': 'Foo drive 23'
  },

  'Beth': {
    'phone': '9102',
    'addr': 'Bar street 42'
  },

  'Cecil': {
    'phone': '3158',
    'addr': 'Baz avenue 90'
  }
}

# 电话号码和地址的描述性标签，供打印输出时使用
labels = {
  'phone': 'phone number',
  'addr': 'address'
}

name = input('Name: ')

# 要查找电话号码还是地址？
request = input('Phone number (p) or address (a)? ')

# 使用正确的键
if request == 'p': key = 'phone'
if request == 'a': key = 'addr'

# 仅当名字是字典包含的键时才打印信息：
if name in people:
  print("{}'s {} is {}.".format(name, labels[key], people[name][key]))
```

运行结果如下：

```python
Name: Alice
Phone number (p) or address (a)? p
Alice's phone number is 2341.
```

### 将字符串格式设置功能用于字典

通过字典，我们可以使用`format_map`来指定一个映射来提供所需的信息：

```python
>>> phonebook = {'Beth': '9102', 'Alice': '2341', 'Cecil': '3258'}
>>> "Cecil's phone number is {Cecil}.".format_map(phonebook)
"Cecil's phone number is 3258."
```

像这样使用字典，可指定任意数量的转换说明符，条件是所有的字段名都是包含在字典中的键，这在模板系统中非常有用。

```python
>>> template = '''<html>
<head><title>{title}</title></head>
<body>
<h1>{title}</h1>
<p>{text}</p>
</body>'''
>>> data = {'title': 'My Home Page', 'text': 'Welcome to my home page!'}
>>> print(template.format_map(data))
<html>
<head><title>My Home Page</title></head>
<body>
<h1>My Home Page</h1>
<p>Welcome to my home page!</p>
</body>
```

### 字典方法

#### clear

方法`clear`删除所有的字典项，这种操作就地执行，因此什么都不会返回，或者说返回`None`

```python
>>> d = {}
>>> d['name'] = 'Gumby'
>>> d['age'] = 42
>>> d
{'name': 'Gumby', 'age': 42}
>>> returned_value = d.clear()
>>> d
{}
>>> print(returned_value)
None
```

下面有两种场景需要注意，看代码：

```python
# 第一种场景
>>> x = {}
>>> y = x # x和y都指向同一个字典对象
>>> x['key'] = 'value'
>>> y
{'key': 'value'}
>>> x = {} # 当给x赋值空字典后，y依然指向原来的对象
>>> y
{'key': 'value'}
```

```python
>>> x = {}
>>> y = x # x和y都指向同一个字典对象
>>> x['key'] = 'value'
>>> y
{'key': 'value'}
>>> x.clear() # 当使用clear清空x后，y的指向也被删除了
>>> y
{}
```

#### copy

方法`copy`返回一个新字典，其包含的键值对与原来的字典相同(浅复制),因为值本身是原件，而非副本。

```python
>>> x = {'username': 'admin', 'machines': ['foo', 'bar', 'baz']}
>>> y = x.copy()
>>> y['username']= 'mlh'
>>> y['machines'].remove('bar')
>>> y
{'username': 'mlh', 'machines': ['foo', 'baz']}
>>> x
{'username': 'admin', 'machines': ['foo', 'baz']}
```

还有一种复制，叫**深复制**,即同时复制值及其包含的所有值，执行深复制可使用模块`copy`中的函数`deepcopy`

```python
>>> from copy import deepcopy
>>> d = {}
>>> d['names'] = ['Alfred', 'Bertrand']
>>> c = d.copy()
>>> dc = deepcopy(d)
>>> d['names'].append('Clive')
>>> c
{'names': ['Alfred', 'Bertrand', 'Clive']}
>>> dc
{'names': ['Alfred', 'Bertrand']}
```

#### fromkeys

方法`fromkeys`创建一个新字典，其中包含指定的键，且每个键对应的值都是`None`

```python
>>> {}.fromkeys(['name', 'age'])
{'name': None, 'age': None}
```

上面的行为有点多余，你可以直接使用`dict`来调用`fromkeys`方法：

```python
>>> dict.fromkeys(['name', 'age'])
{'name': None, 'age': None}
```

如果你不想使用默认值`None`，可以提供特定的值

```python
>>> dict.fromkeys(['name', 'age'], '(unknown)')
{'name': '(unknown)', 'age': '(unknown)'}
```

#### get

方法`get`为访问字典项提供了宽松的环境，通常情况下，如果我们访问字典中没有的项，会引发错误：

```python
>>> d = {}
>>> print(d['name'])
Traceback (most recent call last):
  File "<pyshell#192>", line 1, in <module>
    print(d['name'])
KeyError: 'name'
```

而使用`get`则不会：

```python
>>> d = {}
>>> print(d.get('name'))
None
```

当使用`get`来访问字典中不存在的键时，没有引发异常，而是返回了`None`，我们还可以指定默认值：

```python
>>> d.get('name', 'N/A')
'N/A'
```

如果字典中包含指定的值，则它与普通的字典查找相同。

下面是一个使用`get`查找简单数据库的示例：

```python
# 一个使用get()的简单数据库

people = {
  'Alice': {
    'phone': '2341',
    'addr': 'Foo drive 23'
  },

  'Beth': {
    'phone': '9102',
    'addr': 'Bar street 42'
  },

  'Cecil': {
    'phone': '3158',
    'addr': 'Baz avenue 90'
  }
}

labels = {
  'phone': 'phone number',
  'addr': 'address'
}

name = input('Name: ')

# 要查找电话号码还是地址?
request = input('Phone number(p) or address (a)? ')

# 使用正确的键
key = request # 如果request既不是'p'也不是'a'
if request == 'p': key = 'phone'
if request == 'a': key = 'addr'

# 使用get提供默认值
person = people.get(name, {})
label = labels.get(key, key)
result = person.get(key, 'not available')

print("{}'s {} is {}.".format(name, label, result))
```

运行结果如下：

```python
Name: Beth
Phone number(p) or address (a)? p
Beth's phone number is 9102.
```

#### itmes

方法`items`返回一个包含所有字典项的列表，其中每个元素都为`(key, value)`的形式，字典项咋系列表中的排列顺序不确定。

```python
>>> d = {'title': 'Python Web Site', 'url': 'https://www.python.org', 'spam': 0}
>>> d.items()
dict_items([('title', 'Python Web Site'), ('url', 'https://www.python.org'), ('spam', 0)])
```

返回值是一种名为**字典视图**的特殊类型，字典视图可用于迭代，我们还可以获取其长度以及执行成员资格检查

```python
>>> it = d.items()
>>> len(it)
3
>>> ('spam', 0) in it
True
```

字典视图的优点就是不复制，它们始终是底层字典的反映，即便是修改了底层字典也是如此：

```python
>>> d['spam'] = 1
>>> ('spam', 0) in it
False
>>> d['spam'] = 0
>>> ('spam', 0) in it
True
```

我们也可以手动复制字典项到列表中

```python
>>> list(d.items())
[('title', 'Python Web Site'), ('url', 'https://www.python.org'), ('spam', 0)]
```

#### keys

方法`keys`返回一个字典视图，其中包含指定字典中的键

#### pop

方法`pop`可用于获取与指定键相关联的值，并将该键值对从字典中删除

```python
>>> d = {'x': 1, 'y': 2}
>>> d.pop('x')
1
>>> d
{'y': 2}
```

#### popitem

方法`popitem`随机的弹出一个字典项，因为字典项的顺序是不确定的，没有'最后一个元素'的概念。

```python
>>> d = {'title': 'Python Web Site', 'url': 'https://www.python.org', 'spam': 0}
>>> d.popitem()
('spam', 0)
>>> d
{'title': 'Python Web Site', 'url': 'https://www.python.org'}
```

#### setdefault

方法`setdefault`有点像`get`，因为它也获取与指定键相关联的值，但除此之外，它还在字典不包含指定的键时，在字典中添加指定的键值对

```python
>>> d = {}
>>> d.setdefault('name', 'N/A')
'N/A'
>>> d
{'name': 'N/A'}
>>> d['name'] = 'Gumby'
>>> d.setdefault('name', 'N/A')
'Gumby'
>>> d
{'name': 'Gumby'}
```

#### update

方法`update`使用一个字典的项来更新另一个字典

```python
>>> d = {
	'title': 'Python Web Site',
	'url': 'https://www.python.org',
	'changed': 'Mar 14 22:09:15 MET 2016'
	}
>>> x = {'title': 'Python Language Website'}
>>> d.update(x)
>>> d
{'title': 'Python Language Website', 'url': 'https://www.python.org', 'changed': 'Mar 14 22:09:15 MET 2016'}
```

#### values

方法`values`返回一个由字典中的值组成的字典视图，它不同于方法`keys`，方法`values`返回的视图可能包含重复的值。

```python
>>> d = {}
>>> d[1] = 1
>>> d[2] = 2
>>> d[3] = 3
>>> d[4] = 1
>>> d.values()
dict_values([1, 2, 3, 1])
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

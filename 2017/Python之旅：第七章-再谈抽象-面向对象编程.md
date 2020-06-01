# Python之旅：第七章 再谈抽象-面向对象编程

> 前面我们介绍了Python内置的主要对象类型(数、字符串、列表、元组和字典),还有众多的内置函数和标准库，自定义函数，本章主要介绍自定义对象。

创建自定义对象(对象类型或类)是Python的一个核心概念。这个概念非常重要，它使得Python被视为一种面向对象的语言。

## 对象魔法

在面向对象编程中，对象就是一些列的数据(属性)以及一套访问和操作这些数据的方法，它主要有以下特性：

- 多态：可对不同类型的对象执行相同的操作
- 封装：对外隐藏有关对象工作原理的细节
- 继承：可基于通用类创建出专用类

### 多态

多态(polymorephism)，源自希腊语，意思就是"有多重形态"，它意味着即便你不知道变量指向的是那种对象，也能够对其执行操作，且操作的行为将随对象所属的类型而异。

例如，我们在设计电子商务系统时，需要获取商品价格，而表示商品价格的形式有很多种，如果我们使用元组来表示，可以像下面这样获取价格：

```python
# 实际开发中不要像这样做

def get_price(object):
    if isinstance(object, tuple):
        return object[1]
    else:
        return magic_network_method(object)
```

但如果有其他人将表示价格的对象换成了字典呢？？ 可以像这样：

```python
# 实际开发中不要像这样做

def get_price(object):
    if isinstance(object, tuple):
        return object[1]
    elif isinstance(object, dict):
        return int(object['price'])
    else:
        return magic_network_method(object)
```

这时，要获取的对象类型又变成了其他新的字典对象，且存储的键并不在`price`下面，又怎么办呢？很显然，这种方法不灵活也不切实际。其实我们可以让每种新对象自己获取或计算其价格并返回结果。

### 多态和方法

如上所述，当你接收到一个对象，可使用其内置的函数返回其价格：

```python
>>> object.get_price()
2.5
```

这种与对象属性相关联的函数称为方法。在Python的标准库模块`random`中包含一个名为`choice`的方法，它从序列中随机选择一个元素：

```python
from random import choice
x = choice(['Hello world!', [1, 2, 'e', 'e', 4]])
```

当执行上述代码后，变量`x`有可能包含字符串`Hello world!`，也有可能是后面的列表，当然，我们可以不关心其类型是什么，直接调用`count`方法来统计字母`e`出现的次数

```python
>>> x.count('e')
2
```

Python中内置运算符和函数都大量使用了多态：

```python
>>> 1 + 2
3
>>> 'Fish' + 'license'
Fishlicense
```

加法运算符并不关心加入计算的两个元素是何种类型，重点在于参数可以是任何支持加法的对象。

### 封装

封装(encapsulation)指的是向外部隐藏不必要的细节。它跟多态有点类似，都源于抽象原则。多态让你无需知道对爱那个所属的类就能调用其方法，而封装让你无需知道对象的构造就能使用它。下面的例子从一个类中实例化一个对象并赋值给一个对象，且使用了其两个方法：

```python
>>> o = OpenObject()  # 从一个类中创建对象实例
>>> o.set_name('Sir Lancelot')
>>> o.get_name()
'Sir Lancelot'
```

但如果对象`o`将其存储在全局变量`global_name`中，任何人都可以修改这个全局变量的值而导致`o`的值发生变化：

```python
>>> global_name
'Sir Lancelot'
>>> global_name = 'Sir Gumby'
>>> o.get_name()
'Sir Gumby'
```

调用对象实例`o`的方法`get_name`获取的值被修改了。这可能不是我们想要的，我们需要把对象`o`的值绑定起来，避免干扰全局变量，将其作为一个属性即可。

属性是归属于对象的变量，就像方法一样。对象的方法可能修改这些属性，因此对象将一系列函数(方法)组合起来，并赋予他们访问一些变量(属性)的权限。(封装机制在后面介绍)

### 继承

继承就是一种"偷懒"的方式，为避免输入过多的重复的代码，其实前面介绍的函数，也属于这种方式。

如果你已经拥有了一个类A，现在像创建另一个类B，这个类B要实现的功能其实在类A中已存在，我们就可以让类B继承类A，那么类B也可以使用这个方法。

## 类

### 类到底是什么

类的定义 - 一种对象，每个对象都属于特定的类，并被称为该类的实例。

例如你看到一只鸟，它就属于"鸟类"的一个实例，鸟类是一个非常通用的、抽象的类，它有多个子类，你看到的这个鸟可能属于鸟类的子类 - "云雀"。我们可以将"鸟类"视为所有鸟组成的集合。一个类的对象为另一个类的对象的子集时，我们称前者是后者的子类，反之，后者为前者的超类(父类)

在Python中，我们约定使用单数并将首字母大写，来表示类，比如：`Bird`(鸟类)，`Lark`(云雀类)

类的所有实例都拥有该类的所有方法，因此子类的所有实例都拥有超类的所有方法。

### 创建自定义类

下面我们来创建自定义类：

```python
class Person:
    def set_name(self, name):
        self.name = name

    def get_name(self):
        return self.name

    def greet(self):
        print('Hello, world! I\'m {}.'.format(self.name))
```

创建自定义类，使用关键字`class`，`Person`是类的名称，`class`语句创建独立的命名空间，用于在其中定义方法。`self`参数指向实例对象本身。

```python
>>> foo = Person()
>>> bar = Person()
>>> foo.set_name('Luke Skywalker')
>>> bar.set_name('Anakin Skywalker')
>>> foo.greet()
Hello, world! I'm Luke Skywalker.
>>> bar.greet()
Hello, world! I'm Anakin Skywalker.
```

`self`参数指向了实例对象本身，实际上这个参数名可以是任意字符，不过习惯上将其命名为`self`。

### 属性、函数和方法

方法和函数的区别表现咋参数`self`上。方法将其第一个参数关联到它所属的实例上。

```python
class Bird:
    song = 'Squaawk!'
    def sing(self):
        print(self.song)

>>> bird = Bird()
>>> bird.sing()
Squaawk!
>>> birdsong = bird.sing
>>> birdsong()
Squaawk!
```

### 再谈隐藏

前面的章节我们提到了封装，现在的对象实例中的方法和属性都可以在外部进行访问和修改，这是不合理的。我们应该将那些我们不想让外部知道的属性或方法设定为私有。私有属性或方法不能从对象外部访问，而只能通过存取器，比如上面的`get_name`和`set_name`方法。

Python没有为私有属性提供直接的支持，但我们可以使用其他方法，要让方法或属性称为私有(不能从外部访问),只需让其名称以两个下划线打头即可：

```python
class Secretive:
    def __inaccessible(self):
        print('Bet you can\'t see me ...')

    def accessible(self):
        print('The secret message is: ')
        self.__inaccessible()
```

```python
>>> s = Secretive()
>>> s.__inaccessible()
Traceback (most recent call last):
  File "<pyshell#89>", line 1, in <module>
    s.__inaccessible()
AttributeError: 'Secretive' object has no attribute '__inaccessible'
>>> s.accessible()
The secret message is: 
Bet you can't see me ...
```

现在从外部不能访问`__inaccessible`，但在类中，可以使用它。

### 类的命名空间

在`class`语句中定义的代码都是在一个特殊的命名空间(类的命名空间)内执行的。而类的所有成员都可以访问这个命名空间。

```python
class MemberCounter:
    members = 0
    def init(self):
        MemberCounter.members += 1

>>> m1 = MemberCounter()
>>> m1.init()
>>> MemberCounter.members
1
>>> m2 = MemberCounter()
>>> m2.init()
>>> MemberCounter.members
2
```

上述代码在类作用域内定义了一个变量，所有的成员(实例)都可以访问它，这里使用它来计算类实例的数量。

### 指定超类

子类扩展了超类的定义，要指定超类，可在`class`语句中的类名后加上超类名，并将其用括号括起来。

```python
class Filter:
    def init(self):
        self.blocked = []

    def filter(self, sequence):
        return [x for x in sequence if x not in self.blocked]

class SpamFilter(Filter):  # SpamFilter是Filter的子类
    # 重写超类Filter的方法init
    def init(self):
        self.blocked = ['SPAM']
```

`Filter`类是一个过滤序列的通用类，实际上它不会过滤掉任何数据。它的用途在于可用作其他类的基类(超类)

```python
>>> f = Filter()
>>> f.init()
>>> f.filter([1, 2, 3])
[1, 2, 3]

>>> s = SpamFilter()
>>> s.init()
>>> s.filter(['SPAM', 'SPAM', 'SPAM', 'SPAM', 'eggs', 'bacon', 'SPAM'])
['eggs', 'bacon']
```

在`SpamFilter`类的定义中我们需要注意两点：

- 以提供新定义的方式重写了`Filter`类中的方法`init`的定义
- 直接从`Filter`类继承了方法`filter`的定义，因此无需重写编写其定义。

### 深入讨论继承

要确定一个类是否是另一个类的子类，可使用内置方法`issubclass`

```python
>>> issubclass(SpamFilter, Filter)
True
>>> issubclass(Filter, SpamFilter)
False
```

如果你有一个类，并想知道它的基类，可以访问其特殊属性`__bases__`

```python
>>> SpamFilter.__bases__
(<class '__main__.Filter'>,)
>>> Filter.__bases__
(<class 'object'>,)
```

同时，要确定对象是否是特定类的实例，可使用`isinstance`

```python
>>> s = SpamFilter()
>>> isinstance(s, SpamFilter)
True
>>> isinstance(s, Filter)
True
>>> isinstance(s, str)
False
```

实例对象`s`是`SpamFilter`类的实例，但同时也是`Filter`类的实例，因为`SpamFilter`继承了`Filter`

如果你要熟悉对象属于哪个类，可使用属性`__class__`

```python
>>> s.__class__
<class '__main__.SpamFilter'>
```

### 多个超类

在Python中，一个类是可以继承多个类的，也就是说，一个类可以有多个超类

```python
class Calculator:
    def calculate(self, expression):
        self.value = eval(expression)

class Talker:
    def talk(self):
        print('Hi, my value is', self.value)

class TalkingCalculator(Calculator, Talker):
    pass
```

子类`TalkingCalculator`本身没有任何功能方法，但它可以从超类那里继承，且是从两个不同的超类中继承了两个不同的方法，计算和行走

像这种一个子类继承多个超类的行为，被称为**多重继承**。然后多重继承会带来有一些问题，比如如果不同的超类有着同名的方法，则调用方法时可能不是我们想要的，因为同名的方法会被覆盖。

### 接口和内省

在Python中，我们并不会像Java那样显式的编写接口，而是假定对象能够完成你要求它完成的任务，如果不能完成，程序将失败。

通常，我们要求对象遵循特定的接口(即实现特定的方法)，但我们也可以不是直接调用方法并期待一切顺利，而是检查所需的方法是否存在。

```python
>>> hasattr(tc, 'talk')
True
>>> hasattr(tc, 'fnord')
False
```

上面的示例使用`hasatrr`检测对象实例`tc`中是否包含属性`talk`(指向方法),我们还可以检查属性是否可调用

```python
>>> callable(getattr(tc, 'talk', None))
True
>>> callable(getattr(tc, 'fnord', None))
```

上面使用了`getattr`，它能在我们指定的属性不存在时使用默认值`None`，然后对返回的对象使用`callable`

### 抽象基类

如上面所介绍的，其实手工检查并不是最好的方案。Python通过引入模块abc提供了官方解决方案。这个模块为所谓的抽象基类提供了支持。一般而言，抽象类是不能也不应该被实例化的类，其职责是定义子类应该实现的一组抽象方法。

```python
>>> from abc import ABC, abstractmethod
>>> class Talker(ABC):
	      @abstractmethod
	      def talk(self):
		        pass
```

抽象类(即包含抽象方法的类)最重要的特征是不能被实例化。

```python
>>> t = Talker()
Traceback (most recent call last):
  File "<pyshell#134>", line 1, in <module>
    t = Talker()
TypeError: Can't instantiate abstract class Talker with abstract methods talk
```

但如果从抽象类`Talker`中派生出的子类也没有实现其指定的方法，这个子类也是不能被实例化的。

```python
>>> class Knigget(Talker):
	      pass

>>> Knigget()
Traceback (most recent call last):
  File "<pyshell#138>", line 1, in <module>
    Knigget()
TypeError: Can't instantiate abstract class Knigget with abstract methods talk
```

像下面这样就没有问题：

```python
>>> class Knigget(Talker):
	def talk(self):
		print('Hi!')

		
>>> t = Knigget()
>>> t.talk()
Hi!
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

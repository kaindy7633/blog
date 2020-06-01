# Python之旅：第九章 魔法方法、特性和迭代器

> 在Python中有一些开头和结尾都是两个下划线的方法，这些方法称为魔法(特殊)方法,它们都会在特定的情况下被Python直接调用，如`__init__`,除此之外，本章还会讨论特性(property)和迭代器(iterator)

## 构造函数

构造函数(`constructor`)是一个魔法方法，命名为`__init__`，构造函数不同于普通方法的地方在于，将在对象创建后自动调用它们。下面我们来创建这个构造函数：

```python
class FooBar:
    def __init__(self):
        self.somevar = 42

>>> f = FooBar()  # 实例化后将会自动调用构造函数__init__
>>> f.somevar
42
```

我们也可以给构造函数添加参数：

```python
class FooBar:
    def __init__(self, value=42):
        self.somevar = value

>>> f = FooBar('This is a constructor argument')
>>> f.somevar
'This is a constructor argument'
```

在Python的所有魔法方法中，`__init__`是使用频率最高的。

另外，Python也提供了魔法方法`__del__`，也叫做析构函数(`destructor`)，它主要在对象被销毁前调用，但建议尽可能不要使用它。

### 重写普通方法和特殊的构造函数

Python中的每个类都有一个或多个超类，并从它们那里继承行为，比如，有一个类B，它继承自超类A:

```python
class A:
    def hello(self):
        print('Hello, I\'m A.')

class B(A):
    pass
```

实例化调用：

```python
>>> a = A()
>>> b = B()
>>> a.hello()
Hello, I'm A.
>>> b.hello()
Hello, I'm A.
```

实例化`A`之后调用`hello`方法，能正确打印，实例化类B后，类B并没有`hello`方法，也能正确调用是因为类B继承了超类A中的`hello`方法。

当然，类B也是可以自定义(重写)`hello`方法的：

```python
class B(A):
    def hello(self):
        print('Hello, I\'m B')
```

虽然所有方法的重写机制都相同，但与普通方法相比，重写构造函数时，必须调用超类的构造函数，否则可能无法正确的初始化对象，看下面的例子：

```python
class Bird:
    def __init__(self):
        self.hungry = True

    def eat(self):
        if self.hungry:
            print('Aaaa ...')
            self.hungry = False
        else:
            print('No, thanks!')
```

上面定义了一个鸟类，下面我们来定义个`SongBird`，继承鸟类并新增鸣叫功能：

```python
class SongBird(Bird):
    def __init__(self):
        self.sound = 'Squawk!'

    def sing(self):
        print(self.sound)
```

实例化`SongBird`类，并调用`sing`方法：

```python
>>> sb = SongBird()
>>> sb.sing()
Squawk!
```

没有问题，`SongBird`类继承自`Bird`类，那么是不是也可以调用`Bird`类中的`eat`方法呢？

```python
>>> sb.ear()
Traceback (most recent call last):
  File "<pyshell#32>", line 1, in <module>
    sb.ear()
AttributeError: 'SongBird' object has no attribute 'ear'
```

报错了，要修复这个错误，`SongBird`类的构造函数必须调用其超类(`Bird`)的构造函数，以确保基本的初始化得以执行，为此，有两种方法：调用未关联的超类构造函数，或者使用函数`super`

### 调用未关联的超类构造函数

调用未关联的超类构造函数方法其实是比较老套的方法，在新版的Python中，应使用函数`super`，不过这里也要介绍一下此方法。这种方法很简单，只需要一行代码：

```python
class SongBird(Bird):
    def __init__(self):
        Bird.__init__(self)
        self.sound = 'Squawk!'

    def sing(self):
        print(self.sound)
```

运行结果如下：

```python
>>> sb = SongBird()
>>> sb.sing()
Squawk!
>>> sb.eat()
Aaaa ...
>>> sb.eat()
No, thanks!
```

### 使用函数`super`

如果你使用的是Python3，则应该使用函数`super`，且无需提供任何参数：

```python
class Bird:
    def __init__(self):
        self.hungry = True

    def eat(self):
        if self.hungry:
            print('Aaaa ...')
            self.hungry = False
        else:
            print('No, thanks!')
```

```python
class SongBird(Bird):
    def __init__(self):
        super().__init__()
        self.sound = 'Squawk!'

    def sing(self):
        print(self.sound)
```

运行结果如下：

```python
>>> sb = SongBird()
>>> sb.sing()
Squawk!
>>> sb.eat()
Aaaa ...
>>> sb.eat()
No, thanks!
```

## 元素访问

下面我们将介绍一些魔法方法，它们让你能够创建行为类似于序列或映射的对象。注意：在Python中，**协议**通常指的是规范行为的规则，有点类似于接口。协议指定应实现那些方法以及这些方法应做什么。在其他语言里，可能要求对象属于特定的类或实现了特定的接口，但Python通常只要求对象遵循特定的协议，因此，要成为序列，只需遵循序列协议即可。

### 基本的序列和映射协议

序列和映射基本上是元素(item)的集合，要实现它们的基本行为(协议),不可变对象需要实现2个方法，而可变对象需要实现4个

- `__len__(self)`：这个方法应返回集合包含的项数，对序列来说为元素的个数，对映射来说为键值对的个数，如果它返回零(且没有实现覆盖这种行为的`__nonzero__`)，对象在布尔上下文中将被视为假(就像空列表、空元组、空字符串和空字典一样)

- `__getitem__(self, key)`：这个方法应返回与指定键相关联的值。对于序列来说，键应该是`0~n - 1`的整数(也可以是负数),qizhong `n`为序列的长度，对于映射来说，键可以是任何类型

- `__setitem__(self, key, value)`：这个方法应与键相关联的方式存储值，以便以后可以使用`__getitem__`来获取。仅当对象可变时才需要实现这个方法。

- `__delitem__(self, key)`：这个方法在对对象的组成部分使用`__del__`语句时被调用，应删除与key相关联的值，仅当对象可变时才需要实现这个方法。

下面我们来创建一个无穷序列：

```python
# 定义检查key是否合法的函数
def check_index(key):
    '''
    指定的键是否是可接受的索引？

    键必须是非负整数才是可接受的，如果不是整数，将引发TypeError异常；
    如果是负数，将引发IndexError异常
    '''
    if not isinstance(key, int): raise TypeError
    if key < 0: raise IndexError

# 定义类
class ArithmeticSequence:
    def __init__(self, start=0, step=1):
        '''
        初始化这个算术序列

        start - 序列中的第一个值
        step - 两个相邻值的差
        changed - 一个字典，包含用户修改后的值
        '''
        self.start = start    # 存储起始值
        self.step = step      # 存储步长值
        self.changed = {}     # 没有任何元素被修改

    def __getitem__(self, key):
        '''
        从算术序列中获取一个元素
        '''
        check_index(key)

        try: return self.changed[key]     # 修改过?
        except KeyError:                  # 如果没有修改过
            return self.start + key * self.step     # 计算元素的值

    def __setitem__(self, key, value):
        '''
        修改算术序列中的元素
        '''
        check_index(key)

        self.changed[key] = value     # 存储修改后的值
```

运行结果如下：

```python
>>> s = ArithmeticSequence(1, 2)
>>> s[4]
9
>>> s[4] = 2
>>> s[4]
2
>>> s[5]
11
```

请注意，上面没有定义`__delitem__`方法，是因为要禁止删除元素

```python
>>> del s[4]
Traceback (most recent call last):
  File "<pyshell#39>", line 1, in <module>
    del s[4]
AttributeError: __delitem__
```

另外，这个类也没有`__len__`方法，因为其长度是无穷的。`check_index`方法将检查索引是否非法，如果类型不正确，将引发`TypeError`异常，如果不在允许的范围内，将引发`IndexError`异常

```python
>>> s['four']
Traceback (most recent call last):
  File "<pyshell#40>", line 1, in <module>
    s['four']
  File "<pyshell#31>", line 19, in __getitem__
    check_index(key)
  File "<pyshell#29>", line 8, in check_index
    if not isinstance(key, int): raise TypeError
TypeError
>>> s[-42]
Traceback (most recent call last):
  File "<pyshell#41>", line 1, in <module>
    s[-42]
  File "<pyshell#31>", line 19, in __getitem__
    check_index(key)
  File "<pyshell#29>", line 9, in check_index
    if key < 0: raise IndexError
IndexError
```

### 从`list`、`dict`和`str`派生

除了上面介绍的序列/映射协议的方法之外，序列还有很多其他有用的魔法方法和普通方法，要实现所有这些方法，不仅工作量大，而且难度也不小，如果只是想定制某种操作的行为，就没有理由去重新实现所有其他方法。那该怎么做呢？答案就是**继承**，在标准库中，模块`collections`提供了抽象和具体的基类，但我们也可以继承内置类型，因此要实现一种行为类似于内置列表的序列类型，可以直接继承`list`

```python
class CounterList(list):
    def __init__(self, *args):
        super().__init__(*args)
        self.counter = 0

    def __getitem__(self, index):
        self.counter += 1
        return super(CounterList, self).__getitem__(index)
```

调用如下：

```python
>>> cl = CounterList(range(10))
>>> cl
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
>>> cl.reverse()
>>> cl
[9, 8, 7, 6, 5, 4, 3, 2, 1, 0]
>>> del cl[3:6]
>>> cl
[9, 8, 7, 3, 2, 1, 0]
>>> cl.counter
0
>>> cl[4] + cl[2]
9
>>> cl.counter
2
```

## 特性

在前面我们曾经说过**存取方法**，它们一般都用于获取或设置属性，比如下面的例子：

```python
class Rectangle:
    def __init__(self):
        self.width = 0
        self.height = 0

    def set_size(self, size):
        self.width, self.height = size

    def get_size(self):
        return self.width, self.height
```

调用结果如下：

```python
>>> r = Rectangle()
>>> r.width = 10
>>> r.height = 5
>>> r.get_size()
(10, 5)
>>> r.set_size((150, 100))
>>> r.width
150
```

上面的类编写的没有问题，但有缺陷。如果有一天这个类中的其他属性也需要一些存取方法呢？我们就要重写编写这个类。而给所有的属性都编写一套存取方法也是不现实的。Python能替我们隐藏存取方法，让所有的属性看起来都一样，通过存取方法定义的属性通常称为**特性**(`property`)

在新版的Python中，可以使用函数`property`来实现特性。

### 函数`property`

函数`property`使用起来很简单，如上面的示例，我们仅需加一段代码即可：

```python
class Rectangle:
    def __init__(self):
        self.width = 0
        self.height = 0

    def set_size(self, size):
        self.width, self.height = size

    def get_size(self):
        return self.width, self.height

    size = property(get_size, set_size)
```

我们通过调用函数`property`将存取方法作为参数(获取方法在前，设置方法在后),创建了一个特性，并将名称`size`关联到这个特性。

```python
>>> r = Rectangle()
>>> r.width = 10
>>> r.height = 5
>>> r.size
(10, 5)
>>> r.width
10
```

实际上调用`property`函数时，也可以不传参数、指定一个参数、指定三个参数或指定四个参数。如果没有指定任何参数，则创建的特性既不可读也不可写，如果只指定一个参数(获取方法),创建的方法是只读的，第三个参数是可选的，指定用于删除属性的方法，第四个参数也是可选的，指定一个文档字符串，这些参数分别名为`fget`、`fset`、`fdel`和`doc`。

### 静态方法和类方法

静态方法和类方法是这样创建的：将它们分别包装在`staticmethod`和`classmethod`类的对象中。静态方法的定义中没有参数`self`，可直接通过类来调用。类方法的定义中包含类似于`self`的参数，通常被命名为`cls`，对于类方法，也可以通过对象直接调用，但参数`cls`将自动关联到类。

```python
class MyClass:
    def smeth():
        print('This is a static method')
    smeth = staticmethod(smeth)

    def cmeth(cls):
        print('This is a class method of ', cls)
    cmeth = classmethod(cmeth)
```

上面示例中的包装方法很繁琐，我们可以引入一种名为**装饰器**的新语法，可用于像这样包装方法(装饰器可用于包装任何可调用的对象，并且可用于方法和函数)，可指定一个或多个装饰器，为此可在方法(或函数)前面使用运算符`@`列出这些装饰器。

```python
class MyClass:

    @staticmethod
    def smeth():
        print('This is a static method')

    @classmethod
    def cmeth(cls):
        print('This is a class method of ', cls)
```

定义之后无需实例化可直接实用类名调用：

```python
>>> MyClass.smeth()
This is a static method
>>> MyClass.cmeth()
This is a class method of  <class '__main__.MyClass'>
```

### `__getattr__`和`__setattr__`等方法

`__getattr__`和`__setattr__`等魔法方法可以拦截对对象属性的所有访问，要在属性被访问时执行一段代码，必须使用一些魔法方法,下面的四个魔法方法提供了所有功能：

- `__getattribute__(self, name)`：在属性被访问时自动调用(只适用于新版Python类)

- `__getattr__(self, name)`：在属性被访问时而对象没有这样的属性时自动调用

- `__setattr__(self, name, value)`：试图给属性赋值时自动调用

- `__delattr__(self, name)`：试图删除属性时自动调用

这些魔法方法相对于`property`来讲比较麻烦一些，可能的话，还是尽量使用`property`

```python
class Rectangle:
    delf __init__(self):
        self.width = 0
        self.height = 0

    def __setattr__(self, name, value):
        if name == 'size':
            self.width, self.height = value
        else:
            self.__dict__[name] = value

    def __getattr__(self, name):
        if name == 'size':
            return self.width, self.height
        else:
            raise AttributeError()
```

## 迭代器

### 迭代器协议

迭代(`iterate`)意味着重复多次，就像循环那样，前面我们只使用`for`循环迭代过序列和字典，但实际上也可以迭代其他对象：实现了方法`__iter__`的对象。

方法`__iter__`返回一个迭代器，它是一个包含方法`__next__`的对象，而调用这个方法时可以不提供任何参数，当调用方法`__next__`时，迭代器会返回下一个值。如果迭代器没有课供返回的值，应引发`StopIteration`异常。

那么迭代器有什么意义呢？列表使用`for`循环一样能完成迭代的功能。然后，它们的不同之处在于，列表会存储所有的项，当然会占用过多的内存，而迭代器不会，看下面的例子，我们要做一个斐波那契数列：

```python
class Fibs:
    def __init__(self):
        self.a = 0
        self.b = 1

    def __next__(self):
        self.a, self.b = self.b, self.a + self.b
        return self.a

    def __iter__(self):
        return self
```

上面例子中的迭代器实现了方法`__iter__`，而这个方法返回了迭代器本身。在大多数情况下，都在另一个对象中实现返回迭代器的方法`__iter__`，并在`for`循环中使用这个对象。

```python
>> fibs = Fibs()  # 创建对象，然后在这个对象中使用for循环，找出第一个大于1000的斐波那契数
>>> for f in fibs:
	      if f > 1000:
		        print(f)
		        break

1597
```

我们也可以通过对可迭代对象调用内置函数`iter`，来获得一个迭代器：

```python
>>> it = iter([1, 2, 3])
>>> next(it)
1
>>> next(it)
2
>>> next(it)
3
>>> next(it)
Traceback (most recent call last):
  File "<pyshell#86>", line 1, in <module>
    next(it)
StopIteration
```

### 从迭代器创建序列

迭代器和可迭代对象也可以转换为序列，我们可以使用构造函数`list`显式的将迭代器转换为列表

```python
class TestIterator:
    value = 0
    def __next__(self):
        self.value += 1
        if self.value > 10: raise StopIteration
        return self.value

    def __iter__(self):
        return self
```

```python
>>> ti = TestIterator()
>>> list(ti)
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```

## 生成器

生成器是一个相对较新的Python概念，它也被称为简单生成器。生成器是一个比较复杂的概念，但无论编写什么程序，都可以完全不使用生成器。

简单来说，生成器是一种使用普通函数语法定义的迭代器。

### 创建生成器

创建生成器与创建函数很相似，我们用一个例子来说明，下面是一个列表，列表中的元素也是列表，现在要定义一个函数将其中的元素展开：

```python
nested = [[1, 2], [3, 4], [5]]
```

下面看如何定义这个函数：

```python
def flatten(nested):
    for sublist in nested:
        for element in sublist:
            yield element
```

这个函数很普通，但看到`yield`这样的关键字是不是有点懵？ 包含`yield`语句的函数都被称为**生成器**。虽然它与函数很相似，但功能却截然不同，生成器不是使用`return`返回一个值，而是生成多个值，每次一个。每次使用`yield`生成一个值后，函数将被冻结，即在此停止执行，等待被重新唤醒，被重新唤醒后，函数将从停止的地方开始继续执行。

下面对生成器进行迭代：

```python
>>> nested = [[1, 2], [3, 4], [5]]
>>> for num in flatten(nested):
	      print(num)

1
2
3
4
5
```

或者生成一个列表：

```python
>>> list(flatten(nested))
[1, 2, 3, 4, 5]
```

### 递归式生成器

在上面的例子中，列表只有两层嵌套，如果要处理任意层嵌套的列表呢？这里就要使用到递归了。

```python
def flatten(nested):
    try:
        for sublist in nested:
            for element in flatten(sublist):
                yield element
    except TypeError:
        yield nested
```

一般我们在处理递归时会有两种可能性：基线条件和递归条件。在基线条件下，要求这个函数展开单个元素(比如一个数字),这将引发`TypeError`异常。在递归条件下，需要展开的就是一个列表或其他可迭代对象。

```python
>>> list(flatten([[[1], 2], 3, 4, [5, [6, 7]], 8]))
[1, 2, 3, 4, 5, 6, 7, 8]
```

然后，这个方案存在一个问题，如果参数是一个字符串或类似字符串的对象，它也属于序列，不会引发`TypeError`异常，但我们并不想对它进行迭代。

要处理这个问题，必须在生成器开头进行检查。要检查对象是否类似于字符串，可以将对象与一个空字符串拼接起来，并检查是否会引发`TypeError`异常：

```python
def flatten(nested):
    try:
        # 不迭代类似于字符串的对象
        try: nested + ''
        except TypeError: pass
        else: raise TypeError
        for sublist in nested:
            for element in flatten(sublist):
                yield element
    except TypeError:
        yield nested
```

结果如下：

```python
>>> list(flatten(['foo', ['bar', ['baz']]]))
['foo', 'bar', 'baz']
```

### 通用生成器

生成器是包含关键字`yield`的函数，但被调用时不会执行函数体内的代码，而是返回一个迭代器。每次请求值时，都将执行生成器的代码，直至遇到`yield`或`return`。`yield`意味着应生成一个值，而`return`意味着生成器应停止执行。

生成器由两个单独的部分组成：生成器的函数和生成器的迭代器。生成器的函数是由`def`语句定义，其中包含`yield`，而生成器的迭代器是这个函数返回的结果。

```python
>>> def simple_generator():
  	    yield 1

>>> simple_generator
<function simple_generator at 0x104706f28>
>>> simple_generator()
<generator object simple_generator at 0x112432830>
```

### 生成器的方法

在生成器开始运行后，可使用生成器和外部之间的通信渠道向它提供值。这个通信渠道包含以下两个端点：

- 外部： 外部可访问生成器的方法`send`，这个方法类似于`next`，但可接受一个参数，即要发送的消息，可以是任意对象。

- 生成器：在生成器内部，`yield`可能用作表达式，而不是语句。

- 方法`throw`: 用于在生成器中引发异常，调用时刻提供一个异常类型、一个可选值和一个`traceback`对象。

- 方法`close`：用于停止生成器，调用时无需提供任何参数。

## 八皇后问题

### 生成器的回溯

对于逐步得到结果的复杂递归算法，非常适合使用生成器来实现。要在不使用生成器的情况下实现，通常必须通过额外的参数来传递部分结果，让递归调用能够接着往下计算。通过使用生成器，所有的递归调用都只需生成其负责部分的结果，我们可以使用这种策略来遍历图结构和数结构。

### 问题

八皇后问题：你需要将8个皇后放在棋盘上，条件是任何一个皇后都不能威胁其他皇后(不能同行同列，也不能在一条对角线上)。

这是一个典型的回朔问题：我们可以在棋盘的第一行尝试为第一个皇后选择一个位置，再在第二行尝试为第二个皇后选择一个问题，以此类推，当你发现无法为一个皇后选择合适的位置后，就回朔到前一个皇后，并尝试为它选择另一个位置。

这里我们假设有任意数量的皇后，从而更像现实世界的回朔问题。

### 状态表示

我们可以使用元组(或列表)来表示可能的解，其中每个元素表示相应行中皇后所在的位置(即列)。因此，如果`state[0] == 3`，则表示第一行的皇后放在第4列。在特定的递归层级，也就是皇后的总数，我们只表示各皇后的位置，因此元组长度小于8。

### 检验冲突

我们定义一个函数`conflict`来检查两个皇后之间是否有位置冲突，即不能同行同列，也不能在一条对角线上。

```python
def conflict(state, nextX):
    nextY = len(state)
    for i in range(nextY):
        if abs(state[i] - nextX) in (0, nextY - i):
            return True
    return False
```

参数`nextX`表示下一个皇后的水平位置x，即列，而`nextY`为下一个皇后的垂直坐标y，即行。如果下一个皇后与当前皇后的x坐标相同或在同一对角线上，将发生冲突，返回`True`，否则返回`False`

### 基线条件

看下面的代码：

```python
def queens(num, state):
    if len(state) == num - 1:
        for pos in range(num):
            if not conflict(state, pos):
                yield pos
```

上面这段代码的意思是，如果只剩下最后一个皇后没有放好，就遍历所有可能的位置，并返回那些不会引发冲突的位置。参数`num`为皇后的总数，而参数`state`是一个元组，包含已放好的皇后的位置。

```python
>>> list(queens(4, (1, 3, 0)))
[2]
```

假设有4个皇后，前面3个的排列位置分别是1， 3， 0，也就是第2列，第4列和第1列，那么最后一个皇后的位置就是第3列。

### 递归条件

对于递归调用，向它提供的是由当前行上面的皇后位置组成的元组。对于当前皇后的每个合法位置，递归调用返回的是由下面的皇后位置组成的元组。最终的代码如下：

```python
def queens(num=8, state=()):
    for pos in range(num):
        if not conflict(state, pos):
            if len(state) == num - 1:
                yield (pos,)
            else:
                for result in queens(num, state + (pos,)):
                    yield (pos,) + result
```

结果如下：

```python
>>> list(queens(3))
[]
>>> list(queens(4))
[(1, 3, 0, 2), (2, 0, 3, 1)]
>>> for solution in queens(8):
	      print(solution)

(0, 4, 7, 5, 2, 6, 1, 3)
(0, 5, 7, 2, 6, 3, 1, 4)
(0, 6, 3, 5, 7, 1, 4, 2)
...
(7, 1, 4, 2, 0, 6, 3, 5)
(7, 2, 0, 5, 1, 4, 6, 3)
(7, 3, 0, 2, 5, 1, 6, 4)
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

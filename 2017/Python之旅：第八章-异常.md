<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Python之旅：第八章 异常](#python%E4%B9%8B%E6%97%85%E7%AC%AC%E5%85%AB%E7%AB%A0-%E5%BC%82%E5%B8%B8)
  - [异常是什么](#%E5%BC%82%E5%B8%B8%E6%98%AF%E4%BB%80%E4%B9%88)
  - [让事情沿你指定的轨道出错](#%E8%AE%A9%E4%BA%8B%E6%83%85%E6%B2%BF%E4%BD%A0%E6%8C%87%E5%AE%9A%E7%9A%84%E8%BD%A8%E9%81%93%E5%87%BA%E9%94%99)
    - [raise语句](#raise%E8%AF%AD%E5%8F%A5)
    - [自定义的异常类](#%E8%87%AA%E5%AE%9A%E4%B9%89%E7%9A%84%E5%BC%82%E5%B8%B8%E7%B1%BB)
  - [捕获异常](#%E6%8D%95%E8%8E%B7%E5%BC%82%E5%B8%B8)
    - [不用提供参数](#%E4%B8%8D%E7%94%A8%E6%8F%90%E4%BE%9B%E5%8F%82%E6%95%B0)
    - [多个except子句](#%E5%A4%9A%E4%B8%AAexcept%E5%AD%90%E5%8F%A5)
    - [一箭双雕](#%E4%B8%80%E7%AE%AD%E5%8F%8C%E9%9B%95)
    - [捕获对象](#%E6%8D%95%E8%8E%B7%E5%AF%B9%E8%B1%A1)
    - [一网打尽](#%E4%B8%80%E7%BD%91%E6%89%93%E5%B0%BD)
    - [万事大吉时](#%E4%B8%87%E4%BA%8B%E5%A4%A7%E5%90%89%E6%97%B6)
    - [最后](#%E6%9C%80%E5%90%8E)
  - [异常和函数](#%E5%BC%82%E5%B8%B8%E5%92%8C%E5%87%BD%E6%95%B0)
  - [异常之禅](#%E5%BC%82%E5%B8%B8%E4%B9%8B%E7%A6%85)
  - [不那么异常的情况](#%E4%B8%8D%E9%82%A3%E4%B9%88%E5%BC%82%E5%B8%B8%E7%9A%84%E6%83%85%E5%86%B5)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Python之旅：第八章 异常

## 异常是什么

Python使用**异常对象**来表示异常状态，并在遇到错误时引发异常，异常对象未被处理(捕获)时，程序将终止并显示一条错误信息：

```py
>>> 1 / 0
Traceback (most recent call last):
  File "<pyshell#147>", line 1, in <module>
    1 / 0
ZeroDivisionError: division by zero
```

每个异常都是`ZeroDivisionError`类的实例，我们可以使用各种方式引发和捕获这些实例，从而采取措施而不是放任整个程序失败。

## 让事情沿你指定的轨道出错

### raise语句

在Python中，我们可以使用`raise`语句来引发异常，并将一个类(必须是`Exception`类的子类)或实例作为参数，将类作为参数时，将自动创建一个实例。下面的示例使用的是内置异常类`Exception`:

```py
>>> raise Exception
Traceback (most recent call last):
  File "<pyshell#148>", line 1, in <module>
    raise Exception
Exception

>>> raise Exception('hyperdrive overload')
Traceback (most recent call last):
  File "<pyshell#149>", line 1, in <module>
    raise Exception('hyperdrive overload')
Exception: hyperdrive overload
```

Python内置了很多异常类，下表描述了一些重要的，这些异常类都可以用于`raise`语句。

| 类名 | 描述 |
| --- | --- |
| `Exception` | 几乎所有的异常类都是从它派生而来的 |
| `AttributeError` | 引用属性或给它赋值失败时引发 |
| `OSError` | 操作系统不能执行指定的任务时触发，有多个子类 |
| `IndexError` | 使用序列中不存在的索引时触发，为`LookupError`的子类 |
| `KeyError` | 使用映射中不存在的键时触发，为`LookupError`的子类 |
| `NameError` | 找不到名称(变量)时引发 |
| `TypeError` | 将内置操作或函数用于不正确的对象时引发 |
| `ValueError` | 将内置操作或函数用于这样的对象时引发：其类型正确但包含的值不合适 |
| `ZeroDivisionError` | 在除法或求模运算的第二个参数为零时引发 |

### 自定义的异常类

虽然Python内置了大量的异常类，供我们使用，但有时也需要我们自定义异常类，创建自定义异常类，跟创建其他类一样，只是需要直接或间接的继承`Exception`类(从其他的异常类派生也是可以的，因为所有的异常类都派生自`Exception`类):

```py
class SomeCustomException(Exception): pass
```

如果有需要，也可以在自定义异常类中添加方法。

## 捕获异常

在Python中，我们可以使用`try/except`语句来捕获异常，比如我们有一段程序，让用户输入两个数，然后将它们相除，如果用户输入的第二个数为零，则我们需要捕获这个异常：

```py
try:
    x = int(input('Enter the first number: '))
    y = int(input('Enter the second number: '))
    print(x / y)
except ZeroDivisionError:
    print('The second number can\'t be zero!')
```

执行结果如下，我们对这种情况友好的做了提示：

```py
Enter the first number: 2
Enter the second number: 0
The second number can't be zero!
```

好像这种情况使用`if`语句更简单，但如果程序很庞大，里面有多个像这样的计算任务，使用一个`try/except`就可以捕获所有的错误。

**注意**：异常是从函数向外传播到调用函数的地方的，如果异常在这里没有被捕获，那么它将向程序的最顶层传播。

### 不用提供参数

捕获异常后，如果要重新引发它(继续向上传播)，可调用`raise`且不提供任何参数。

```py
class MuffleCalculator:
    muffled = False
    def calc(self, expr):
        try:
            return eval(expr)
        except ZeroDivisionError:
            # 带有’抑制‘功能
            if self.muffled:
                print('Division by zero is illegal')
            else:
                raise
```

上面的例子运行如下：

```py
>>> calculator = MuffleCalculator()
>>> calculator.calc('10 / 2')
5.0
>>> calculator.calc('10 / 0')
Traceback (most recent call last):
  File "<pyshell#159>", line 1, in <module>
    calculator.calc('10 / 0')
  File "<pyshell#155>", line 5, in calc
    return eval(expr)
  File "<string>", line 1, in <module>
ZeroDivisionError: division by zero  # 关闭抑制功能，捕获了异常，但继续向上传播
>>> calculator.muffled = True
>>> calculator.calc('10 / 0')
Division by zero is illegal
```

### 多个except子句

如果程序需要同时捕获多个异常，我们可以在`try/except`语句中再添加一个`except`子句：

```py
try:
    x = int(input('Enter the first number: '))
    y = int(input('Enter the second number: '))
    print(x / y)
except ZeroDivisionError:
    print('The second number can\'t be zero!')
except TypeError:
    print('That wasn\'t a number, was it?')
```

### 一箭双雕

如果我们只想使用一个`except`语句来捕获多个异常呢？可以在一个元组中指定这些异常。

```py
try:
    x = int(input('Enter the first number: '))
    y = int(input('Enter the second number: '))
    print(x / y)
except (ZeroDivisionError, TypeError, NameError):
    print('Your numbers were bogus ...')
```

### 捕获对象

要在`except`子句中访问异常对象本身，可使用两个二不是一个参数，这种方式可以让程序继续运行并记录错误：

```py
try:
    x = int(input('Enter the first number: '))
    y = int(input('Enter the second number: '))
    print(x / y)
except (ZeroDivisionError, TypeError) as e:
    print(e)
```

### 一网打尽

如果我们不在`except`语句中指定任何异常类，那么我们将可以捕获所有的异常：

```py
try:
    x = int(input('Enter the first number: '))
    y = int(input('Enter the second number: '))
    print(x / y)
except:
    print('Something wrong happended ...')
```

使用这样的方式并不是很好，因为这样不仅会隐藏我们已知的错误，还会隐藏我们没有考虑到的错误。所以，在大多数情况下，更好的选择是使用`execpt Exception as e`并对异常对象进行检查。

### 万事大吉时

我们还可以给`try/execpt`语句加上一个`else`子句，当没有异常发生时，`else`里的语句将会被执行。

```py
try:
    print('A simple task')
except:
    print('What? Something went wrong?')
else:
    print('Ah... It went as planned.')
```

使用`else`子句，可以实现前面的一个循环获取用户输入的示例，只有当没有引发异常时，才会跳出循环，如果用户输入错误，则会一直提示用户输入：

```py
while True:
    try:
        x = int(input('Enter the first number: '))
        y = int(input('Enter the second number: '))
        value = x / y
        print('x / y is ', value)
    except:
        print('Invalid input. Please try again.')
    else:
        break
```

运行结果如下：

```py
Enter the first number: 1
Enter the second number: 0
Invalid input. Please try again.
Enter the first number: foo
Invalid input. Please try again.
Enter the first number: 'foo'
Invalid input. Please try again.
Enter the first number: 10
Enter the second number: 2
x / y is  5.0
```

我们也可以使用`except Exception as e`这种方式打印更有用的错误信息：

```py
while True:
    try:
        x = int(input('Enter the first number: '))
        y = int(input('Enter the second number: '))
        value = x / y
        print('x / y is ', value)
    except Exception as e:
        print('Invalid input: ', e)
        print('Please try again')
    else:
        break
```

运行结果如下：

```py
Enter the first number: 1
Enter the second number: 0
Invalid input:  division by zero
Please try again
Enter the first number: 'x'
Invalid input:  invalid literal for int() with base 10: "'x'"
Please try again
Enter the first number: 10
Enter the second number: 2
x / y is  5.0
```

### 最后

最后，还有一个`finally`子句，它可用于在发生异常时执行清理工作，这个子句是与`try`子句配套的。

```py
x = None
try:
    x = 1 / 0
finally:
    print('Clearing up ...')
    del x
```

不管`try`子句中发生什么异常，都将执行`finally`子句。`finally`子句也非常适合用于确保文件或网络套接字被关闭。

我们也可以在一条语句中同时包含`try`、`except`、`finally`和`else`,或其中的3个

```py
try:
    1 / 0
except NameError:
    print('Unknown variable')
else:
    print('That went well!')
finally:
    print('Clearing up.')
```

## 异常和函数

通常如果不处理在函数中引发的异常，它就会向上传播到调用函数的地方，如果那里也未得到处理，异常将继续传播，直至到达主程序(全局作用域),如果主程序也没有异常处理，那么程序将终止并显示栈跟踪信息。

```py
>>> def faulty():
        raise Exception('Something is wrong')

>>> def ignore_exception():
        faulty()

>>> def handle_exception():
        try:
            faulty()
        except:
            print('Exception handled!')
```

调用结果如下：

```py
>>> ignore_exception()
Traceback (most recent call last):
  File "<pyshell#178>", line 1, in <module>
    ignore_exception()
  File "<pyshell#175>", line 2, in ignore_exception
    faulty()
  File "<pyshell#173>", line 2, in faulty
    raise Exception('Something is wrong')
Exception: Something is wrong
>>> handle_exception()
Exception handled!
```

## 异常之禅

如果你知道代码可能引发某种异常，且不希望出现这种异常时程序终止并系那是栈跟踪信息，可以添加必要的`try/except`或`try/finally`语句来处理它。

有时候你可能觉得使用`if/else`更自然一些，但使用`try/except`要比`if/else`效率更高。例如我们要打印某人的信息，且参数传入了一个字典：

```py
def describe_person(person):
    print('Description of ', person['name'])
    print('Age: ', person['age'])
    if 'occupation' in person:
        print('Occupation: ', person['occupation'])
```

像上面的这段代码，程序必须两次检查`occupation`键是否存在于参数字典`person`中，一次检查，一次调用。如果我们换成`try/except`来完成，则效率更高：

```py
def describe_person(person):
    print('Description of ', person['name'])
    print('Age: ', person['age'])
    try:
        print('Occupation: ', person['occupation'])
    except KeyError: pass
```

往往在检查对象是否包含特定的属性时，`try/except`就很有用。然而，这种效率方面的提升并不明显，但使用`try/except`更符合Python风格，因此我们应养成多使用它的习惯。

## 不那么异常的情况

如果我们想在程序运行出现问题时发出警告，则可以使用模块`warnings`中的函数`warn`

```py
>>> from warnings import warn
>>> warn('I\'ve got a bad feeling about this.')

Warning (from warnings module):
  File "__main__", line 1
UserWarning: I've got a bad feeling about this.
```

我们也可以使用`warnings`中的函数`filterwarnings`来抑制你发出的警告并指定要采取的措施

```py
>>> from warnings import filterwarnings
>>> filterwarnings('ignore')
>>> warn('ANyone out there?')
>>> filterwarnings('error')
>>> warn('Something is very wrong!')
Traceback (most recent call last):
  File "<pyshell#8>", line 1, in <module>
    warn('Something is very wrong!')
UserWarning: Something is very wrong!
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

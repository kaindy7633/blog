<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Python之旅：第十三章 数据库支持](#python%E4%B9%8B%E6%97%85%E7%AC%AC%E5%8D%81%E4%B8%89%E7%AB%A0-%E6%95%B0%E6%8D%AE%E5%BA%93%E6%94%AF%E6%8C%81)
  - [Python数据库API](#python%E6%95%B0%E6%8D%AE%E5%BA%93api)
    - [全局变量](#%E5%85%A8%E5%B1%80%E5%8F%98%E9%87%8F)
    - [异常](#%E5%BC%82%E5%B8%B8)
    - [连接和游标](#%E8%BF%9E%E6%8E%A5%E5%92%8C%E6%B8%B8%E6%A0%87)
    - [类型](#%E7%B1%BB%E5%9E%8B)
  - [SQLite和PySQLite](#sqlite%E5%92%8Cpysqlite)
    - [起步](#%E8%B5%B7%E6%AD%A5)
    - [数据库应用程序示例](#%E6%95%B0%E6%8D%AE%E5%BA%93%E5%BA%94%E7%94%A8%E7%A8%8B%E5%BA%8F%E7%A4%BA%E4%BE%8B)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Python之旅：第十三章 数据库支持

> Python支持对多种数据库的访问操作，它支持数据并发访问，并允许多个用户读写磁盘数据，也可以根据多个数据字段或属性进行复杂的搜索。本章将谈论Python数据库API，一种链接到SQL数据库的标准化方式，并演示如何使用这个API来执行一些基本的SQL操作。当然除了SQL数据库，Python也支持访问对象数据库，或一些NOSQL数据库，比如MongoDB等。

## Python数据库API

在Python中，有一个标准数据库API(DB API)。

### 全局变量

所有与DB API 2.0兼容的数据库模块都必须包含三个全局变量，它们描述了模块的特征。如果要让程序能够使用多种不同的数据库，可能比较麻烦，一种更现实的做法是检查这些变量，看看给定的模块是否是程序能够接受的，如果不是，就显示何时的错误信息并退出或引发异常。

| 变量名 | 描述 |
| ----- | --- |
| `apilevel` | 使用的Python DB API版本 |
| `threadsafety` | 模块的线程安全程序如何 |
| `paramstyle` | 在SQL查询中使用哪种参数风格 |

API级别(`apilevel`)是一个字符串常量，它指出了使用的API版本。在DB API 2.0中，这个变量的值为`1.0`或`2.0`,如果没有这个变量，就说明模块不与DB API2.0兼容。

线程安全程度(threadsafety)是一个0~3(含)的整数：

- 0表示线程不能共享模块
- 1表示线程可共享模块本身，但不能共享连接。
- 2表示线程可共享模块和连接，但不能共享游标。
- 3表示线程是绝对安全的。

参数风格(paramstyle)表示当你执行多个类似的数据库查询时，如何在SQL查询中插入参数。

### 异常

DB API定义了多种异常，这些异常构成了一个层次结构，因此使用一个`except`块就可捕获多种异常。

| 异常 | 超类 | 描述 |
| --- | --- | --- |
| `StandardError` |  | 所有异常的超类 |
| `Warning` | `StandardError` | 发生非致命问题时引发 |
| `Error` | `StandardError` | 所有错误条件的超类 |
| `InterfaceError` | `Error` | 与接口(而不是数据库)相关的错误 |
| `DatabaseError` | `Error` | 与数据库相关的错误的超类 |
| `DataError` | `DatabaseError` | 与数据相关的问题，如值不再合法的范围内 |
| `OperationalError` | `DatabaseError` | 数据库操作内部的错误 |
| `IntegrityError` | `DatabaseError` | 关系完整性遭到破坏，如键未通过检查 |
| `InternalError` | `DatabaseError` | 数据库内部的错误，如游标无效 |
| `ProgrammingError` | `DatabaseError` | 用户编程错误，如未找到数据库表 |
| `NotSupportedError` | `DatabaseError` | 请求不支持的功能，如回滚 |

### 连接和游标

要使用底层的数据库系统，必须先连接到它，连接数据库使用函数`connect`,这个函数接收多个参数：

| 参数名 | 描述 | 是否可选 |
| ----- | --- | ------- |
| `dsn` | 数据源名称，具体含义随数据库而异 | 否 |
| `user` | 用户名 | 是 |
| `password` | 用户密码 | 是 |
| `host` | 主机名 | 是 |
| `database` | 数据库名称 | 是 |

函数`connect`返回一个连接对象，表示当前到数据库的会话，这个对象有如下方法：

| 方法名 | 描述 |
| ----- | --- |
| `close()` | 关闭连接对象，之后连接对象及其游标将不可用 |
| `commit()` | 提交事务，如果当前数据库支持的话，否则什么都不做 |
| `rollback()` | 回滚未提交的事务，可能不可用 |
| `cursor()` | 返回连接的游标对象 |

方法`rollback`可能不可用，因为并非所有的数据库都支持事务。如果可用，这个方法将撤销所有未提交的事务。

方法`commit`总是可用的，它提交未提交的事务，但如果数据库不支持事务，则什么都不做。

方法`cursor`返回当前的游标对象。我们可以使用游标对象来执行SQL查询和查看结果：

| 名称 | 描述 |
| --- | --- |
| `callproc(name[, params])` | 使用指定的参数调用指定的数据库过程 |
| `close()` | 关闭游标，之后游标不可用 |
| `execute(oper[, params])` | 执行一个SQL操作 |
| `executemany(oper, pseq)` | 多次执行指定的SQL操作 |
| `fetchone()` | 以序列的方式取回查询结果中的下一行，如果没有更多行，则返回`None` |
| `fetchall()` | 以序列的方式取回余下的所有行 |
| `nextset()` | 跳到下一个结果集 |
| `setinputsizes(sizes)` | 用于为参数预定义内存区域 |
| `setoutputsize(size[, col])` | 为取回大量数据而设置缓冲区长度 |

游标对象的属性如下：

| 名称 | 描述 |
| --- | --- |
| `description` | 由结果列描述组成的序列(只读) |
| `rowcount` | 结果包含的行数(只读) |
| `arraysize` | `fetchmany`返回的行数，默认为1 |

### 类型

对于插入到某些类型的列中的值，底层SQL数据库可能要求它们满足一定的条件，为了能够与底层SQL数据库正确的互操作，DB API定义了一些构造函数和常量，用于提供特殊的类型和值。比如要在数据库添加日期，应使用相应数据库连接模块中的构造函数`Date`来创建它。

| 名称 | 描述 |
| --- | --- |
| `Date(year, month, day)` | 创建包含日期值的对象 |
| `Time(hour, minute, second)` | 创建包含时间值的对象 |
| `Timestamp(y, mon, d, h, min, s)` | 创建包含时间戳的对象 |
| `DateFromTIcks(ticks)` | 根据从新纪元开始过去的秒数创建包含日期值的对象 |
| `TimeFromTicks(ticks)` | 根据从新纪元开始过去的秒数创建包含时间值的对象 |
| `imestampFromTicks(ticks)` | 根据从新纪元开始过去的秒数创建包含时间戳的对象 |
| `Binary(string)` | 创建包含二进制字符串值的对象 |
| `STRING` | 描述基于字符串的列(如CHAR) |
| `BINARY` | 描述二进制列(如LONG或RAW) |
| `NUMBER` | 描述数字列 |
| `DATETIME` | 描述日期/时间列 |
| `ROWID` | 描述行ID列 |

## SQLite和PySQLite

在新版本的Python中，标准库包含了一个SQLite包装器：使用模块`sqlite3`实现的`PySQLite`。

### 起步

要使用Python标准库中的SQLite，可导入模块`sqlite3`，然后，你就可以创建直接到数据库文件的连接，为此，你只需提供一个文件名(它可以是文件的相对路径或绝对路径),如果指定的文件不存在，将自动创建它。

```python
>>> import sqlite3
>>> conn = sqlite3.connect('somedatabase.db')
```

接下来我们可以从连接获取游标：

```python
>>> curs = conn.cursor()
```

这个游标可用来执行SQL查询，执行完查询后，如果修改了数据，务必提交所做的修改，这样才会将其保存到文件中。

```python
# 提交修改
>>> conn.commit()
```

要关闭连接，可以使用`close`方法

```python
>>> conn.close()
```

### 数据库应用程序示例

```python
import sqlite3

def convert(value):
    if value.startswith('~'):
        return value.strip('~')
    if not value:
        value = '0'
    return float(value)

conn = sqlite3.connect('/Users/liuzhen/python/food.db')
curs = conn.cursor()

curs.execute('''
CREATE TABLE food (
id TEXT PRIMARY KEY,
desc TEXT,
water FLOAT,
kcal FLOAT,
protein FLOAT,
fat FLOAT,
ash FLOAT,
carbs FLOAT,
fiber FLOAT,
sugar FLOAT
)
''')

query = 'INSERT INTO food VALUES (?,?,?,?,?,?,?,?,?,?)'
field_count = 10
for line in open('/Users/liuzhen/python/ABBREV.TXT'):
    fields = line.split('^')
    vals = [convert(f) for f in fields[:field_count]]
    curs.execute(query, vals)

conn.commit()
conn.close()
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

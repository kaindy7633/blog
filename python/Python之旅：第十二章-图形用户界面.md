<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Python之旅：第十二章-图形用户界面/](#python%E4%B9%8B%E6%97%85%E7%AC%AC%E5%8D%81%E4%BA%8C%E7%AB%A0-%E5%9B%BE%E5%BD%A2%E7%94%A8%E6%88%B7%E7%95%8C%E9%9D%A2)
  - [创建GUI示例程序](#%E5%88%9B%E5%BB%BAgui%E7%A4%BA%E4%BE%8B%E7%A8%8B%E5%BA%8F)
    - [初探](#%E5%88%9D%E6%8E%A2)
    - [布局](#%E5%B8%83%E5%B1%80)
    - [事件处理](#%E4%BA%8B%E4%BB%B6%E5%A4%84%E7%90%86)
    - [最终程序](#%E6%9C%80%E7%BB%88%E7%A8%8B%E5%BA%8F)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Python之旅：第十二章-图形用户界面/

> 本章将简短的介绍Python程序创建图形用户界面(GUI)的基本知识。GUI就是包含按钮、文本框等空间的窗口。`Tkinter`是Python标准的GUI工具包，包含在Python的标准安装中。

## 创建GUI示例程序

为了演示`Tkinter`的用法，我们将创建一个简单的GUI应用程序，这个程序是一个非常简单的文本编辑器。它主要有以下功能：

- 让用户能打开指定的文本文件
- 让用户能编辑文本文件
- 让用户能保存文本文件
- 让用户能退出程序

### 初探

首先，我们必须导入`tkinter`，为保留其命名空间，也可以对其重命名。

```python
>>> import tkinter as tk
```

当然，如果你愿意，也可以导入整个模块的所有内容

```python
>>> from tkinter import *
```

我们在交互式解释器上做这些工作，要创建GUI，可创建一个充当主窗口的顶级组件(控件),为此，可实例化一个`TK`对象。

```python
>>> top = tk.Tk()
```

此时将出现一个窗口，在常规程序中，我们将调用函数`mainloop`以进入`Tkinter`主事件循环，而不是直接退出程序。

```python
>>> mainloop()
```

现在我们来创建一个按钮，可直接调用实例`tk`中的`Button`方法来创建,然后使用`pack`方法来布局

```python
>>> btn = tk.Button()
>>> btn.pack()
```

这时你应该能看到一个空白的按钮出现在GUI窗口上了，不过这个按钮还没有文本，我们来添加一个

```python
>>> btn['text'] = 'Click me!'
```

同时，我们也可以给这个按钮添加行为，先定义一个函数，然后将这个函数应用到这个按钮上

```python
def clicked():
    print('I was clicked!')

>>> btn['command'] = clicked
```

我们也可以使用方法`config`来为`btn`同时添加多个属性，而不是一个一个地添加

```python
>>> btn.config(text='Click me!', command=clicked)
```

同时，你也可以使用控件的构造函数来配置控件的各种属性

```python
>>> Button(text='Click me too!', commang=clicked).pack()
```

### 布局

控件调用方法`pack`时，将把控件放在其父控件(主控件)中，要指定主控件，可使用构造函数的第一个可选参数，如果没有指定，则会把顶级主窗口用作主控件

```python
Label(text='I am in the first window!').pack()
second = Toplevel()
Label(second, text="I'm in the second window!").pack()
```

`pack()`方法提供多个参数来控制控件摆放的位置，比如可将参数`side`设置为`LEFT`,`RIGHT`,`TOP`和`BOTTOM`,要让控件在`x`或`y`方向上填满分配给它的空间，可将参数`fill`设置为`x`、`y`或`BOTH`。要让控件随父控件一起增大，可将参数`expand`设置为`True`。如果还想知道更多个选项，可以使用`help`查看

```python
>>> help(Pack.config)
```

布局管理器除了`pack`，还有`grid`和`place`。

### 事件处理

从前面的示例我们知道，可以通过设置属性`command`为按钮指定动作,这是一种特殊的事件处理，但`Tkinter`还为我们提供了更通用的事件处理机制：`bind`，要让控件对特定的事件进行处理，可对其调用方法`bind`，并指定事件的名称和要使用的函数。

```python
>>> import tkinter as tk
>>> top = tk.Tk()
>>> def callback(event):
	    print(event.x, event.y)

>>> top.bind('<Button-1>', callback)
'4591238472callback'
```

### 最终程序

要创建单行文本框，可使用控件`Entry`，要创建可滚动的多行文本区域，可结合使用控件`Text`和`Scrollbar`，但模块`tkinter.scrolledtext`已提供了一种实现。要提取`Entry`控件的内容，可使用其方法`get`，对于`ScrolledText`对象，我们将使用其方法`delete`和`insert`来删除文本。

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
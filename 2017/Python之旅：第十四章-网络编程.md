# Python之旅：第十四章 网络编程

> Python提供了强大的网络编程支持，有很多库实现了常见的网络协议以及基于这些协议的抽象层，让你能够专注于程序的逻辑。

## 几个网络模块

### 模块socket

网络编程中的一个基本组件是**套接字**(`socket`)。套接字是一个信息通道，两端各有一个程序，这些程序位于通过网络连接的不同的计算机上，通过套接字向对方发送消息。

套接字分为两类：服务器套接字和客户端套接字。创建服务器套接字后，它会在某个网络地址进行监听以等待连接请求的到来，直到客户端套接字建立连接，随后，它们就可以通信了。

套接字是模块`socket`中`socket`类的实例。实例化套接字时可指定三个参数：

- 地址族，默认为`socket.AF_INET`
- 类型，是流套接字(`socket.SOCK_STREAM`,默认设置)还是数据报套接字(`socket.SOCK_DGRAM`)
- 协议，使用默认值0

创建普通套接字时，不用提供任何参数。

服务器套接字先调用方法`bind`，再调用方法`listen`来监听特定的地址，然后客户端套接字就可以使用方法`connect`，并提供服务器监听的地址，来连接服务器了。

服务器套接字开始监听后，就可以接收客户端的连接了，这是使用方法`accept`来完成的。当连接到来时，这个方法将阻断，然后返回一个格式为(`client`, `address`)的元组，最后服务器再次调用`accept`以等待新的连接到来。

为传输数据，套接字提供了两个方法：`send`和`recv`。要发送数据，可调用方法`send`并提供一个字符串，要接收数据，可调用`recv`并制定最多接收多少字节的数据，通常1024就可以了。

```python
# 最简单的服务器
import socket
s = socket.socket()

host = socket.gethostname()
port = 1234
s.bind((host, port))

s.listen(5)
while True:
    c, addr = s.accept()
    print('GOT connection from ', addr)
    c.send('Thank you for connecting')
    c.close()
```

```python
# 最简单的客户端
import socket

s = socket.socket()

host = sockent.gethostname()
port = 1234

s.connect((host, port))
print(s.recv(1024))
```

### 模块urllib和urllib2

这两个网络模块能够让你通过网络访问文件。它们的功能很相似，对于简单的下载，使用`urllib`就足够了，如果要实现HTTP身份验证或`Cookie`，又或者血药编写扩展来处理自己的协议，就需要`urllib2`了。

#### 打开远程文件

我们可以使用`urllib`模块轻松的打开远程文件，但只能使用读取模式，跟打开本地文件使用`open`方法不一样，打开远程文件需要使用`urllib.request`中的函数`urlopen`

```python
>>> from urllib.request import urlopen
>>> webpage = urlopen('http://www.python.org')
```

变量`webpage`将包含一个类似于文件的对象。这个独享支持方法`close`、`read`、`readline`和`readlines`，还支持迭代。

#### 获取远程文件

函数`urlopen`返回一个类似于文件的对象，可从中读取数据。如果要下载文件，并将其副本存储在一个本地文件中，可使用`urlretrieve`，这个函数返回一个格式为`(filename, headers)`的元组。`filename`是本地文件的名称，而`headers`包含一些远程文件的信息。如果要给下载的副本指定文件名，可以通过第二个参数来指定。

```python
>>> urlretrieve('http://www.python.org', '/Users/liuzhen/python/python_webpage.html')
```

## SocketServer及相关的类

模块`SocketServer`是Python标准库提供的服务器框架的基石，这个框架包括`BaseHTTPServer`、`SimpleHTTPServer`、`CGIHTTPServer`、`SimpleXMLRPCServer`和`DocXMLRPCServer`等服务器。

`SocketServer`包含4个基本的服务器：`TCPServer`、`UDPServer`,以及很难懂的`UnixStreamServer`和`UnixDatagramServer`。后面3个我们基本上用不上。

```python
# 基于SocketServer的极简服务器
from socketserver import TCPServer, StreamRequestHandler

class Handler(StreamRequestHandler):
    def handle(self):
        addr = self.request.getpeername()
        print('Got connection from ', addr)
        self.wfile.write('Thank you for connecting')

server = TCPServer(('', 1234), Handler)
server.serve_forever()
```

## 多个连接

前面创建的网络链接方式都是同步的，也就是不能同时处理多个连接。若想要处理多个连接，主要有三种方式：分叉(`forking`)、线程化和异步I/O。分叉占用的资源较多，而线程化会带来同步问题。

分叉是一个UNIX术语，对进程进行分叉时，基本上是复制它，而这样得到的两个进程都从当前位置开始继续往下执行，且每个进程都有自己的内存副本。原来的进程为父进程，复制的进程为子进程。在分叉服务器中，对于每个客户端的连接，都将通过分叉创建一个子进程。父进程继续监听新连接，而子进程负责处理客户端请求，客户端请求结束后，子进程直接退出。

分叉占用的资源比较多，还有另一种解决方案：线程化。线程是轻量级进程，都位于同一进程中并共享内存，这减少了资源占用，但也带来了缺点：由于线程共享内存，你必须确保它们不会彼此干扰或同时修改同一项数据，否则将引起混乱，这些问题都属于同步问题。

### 使用SocketServer实现分叉和线程化

```python
# 分叉服务器
from socketserver import TCPServer, ForkingMixIn, StreamRequestHandler

class Server(ForkingMixIn, TCPServer): pass

class Handler(StreamRequestHandler):
    def handle(self):
        addr = self.request.getpeername()
        print('Got connection from ', addr)
        self.wfile.write('Thank you for connecting')

server = Server(('', 1234), handler)
server.serve_forever()
```

```python
# 线程化服务器
from socketserver import TCPServer, ThreadingMixIn, StreamRequestHandler

class Server(ThreadingMinIn, TCPServer): pass

class Handler(StreamRequestHandler):
    def handle(self):
        addr = self.request.getpeername()
        print('Got connection from ', addr)
        self.wfile.write('Thank you for connecting')

server = Server(('', 1234), Handler)
server.serve_forever()
```

### 使用select和poll实现异步IO

异步I/O就是只处理当前正在通信的客户端，无需监听，只需监听后将客户端加入队列即可。这就是框架`asyncore/asynchat`和`Twisted`采用的方法。这种功能的基础是函数`select`或`poll`，它们都位于模块`select`中，其中`poll`可伸缩性更高，但只有UNIX系统支持它。

函数`select`接收三个必不可少的参数和一个可选参数，其中前三个参数为序列，而第四个参数为超时时间。

```python
# 使用select的简单服务器
import socket, select

s = socket.socket()

host = socket.gethostname()
port = 1234
s.bind((host, port))
s.listen(5)
inputs = [s]
while True:
    rs, ws, es = select.select(inputs, [], [])
    for r in rs:
        if r is s:
            c, addr = s.accept()
            print('Got connection from ', addr)
            inputs.append(c)
    else:
        try:
            data = r.recv(1024)
            disconnected = not data
        except socket.error:
            disconnected = True

        if disconnected:
            print(r.getpeername(), 'disconnected')
            inputs.remove(r)
        else:
            print(data)
```

使用`poll`比`select`更容易。调用`poll`时，返回一个轮询对象，你可以使用方法`register`向这个对象注册文件描述符，注册后可使用方法`unregister`将它们删除。注册对象后，就可以调用其方法`poll`。

```python
# 使用poll的简单服务器
import socket, select

s = socket.socket()

host = socket.gethostname()
port = 1234
s.bind((host, port))

fdmap = {s.fileno():s}

s.listen(5)
p = select.poll()
p.register(s)
while True:
    events = p.opll()
    for fd, event inevents:
        if fd in fdmap:
            c, addr = s.accept()
            print('Got connection from ', addr)
            p.register(c)
            fdmap[c.fileno()] = c
        elif event & select.POLLIN:
            data = fdmap[fd].recv(1024)
            if not data: # 没有数据 - 链接已关闭
                print(fdmap[fd].getpeername(), 'disconnected')
                p.unregister(fd)
                del fdmap[fd]
            else:
                print(data)
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



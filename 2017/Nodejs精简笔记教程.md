# Nodejs权威指南读书笔记

## Nodejs介绍

`Nodejs`的目标是提供一种简单的、用于创建高性能服务器及可在该服务器中运行的各种应用程序的开发工具。

`Nodejs`可实现高性能服务器，V8 JavaScript引擎为`Node`提供底层支持。

它是非阻塞型I/O和基于事件环机制的。

我们可以通过`require`函数来引用模块，使用`exports`将模块暴露出去。

`Nodejs`包含了一些核心模块

- fs 用于操作文件及文件系统
- events 为事件处理提供一个基础类
- crypto 用于实现数据的加密解密处理
- buffer 用于实现二进制数据的存储与转换
- child_process 用于实现子进程的创建于管理
- http 用于实现HTTP服务器端及客户端
- https 用于实现HTTPS服务器端和客户端
- path 用于处理文件路径
- querystring 用于处理HTTP请求中使用的查询字符串

在`Nodejs`中，可以直接使用`require`函数来引用这些模块

```js
var http = require('http')
```

`Nodejs`中的一些类、函数和对象

| 类、函数及对象 | 描述 |
| :------------ | :--- |
| Buffer类 | 用于为二进制数据的存储提供一个缓冲区 |
| setTimeout函数 | 用于在指定时间到达时执行一个指定函数 |
| clearTimeout函数 | 用于取消在setTimeout函数内指定的函数的执行 |
| setInterval函数 | 用于指定每隔多少时间执行一个指定函数 |
| clearInterval函数 | 用于取消在setInterval函数内指定的函数执行 |
| require函数 | 用户加载模块 |
| module对象 | 用于访问模块信息 |
| process对象 | 用于访问进程信息 |

一个简单的示例：

```js
var http = require('http')

http.createServer(function (req, res) {
  res.writeHead(200, {'Content-Type': 'text/html'})
  res.write('<head><meta charset="utf-8"/>></head>')
  res.end('你好\n')
}).listen(1337, '127.0.0.1')

console.log('Server running at http://127.0.0.1:1337/')
```

## Nodejs基础

### 控制台

`console.log`方法用于进行标准输出流的输出。

```js
console.log('This is a test string')
```

`console.error`方法用于进行标准错误输出流的输出，即向控制台输出一行错误信息。

```js
console.error('This is a anerror string.')
```

`console.dir`方法用于查看一个对象中的内容并且将该对象的信息输出到控制台中。

```js
var user = {
  name: 'Kaindy',
  getName: function () { return this.name }
  setName: function (name) { this.name = name }
}
console.dir(user)
```

`console.time`和`console.timeEnd`方法用于统计一段代码的执行时间

```js
console.time('small loop')
for (let i = 0; i < 10000; i++) {}
console.timeEnd('small loop')
```

`console.trace`方法用于将当前位置处的栈信息作为标准错误信息进行输出。

`console.assert`方法用于对一个表达式的执行结果进行评估，如果表达式的执行结果为`false`，则输出一个消息字符串并抛出`AssertionError`异常。

### Nodejs中的全局作用域和全局函数

在`Nodejs`中存在一个全局作用域，可以在这个全局作用域中定义一些不需要任何模块的加载即可使用的变量、函数或类。同时，它也预先定义了一些全局方法和全局类。

在`Nodejs`中定义了一个`global`对象，代表`Nodejs`的全局命名空间，任何全局变量、函数或对象都是这个对象的一个属性值。

```js
console.log(global)
```

`nodejs`中的一些全局函数：

- `setTimeout`：指定经过多少毫秒后执行回调函数，与客户端的`setTimeout`行为一致。

  ```js
  var testFunc = function (msg) { console.log(msg) }
  var timer = setTimeout(testFunc, 1000, 'this is a parameter')
  ```

- `clearTimeout`：清除指定的定时器。

  ```js
  var timer = setTimeout(testFunc, 5000, 'this is a test')
  clearTimeout(timer)
  ```

- `setInterval`：指定间隔多少毫秒之后执行回调函数，与客户端的`setInterval`行为一致。

  ```js
  var testFunc = function (msg) { console.log(msg) }
  var timer = setInterval(testFunc, 1000, 'this is a interval')
  ```

- `clearInterval`：清除指定的`setInterval`定时器

  ```js
  clearInterval(timer)
  ```

在`Nodejs`中，为上述的定时器对象定义了`unref`方法和`ref`方法。`unref`方法可以取消回调函数的执行，在执行了取消操作后，仍然可以使用`ref`方法恢复回调函数的执行。

在`Nodejs`中可以使用`require`函数来加载模块。

```js
var foo = require('../foo.js')
var http = require('http')
```

在`Nodejs`中，定义了一个`require.main`变量，用来检测一个模块是否为应用程序中的主模块。

```js
if (module === require.main) {
  console.log('is main module')
}
```

`require.resolve`函数用来查询某个模块文件的文件名，这个文件名是带有完整的绝对路径的。

```js
require.resolve('node.js')    // 'E:\\nodejs\\node.js
```

`require.cache`对象代表缓存了所有已被加载模块的缓存区。

```js
// 查看缓存区
console.log(require.cache)
```

### __filename变量和__dirname变量

在`Nodejs`中，预定义了两个变量：用于获取当前模块文件名的`__filename`变量与用于获取当前目录名的`__dirname`变量。

在任何模块文件内部，都可以使用`__filename`变量来获取当前模块文件带有完整绝对路径的文件名

```js
// 在任意模块文件中写入代码
console.log(__filename)

// 执行这个模块文件
> node node.js    // E:\nodejs\node.js
```

在任何模块文件内部，可以使用`__dirname`变量获取当前模块文件所在目录的完整绝对路径

```js
console.log(__dirnmae)
```

### 事件处理机制及事件环机制

与客户端浏览器中的事件一样，`Nodejs`中也存在事件机制，比如`htt.Server`对象会触发"接受到客户端请求"、"产生链接错误"等事件。

#### EventEmitter类

在`Nodejs`中的用于实现各种事件处理的`event`模块中，定义了一个`EventEmitter`类，所有触发事件的对象都是一个继承了`EventEmitter`类的子类的实例对象。`EventEmitter`类也定义了很多实例方法用于处理各种事件。

| 方法 | 描述 |
| --- | --- |
| addListener(event, listener) | 对指定事件绑定事件处理函数 |
| on(event, listener) | `addListener`的别名，功能一致 |
| once(event, listener) | 对指定事件指定只执行一次的事件处理函数 |
| removeListener(event, listener) | 对指定事件解除事件处理函数 |
| removeAllListeners([event]) | 对指定事件移除所有事件处理函数 |
| setMaxListeners(n) | 指定事件处理函数的最大数量 |
| listeners(event) | 获取指定事件的所有事件处理函数 |
| emit(event,[arg1], [arg2], [...]) | 手动触发指定事件 |

#### EventEmitter类的各个方法

`EventEmitter`类的`on`方法或`addListener`方法用于对指定事件绑定事件处理函数。

```js
emitter.on(event, listener)
emitter.Listener(event, listener)
```

其中第一个参数是指定的事件名，第二个参数是该事件的事件处理函数。

```js
var http = require('http')    // 引用http模块
var server = http.createServer()    // 创建服务器

// 为server服务器在接收到客户端的request请求时绑定事件处理函数
server.on('request', function (req, res) {
  console.log(req.url)
  res.end()
})

server.listen(1337, '127.0.0.1')
```

我们还可以通过`on`方法对同一事件绑定多个事件处理函数。

```js
var http = require('http')
var server = http.createServer()

server.on('request', function (req, res) {
  // 干一些事
})

server.on('request', function (req, res) {
  // 干另外一些事
})

...
```

默认情况下，同一事件最多可绑定10个事件处理函数。可以通过`setMaxListeners`方法来修改最多可绑定的事件处理函数的数量。

要解除事件绑定，可以使用`removeListener`方法

```js
server.removeListener('request', testFunc)
```

`removeAllListeners`方法用于解除某个事件的所有已被指定事件处理函数

```js
emitter.removeAllListeners([event])
```

`emit`方法用于手动触发一个事件。

```js
emitter.emit(event, [arg1], [arg2], [...])
```

```js
var http = require('http')
var server = http.createServer()

server.on('customEvent', function (arg1, arg2, arg3) {
  console.log('自定义事件触发。')
  console.log(arg1)
  console.log(arg2)
  console.log(arg3)
})

// 手动触发自定义事件
server.emit('customEvent', '自定义参数1', '自定义参数2', '自定义参数3')
server.listen(1337, '127.0.0.1')
```

#### 获取指定事件处理函数的数量

`EventEmitter`类自身拥有一个`listenerCount`方法，用于获取某个对象的指定事件的处理函数数量。

```js
EventEmitter.listenerCount(emitter, event)
```

第一个参数是指定的对象，第二个参数是事件名

```js
var http = require('http')
var events = require('events')
var server = http.createServer()

server.on('request', function (req, res) {
  if (req.url !== '/favicon.ico') {
    console.log('接收到客户端请求')
  }
})

server.on('request', function (req, res) {
  if (req.url !== '/favicon.ico') {
    console.log(req.url)
  }
})

server.on('request', function (req, res) {
  if (req.url !== '/favicon.ico') {
    console.log('发送完毕')
  }
})

server.listen(1337, '127.0.0.1')

console.log(events.EventEmitter.listenerCount(server, 'request'))
```

#### EventEmitter类自身所拥有的事件

在`events`模块中，`EventEmitter`类自身有两个事件：`newListener`事件和`removeListener`事件。

任何时候，对继承了`EventEmitter`类的子类的实例对象绑定事件处理函数时，都将触发`newListener`事件

```js
emitter.on('newListener', function (e, f) {
  // ...
})
```

同样，任何时候取消对继承了`EventEmitter`类的子类的实例对象绑定的事件时，都将触发`EventEmitter`类的`removeListener`事件。

```js
emitter.on('removeListener', function (e, f) {
  // ...
})
```

## 模块与npm包

### 核心模块与文件模块

在`Nodejs`中，以模块为单位划分所有的功能，一个`Nodejs`应用程序由大量的模块组成，每一个模块都是一个JavaScript脚本文件。若需要加载模块，可以使用`require`方法。

### 外部访问模块内成员

在一个模块文件内部定义的变量、函数或对象只在当前模块中有效，若需要从外部访问它们，则需要使用`exports`方法。

```js
var myMsg = 'hello'
var myFunc = function () {
  return 'I\'m function'
}

exports.msg = myMsg
exports.myFunc = myFunc
```

将上述代码保存为文件，在需要的地方引入

```js
var foo = require('./foo.js')
console.log(foo.msg)    // 'hello'
console.log(foo.myFunc())   // 'I'm function'
```

同时也可以将模块定义为一个类，然后使用`module.exports`将这个类导出。

```js
var foo = function (name, age) {
  this.name = name
  this.age = age
}

foo.prototype.getName = function () {
  return this.name
}

foo.prototype.setName = function (name) {
  this.name = name
}

foo.prototype.getAge = function () {
  return this.age
}

foo.prototype.setAge = function (age) {
  this.age = age
}

module.exports = foo              
```

## Buffer类

在`Nodejs`中，定义了一个`Buffer`类，该类用来创建一个专门存放二进制数据的缓存区

### 创建Buffer对象

在`Nodejs`中，`Buffer`类是一个可以在任何模块中直接被引用的全局类。我们可以使用`new`关键字来创建该类的实例对象。`Buffer`类有三种形式的构造函数。

第一种是只需将缓存区大小指定为构造函数的参数：

```js
new Buffer(size)
```

被创建的`Buffer`对象有一个`length`属性，表示缓存区大小

```js
buf = new Buffer(128)
buf.length    // 128
```

可以使用`Buffer`对象的`fill`方法来初始化缓存区中的所有内容。

```js
buf.fill(value, [offset], [end])
```

第二种形式的构造函数是直接使用一个数组来初始化缓存区

```js
new Buffer(array)
```

```js
> buf = new Buffer([0, 1 ,2])
// <Buffer 00 01 02>
```

第三种形式是构造函数直接使用一个字符串来初始化缓存区。

```js
new Buffer(str, [encoding])
```

第一个参数是初始化的字符串，第二个是编码，默认为`utf8`

```js
> buf = new Buffer('Hello World')
// <Buffer 48 65 6c 6c 6f 20 57 6f 72 6c 64>
```

### Buffer对象与字符串对象之间的转换

我们可以使用`Buffer`对象的`toString`方法将`Buffer`对象中保存的数据转换为字符串。

```js
buf.toString([encoding], [start], [end])
```

```js
> buf
<Buffer 48 65 6c 6c 6f 20 57 6f 72 6c 64>
> buf.toString()
'Hello World'
```

如果需要向`Buffer`对象中写入字符串，则可使用`write`方法。

```js
buf.write(string, [offset], [length], [encoding])
```

在`Nodejs`中，也可以使用`StringDecoder`对象将`Buffer`中的数据转为字符串，它与`toString`方法行为一致，但对`utf8`支持的更好。

### Buffer对象与JSON对象相互转换

在Nodejs中，可以使用`JSON.stringify`方法将`Buffer`对象中保存的数据转换为一个字符串，也可以使用`JSON.parse`方法将一个经过转换后的字符串还原为一个数组。

```js
> buf = new Buffer('hello world')
<Buffer 68 65 6c 6c 6f 20 77 6f 72 6c 64>
> json = JSON.stringify(buf)
'{"type":"Buffer","data":[104,101,108,108,111,32,119,111,114,108,100]}'
> JSON.parse(json)
{ type: 'Buffer',
  data: [ 104, 101, 108, 108, 111, 32, 119, 111, 114, 108, 100 ] }
> copy = new Buffer(JSON.parse(json))
<Buffer 68 65 6c 6c 6f 20 77 6f 72 6c 64>
> copy.toString()
'hello world'
```

### 复制缓存数据

当有需要复制`Buffer`中的二进制数据时，可以使用`copy`方法

```js
buf.copy(targetBuffer, [targetStart], [sourceStart], [sourceEnd])
```

```js
> buf2 = new Buffer(128)
<Buffer 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
... >
> buf.copy(buf2)
11
> buf2
<Buffer 68 65 6c 6c 6f 20 77 6f 72 6c 64 00 00 00 00 00 00 00 00 00 00 00 00 00
 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
... >
```

### Buffer类的类方法

`Buffer`类定义了四个类方法（相当于静态方法）

- `isBuffer`方法，判断一个对象是否为`Buffer`对象 

  ```js
  Buffer.isBuffer(obj)
  ```

- `byteLength`方法，计算一个指定字符串的字节数

  ```js
  Buffer.byteLength(string, [encoding])
  ```

- `concat`方法，用于将多个`Buffer`对象组合起来创建新的`Buffer`对象

  ```js
  Buffer.concat(list, [totalLength])
  ```

- `isEncoding`方法，用于检测一个字符串是否为一个有效的编码格式字符串

  ```js
  Buffer.isEncoding(encoding)
  ```

## 文件系统操作

在Nodejs中，提供一个`fs`模块，用于实现文件及目录的读写操作。

### 同步与异步

在Nodejs中，使用`fs`模块来实现所有对文件及目录的创建、写入及删除操作。在`fs`模块中，所有的方法都有同步和异步两种。比如：`readFile`方法和`readFileSync`方法，含有`Sync`字符的方法均为同步方法，其他为异步方法。

```js
// 同步方法读取文件，立即返回操作结果，会阻塞后续操作
var fs = require('fs')
var data = fs.readFileSync('./index.html', 'utf8')

// 等待操作返回结果
console.log(data)

// 异步方法读取文件，不阻塞后续操作，通过回调函数执行
fs.readFile('./index.html', 'utf8', function (err, data) {
  consol.elog(data)
})
```

在大多数情况下，我们应该使用异步方法,但在很少的场景下，比如读取配置文件以启动服务器，应该使用同步方法。

### 文件读写

我们可以使用`fs`模块中的`readFile`方法或`readFileSync`方法来读取文件。

#### readFile和readFileSync

```js
fs.readFile(filename, [options], callback)
```

`filename`参数和`callback`参数为必填，分别是完整文件路径及文件名和回调函数。`options`参数为一个对象，可以使用`flag`属性指定对该文件执行什么样的操作，默认为`r`

- `r`：读取文件，文件不存在抛出异常
- `r+`：读取并写入文件，不存在抛出异常
- `rs`：以同步方式读取文件并通知操作系统忽略本地文件系统缓存，不存在抛出异常
- `w`：写入文件，文件不存在则创建该文件，已存在则清空文件内容
- `wx`：与`w`相似，但以排他方式写入文件
- `w+`：读取并写入文件，文件不存在则创建，已存在则清空文件内容
- `wx+`：与`w+`相似，以排他方式打开文件
- `a`：追加写入文件，文件不存在则创建
- `ax`：与`a`相似，以排他方式打开文件
- `a+`：读取并追加写入文件，文件不存在则创建
- `ax+`：与`a+`相似，以排他方式打开文件

除`flag`之外，还可以使用`encoding`属性指定以何种编码读取文件，属性值为`utf8`、`ascii`和`base64`

回调函数`callback`如下：

```js
function (err, data) {
  // ...
}
```

```js
// 读取文件示例
var fs = require('fs')
fs.readFile('./test.txt', function (err, data) {
  if (err) console.log('读取文件时发生错误')
  console.log(data)
  // <Buffer 4e 6f 64 65 2e 6a 73 20 69 73 20 47 6f 6f 64 21 0d 0a 4a 61 76 61 53 63 72 69 70 74 20 69 73 20 47 6f 6f 64 21>
})
```

打印的结果是缓存区里的二进制结果，如果想要字符串，可以使用`data.toString()`方法，或指定`readFile`的字符编码参数为`utf8`

除了上述使用异步方法`readFile`读取文件之外，还可以使用`readFileSync`同步方法来读取文件

```js
var data = fs.readFileSync(filename, [options])
```

参数含义与上述的异步方法一样。

```js
var fs = require('fs')
try {
  var data = fs.readFileSync('./test.txt', 'utf8')
  console.log(data)
} catch (ex) {
  console.log('读取文件时发生错误')
}
```

#### writeFile和writeFileSync

写入文件，可以使用`fs`模块的`writeFile`方法和`writeFileSync`方法。

```js
fs.writeFile(filename, data, [options], callback)
```

其中的`options`参数对象可以使用`flag`属性指定对文件执行何种操作，`mode`属性指定对该文件的读写权限，`encoding`属性指定以何种编码写入文件。

```js
var fs = require('fs')
fs.writeFile('./input.txt', 'Hello\r\nWorld', function (err) {
  if (err) console.log('写入文件失败')
  console.log('写入文件成功')
})
```

下面的示例演示追加写入数据

```js
var fs = require('fs')
var options = {
  flag: 'a'
}
fs.writeFile('./test.txt', 'JavaScript', options, function (err) {
  if (err) console.log('追加数据失败')
  console.log('追加写入数据成功')
})
```

同步的写入内容使用`writeFileSync`方法：

```js
fs.writeFileSync(filename, data, [options])
```

#### appendFile和appendFileSync

当我们需要向文件末尾追加数据时，可以使用`appendFile`或`appendFileSync`方法。

```js
fs.appendFile(filename, data, [options], callback)
```

```js
var fs = require('fs')
fs.appendFile('./test.txt', '这是追加的数据', 'utf8', function (err) {
  if (err) console.log('追加数据失败')
  console.log('追加数据成功')
})
```

同步追加数据操作如下：

```js
fs.appendFileSync(filename, data, [options])
```

#### open和openSync

如果我们要从指定位置开始读写文件，需要先使用`fs`模块的`open`方法或`openSync`方法打开文件。

```js
fs.open(filename, flags, [mode], callback)
```

这两个方法返回一个文件句柄。

```js
var fs = require('fs')
fs.open('./test.txt', 'r', function (err, fd) {
  console.log(fd)
})
```

同步打开

```js
var fd = fs.openSync(filename, flags, [mode])
```

#### read和readSync

在打开文件获取到文件句柄后，可以使用`read`方法，读取文件

```js
fs.read(fd, buffer, offset, length, positon, callback)
```

写入文件内容使用`fs`模块的`write`方法或`writeSync`方法。

```js
fs.write(fd, buffer, offset, length, position, callback)
fs.writeSync(fd, buffer, offset, length, position)
```

### 创建与读写目录

#### mkdir和mkdirSync

在`fs`模块中，可以使用`mkdir`方法创建目录。

```js
fs.mkdir(path, [mode], callback)
```

```js
var fs = require('fs')
fs.mkdir('./test', function (err) {
  if (err) console.log('创建目录失败')
  console.log('创建目录成功')
})
```

以同步的方式创建目录，使用`mkdirSync`方法

```js
fs.mkdirSync(path, [mode])
```

#### readdir和readdirSync

在`fs`模块中，使用`readdir`方法读取目录

```js
fs.readdir(path, callback)
```

```js
var fs = require('fs')
fs.readdir('./', function (err, files) {
  if (err) console.log('读取目录失败')
  console.log(files)
  // [ '.node.js.swp', 'input.txt', 'node.js', 'test', 'test.txt' ]
})
```

同步读取使用`readdirSync`方法

```js
var files = fs.readdirSync(path)
```

### 查看与修改文件或目录信息

#### stat和lstat

在`fs`模块中，使用`stat`方法或`lstat`方法查看一个文件或目录的信息。

```js
fs.stat(path, callback)
fs.lstat(path, callback)
```

回调函数如下：

```js
function (err, stats) {
  // ...
}
```

其中，`stats`参数表示一个`fs.Stats`对象，它有如下一些方法：

- `isFile`：判断是否为一个文件
- `isDirectory`：判断是否为一个目录
- `isBlockDevice`：判断是否为一个块设备文件。
- `isCharacterDevice`：判断是否为一个字符设备文件。
- `isSymbolicLink`：判断是否为一个符号链接文件。
- `isFIFO`：判断是否为一个FIFO文件
- `isSocket`：判断是否为一个socket文件。

#### exists

在`fs`模块中，使用`exists`方法检查一个文件或目录是否存在。

```js
fs.exists(path, function (exists) {
  // 参数exists为true，该文件或目录存在，否则不存在。
})
```

#### realpath

获取文件或目录的绝对路径使用`realpath`方法。

```js
fs.realpath(path, [cache], callback)
```

#### utimes和utimesSync

在`fs`模块中，使用`utimes`方法修改文件的访问时间及修改事件。

```js
fs.utimes(path, atime, mtime, callback)
```

参数`atime`用于指定修改后的访问时间，参数`mtime`用于指定修改时间

同步方式修改使用`utimesSync`方法

```js
fs.utimesSync(path, atime, mtime)
```

#### chmod和chmodSync

在`fs`模块中，使用`chmod`方法修改文件或目录的读写权限。

```js
fs.chmod(path, mode, callback)
```

参数`mode`用于指定修改后的文件或目录的读写权限。

以同步方式修改文件或目录的读写权限，使用`chmodSync`方法

```js
fs.chmodSync(path, mode)
```

### 对文件或目录的其他操作

#### rename和renameSync

在`fs`模块中，可以使用`rename`方法移动文件或目录

```js
fs.rename(oldPath, newPath, callback)
```

以同步方式移动文件或目录，使用`renameSync`方法

```js
fs.renameSync(oldPath, newPath)
```

#### link和linkSync

在`fs`中，使用`link`方法创建文件的硬链接，同步操作使用`linkSync`

```js
fs.link(scrpath, dstpath, callback)
```

#### symlink和symlinkSync

在`fs`中，使用`symlink`方法创建文件或目录的符号链接，同步操作使用`symlinkSync`。

```js
fs.symlink(srcpath, dstpath, [type], callback)
```

#### truncate

在`fs`模块中，使用`truncate`方法对文件进行截断操作

```js
fs.truncate(filename, len, callback)
```

#### rmdir

在`fs`模块中，使用`rmdir`方法删除空目录。

```js
fs.rmdir(path, callback)
```

#### watchFile

在`fs`模块中，使用`watchFile`对文件进行监视。

```js
fs.watchFile(filename, [options], listener)
```

### 文件流

#### 基本概念

在应用程序中，流是一组有序的、有起点和终点的字节数据的传输手段。在应用程序中各种对象之间交换与传输数据的时候，总是先将该对象中所包含的数据转换为各种形式的流数据，在通过流传输，到达目标对象后再将流数据转换为该对象可用的数据。

#### ReadStream

在`fs`模块中，使用`createReadStrema`方法创建一个将文件内容读取为流数据的`ReadStream`对象

```js
fs.createReadStream(path, [options])
```

`options`参数是一个对象，可能的值如下：

- `flags`：对文件采取什么样的操作，默认为`r`
- `encoding`：指定使用什么编码来读取该文件
- `autoClose`：指定是否关闭在读取文件时操作系统内部使用的文件描述符，默认为`true`
- `start`：使用整数值来指定文件的开始读取位置
- `end`：使用整数值来指定文件的结束读取位置

```js
var fs = require('fs')
var file = fs.createReadStream('./test.txt', { start:1, end:12 })

file.on('open', function (fd) {
  console.log('开始读取文件')
})

file.on('data', function (data) {
  console.log('读取到数据')
  console.log(data)
})

file.on('end', function () {
  console.log('文件已全部读取完毕')
})

file.on('close', function () {
  console.log('文件被关闭')
})

file.on('error', function (err) {
  console.log('读取文件失败')
})
```

#### WriteStream

在`fs`中，可以使用`createWriteStream`方法创建一个将流数据写入文件中的`WriteStream`对象

```js
fs.createWriteStream(path, [options])
```

### path模块

在Nodejs中，提供一个`path`模块，它具有以下方法：

| 方法 | 描述 | 示例 |
| --- | --- | --- |
| `normalize` | 该方法将非标准路径字符串转换为标准路径字符串 | `path.normalize(p)` |
| `join` | 该方法将多个参数值字符串结合为一个路径字符串 | `path.join([path1], [path2], [...])` |
| `resolve` | 该方法以应用程序为起点，根据所有的参数值字符串解析出一个绝对路径 | `path.resolve(path1, [path2], [...])` |
| `relative` | 该方法用于获取两个路径之间的相对关系 | `path.relative(from, to)` |
| `dirname` | 该方法用于获取一个路径中的目录名 | `path.dirname(p)` |
| `basename` | 该方法用于获取一个路径中的文件名 | `path.basename(p, [ext])` |
| `extname` | 该方法用于获取一个路径中的扩展名 | `path.extname(p)` |
| `path.sep` | 该属性值为操作系统指定的文件分隔符 | `path.sep` |
| `path.delimiter` | 该属性值为操作系统指定的路径分隔符 ||

## TCP与UDP数据通信

在`Nodejs`中，提供一个`net`模块和一个`dgram`模块，分别用于实现基于TCP和UDP的数据通信。

### net模块

在`Nodejs`中，使用`net`模块实现TCP通信

#### 创建TCP服务器

在`Nodejs`中，调用`net`模块中的`createServer`方法创建TCP服务器

```js
var server = net.createServer([options], [connectionListener])
```

`options`选项是一个对象，其中包含一个布尔类型的`allowHalfOpen`属性，默认为`false`。
`connectionListener`参数指定当客户端与服务器简历连接时调用的回调函数：

```js
function (socket) {
  // ...
}
```

当客户端与服务器建立连接时，触发`connection`事件，我们可以监听此事件来调用回调函数

```js
server.on('connection', function (socket) {
  // ...
})
```

在创建了TCP服务器后，可以使用`listen`方法通知服务器开始监听客户端连接。

```js
server.listen(port, [host], [backlog], [callback])
```

上面的参数中，`port`指定端口，`host`指定主机名，`backlog`指定最大连接数，默认值为511.

```js
var net = require('net')
var server = net.createServer(function (socket) {
  console.log('客户端与服务器端连接已建立')
})

server.listen(8431, 'localhost', function () {
  console.log('服务器开始监听')
})
```

创建TCP服务器之后，可以使用`address`方法查看该服务器所监听的地址信息

```js
var address = server.address()
```

我们还可以使用`getConnections`方法查看当前与TCP服务器建立连接的客户端数量

```js
server.getConnections(function (err, count) {
  console.log(count)
})
```

TCP服务器还可以设置一个整数类型的`maxConnections`属性值，用于指定TCP服务器可以接收的客户端连接最大数量。

最后，我们可以使用`close`方法显式的指定服务器拒绝所有新的客户端连接。

```js
server.close(function () {
  // ...
})
```

#### socket端口对象

在`Nodejs`中，使用`net.Socket`代表一个`socket`端口对象。

#### 创建TCP客户端

在`Nodejs`中，创建TCP客户端只需创建一个用于连接TCP服务器的`socket`端口对象即可。

```js
var net = new net.Socket([options])
```

```js
// 创建服务器端
var net = require('net')
var server = net.createServer()

server.on('connection', function (socket) {
  console.log('客户端与服务器端连接已建立')
  socket.setEncoding('utf8')
  socket.on('data', function (data) {
    console.log('已接收到客户端发送的数据：' + data)
    if (data === 'Hello Nodejs') {
      socket.write('数据已被确认：OK!')
    } else {
      socket.write('数据错误：Error!')
    }
  })
})

server.listen(8431, 'localhost')

// 创建客户端
var net = require('net')
var client = new net.Socket()
client.setEncoding('utf8')
client.connect(8431, 'localhost', function () {
  console.log('已连接到服务器端')
  client.write('Hello Nodejs!')
})

client.on('data', function (data) {
  console.log('已接收到服务器端发送的数据：' + data)
})
```

### dgram模块

TCP是一种基于连接的协议，通信之前客户端与服务器端必须先建立连接，而UDP是面向非连接协议，不需要建立连接，所以UDP是一种不可靠的协议，但速度很快。

在`Nodejs`中，`dgram`模块用来创建UDP服务器端和客户端。

## 创建HTTP和HTTPS服务器端

在`Nodejs`中，提供`http`模块和`https`模块，用于创建HTTP或HTTPS服务器和客户端。

### HTTP服务器

在`Nodejs`中，使用`http`模块中的`createServer`方法创建HTTP服务器

```js
var server = http.createServer(function (request, response) {
  // ...
})
```

在回调函数中，第一个参数`request`表示一个客户端请求对象，第二个参数`response`表示一个服务器端响应对象。

在创建了HTTP服务器之后，使用`listen`方法进行监听

```js
server.listen(port, [host], [backlog], [callback])
```

```js
var http = require('http')
var server = http.createServer(function (req, res) {
  // ...
}).listen(1337, '127.0.0.1', function () {
  console.log('服务器端开始监听')
})
```

可以使用`close`方法关闭HTTP服务器

```js
server.close()
```

可以监听服务器的关闭事件

```js
server.on('close', function () {
  // ....
})
```

当客户端与服务器端建立连接时，会触发HTTP服务器对象的`connection`事件。

```js
var http = require('http')
var server = http.createServer(function (req, res) {
  // ...
}).listen(1337, '127.0.0.1')

server.on('connection', function (socket) {
  console.log('客户端连接已建立')
})
```

HTTP服务器的`setTimeout`方法用来设置服务器的超时时间

```js
server.setTimeout(60 * 1000, function (socket) {
  console.log('服务器超时')
  console.log(socket)
})
```

另外，HTTP服务器有一个`timeout`属性，属性值为整数值，单位为毫秒，可以用查看或修改服务器的超时时间

```js
server.timeout = 1000
console.log(server.timeout)
```

## 进程与子进程

## 错误处理与断言处理

## 加密与压缩

## 其他模块

## 数据库访问

## Express

## WebSocket通信
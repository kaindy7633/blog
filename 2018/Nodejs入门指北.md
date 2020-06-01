# Node是什么?

`Node` 到底是什么? 我们来看官网的定义：

> Node是一个JavaScript（ECMAScript）运行时（runtime）, runtime也可以是运行时组件。我们也可以将其理解为一种编程语言的运行环境，而此环境包含了代码运行所需要的编译器以及操作系统支持。

`Node` 底层由 `C++` 实现，语法则遵循 `ECMAScript` 规范。

`Node` 选择 `JavaScript` 是因为它提供了足够高德效率和实现，比如非阻塞IO和事件驱动等特性。

# Node的内部机制

程序由CPU执行，而在完成任务之前，CPU不会暂停或停止，它的运行和同步、异步或者阻塞、非租塞没有必然的联系。操作系统保证CPU始终处于运行状态，是通过调度来实现的，具体一点就是在不同的进程/线程间来回切换。

## 回调

回调就是通过函数参数的参数传递到其他代码的，某段可执行代码的引用。通俗的讲，就是将一个函数作为参数传递给另一个函数，并且作为参数的函数可被执行，它本质上是一个高阶函数。

> 高阶函数的概念：接受一个或多个函数作为参数输入，且会输出一个函数。

单线程的程序在运行时需要考虑这样的问题：如果遇到一个耗时操作，要不要等待操作完成后再进行下一步?

`Node` 没有选择这样方式，而是通过异步+回调的方式进行处理。当 `Node` 遇到耗时操作，比如IO操作时，会发起一个调用后继续向下执行，当IO操作完成后，再执行对应的回调函数(异步).

```js
var fs = require('fs');
var callback = function (err, data) {
  if (err) return;
  sole.log(data.toString());
}
fs.readFile('foo.txt', callback);
```

## 同步/异步和阻塞/非阻塞

同步/异步描述的是进程/线程的调用方式。

同步指的是进程/线程发起调用后，会一直等待调用返回后才继续往下执行，这段时间，CPU会通过系统调度去另外的进程/线程执行任务，而后再回到现有的进程/线程上来。

而异步则是进程/线程发起调用后，不等待继续往下执行，当调用完成后，获取通知再回过头来执行。

阻塞和非阻塞是针对IO而言的，它关注程序在等待IO调用返回这段时间的状态。

## 单线程和多线程

`Java`、`C++`等高级语言都有多线程的语言特性，而 `Node` 没有提供多线程支持，我们的代码只能在单线程中运行。

而 `Node` 的底层并非是单线程的。`Libuv` 是 `Node` 的底层实现，它就有线程池的概念。

`Libuv` 是一个跨平台的异步IO库，专为 `Node` 提供了多平台下的异步IO支持，本身由 `C/C++` 实现，`Node` 的非阻塞IO以及事件循环都是由它来完成并实现的。

## 并行和并发

并行和并发是两个完全不同的概念。

打个比方，并发好比两队人取票，但只有一个取票机，A队第一个取完，就由B队的第一个来取。而并行则是两队人取票，但有两个取票机，各自队的人使用各自对应的取票机。

`Node` 通过异步+事件驱动的单线程特性来实现高并发，异步使得代码在面临多个请求时不会发生阻塞，事件驱动提供了IO调用后执行回调函数的能力。

# 事件循环（Event Loop）

事件循环就是程序在执行期间不间断的以某种特定的方式进行的死循环。

事件就是由用户操作产生的，比如元素单击、拖动元素，`ajax`请求、文件读取等，这些事件会按照顺序被加载到一个队列中去。

在客户端，事件循环是由浏览器完成的，而在 `Node` 中，是由 `libuv` 实现的。

<img src="./images/20190316165725.png" width="800px" />

`Node` 中的事件循环，共分为6个阶段，每个阶段都维护着一个回调函数的队列。

- `Timers`：用来处理 `setTimeout` 和 `setInterval` 的回调
- `I/O callbacks`：大多数的回调方法都在这个阶段执行，除了 `timers`、`close` 和 `setImmediate`
- `idle, prepare`：内部使用，无需关注
- `Poll`：轮询，不断检查有没有新的IO事件
- `Check`：处理 `setImmediate` 事件回调
- `close callbacks`：处理一些 `close` 相关的事件

## process.nextTick

`process.nextTick` 就是定义一个异步动作，并让这个动作在事件循环当前阶段结束后执行。

```js
process.nextTick(function() {
  console.log('first');
})
console.log('next');
// next
// first
```

`process.nextTick` 并不是事件循环的一部分，但它的回调方法是由事件循环调用的。该方法会把回调加入到一个 `nextTickQueue` 的队列中，在事件循环的任何阶段，如果 `nextTickQueue` 队列不为空，那么就会在当前阶段操作完成后优先执行该队列中的回调函数，当 `nextTickQueue` 队列中的回调执行完毕后，事件循环才会继续向下执行。

## nextTick与setImmediate

`setImmediate` 是 `Node` 提出的新方法，它同样会将回调函数加入到事件队列中，不同于 `setTimeout` 和 `setInterval` ，`setImmediate` 并不接受一个事件作为参数，而是在当前事件循环的结尾触发。

`setImmediate` 与 `nextTick` 很相似，由于 `process.nextTick` 总是在当前操作完成后立即执行，所以，它总会在 `setImmediate` 之前被执行。

```js
setImmediate(function(arg) {
  console.log('executing immediate', arg);
}， 'so immediate')
process.nextTick(function() {
  console.log('next tick');
})

// next tick
// executing immediate: so immediate
```

## setImmediate和setTimeout

`setImmediate` 方法会在 `poll` 阶段结束后执行，而 `setTimeout` 会在规定的事件到期后执行，所以如果把两者放在一个IO操作的 `callbacks` 中，则永远是 `setImmediate` 先执行。

```js
setTimeout(function() {
  console.log('timeout');
}, 0);
setImmediate(function() {
  console.log('immediate');
});
// immediate
// timeout
```

在 `readFile` 方法中，事件循环位于 `poll` 阶段，因此事件循环会先进入 `check` 阶段执行 `setImmediate` 的回调，然后再进入 `timers` 阶段执行 `setTimeout` 的回调。

```js
require('fs').readFile('foo.txt', function() {
  setTimeout(function() {
    console.log('timeout');
  }, 0);

  setImmediate(function() {
    console.log('immediate');
  })
})
```

# Buffer

`Buffer` 是 `Node` 特有的数据类型，主要用来操作二进制数据。而在客户端浏览器，ES2015增加了 `ArrayBuffer` 类型用来操作二进制数据流。

在文件操作和网络操作中，如果不显式的声明编码格式，其返回数据默认的类型就是 `Buffer`。

```js
var fs = require('fs');
fs.readFile('foo.txt', function(err, results) {
  console.log(results);
  // <Buffer 48 65 6c 6c 6f 20 57 6f 72 6c 64> (Hello Node)
})
```

上面的代码中，打印的是十六进制的数据，由于二进制不便于阅读， `Buffer` 通常表现为十六进制的字符串。

## Buffer的构建与转换

可以直接使用 `Buffer` 类初始化一个 `Buffer` 对象，参数可以是由二进制数据组成的数组。

```js
var buffer = new Buffer([0x48, 0x65, 0x6c, 0x6c, 0x20, 0x4e, 0x6f, 0x64, 0x65]);
// Hello Node
```

同样可以使用构造函数，传入字符串来得到一个 `Buffer`

```js
var buffer = new Buffer('Hello Node');
console.log(buffer);
// <Buffer 48 65 6c 6c 6f 20 4e 6f 64 65>
```

目前在新版的 `Node` 中，已采用 `Buffer.from` 来初始换一个 `Buffer` 对象，上面的代码可以修改为如下：

```js
var buffer = Buffer.from([0x48, 0x65, 0x6c, 0x6c, 0x20, 0x4e, 0x6f, 0x64, 0x65]);
// Hello Node
var buffer = Buffer.from('Hello Node');
console.log(buffer);
// <Buffer 48 65 6c 6c 6f 20 4e 6f 64 65>
```

如果想要把 `Buffer` 转为字符串，可以使用 `toString` 方法

```js
buffer.toString([encoding], [start], [end])
// encoding: 目标编码格式
// start: 开始位置
// end： 结束位置
```

目前 `Buffer` 提供以下6种编码格式：

- `ASCII`
- `Base64`
- `Binary`
- `Hex`
- `UTF-8`
- `UTF-16LE/UCS-2`

`Buffer` 还提供了 `isEncoding` 方法来判断是否支持转换为目标编码格式。

```js
console.log(buffer.toString('utf-8', 0, 5));
// Hello
```

## Buffer的拼接

如果我们要处理的字符串中有中文字符，那么可能会出现回文问题，一个中文字符占3个字节，使用 `+=` 这样的方式拼接 `Buffer`时，由于这个过程包含一个隐式的编码转换，就会出现乱码问题。所以， `+=` 这样的方式已废弃，推荐使用 `push` 方法来拼接 `Buffer`

```js
var data = [];
// 现将Buffer放入数组里面
rs.on('data', function(chunk) {
  data.push(chunk);
});
// 结束后再进行编码转换
rs.on('end', function() {
  var buf = Buffer.concat(data);
  console.log(buf.toString());
})
```

# Events

# File System

`File System` 模块为 `Node` 提供了文件读写的能力，它借助了底层 `libuv` 的 `C++` API实现的。`File System` 包含了数十个用于文件操作的API，大多都提供了同步和异步两个版本。

## readFile

```js
fs.readFile(file [, options], callback);
```

该方法异步读取文件中的内容

```js
fs.readFile('foo.txt', function(err, data) {
  if (err) throw err;
  console.log(data);
})
```

`readFile` 将一个文件的所有内容都读取到内存中，适用于小文件，对于过大的文件，则建议使用 `stream` 来处理。`readFile` 是异步读取文件内容，而 `readFileSync` 则是直接返回文件数据内容。

```js
var fs = require('fs');
var data = fs.readFileSycn('foo.txt', { encoding: 'utf-8' }); 
// 不指定encoding，会返回buffer，需要调用toString方法转换一次
console.log(data);
```

## writeFile

```js
fs.writeFile(file, data[, opotions], callback);
```

如果要写入内容的文件不存在，默认则会创建此文件

```js
fs.writeFile('foo.txt', 'Hello Node', { flag: 'a', encoding: 'utf-8' }, function(err) {
  if (err) {
    console.log(err);
    return;
  }
  console.log('success');
})
```

## stat

```js
fs.stat(path, callback);
```

该方法通常用来获取文件状态，比如在执行 `open`、`read` 等方法前先检查文件是否存在

```js
var fs = require('fs');
fs.stat('foo.txt', function(err, result) {
  if (err) throw err;
  console.log(result)
})
```

在 `File System` 模块提供的API中，还有一个 `fstat` ，它与 `stat` 在功能上是等价的，唯一不同的是，`fstat` 方法的第一个参数是文件描述符，它通常与 `open` 方法配合使用

```js
fs.open('foo.txt', function(err, fd) {
  if (err) throw new Error(err);
  console.log(fd);

  fs.fstat(fd, function(err, result) {
    if (err) throw new Error(err);
    console.log(result);
  })
})
```

在日常应用中，我们经常使用 `readdir` 和 `stat` 两个方法来获取目录下的所有文件名，`fs.readdir` 方法获取当前目录下所有文件或子目录，而 `fs.stat` 用于判断每条记录是文件还是文件夹，如果是文件夹，则递归调用自己。

```js
var fs = require('fs');
function getAllFileFromPath(path) {
  fs.readdir(path, function(err, res) {
    if (err) throw new Error(err);
    for (let subPath of res) {
      // 使用同步方法
      let statObj = fs.statSync(path + '/' + subPath);
      if (statObj.isDirectory()) {  // 判断是否为目录
        console.log('Dir: ', subPath);
        getAllFileFromPath(path + '/' + subPath);
      } else {
        console.log('File: ', subPath);
      }
    }
  })
}

getAllFileFromPath(__dirname);
```

# HTTP服务

`HTTP` 模块是 `Node` 的核心模块，主要提供了一系列用于网络传输的API

下面是在 `HTTP` 模块中定义的顶级类、属性以及方法：

- Class: `http.Agent`
- Class: `http.ClientRequest`
- Class: `http.Server`
- Class: `http.ServerResponse`
- Class: `http.IncomingMessage`
- `http.METHODS`
- `http.STATUS_CODES`
- `http.createClient([port] [, host])`
- `http.createServer([requiestListener])`
- `http.get(options[, callback])`
- `http.globalAgent`
- `http.request(options[, callback])`

## 创建HTTP服务器

通常我们使用 `createServer` 方法来创建 `HTTP` 服务器

```js
var http = require('http');
var server = http.createServer(function(req, res) {
  res.writeHead(200, { 'Content-Type': 'text/plain' });
  res.end('Hello Node!');
});

server.listen(3000);
```

上面的代码中，`createServer` 方法返回一个 `http.server` 类的实例，它包含一个匿名的回调函数，该函数有 `req` 和 `res` 两个参数，分别是 `InComingMessage` 和 `ServerResponse` 的实例，代表 `request` 和 `response` 对象，服务创建完成后， `Node` 进程开始循环监听3000端口。

当客户端访问该服务时，会触发 `connection` 和 `request` 事件，示例如下：

```js
var http = require('http');
var server = http.createServer(function(req, res) {
  res.writeHead(200, { 'Content-Type': 'text/plain' });
  res.end('Hello Node');
});


server.on('connection', function(req, res) {
  console.log('connected');
});

server.on('request', function(req, res) {
  console.log('request');
});

server.listen(3000);
// connected
// request
// request
```

下面我们来创建一个简单的文件服务器

```js
var http = require('http');
var fs = require('fs');
var server = http.createServer(function(req, res) {
  if (req.url === '/') {
    // 访问的是根目录，显式文件列表
    var fileList = fs.readFileSync('./');
    res.writeHead(200, { 'Content-Type': 'text/plain' });
    // 将数组转换为字符串后打印
    res.end(fileList.toString());
  } else {
    var path = req.url;
    fs.readFile(`.${path}`, function (err, data) {
      if (err) {
        res.end('Internal Error');
        throw new Error(err);
      }
      res.writeHead(200, { 'Content-Type': 'text/plain' });
      res.end(data);
    });
  }
});

server.listen(9527);
console.log('server is running at 9527...');

// 处理异常
process.on('uncaughtException', function() {
  console.log('got error');
})
```

## 处理http请求

当处理 `http` 请求时，最先做的就是获取请求的 `URL`、`method` 等信息。`Node` 将相关信息都封装在 `request` 对象中，它是 `IncomingMessage` 的实例。

```js
var method = req.method;
var url = req.url;
```

`method` 的值通常是 `get`、 `post`、`put`、`delete` 和 `update`.

`header` 是一个JSON对象，可以通过属性名进行单独索引

```js
var headers = req.headers;
var userAgent = headers['user-agent'];
```

`Node` 使用 `stream` 来处理 `HTTP` 的请求体，它注册了 `data` 和 `end` 两个事件

```js
var body = [];
request.on('data', function(chunk) {
  body.push(chunk);
}).on('end', function() {
  body = Buffer.concat(body).toString();
})
```

## Response对象

设置状态码 `statusCode` ，在 `Node` 并非必须，如果没有设置则默认都是200，但这不能代表所有的情况，所以，最佳实践就是手动设置状态码。

我们通过 `setHeader` 方法来设置 `response` 的头部信息

```js
response.setHeader('Content-Type': 'application/json');
response.setHeader('X-Powered-By', 'bacon');
```

`setHeader` 一次只能设置单个属性，如果想设置多个，可以使用 `writeHead` 方法。

```js
response.writeHead(200, {
  'Content-Length': Buffer.byteLength(body),
  'Content-Type': 'text/plain'
})
```

`response` 对象时一个 `writableStream` 实例，可以直接使用 `write` 方法写入，写入完成后再调用 `end` 方法发送到客户端

```js
response.write('<html>');
response.write('<body>');
response.write('<h1>Hello, World!</h1>');
response.write('</body>');
response.write('</html>');
response.end();
```

但这样写太麻烦，我们可以直接将返回的内容作为参数写到 `end` 方法中

```js
response.end('<html><body><h1>Hello, World!</h1></body></html>');
```

`response.end` 方法在每个 `HTTP` 请求的最后都会被调用。当客户端请求完成后，我们应该调用该方法来结束 `HTTP` 请求。

`end` 方法支持一个字符串或 `buffer` 作为参数，以指定请求最后返回的数据，如果定义了回调方法，那么会在 `end` 返回后调用。

```js
res.end('Hello Node', function() {
  console.log('http cycle end');
})
```

## 数据上传

在传统的Web开发中，最常用的HTTP请求只有 `get` 和 `post` 两种，`get` 请求的报文简单，只有请求行和请求头，`post` 还有请求体。

对于 `Node` 而言，可以通过 `req.method` 属性来判断请求方法的类型。

```js
var http = require('http');
var server = http.createServer(function(req, res) {
  if (req.method === 'get') {
    // todo..
  }

  if (req.method === 'post') {
    // todo...
  }
})
```

## HTTP客户端服务

HTTP模块除了能在服务端处理请求之外，还可以作为客户端向其他服务器发起请求。

```js
var http = require('http');
http.get('https://blockchain.info/ticker', function(res) {
  var statusCode = res.statusCode;
  if (statusCode === 200) {
    var result = '';
    res.on('data', function(data) {
      result += data;
    })
    res.on('end', function() {
      console.log(result.toString());
    })
    res.on('error', function() {
      console.log(e.message);
    })
  }
})
```

# Module

目前 `JavaScript` 有两种流行的模块化方案，分别是 `CommonJS` 和 `AMD`。

`CommonJS` 将每个文件看做一个模块，模块内部定义的变量都是私有的，无法被外部模块调用。但可以通过预定义方法（`expoets`、`require`）将其暴露出来。`CommonJS` 的应用实现就是 `Node`

`CommonJS` 有一个显著的特点就是模块加载是同步的。

`AMD` 就是 `Asynchronous Module Definition` 的缩写，意思就是异步模块定义，它采用异步方式加载模块。

## require

`CommonJS` 使用 `require` 关键字来加载模块

```js
// person.js
var person = {
  talk: function() {
    console.log('I am talking...');
  }，
  listen: function() {
    console.log('I am listening....');
  }
  // more functions ..
}
module.exports = person;
```

外部模块如果需要使用上面的 `person` 接口，使用 `require` 加载即可。

```js
var person = require('./perosn.js');
person.talk();
```

同时，我们也可以只引入 `person` 接口的一部分方法

```js
var talk = require('./person').talk;
talk();
```

在 `Node` 中，我们无需担心模块重复加载的问题，因为 `Node` 默认是从缓存中加载模块的，当一个模块首次被加载后，会在缓存中保留一个副本，后面如果再次加载同样的模块， `Node` 会从缓存中直接读取此模块的唯一的一个实例。

`require` 的缓存策略，上面说过，当 `Node` 第一次加载模块后，会在缓存中保留一份此模块的实例，这种缓存策略是基于**文件路**径来定位的，也就是说，如果有两个一模一样的文件，但其存放的路径不一样，那么 `Node` 也会保留两份模块的实例。

## 作用域

`Node` 中的作用域和浏览器中的有一些区别，它是以不同情况来区分的。

在控制台（`Node repl`）中，全局的 `this` 指向 `global` 对象。

而在文件脚本中，`this` 则指向了 `module.exports`

在 `Node` 中，有以下几种作用域类型：

- 全局作用域：如果一个变量没有使用 `var`、`let` 或 `const` 定义，那么它就属于全局作用域，可以通过 `global` 对象访问。
- 模块作用域：如果变量在文件中使用 `var`、`let` 或 `const` 定义，那么此时的 `this` 指向`module.exports`
- 函数作用域
- 块级作用域

# Process对象

# Stream

`Stream` 模块为Node操作流式数据提供了支持。要使用 `Stream`模块，需要增加引用。

```js
var stream = require('stream');
```

## 分类

在Node中，有四种基础的 `stream` 类型：

- `Readable`：可读流（`fs.createReadStream()`）
- `Writable`：可写流（`fs.createWriteStream()`）
- `Duplex`：既可读，又可写(`net.Socket`)
- `Transform`：操作写入的数据，然后读取结果。

# TCP服务

相对于HTTP服务，TCP的出场率并不高。

我们都知道 `Socket` ，它是对TCP协议的一种封装。`Socket` 并不是协议，而是一个编程接口，如果一种编程语言实现了 `Socket` 接口，那么就可以通过 `Socket` 接口预定义的方法来解析使用TCP协议传输的数据流。

`Node` 中有三种 `Socket`，分别对应实现TCP、UDP和Unix Socket。

Net模块和HTTP模块很相似，包含了 `Server` 类、`Socket` 类以及一些预定义方法。下面我们来创建一个TCP Server.

```js
var net = require('net');
var server = net.createServer(function(c) {
  console.log('client connected');
  c.on('end', function() {
    console.log('client disconnected');
  });
  c.write('hello\r\n');
  c.pipe(c);
});
server.on('error', function(err) {
  throw err;
});
server.listen(8124, function() {
  console.log('server bound');
})
```

下面我们写一个客户端来连接它：

```js
const net = require('net');
const client = net.connect({ port: 8124 }, function() {
  // 'connect' listener
  console.log('connected to server!');
  client.write('world!\r\n');
});
client.on('data', function(data) {
  console.log(data.toString());
  client.end();
});
client.on('end', function() {
  console.log('disconnected from server');
})
```

# Timer

# WebSocket

WebSocket可以看做是HTTP的升级版，它主要是为了弥补HTTP协议无法持久化和无状态而诞生的。

WebSocket提供了客户端和服务端之间全双工的通信机制。

## 保持通话

HTTP非持久化，当客户端发起 `request` 时，服务器会返回一个 `response`，那么HTTP连接就结束了，TCP也随之关闭，如果想要继续访问服务器就必须重新发起连接。

为了改进，HTTP1.1在请求头中增加了 `Connection: Keep-Alive` 字段，当服务器接受到这个字段后，会保持TCP连接不断开，同时，`response` 中也会增加这一字段，这样，客户端和服务器端就可以只建立一次连接而进行多次HTTP通信了。

这个属性已被加入到标准之中，除非指定 `close` ，为了避免无限制的长连接，服务器也会设置一个 `timeout` 属性，用来指定该长连接可以保持的最长时间。

`Keep-Alive` 解决了因为多次的TCP握手带来的性能损耗，但它没有从根本上解决实时通信的问题。

## WebSocket的意义

`WebSocket` 就是为了解决实时通信的问题而生的。请求不再只由客户端发起，服务器端可以主动推送消息给客户端。

客户端发送 `WebSocket` 的请求头如下：

<img src="./images/20190319223722.png" />

服务器端返回消息如下：

<img src="./images/20190319223738.png" />

在请求头中，`Connection` 字段必须设置成 `Upgrade`，表示客户端希望升级连接。 `Upgrade` 字段设置成 `WebSocket`，表示希望升级到 `WebSocket` 协议。

`Sec-WebSocket-Key` 是一串随机字符串，服务器端会用这些数据构造出一个SHA-1的信息摘要。

`Sec-WebSocket-Version` 表示支持的 `WebSocket` 版本。

## 在Node中使用WebSocket

在Node中，由很多支持 `WebSocket` 的三方模块，其中 `WS` 就是其中之一。

```js
// JavaScript 连接到WebSocket
var ws = new WebSocket('ws://localhost:3004');
ws.onopen = function() {
  ws.send('Hello');
}
ws.onmessage = function(msg) {
  console.log(msg.data);
}

// Node实现WebSocket
var WebSocketServer = require('ws').Server;
var wss = new WebSocketServer({ port: 3004 });
wss.on('connection', function(ws) {
  ws.on('message', function(message) {
    console.log('recevied: %s', message);
  });
  ws.send('I am a message sent from a ws server!');
})
```

在Node中，比较出名的 `WebSocket` 模块还有 `Socket.IO`，常被用来做在线聊天或推送服务等。

# 多进程服务

# 安全传输SSL

在企业级开发中，安全至关重要，普通的HTTP都是铭文传输数据，所以我们需要更安全的HTTPS（HTTP+SSL）。

<img src="./images/20190318222726.png" width="300px" />

## 什么是SSL

SSL(Secure Sockets Layer 安全套接层),协议以及继任者TLS协议是为网络通信提供安全及数据完整性的一种安全协议。它们在传输层对网络连接加密，它和HTTP组合为HTTPS，和WebSocket组合为WSS

# ECMAScript6

# Iterator

# Set和Map

# 函数

# 块级作用域

# 对象

# 数组

# 类

# 类的继承

# 使用Promise

# 回调终点-async/await

# 异步操作的返回值

# 组织回调方法

# 过渡方案Generator

# Koa入门

# Koa源码剖析

# Middleware

# NodeWeb发展历程

# 使用Redis实现持久化

# 健壮的Web应用

# 内容规划

# 常用服务实现

# 网站部署


------------

### 未完待续!

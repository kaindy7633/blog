<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [XMLHttpRequest对象](#xmlhttprequest%E5%AF%B9%E8%B1%A1)
- [XHR用法](#xhr%E7%94%A8%E6%B3%95)
- [发送异步请求](#%E5%8F%91%E9%80%81%E5%BC%82%E6%AD%A5%E8%AF%B7%E6%B1%82)
- [HTTP头部信息](#http%E5%A4%B4%E9%83%A8%E4%BF%A1%E6%81%AF)
- [GET请求](#get%E8%AF%B7%E6%B1%82)
- [POST请求](#post%E8%AF%B7%E6%B1%82)
- [XMLHttpRequest2级](#xmlhttprequest2%E7%BA%A7)
  - [FormData](#formdata)
- [跨域资源共享](#%E8%B7%A8%E5%9F%9F%E8%B5%84%E6%BA%90%E5%85%B1%E4%BA%AB)
- [IE 对 CORS 的实现](#ie-%E5%AF%B9-cors-%E7%9A%84%E5%AE%9E%E7%8E%B0)
- [其他浏览器对 CORS 的实现](#%E5%85%B6%E4%BB%96%E6%B5%8F%E8%A7%88%E5%99%A8%E5%AF%B9-cors-%E7%9A%84%E5%AE%9E%E7%8E%B0)
- [Preflighted Requests](#preflighted-requests)
- [带凭据的请求（Requests with Credential）](#%E5%B8%A6%E5%87%AD%E6%8D%AE%E7%9A%84%E8%AF%B7%E6%B1%82requests-with-credential)
- [跨浏览器的 CORS (兼容性 CORS的写法)](#%E8%B7%A8%E6%B5%8F%E8%A7%88%E5%99%A8%E7%9A%84-cors-%E5%85%BC%E5%AE%B9%E6%80%A7-cors%E7%9A%84%E5%86%99%E6%B3%95)
- [其他跨域技术](#%E5%85%B6%E4%BB%96%E8%B7%A8%E5%9F%9F%E6%8A%80%E6%9C%AF)
  - [JSONP](#jsonp)
- [其他跨域](#%E5%85%B6%E4%BB%96%E8%B7%A8%E5%9F%9F)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## XMLHttpRequest对象

IE7+,FireFox,Chrome,Opera,Safari创建XHR对象:

```javascript
var xhr=new XMLHttpRequest();
```

创建XHR对象的兼容性写法:

```javascript
function createXHR(){
  if(typeof XMLHttpRequest!="undefined"){
    return new XMLHttpRequest();
  }else if(typeof ActiveXObject!="undefined"){
    if(typeof arguments.callee.activeXString!="string"){
      var versions=["MSXML2.XMLHttp.6.0","MSXML2.XMLHttp.3.0","MSXML2.XMLHttp"],
          i,len;
      for(i=0,len=versions.length;i<len;i++){
        try{
          new ActiveXObject(versions[i]);
          arguments.callee.activeXString=versions[i];
          break;
        }catch(ex){
     
        }
      }
    }
    return new ActiveXObject(arguments.callee.activeXString);
  }else{
    throw new Error("NO XHR object available");
  }
}
     
var xhr=new createXHR();
```

## XHR用法

发送同步请求

使用 `XHR` 时，首先要调用 `open()` 方法，传递三个参数：

1. 要发送的请求类型（ get , post 等）
2. 请求的 url
3. 是否异步发送

要发送特定的请求，必需像下面这样调用 `send()` 方法

```javascript
xhr.open("get","example.php",false);
xhr.send(null);
```

这里 `send()` 方法接收一个参数，作为请求主体发送的数据。如果不需要通过请求主体发送数据，这里必须传入 `null` ，因为这个参数对有些浏览器来说是必需的。调用 `send()` 之后，请求就会被分派到服务器。

由于这次请求是同步的，JavaScript 代码会等到服务器响应之后再继续执行。在收到响应之后，相应的数据会自动填充XHR对象的属性，相关的属性简介如下：

- `responseText`: 作为响应主体被返回的文本。
- `responseXML`: 如果响应的内容类型是 “text/xml”或”application/xml”，这个属性中将保存包含着相应数据的XML DOM文档。
- `status`: 响应的HTTP状态。
- `statusText`: HTTP状态的说明。

接受响应之后，第一步是检查 `status` 属性，以确定响应已经成功返回。状态码：

- 200 表示成功
- 304 表示请求的资源并没有修改，可以直接使用浏览器中缓存的版本，响应也是有效的

像下面这样检查上述这两种状态码的状态：

```javascript
xhr.open("get","example.txt",false);
xhr.send(null);
     
if((xhr.status >= 200 && xhr.status < 300)|| xhr.status == 304){
  alert(xhr.responseText);
}else{
  alert("Request was unsuccessful: " + xhr.status);
}  
```

注意：无论内容类型是什么，响应主体的内容都会保存到 `responseText` 属性中；而对于非 `XML` 数据而言， `responseXML` 属性的值将为 `null`。

## 发送异步请求

像前面这样发送同步请求当然没问题，但多数情况下，我们还是要发送异步请求，才能让 JavaScript 继续执行而不必等待响应。此时，可以检测 `XHR` 对象的 `readyState` 属性，该属性表示请求/响应过程中的当前活动阶段。这个属性可取的值如下：

- 0：未初始化。尚未调用 `open()` 方法。
- 1：启动。已经调用 `open()` 方法，但尚未调用 `send()` 方法。
- 2：发送。已经调用 `send()` 方法，但尚未接收响应。
- 3：接收。已经接收到部分响应数据。
- 4：完成。已经接收到全部响应数据，而且已经可以在客户端使用了。

只要 `readyState` 属性的值由一个值变为另一个值，都会触发一次 `readystatechange` 事件。可以利用这个事件来检测每次状态变化后的 `readyState` 的值，通常，我们只对 `readyState` 值为 `4` 的阶段感兴趣，因为这时所有的数据都已经就绪。不过，必须在调用 `open()` 之前指定 `onreadyState` 事件处理程序才能确保跨浏览器兼容性。例子如下：

```javascript
var xhr = createXHR();
xhr.onreadyStatechange = function(){
  if(xhr.readyState == 4){
    if((xhr.status >= 200 && xhr.status < 300) || xhr.status == 304){
      alert(xhr.responseText);
    }else{
      alert("Request was unsuccessful:" + xhr.status );
    }
  }
};
     
xhr.open("get","example.txt",true);
xhr.send(null);
```

另外，在接收到响应之前还可以调用 `abort()` 方法来取消异步请求，如下所示：

```javascript
xhr.absort();
```

调用这个方法后，`XHR` 对象会停止触发事件，而且也不再允许访问任何与响应有关的对象属性。

## HTTP头部信息

每个 `HTTP` 请求和响应都会带有响应的头部信息，有的对开发人员有用，有的也没有什么用，`XHR` 对象也提供了操作这两种头部（即请求头部和响应头部）信息的方法。 默认情况下，在发送 `XHR` 请求的同事，还会发送下列头部信息。

- Accept: 浏览器能够处理的内容类型。
- Accept-Charset: 浏览器能够显示的字符集。
- Accept-Encoding: 浏览器能够处理的压缩编码。
- Accept-Language: 浏览器当前设置的语言。
- Connection: 浏览器与服务器之间连接的类型。
- Cookie: 当前页面设置的语言。
- Host: 发出请求的页面所在的域。
- Referer: 发出请求的页面的URI。
- User-Agent: 浏览器的用户代理字符串。

使用 `setRequestHeader()` 方法可以设置自定义的请求头部信息。这个方法接受两个参数：头部字段的名称和头部字段的值。要成功发送请求头部信息，必须在调用 `open()` 方法之后且调用 `send()` 方法之前调用 `setRequestHeader()`,如下面的例子所示。

```javascript
var xhr = createXHR();
xhr.onreadystatechange = function(){
  if(xhr.readyState == 4){
    if((xhr.status >= 200 && xhr.status < 300) || xhr.status = 304){
      alert(xhr.responseText);
    }else{
      alert("Request was unsuccessful: " + xhr.status);
    }
  }
};

xhr.open("get","example.php",true);
xhr.setRequestHeader("MyHeader","MyValue");
xhr.send(null); 
```

服务器在接收到这种自定义的头部信息之后，可移植性响应的后续操作。建议使用自定义的头部字段名称，不要使用浏览器正常发送的字段名称。

调用 `XHR` 对象的 `getResponseHeader()` 方法并传入头部字段名称，可以取得相应的响应头部信息。而调用 `getAllResponseHeaders()` 方法可以取得一个包含所有头部信息的长字符串。看下面的例子：

```javascript
var myHeader=xhr.getResponseHeader("MyHeader");
var allHeader=xhr.getAllResponseHeaders();
```

## GET请求

`GET` 是最常见的请求类型，最常用于向服务器查询某些信息。必要时，可以讲查询字符串参数追加到 `URL` 的末尾，以便将信息发送给服务器。对 `XHR` 而言，位于传入 `open()` 方法的 `URL` 末尾的查询字符串必须经过正确的编码才行。

使用 `GET` 请求经常会发生的一个错误，及时查询字符串的格式有问题。查询字符串中每个参数的名称和值必须使用 `encodeURIComponent()` 进行编码，然后才能放到 `URL` 的末尾；而且所有名-值对都必须由和号(`&`)分隔，例子如下：

```javascript
xhr.open("get","example.php?name1=value1&name2=value2",true);
```

下面这个函数可以辅助向现有 `URL` 的末尾添加查询字符串参数：

```javascript
function addURLParam(url,name,value){
  url += (url.indexOf("?") == -1? "?":"&");
  url += encodeURIComponent(name) + "=" + encodeURIComponent(value);
}
```

使用方法：

```javascript
var url="example.php";
 
//添加参数
url = addURLParam(url,"name","Nocholas");
url = addRULParam(rul,"book","Professional JavaScript");
 
//初始化请求
xhr.open("get",url,false);
```

## POST请求

`POST` 请求通常用于向服务器发送应该被保存的数据。`POST` 请求应该吧数据作为请求的主体提交，而 `GET` 请求传统上不是这样。

默认情况下，服务器对 `POST` 请求和提交 Web 表单的请求并不会一视同仁。因此，服务器端必须有程序来读取发送过来的原始数据，并从中解析出有用的部分。不过，我们可以使用 `XHR` 来模仿表单提交：首先将 `Content-Type` 头部信息设置为 `application/x-www-from-urlencoded` ,也就是表单提交时的内容类型，其次是以适当的格式创建一个字符串。如下所示：

```javascript
function submitData(){
  var xhr = createXHR();
  xhr.onreadystatechange = function(){
    if(xhr.readyState == 4){
      if((xhr.status >= 200 && xhr.status < 300) || xhr.status = 304){
        alert(xhr.responseText);
      }else{
        alert("Request was unsuccessful: " + xhr.status);
      }
    }
  };
  xhr.open("post","example.php",true);
  xhr.setRequestHeader("Content-Type","application/x-www-from-urlencoded");
  var form=document.getElementById("user-info");
  xhr.send(serialize(form));
} 
```

这个函数可以将 ID 为 “user-info” 的表单中的数据序列化之后发送给服务器。

## XMLHttpRequest2级

`XMLHttpRequest` 1级只是把已有的 `XHR` 对象的实现细节描述了出来。而 `XMLHttpRequest` 2级则进一步发展了 `XHR`。并非所有浏览器都完整地实现了 `XMLHttpRequest` 2级规范。

### FormData

现代 Web 应用中频繁使用的一项功能就是表单数据的序列化，`XMLHttpRequest` 2级为此定义了 `FormData` 类型。`FormData` 为序列化表单以及创建与表单格式相同的数据提供了便利。下面代码创建了 `FormData` 对象，并向其中添加了一些数据。

```javascript
var data = new FormData();
data.append("name","Nicholas");
```

这个 `append()` 方法接受两个参数：键和值，分别对应表单字段的名字和字段中包含的值。可以像这样添加任意多的键值对。而通过向 `FormData` 构造函数中传入表单元素，也可以用表单元素的数据预先向其中填入键值对：

```javascript
var data=new FormData(document.forms[0]);
```

创建了 `FormData` 的实例后，可以将它直接传给 `XHR` 的 `send()` 方法，如下所示：

```javascript
function submitData(){
  var xhr = createXHR();
  xhr.onreadystatechange = function(){
    if(xhr.readyState == 4){
      if((xhr.status >= 200 && xhr.status < 300) || xhr.status = 304){
        alert(xhr.responseText);
      }else{
        alert("Request was unsuccessful: " + xhr.status);
      }
    }
  };

  xhr.open("post","example.php",true);
  var form=document.getElementById("user-info");
  xhr.send(new FormData(form));
} 
```

使用 `FormData` 的方便之处在于不必明确地在 `XHR` 对象上设置请求头部。`XHR` 对象能够识别传入的数据类型是 `FormData` 的实例，并配置适当的头部信息。

支持 `FormData` 的浏览器有 Firefox4+，Safari5+，Chrome和Android3+版WebKit。

## 跨域资源共享

通过 `XHR` 实现 `Ajax` 通信的一个主要限制，来源于跨域安全策略。

CORS(Cross-Origin Resource Sharing，跨域资源共享)背后的基本思想，及时使用自定义的HTTP头部让浏览器与服务器进行沟通，从而决定请求或响应是应该成功，还是应该失败。

比如一个简单地使用 `GET` 或 `POST` 发送的请求，它没有自定义的头部，而主题内容是 `text/plain`。在发送该请求时，需要给它附加一个额外的 `Origin` 头部，其中包括请求页面的源信息（协议、域名、端口），以便服务器根据这个头部信息来决定是否给予响应，下面是 `Oringin` 头部的一个示例：

```
Origin: http://www.nczonline.net
```

如果服务器认为这个请求可以接受，就在 `Access-Control-Allow-Origin` 头部中回发相同的源信息（如果是公共资源，可以回发 “*”）。例如：

```
Access-Control-Allow-Origin: http://www.nczonline.net
```

如果没有这个头部，或者有这个头部但源信息不匹配，浏览器就会驳回请求。正常情况下，浏览器会处理请求。注意，请求和响应都不包含 `cookie` 信息。

## IE 对 CORS 的实现

微软在 IE8 中引入了 `XDR` (XDomainRequest) 类型。这个对象与 `XHR` 类似，但能实现安全可靠的跨域通信。`XDR` 对象的安全机制部分实现了 `W3C` 的 `CORS` 规范。以下是 `XDR` 与 `XHR` 的一些不同之处。

- `cookie` 不会随请求发送，也不会随响应返回。
- 只能设置请求头部信息的 `Content-Type` 字段。
- 不能访问响应头部信息。
- 只支持`GET`和`POST`请求。

所有的 `XDR` 请求都是异步执行的，不能用它来创建同步请求。请求返回之后，会触发 `load` 事件，响应的数据也会保存在 `responseText` 属性中。

在接收到响应后，你只能访问响应的原始文本；没有办法确定响应的状态代码。而且，只要响应有效就会触发 `load` 事件，如果失败（包括响应中缺少 `Access-Control-Allow-Origin` 头部），就会触发 `error` 事件。遗憾的是，除了错误本身之外，没有其他信息可用，因此唯一能够确定的就只有请求未成功了。要检测错误，可以像下面这样指定一个 `onerror` 事件处理程序。

```javascript
var xdr=new XDomainRequest();
xdr.onload=function(){
  alert(xdr.responseText);
};
xdr.onerror=function(){
  alert("An erro occurred.");
};
xdr.open("get","http://www.somewhere-else.com/page");
xdr.send(null);
```

为支持 `POST` 请求，`XDR` 对象提供了 `contentType` 属性，用来表示发送数据的格式，如下所示：

```javascript
var xdr=new XDomainRequest();
xdr.onload=function(){
  alert(xdr.responseText);
};
xdr.onerror=function(){
  alert("An erro occurred.");
};
xdr.open("post","http://www.somewhere-else.com/page");
xdr.contentType="application/x-www-form-urlencoded";
xdr.send("name1=value1&name2=value2");
```

这个属性通过 `XDR` 对象影响头部信息的唯一方式。

## 其他浏览器对 CORS 的实现

Forefox3.5+,Sarari4+,Chrome,iOS 版 Sarari 和 Android 平台中的 `WebKit` 都通过 `XMLHttpRequest` 对象实现了对 `CORS` 的原生支持。在尝试打开不同来源的资源时，无需额外编写代码就可以出发这个行为。要请求位于另一个域中的资源，使用标准的 `XHR` 对象并在 `open()` 方法中传入绝对 `URL` 即可，例如：

```javascript
var xhr=createXHR();
xhr.onreadystatechange=function(){
  if(xhr.readyState == 4){
    if((xhr.status >= 200 && xhr.status < 300) || xhr.status == 304){
      alert(xhr.responseText);
    }else{
      alert("Request was unsuccessful: " + xhr.status);
    }
  }
};

xhr.open("get","http://www.somewhere-else.com/page/",true);
xhr.send(null); 
```

与 IE 中的 `XDR` 对象不同，通过跨域 `XHR` 对象可以访问 `status` 和 `statusText` 属性，而且还支持同步请求，跨域 `XHR` 对象也有一些限制，但为了安全，这些限制是必需的，一下就是这些限制。

- 不能使用 `setRequestHeader()` 设置自定义头部。
- 不能发送和接收 `cookie`。
- 调用 `getAllResponseHeaders()` 方法总会返回空字符串。

对于本地资源，最好使用相对 `RUL`,在访问远程资源时再使用绝对 URL。

## Preflighted Requests

`CORS` 通过一种叫做 `Preflighted Requests` 的透明服务器验证机制支持开发人员使用自定义的头部，`GET` 或 `POST` 之外的方法，以及不同类型的主体内容，在使用下列高级选项来发送请求时，就会像服务器发送一个 `Preflight` 请求。这种请求使用 `OPTIONS` 方法，发送下列头部。

- `Origin`: 与简单的请求相同。
- `Access-Control-Request-Method`: 请求自身使用的方法。
- `Access-Control-Request-Headers`: (可选) 自定义的头部信息，多个头部以逗号分隔。

以下是一个带有自定义头部的 `NCZ` 的使用 `POST` 方法发送的请求。

```
Origin: http://www.nczonline.net
Access-Control-Request-Method: POST
Access-Control-Request-Headers: NCZ
```

发送这个请求后，服务器可以决定是否允许这种类型的请求。服务器通过在响应中发送如下头部与浏览器进行沟通。

```
Access-Control-Allow-Origin: 与简单的请求相同。
Access-Control-Allow-Method: 允许的方法，多个方法以逗号分隔。
Access-Control-Allow-Headers: 允许的头部，多个头部以逗号分隔。
Access-Control-Max-Age: 应该将这个 Preflight 请求缓存多长时间（以秒表示）。
```
例如：

```
Access-Control-Allow-Origin: http://www.nczonline.net
Access-Control-Allow-Method: GET,POST
Access-Control-Allow-Headers: NCZ
Access-Control-Max-Age: 1728000
```

`Preflight` 请求结束后，结果将按照响应中指定的事件缓存起来。而为此付出的代价只是第一次发送这种请求时会多一次 `HTTP` 请求。

支持 `Preflight` 请求的浏览器包括 Firefox3.5+， Sarari4+ 和 Chrome。IE10 及更早版本都不支持。

## 带凭据的请求（Requests with Credential）

默认情况下，跨域请求不提供凭据（Cookie、HTTP 认证及客户端 SSL 证明等）。通过将 `withCredentials` 属性设置为 `true`，可以指定某个请求应该发送凭据。如果服务器接收带凭据的请求，会用下面的 `HTTP` 头部来响应。

```
Access-Control-Allow-Credentials: true
```

如果发送的是带凭据的请求，单服务器的响应中没有包含这个头部，那么浏览器就不会把响应交给 JavaScript （于是，`responseText` 中将是空字符串，`status` 的值为0，而且会调用 `onerror()` 事件处理程序）。

支持 `withCredentials` 属性的浏览器有 Firefox3.5+，Sarari4+ 和 Chrome。IE10 及更早版本都不支持。

下面这篇文章讲的特别好，介绍了简单地跨域请求、`Preflight` 请求和带凭据的请求三种请求的区别和请求流程。 文章地址：http://www.cnblogs.com/loveis715/p/4592246.html

## 跨浏览器的 CORS (兼容性 CORS的写法)

即使浏览器对 `CORS` 的支持程度并不都一样，但所有浏览器都支持简单地（非 Preflight 和不带凭据的）请求，因此有必要实现一个跨浏览器的方案。检测 `XHR` 是否支持 `CORS` 的最简单的方式，就是检查是否存在 
`withCredentials` 属性，再结合检测 `XDomainRequest` 对象是否存在，就可以兼顾所有浏览器了。

```javascript
function createCORSRequest(method,url){
  var xhr=new XMLHttpRequest();
  if("withCredentials" in xhr){
    xhr.open(method,url,true);
  }else if(typeof XDomainRequest != "undefined"){
    xhr = new XDomainRequest();
    xhr.open(method,url);
  }else {
    xhr = null;
  }
  return xhr;
}
 
var request = createCORSRequest("get","http://www.somewhere-else.com/page/");
if(request){
  request.onload = function(){
    //对request。responseText进行处理
  };
  request.send();
}
```

## 其他跨域技术

### JSONP

`JSONP` 原理：`JSONP` 是通过动态`script`元素来使用的，使用时可以作为 `src` 属性指定一个跨域 URL。 这里的script元素有能力不受限制地从其他域加载资源。因为 JSONP 是有效的 JavaScript 代码，所以在请求完成后，即在 JSONP 响应加载到页面中以后，就会立即执行。来看一个例子。

```javascript
function handleResponse(response){
  alert("you are at IP address "+ response.ip+", which is in "+response.city+", "+response.region_name);
}
 
var script=document.createElement("script");
script.src="http://freegeoip.net/json/?callback=handleResponse";
document.body.insertBefore(script,document.body.firstChild);
```

下面这篇文章介绍了 `JSON` 和 `JSONP`,值得一看 文章地址：http://kb.cnblogs.com/page/139725/

## 其他跨域

其他跨域技术还有 Comet、SSE、WebSockets等。感兴趣的读者可以查阅相关资料进行了解。

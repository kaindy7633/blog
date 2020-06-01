# JavaScript装逼指南

## Boolean

```javascript
!!'foo'
```

通过两个取反，可以强制转换为`Boolean`类型

## Number

```javascript
+'45'
+new Date
```

自动转化为`number`类型的

## IIFE(自动执行函数)

```javascript
(function(arg) {
  // do something
})(arg)
```

## Closure(闭包)

```javascript
var counter = function() {
  var count = 0;
  return function() {
    retrun count++;
  }
}
```

好像没什么实用价值,看看下面的代码

```javascript
var isType = function(type) {
  retrun function(obj) {
    return toString.call(obj) == '[Object ' + type + ']';  
  }
}
```

## Event

如何写一个计数器呢?

```javascript
var times = 0;
var foo = document.querySelector('.foo');
foo.addEventListener('click', function() {
  times++;
  console.log(times);
}, false);
```

变量times被放在了外面，没封装啊，有命名冲突怎么办？

```javascript
foo.addEventListener('click', (function() {
  var times = 0;
  return function() {
    times++;
    console.log(times);
  }
})(), false);
```

通过创建一个闭包，把times封装到里面，然后返回函数,瞬间逼格高了起来!

## parseInt

现在摁下F12，在console里复制粘贴这样的代码：

```javascript
~~3.14159    // => 3
~~5.678      // => 5
```

~是一个叫做按位非的操作，会返回数值的反码。是二进制操作。JavaScript中的`number`都是`double`类型的，在位操作的时候要转化成`int`，两次~就还是原数。

## Hex

十六进制操作。其实就是一个`Array.prototype.toString(16)`的用法,做到随机的话可以这样

```javascript
(~~(Math.random()*(1<<24))).toString(16)
```

## «

左移操作,这个也是二进制操作。将数值二进制左移,解释上面的1<<24的操作。其实是1左移24位。000000000000000000000001左移24位，变成了1000000000000000000000000

其实还有一种更容易理解的方法来解释

```javascript
Math.pow(2,24) === (1 << 24)
```

因为是二进制操作，所以速度是很快的。

## BTW

```javascript
[].forEach.call($$("*"),function(a){
 a.style.outline="1px solid #"+(~~(Math.random()*(1<<24))).toString(16)
})
```

翻译成正常语言就是这样的

```javascript
Array.prototype.forEach.call(document.querySelectorAll('*'),
dom => dom.style.outline = `1px solid #${parseInt(Math.random() * Math.pow(2,24)).toString(16)}`)
```

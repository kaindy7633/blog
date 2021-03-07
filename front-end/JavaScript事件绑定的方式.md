## JavaScript 事件绑定

本文介绍一些 JavaScript 事件绑定的常用方法及其优缺点，同时在最后展示一个由 Dean Edwards 写的一个比较完美的事件绑定方案。

## 传统方式

```javascript
element.onclick = function(e){ // ... };
```

1. 传统绑定的优点

- 非常简单和稳定，可以确保它在你使用的不同浏览器中运作一致

- 处理事件时，`this` 关键字引用的是当前元素，这很有帮组

2. 传统绑定的缺点

- 传统方法只会在事件冒泡中运行，而非捕获和冒泡

- 一个元素一次只能绑定一个事件处理函数。新绑定的事件处理函数会覆盖旧的事件处理函数

- 事件对象参数(e)仅非 IE 浏览器可用

## W3C 方式

```javascript
element.addEventListener('click', function(e){ // ... }, false);
```

1. W3C 绑定的优点

- 该方法同时支持事件处理的捕获和冒泡阶段。事件阶段取决于 `addEventListener` 最后的参数设置：`false` (冒泡) 或 `true` (捕获)。

- 在事件处理函数内部，this 关键字引用当前元素。

- 事件对象总是可以通过处理函数的第一个参数(e)捕获。

- 可以为同一个元素绑定你所希望的多个事件，同时并不会覆盖先前绑定的事件

2. W3C 绑定的缺点

- IE 不支持，你必须使用 IE 的 `attachEvent` 函数替代。

## IE 方式

```javascript
element.attachEvent('onclick', function(){ // ... });
```

1. IE 方式的优点

- 可以为同一个元素绑定你所希望的多个事件，同时并不会覆盖先前绑定的事件。

2. IE 方式的缺点

- IE 仅支持事件捕获的冒泡阶段

- 事件监听函数内的 `this` 关键字指向了 `window` 对象，而不是当前元素（IE 的一个巨大缺点）

- 事件对象仅存在与 1window.event`参数中

- 事件必须以 `ontype` 的形式命名，比如，`onclick` 而非 `click`

- 仅 IE 可用。你必须在非 IE 浏览器中使用 W3C 的 `addEventListener`

## Dean Edwards 的方案（addEvent/removeEvent 库）

```javascript
function addEvent(elementment, type, handler) {
        // 为每个事件处理函数赋予一个独立的ID
        if(!handler.$$guid) handler.$$guid = addEvent.guid++;

        // 为元素建立一个事件类型的散列表
        if(!elementment.events) elementment.events = {};

        // 为每对元素/事件建立一个事件处理函数的散列表
        var handlers = elementment.events[type];

        if(!handlers) {
            handlers = elementment.events[type] = {};
            // 存储已有的事件处理函数(如果已存在一个)
            if(elementment["on" + type]) {
                handlers[0] = elementment["on" + type];
            }
        }

        // 在散列表中存储该事件函数
        handlers[handler.$$guid] = handler;

        // 赋予一个全局事件处理函数来出来所有工作
        elementment["on" + type] = handleEvent;
    }

    // 创建独立ID的计数器
    addEvent.guid = 1;

    function removeEvent(elementment, type, handler) {
        // 从散列表中删除事件处理函数
        if(elementment.events && elementment.events[type]) {
            delementte elementment.events[type][handler.$$guid];
        }
    }

    function handleEvent(event) {
        var returnValue = true;

        // 获取事件对象(IE使用全局的事件对象)
        event = event || fixEvent(window.event);

        // 获取事件处理函数散列表的引用
        var handlers = this.events[event.type];

        // 依次执行每个事件处理函数
        for(var i in handlers) {
            this.$$handerEvent = handlers[i];
            if(this.$$handlerEvent(event) === fasle) {
                returnValue = false;
            }
        }
        return returnValue;
    }

    // 增加一些IE事件对象缺乏的方法
    function fixEvent(event) {
        event.preventDefault = fixEvent.preventDefault;
        event.stopPropagation = fixEvent.stopPropagation;
        return event;
    }

    fixEvent.preventDefault = function() {
        this.returnValue = false;
    }

    fixEvent.stopPropagation = function() {
        this.cancelBubble = true;
    }
```

1. `addEvent` 的优点

- 可以在所有浏览器中工作，就算是更古老无任何支持的浏览器

- `this` 关键字可以在所有的绑定函数中使用，指向的是当前元素

- 中和了所有防止浏览器默认行为和阻止事件冒泡的各种浏览器特定函数

- 不管浏览器类型，事件对象总是作为第一个对象传入

2. `addEvent` 的缺点

- 仅工作在冒泡阶段（因为它深入使用事件绑定的传统方式）

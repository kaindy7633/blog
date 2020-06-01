# Web性能优化 - 关键渲染路径及其优化策略

想一想，如果你希望你的网站在一秒钟之内呈现用户想看的关键信息，有哪些可行的手段？Minify，压缩，雪碧图等等。

Google的Web性能工程师 `Ilya Grigorik` 会告诉你，你只需要理解浏览器的关键渲染路径。

## 页面性能可能是一个感性的东西

页面的性能，看似是一个理性和量化的概念，实则也来自于用户的感知，主观的评价，是一个偏感性的东西。

![](https://todever-images.oss-cn-beijing.aliyuncs.com/640.webp)

如果页面可以做到优先显示与用户操作有关的内容，就可以让用户更快速的感知到操作得到响应，这个过程叫做“优化关键渲染路径”。

## 什么是关键渲染路径

关键渲染路径就是描述浏览器从收到 HTML、CSS 和 JavaScript 字节开始，到如何使用HTML、CSS 和 JavaScript 在屏幕上渲染像素的中间过程。

如果我们能够优化这条路径，就能让页面更快速的展示内容，给用户更好的体验。

## 全景图

![](https://todever-images.oss-cn-beijing.aliyuncs.com/00002.webp)

## 文档对象模型 (DOM)

DOM概念之于Web开发人员再熟悉不过了，当浏览器发出请求并接收到HTML文档后，它会有这样一个流程来构建DOM：字节 → 字符 → 令牌 → 节点 → 对象模型。

以下面这段代码为例：

```html
<html>
  <head>
    <meta name="viewport" content="width=device-width,initial-scale=1">
    <link href="style.css" rel="stylesheet">
    <title>Critical Path</title>
  </head>
  <body>
    <p>Hello <span>web performance</span> students!</p>
    <div><img src="awesome-photo.jpg"></div>
  </body>
</html>
```

浏览器接收到HTML请求的返回结果，根据预定的流程解析HTML，文档中的“开始标签”，比如`<html>`，`<head>`等会转换成一个令牌（`Token`），然后令牌转换成节点对象（`Node`）

这个令牌解析并转换为节点对象的过程，也是每个节点建立关系（树形结构）的过程。例如：`head`的令牌出现在`html`令牌之后，但其闭标签出现在`html`闭标签之前，这就意味着`head`是`html`的子节点，以此类推，建立节点的父子关系。

![](https://todever-images.oss-cn-beijing.aliyuncs.com/003.webp)

这个过程在浏览器中，叫做“Parse HTML”。

![](https://todever-images.oss-cn-beijing.aliyuncs.com/004.webp)

## CSS 对象模型 (CSSOM)

当DOM捕获了页面的内容，我们还需要知道页面如何展示这些内容，所以需要构建 `CSS` 对象模型（`CSSOM`）。

浏览器解析DOM，遇到了`link`标签，发现它引用了一个外部样式资源：`style.css`，于是浏览器会向外部请求样式资源，然后进行后续的DOM构建工作。

`CSS` 被视为阻塞渲染的资源，这意味着浏览器将不会渲染任何已处理的内容，直至 `CSSOM` 构建完毕。

![](https://todever-images.oss-cn-beijing.aliyuncs.com/key_rendering%20_path-005.webp)

CSSOM有着一个和DOM构建相似的流程：字节 → 字符 → 令牌 → 节点 → CSS对象模型。

![](https://todever-images.oss-cn-beijing.aliyuncs.com/key_rendering_path-006.webp)

以下面的CSS样式为例，它会根据具体解析规则，将CSS文档转换成下面的树形结构：

```css
body { font-size: 16px }
p { font-weight: bold }
span { color: red }
p span { display: none }
img { float: right }
```

![](https://todever-images.oss-cn-beijing.aliyuncs.com/key_rendering_path-007.webp)

这种树形结构让CSS有层级继承关系，子节点会继承父节点的样式。

前面谈到CSS会阻塞浏览器的渲染过程，因为渲染树的构建同时需要DOM和CSSOM，所以当浏览器请求的`style.css`返回之后，浏览器会开始解析样式表，并重新计算样式（`Recalculate Style`），将CSS转换成CSSOM，然后进行后续的操作。

![](https://todever-images.oss-cn-beijing.aliyuncs.com/key_rendering_path-008.webp)

值得注意的是，CSSOM运算是一个非常复杂的过程，性能消耗会比较大，所以你会常常听到“老人们”说写样式“尽量使用`class`和`id`，保证层级扁平，减少过度层叠”，而且越是通用的CSS样式，执行速度越快，越是具体（选择器）的CSS样式，则执行速度越慢

## DOM + CSSOM = 渲染树

渲染树和DOM树不同，它只会捕获一些页面上可见的元素，比如，Header或display:none的元素不会放在渲染树中。

渲染树的构建会从DOM的根节点开始遍历，对于不可见节点会忽略，然后在CSSOM中找到每个对应节点的样式规则并应用，最后输出的渲染树会包含所有的可见内容和样式信息，如下图：

![](https://todever-images.oss-cn-beijing.aliyuncs.com/key_rendering_path-009.webp)

## 布局和绘制

有了渲染树，浏览器会进入布局和绘制阶段。

![](https://todever-images.oss-cn-beijing.aliyuncs.com/key_rendering_path-010.webp)

布局就是弄清每个对象在页面视窗（Viewport）上的确切大小和位置，它的输出是一个“盒模型”，里面准确的捕获每一个元素在页面视窗中的位置和尺寸。

在布局工作完成之后，浏览器会开始绘制，将渲染树转换成屏幕上的像素，这样，我们就能在浏览器中看到页面的内容。

短暂回顾一下“关键渲染路径”的步骤

- 处理 `HTML` 标记并构建 `DOM` 树
- 处理 `CSS` 标记并构建 `CSSOM` 树
- 将 `DOM` 与 `CSSOM` 合并成一个渲染树
- 根据渲染树来布局
- 将各个节点绘制到屏幕上

当`DOM`或者`CSSOM`发生变化的时候，浏览器就需要再次执行一次上面的步骤。

## JavaScript

JavaScript在整个关键渲染路径中扮演着非常重要的角色，就如全景图中画的那样，我们从一段简单的代码开始：

```html
<body>
  <p>Hello <span>web performance</span> students!</p>
  <script>
    var span = document.getElementsByTagName('span')[0];
    span.textContent = 'javascript';
  </script>
</body>
```

一个大家都知道的重要事实是：脚本在文档的何处插入，就在何处执行。

当HTML解析过程中遇到一个`script`标记时，它会暂停`DOM`构建，将控制权移交给JavaScript引擎，等JavaScript引擎运行完毕，浏览器再从中断的地方恢复`DOM`构建。也就是说，执行内联的JavaScript会阻塞页面的首次渲染。

现在我们假设，这段JavaScript是外部资源。

```html
<body>
  <p>Hello <span>web performance</span> students!</p>
  <script src="write.js"></script>
</body>
```

则浏览器的渲染会阻塞直到`write.js`的请求返回后，并执行JavaScript后，继续。

![](https://todever-images.oss-cn-beijing.aliyuncs.com/key_rendering_path-011.webp)

需要注意的是，在网页中引入JavaScript脚本有一个微妙事实，就是JavaScript不仅可以读取和修改`DOM`属性，还可以读取和修改`CSSOM`属性。

前面我们提到CSS是阻塞渲染的资源，当它和JavaScript一起出现在页面上时，会发生这样的事情：

```html
<html>
  <head>
    <meta name="viewport" content="width=device-width,initial-scale=1">
    <link href="style.css" rel="stylesheet">
    <title>Critical Path: Script</title>
  </head>
  <body>
    <p>Hello <script>document.write('web performance')</script> students!</p>
  </body>
</html>
```

在浏览器解析HTML构建DOM过程中，发现了`link`标签，于是发出请求获取`style.css`，然后继续构建DOM，此时，它发现`script`标签，由于JavaScript可能会访问样式属性，所以它会阻止JavaScript的执行直到`styles.css`返回并完成`CSSOM`构建，然后执行这一段JavaScript代码，再继续后面`DOM`的构建和相关渲染操作

于是`styles.css`的请求不仅阻塞后面的渲染，还阻塞了`DOM`的构建。

![](https://todever-images.oss-cn-beijing.aliyuncs.com/key_rendering_path-012.webp)

如果将这段JavaScript作为外部资源，就是一个比较典型的页面结构

```html
<html>
  <head>
    <meta name="viewport" content="width=device-width,initial-scale=1">
    <link href="style.css" rel="stylesheet">
    <title>Critical Path Render</title>
  </head>
  <body>
    <p>Hello <span>web performance</span></p>
    <script src="app.js"></script>
  </body>
</html>
```

![](https://todever-images.oss-cn-beijing.aliyuncs.com/key_rendering_path-013.webp)

JavaScript和CSS资源请求是并行的，但仍然需要等到CSSOM构建完成之后，JavaScript才可以执行，然后在进行后面的渲染工作。于是，当 `DOM`、`CSSOM` 和 `JavaScript` 执行之间有大量的依赖关系时，就很可能导致浏览器在处理及渲染网页时出现延迟。

## 优化策略

我们花了大量的篇幅来理解浏览器的渲染过程，理解DOM，CSSOM，渲染树，浏览器绘制，分析HTML，CSS和JS在渲染过程中的关系，我相信你已然受益匪浅，现在，我们来运用这些知识加速你的网站。

### 第一步，分析你的网站渲染状况

我们以Google为例，通过Chrome的`Performance`工具查看页面渲染情况，如下图，你应该可以清晰的看到图中有四条竖线，他们分别是什么含义呢？

![](https://todever-images.oss-cn-beijing.aliyuncs.com/key_rendering_path-014.webp)

- 绿色竖线，代表`First Paint`，即浏览器开始进行像素的绘制
- 黄色竖线，代表`First Meaningful Paint`（首次有效绘制）用户可以开始看到部分内容，但绘制仍在继续
- 蓝色竖线，代表大家比较熟悉的DOMContentLoaded
- 红色竖线，代表load，页面加载完成

优秀的网站都能够把“首次有效渲染”做到1秒之内完成，这样能够让用户更快的看到所请求的页面得到响应。如果你的网站“首次有效渲染”超过1秒，那么就非常有必要重新分析一下网站的关键渲染路径是否合理。

### 第二步，分析关键渲染路径

在关键渲染路径中，我们通常要关注三个点：

- 页面首次渲染需要的关键资源数量 
- 关键资源的大小 
- 关键渲染路径的往返次数（Roundtrip）

我们的策略也非常简单，就是减少关键资源数量，降低资源大小，减少关键路径的往返次数。

关键渲染的资源一般是阻止屏幕首次渲染HTML，CSS和JavaScript，所以最重要也是最难的部分的是你需要根据自己网站的实际情况分析，哪些是页面绘制的所必须的，哪些是无关的。

### 第三步，根据分析采取优化手段

#### 1、减少关键资源的大小

我们首先从最简单也是最直接的减少关键资源的大小开始：

对于所有的资源（HTML，JavaScript，CSS，Image等），你都应该用上三大绝招：Minify，Compression和Cache，这里不过多的赘述里面的细节。

这一点对于HTML来说，非常关键，HTML作为渲染的关键资源，消除或者延迟加载肯定不太可能(这里指的是非局部渲染的关键HTML)，能够做到是消除无用代码（比如：注释）和最小化代码（Minify）以及动态局部渲染等。

![](https://todever-images.oss-cn-beijing.aliyuncs.com/key_rendering_path-015.webp)

#### 2、延迟JavaScript非阻塞资源加载

JavaScript和CSS都是阻塞渲染的资源，对于已经鉴别出的对于首次渲染没有起到关键作用的代码，我们首先想到的是要延迟它的加载，让它脱离关键渲染路径。

首先，对于阻塞渲染的JavaScript，应该将它放置在页面body的底部，为什么呢？

JavaScript可以查询和操作DOM和CSSOM，正如前面介绍的，HTML解析过程中构建DOM，当遇到JavaScript就停止DOM构建执行JavaScript，如果被执行的JavaScript是放置在head附近，那么很可能要被操作或者查询的DOM还没有构建到DOM当中。

而对于，非阻塞渲染的JavaScript，我们应该采用异步的方式加载，如下：

```html
  <script src="script.js"></script>
  <script async src="script.js"></script>
  <script defer src="myscript.js"></script>
</body>
</html>
```

方式一：即阻塞的JavaScript，HTML解析过程中遇到script标签，发出网络请求获取`script.js`，在网络请求返回后，解析并执行`script.js`，然后浏览器继续HTML解析。

方式二：`async`，完全的异步操作，HTML解析遇到该标签后，发出网络请求，但不阻止HTML解析和其后面的渲染操作，当JavaScript请求返回后立刻执行，且不等待HTML解析或其他操作的完成。所以，如果脚本中有DOM操作，就并不适合。

方式三：`defer`，HTML的解析和对JavaScript资源的网络请求是并行的，但它会等待HTML解析完成之后，才执行脚本。

![](https://todever-images.oss-cn-beijing.aliyuncs.com/key_rendering_path-016.webp)

不过，`async`和`defer`，他们对浏览器的兼容性有一定的要求，但仍然应该使用它们，同时可以采用退而求其次的延迟代码执行的方法（比如：`on DOMContentLoad`后），特别是与首次渲染无关的计算逻辑和功能。

#### 3、尽早和按需的加载CSS

你可能在思考，有没有异步加载CSS的需求？我认为不应该有，页面应该只引用与该页面相关的样式文件。（只不过很多时候，我们将所有的CSS都打包在了一个压缩的CSS文件中了。）目前，已经有许多帮助你分析关键渲染路径上的所需要的CSS的工具：grunt-criticalcss，critical，criticalCSS，在线CRPCSS工具。

前面已经提到，CSS是阻塞渲染的资源，在CSSOM完全解析完成之前，浏览器不可能开始屏幕的绘画。

所以，我们应该尽早的开始对样式资源的请求，将它尽早、尽快地下载到客户端，这样解释了为什么我们看到样式资源的`link`标签一般都放在`head`表中：

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <title>Sample Site</title>
  <link href="style.css" rel="stylesheet">
</head>
```

CSSOM的运算是一个非常复杂和相对耗时的过程，但它也有一个特点，就是可能只有在特定的情况下才会起作用，比如：响应式设计的页面。

对于响应式页面，我们可以考虑将不同媒体上的样式分离，在`<link>`中使用媒体查询，浏览器仍然会下载对应的资源，但是可以避免不必要的CSSOM解析导致对渲染的阻塞。

```html
<link href="style.css" rel="stylesheet" media="all">
<link href="portrait.css" rel="stylesheet" media="orientation:portrait">
<link href="print.css" rel="stylesheet" media="print">
```

同时，我们还应该避免在首次渲染的CSS样式中使用`@import`指令，因为它只有在收到并解析完带有`@import`规则的CSS资源之后，才会发现导入的 CSS 资源，这个时候就会重新请求，从而增加了关键渲染路径的往返次数。

#### 4、内联CSS来提高渲染性能

到目前为止，我们已经做到了识别关键渲染资源，将非关键资源延迟加载或者不加载。那么，减少关键路径的往返次数是什么意思？其实就是减少关键渲染资源从服务器端到客户端的往返次数。比如，外链的JS和CSS文件以前CSS的`@import`，在页面渲染的过程中，都会重新去服务器端请求。这其实，和我们常说的减少http请求量（合并http请求）类似，但是我么从渲染路径的角度来理解这样一种性能的消耗。

根据这样的逻辑，我们很容易就想到可以将渲染必备CSS内联到HTML中，来减少渲染路径的往返次数。

实际上不少的优秀网站都采用了在`head`内联样式的做法：Google，百度，淘宝，京东。

关于内联样式还有更进一步的做法，在文章的一开始就提到，优化关键渲染路径就是要优先显示和用户先关内容。

所以，我们可以考虑仅仅将当前屏幕展示的内容（above-the-fold，一屏）所需的CSS内联到HTML的`head`中，然后采用异步的方式加载整个页面所需要的完整CSS，以便用户能够更快的看到首屏出现的内容。

#### 5、一个神奇的数字14kb

在最开始我们提到，要减小关键资源的大小，那么多小比较合适呢？（废话，当然是越小越好）。

其实，有一个神奇的数字14kb，它是怎么来？

HTTP的传输层协议是TCP，TCP协议有一个慢启动的过程，即它在第一次传递数据时，只能同时传递14kb的数据块，所以当数据超多14kb时，TCP协议传递数据实际是多次的往返（roundtrip）。如果能够将渲染所需要的资源控制在14kb之内，那么就能TCP协议启动时，一次完成数据的传递。

## 其他Web资源和关键渲染路径的关系

你一定会思考，除了HTML，JavaScript和CSS，Web页面还包含许多其他的资源，比如：图片，网络字体（Icon Font），他们和关键渲染路径的关系是什么？

大家对图片加载感受都应该大致一样，它会在页面加载过程中或完成后，逐步显示，也就是说它不是阻塞渲染的资源，它的痛点主要在于质量和资源大小的权衡，以及请求数量带来的性能消耗（雪碧图）。

网络字体，在网络加载比较慢的情况下，用户可能会感受到字体或者图形的变化（Icon Font）。其实，浏览器在渲染树构建完成之后，会指示需要哪些字体在网页上渲染指定文本，然后分派字体请求，浏览器执行布局并将内容绘制到屏幕上，如果字体尚不可用，浏览器可能不会渲染任何文本像素，待字体可用之后，再绘制文本像素，当然，不同浏览器之间实际行为有所差异，这里不在赘述
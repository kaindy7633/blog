> 研究web前端优化时最多的建议就是不要使用 css @import 因为用这种方式加载css相当于把css放在了html底部

网上很多文章提及到的`@import`，其关注的问题是：

不要使用 `css @import`, 因为用这种方式加载css相当于把css放在了html底部。

那为什么用`@import`就等于把css放在了页面底部呢？在google developers看一篇文章时，无意间找到了这个原因，原文如下：

```
Avoid CSS @import Overview

Using CSS @import in an external stylesheet can add additional delays during the loading of a web page. Details

CSS @importallows stylesheets to import other stylesheets. When CSS @import isused from an external stylesheet, the browser is unable to downloadthe stylesheets in parallel, which adds additional round-trip timesto the overall page load. For instance, iffirst.css contains the following content:

@import url("second.css")

The browser must download, parse, andexecute first.css before it is able to discover that itneeds to downloadsecond.css. Recommendations

Use the <link> tag instead of CSS @import Instead of @import, use a <link> tag for each stylesheet. This allows the browser to download stylesheets in parallel, which results in faster page load times:

<link rel="stylesheet" href="first.css"> <link rel="stylesheet" href="second.css">
```

我们确实要避免使用`css @import`， 但原因却不是什么相当于放在了页面底部，而是这样做会导致css无法并行下载，因为使用`@import`引用的文件只有在引用它的那个css文件被下载、解析之后，浏览器才会知道还有另外一个css需要下载，这时才去下载，然后下载后开始解析、构建render tree等一系列操作。

浏览器在页面所有css下载并解析完成后才会开始渲染页面（Before a browser can begin to render a web page, it mustdownload and parse any stylesheets that are required to lay out thepage. Even if a stylesheet is in an external file that is cached,rendering is blocked until the browser loads the stylesheet from disk.）

因此`css @import`引起的css解析延迟会加长页面留白期。 所以，要尽量避免使用`css @import`而尽量采用`link`标签的方式引入。

# PWA概述

## 什么是PWA

> PWA，即Progressive Web App, 是提升 Web App 的体验的一种新方法，能给用户原生应用的体验。

PWA不是某一项技术，或者某一个新的产物；而是一系列Web技术与标准的集合与应用。通过应用这些新的技术与标准，可以从安全、性能和体验三个方面，优化我们的Web App。所以，其实PWA本质上依然是一个Web App

## PWA中所涉及到的一些技术

PWA本身其实是一个概念集合，它不是指某一项技术，而是通过一系列的Web技术与Web标准来优化Web App的安全、性能和体验。其中涉及到的一些技术概念包括了：

- Web App Manifest
- Service Worker
- Cache API 缓存
- Push&Notification 推送与通知
- Background Sync 后台同步
- 响应式设计
……

## DEMO

我们将通过实践一个demo项目来学习PWA

# PWA中的Manifest

在chrome（等一些现代浏览器）中，你可以将访问的网站添加到桌面，这样就会在桌面生成一个类似“快捷方式”的图标，当你点击该图标时，便可以快速访问该网站（Web App）

然而，对于PWA来说，有一些重要的特性：

- Web App可以被添加到桌面并有它自己的应用图标；
- 同时，从桌面开启时，会和原生app一样有它自己的“开屏图”；
- 更进一步的，这个Web App在的样子几乎和原生应用一样——没有浏览器的地址栏、工具条，似乎和Native App一样运行在一个独立的容器中。

## Web App Manifest

Manifest是一个JSON格式的文件，你可以把它理解为一个指定了Web App桌面图标、名称、开屏图标、运行模式等一系列资源的一个清单。

> manifest 的目的是将Web应用程序安装到设备的主屏幕，为用户提供更快的访问和更丰富的体验。 —— MDN

下面来看下这个 `manifest.json`的内容：

```json
{
    "name": "图书搜索",
    "short_name": "书查",
    "start_url": "/",
    "display": "standalone",
    "background_color": "#333",
    "description": "一个搜索图书的小WebAPP（基于豆瓣开放接口）",
    "orientation": "portrait-primary",
    "theme_color": "#5eace0",
    "icons": [{
        "src": "img/icons/book-32.png",
        "sizes": "32x32",
        "type": "image/png"
    }, {
        "src": "img/icons/book-72.png",
        "sizes": "72x72",
        "type": "image/png"
    }, {
        "src": "img/icons/book-128.png",
        "sizes": "128x128",
        "type": "image/png"
    }, {
        "src": "img/icons/book-144.png",
        "sizes": "144x144",
        "type": "image/png"
    }, {
        "src": "img/icons/book-192.png",
        "sizes": "192x192",
        "type": "image/png"
    }, {
        "src": "img/icons/book-256.png",
        "sizes": "256x256",
        "type": "image/png"
    }, {
        "src": "img/icons/book-512.png",
        "sizes": "512x512",
        "type": "image/png"
    }]
}
```

### name, short_name

指定了Web App的名称。`short_name`其实是该应用的一个简称。一般来说，当没有足够空间展示应用的`name`时，系统就会使用`short_name`

### start_url

这个属性指定了用户打开该Web App时加载的URL。相对URL会相对于`manifest`。这里我们指定了`start_url`为`/`，访问根目录。

### display

`display`控制了应用的显示模式，它有四个值可以选择：`fullscreen`、`standalone`、`minimal-ui`和`browser`。

- `fullscreen`：全屏显示，会尽可能将所有的显示区域都占满；
- `standalone`：独立应用模式，这种模式下打开的应用有自己的启动图标，并且不会有浏览器的地址栏。因此看起来更像一个Native App；
- `minimal-ui`：与standalone相比，该模式会多出地址栏；
- `browser`：一般来说，会和正常使用浏览器打开样式一致。

### orientation

控制Web App的方向。设置某些值会具有类似锁屏的效果（禁止旋转），例如例子中的`portrait-primary`。具体的值包括：`any`, `natural`, `landscape`, `landscape-primary`, `landscape-secondary`, `portrait`, `portrait-primary`, `portrait-secondary`。

### icons， background_color

`icons`用来指定应用的桌面图标。`icons`本身是一个数组，每个元素包含三个属性：

- `sizes`：图标的大小。通过指定大小，系统会选取最合适的图标展示在相应位置上。
- `src`：图标的文件路径。注意相对路径是相对于`manifest`。
- `type`：图标的图片类型。

`background_color`是在应用的样式资源为加载完毕前的默认背景，因此会展示在开屏界面。`background_color`加上我们刚才定义的`icons`就组成了Web App打开时的“开屏图”

### theme_color

定义应用程序的默认主题颜色。 这有时会影响操作系统显示应用程序的方式（例如，在Android的任务切换器上，主题颜色包围应用程序）。此外，还可以在`meta`标签中设置`theme_color`：`<meta name="theme-color" content="#5eace0"/>`

### description

这个字段的含义非常简单，就是一段对该应用的描述。

## 使用Manifest

创建好`manifest`文件后，下一步就是需要知道如何能让我们的Web App使用它——非常简单，只需要在`head`中添加一个`link`标签：

```html
<!-- 在index.html中添加以下meta标签 -->
<link rel="manifest" href="/manifest.json">
```

## iOS（safari）中的处理方式

一切看上去很美好，但到了IOS或windows，就不是那么回事了。

safari虽然不支持Web App `Manifest`，但是它有自己的一些`head`标签来定义相应的资源与展示形式：

- `apple-touch-icon`：桌面图标，通过在`head中`添加

```html
<link rel="apple-touch-icon" href="your_icon.png">
```

其中还可以添加`sizes`属性，来指示系统使用在各类平台（iphone、ipad…）中使用最合适的图标

- `apple-mobile-web-app-title`：应用的标题。注意，这里需要使用`meta`标签

```html
<meta name="apple-mobile-web-app-title" content="AppTitle">
```

- `apple-mobile-web-app-capable`：类似于`manifest`中的`display`的功能，通过设置为`yes`可以进入`standalone`模式，同样也是`meta`标签

```html
<meta name="apple-mobile-web-app-capable" content="yes">
```

- `apple-mobile-web-app-status-bar-style`：这会改变iOS移动设备的状态栏的样式，并且只有在`standalone`模式中才会有效果。

```html
<meta name="apple-mobile-web-app-status-bar-style" content="black">
```

不过在iPhoneX上black会导致状态栏不显示任何东西。

清单设置如下：

```html
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="default">
<meta name="apple-mobile-web-app-title" content="图书搜索">
<link rel="apple-touch-icon" href="img/icons/book-256.png">
```

## IE中的处理方式

与Safari类似，IE中也有自己的`meta`标签来指示相应的资源。其中比较重要的有：

- `application-name`：指明了`app`的名称
- `msapplication-TileColor`：指明了“tile”的背景颜色
- `msapplication-xxxlogo`：不同大小的“tile”所使用的图标，包括这几种：`msapplication-square70x70logo`, `msapplication-square150x150logo`, `msapplication-wide310x150logo`, `msapplication-square310x310logo`

设置如下：

```html
<meta name="application-name" content="图书搜索" />
<meta name="msapplication-TileColor" content="#222">
<meta name="msapplication-square70x70logo" content="img/icons/book-72.png" />
<meta name="msapplication-square150x150logo" content="img/icons/book-144.png" />
<meta name="msapplication-square310x310logo" content="img/icons/book-256.png" />
```



# 离线可用的WebApp

# TroubleShooting

# Web Push功能

# 在Chrome中调试PWA

# 使用Notification API进行提醒

# Service Worker

# PWA实践中的问题与解决方案

# Resource Hint

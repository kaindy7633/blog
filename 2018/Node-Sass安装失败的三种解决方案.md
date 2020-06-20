<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [node-sass 安装失败的原因](#node-sass-%E5%AE%89%E8%A3%85%E5%A4%B1%E8%B4%A5%E7%9A%84%E5%8E%9F%E5%9B%A0)
- [解决方法一：使用淘宝镜像源（推荐）](#%E8%A7%A3%E5%86%B3%E6%96%B9%E6%B3%95%E4%B8%80%E4%BD%BF%E7%94%A8%E6%B7%98%E5%AE%9D%E9%95%9C%E5%83%8F%E6%BA%90%E6%8E%A8%E8%8D%90)
- [解决方法二：使用 cnpm](#%E8%A7%A3%E5%86%B3%E6%96%B9%E6%B3%95%E4%BA%8C%E4%BD%BF%E7%94%A8-cnpm)
- [解决方法三：创建.npmrc文件](#%E8%A7%A3%E5%86%B3%E6%96%B9%E6%B3%95%E4%B8%89%E5%88%9B%E5%BB%BAnpmrc%E6%96%87%E4%BB%B6)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## node-sass 安装失败的原因

`npm` 安装 `node-sass` 依赖时，会从 `github.com` 上下载 `.node` 文件。由于国内网络环境的问题，这个下载时间可能会很长，甚至导致超时失败。

这是使用 `sass` 的同学可能都会遇到的郁闷的问题。

解决方案就是使用其他源，或者使用工具下载，然后将安装源指定到本地。

## 解决方法一：使用淘宝镜像源（推荐）

设置变量 `sass_binary_site`，指向淘宝镜像地址。示例：

```bash
npm i node-sass --sass_binary_site=https://npm.taobao.org/mirrors/node-sass/

// 也可以设置系统环境变量的方式。示例
// linux、mac 下
SASS_BINARY_SITE=https://npm.taobao.org/mirrors/node-sass/ npm install node-sass

// window 下
set SASS_BINARY_SITE=https://npm.taobao.org/mirrors/node-sass/ && npm install node-sass
```

或者设置全局镜像源：

```bash
npm config set sass_binary_site https://npm.taobao.org/mirrors/node-sass/
```

之后再涉及到 `node-sass` 的安装时就会从淘宝镜像下载。

## 解决方法二：使用 cnpm

使用 `cnpm` 安装 `node-sass` 会默认从淘宝镜像源下载，也是一个办法：

```bash
cnpm install node-sass
```

## 解决方法三：创建.npmrc文件

在项目根目录创建`.npmrc`文件，复制下面代码到该文件。

```bash
phantomjs_cdnurl=http://cnpmjs.org/downloads
sass_binary_site=https://npm.taobao.org/mirrors/node-sass/
registry=https://registry.npm.taobao.org
```

保存后 删除之前安装失败的包(第一次安装请跳过此步)

```bash
npm uninstall node-sass
```

重新安装

```bash
npm install node-sass
```
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
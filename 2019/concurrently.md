<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [concurrently](#concurrently)
  - [安装](#%E5%AE%89%E8%A3%85)
  - [使用](#%E4%BD%BF%E7%94%A8)
  - [更多参考](#%E6%9B%B4%E5%A4%9A%E5%8F%82%E8%80%83)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## concurrently

> 在前端工程中，`concurrently`方便我们同时启动多个应用，比如这样的场景：我们需要在某个工程下对配置文件进行读写，但直接使用JavaScript不太方便，所以我们需要启动一个Server并提供服务，该服务会根据参数对相应的文件进行读写操作，以完成配置的可视化操作

`concurrently` 就是用来启动前端工程和其他`Server`进程的。

文档地址： <a href="https://www.npmjs.com/package/concurrently">https://www.npmjs.com/package/concurrently</a>

github地址: <a href="https://github.com/kimmobrunfeldt/concurrently">https://github.com/kimmobrunfeldt/concurrently</a>

### 安装

```bash
yarn add concurrently -D
```

或者:

```bash
npm install concurrently -D
```

### 使用

```bash
"start": "concurrently \"command1 arg\" \"command2 arg\""
```

比如在我们的前端工程里，我们需要启动前端的DevServer，还需要启动一个`Express`服务，用于对本地文件进行读写

```bash
"start:mock": "concurrently \"cross-env REACT_APP_ENV=dev UMI_UI=none umi dev\" \"node ./server/index.js\" ",
```

### 更多参考

[前端工程化并行解决方案-concurrently](https://zhuanlan.zhihu.com/p/65564606)
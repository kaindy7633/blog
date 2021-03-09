<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [使用Github](#%E4%BD%BF%E7%94%A8github)
- [自定义Git](#%E8%87%AA%E5%AE%9A%E4%B9%89git)
- [忽略特殊文件](#%E5%BF%BD%E7%95%A5%E7%89%B9%E6%AE%8A%E6%96%87%E4%BB%B6)
- [配置别名](#%E9%85%8D%E7%BD%AE%E5%88%AB%E5%90%8D)
- [配置文件](#%E9%85%8D%E7%BD%AE%E6%96%87%E4%BB%B6)
- [搭建Git服务器](#%E6%90%AD%E5%BB%BAgit%E6%9C%8D%E5%8A%A1%E5%99%A8)
  - [第一步： 安装git](#%E7%AC%AC%E4%B8%80%E6%AD%A5-%E5%AE%89%E8%A3%85git)
  - [第二步： 创建一个git用户，用来运行git服务](#%E7%AC%AC%E4%BA%8C%E6%AD%A5-%E5%88%9B%E5%BB%BA%E4%B8%80%E4%B8%AAgit%E7%94%A8%E6%88%B7%E7%94%A8%E6%9D%A5%E8%BF%90%E8%A1%8Cgit%E6%9C%8D%E5%8A%A1)
  - [第三步： 创建证书登录](#%E7%AC%AC%E4%B8%89%E6%AD%A5-%E5%88%9B%E5%BB%BA%E8%AF%81%E4%B9%A6%E7%99%BB%E5%BD%95)
  - [第四步： 初始化Git仓库](#%E7%AC%AC%E5%9B%9B%E6%AD%A5-%E5%88%9D%E5%A7%8B%E5%8C%96git%E4%BB%93%E5%BA%93)
  - [第五步： 禁用shell登录](#%E7%AC%AC%E4%BA%94%E6%AD%A5-%E7%A6%81%E7%94%A8shell%E7%99%BB%E5%BD%95)
  - [第六步： 克隆远程仓库](#%E7%AC%AC%E5%85%AD%E6%AD%A5-%E5%85%8B%E9%9A%86%E8%BF%9C%E7%A8%8B%E4%BB%93%E5%BA%93)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

> 使用github、自定义git、自己搭建git服务器

## 使用Github

在Github上面，所有的项目都是开源的，我们可以参与别人的开源项目，别人也可以参与自己的项目。

那么，我们怎么去参与别人的项目呢？比如我们想参与某个项目，并修复它的一个bug

我们先 `Fork` 一下这个项目，意思就是将当前的项目克隆一份到自己的Github账号上，然后从自己的远程仓库里 `clone` 一份到本地进行修改，修改完成后就可以`push`到远程自己的仓库里。

完成之后，就可以在Github上发起一个 `pull request` (简称PR)，这样就把你的修改提交到了项目的发起人那里，当然，我们的修复是否被项目拥有人接受就不一定了。

## 自定义Git

我们在进行Git配置时，配置了`user.name`和`user.email`属性，除此之外，我们还可以为Git配置颜色

```bash
git config --global color.ui true
```

## 忽略特殊文件

有时候，我们需要让Git忽略一些文件，这些文件不需要被跟踪，Git为我们提供了方法

在Git工作区的根目录下创建一个 `.gitignore` 文件，然后把需要忽略的文件名写进去，Git就会自动忽略这些文件

最后把这个`.gitignore`文件提交到Git就完成了。

有时候我们需要强制提交一些被忽略的文件，那么我们可以使用`-f`参数

```bash
$ git add -f xxx.class
```

另外我们还可以使用`git check-ignore`命令来查看哪些规则写错了

```bash
$ git check-ignore -v xxx.class
```

## 配置别名

有时候我们会觉得有些命令太长，不太好记，OK，Git为我们提供了设置别名的功能

比如，我们可以将命令`git status`设置成`git st`

```bash
$ git config --global alias.st status
```

除此之外，我们还可以设置更多的别名，比如用`co`表示`checkout`,`ci`表示`commit`,`br`表示`branch`

```bash
$ git config --global alias.co checkout
$ git config --global alias.ci commit
$ git config --global alias.br branch
```

以后如果我们需要提交修改，就可以使用下面的简写代码：

```bash
$ git ci -m "bala bala bala..."
```

## 配置文件

我们在配置Git的时候，加上`--global`参数，表示对当前用户起作用，如果不加，只对当前仓库起作用

Git的配置文件都放在`.git/config`里

```bash
cat .git/config
[core]
	repositoryformatversion = 0
	filemode = true
	bare = false
	logallrefupdates = true
	ignorecase = true
	precomposeunicode = true
[remote "origin"]
	url = git@github.com:kaindy7633/gitTest.git
	fetch = +refs/heads/*:refs/remotes/origin/*
[branch "master"]
	remote = origin
	merge = refs/heads/master
[branch "dev"]
	remote = origin
	merge = refs/heads/dev
```

而当前用户的Git配置文件放在用户主目录下的隐藏文件`.gitconfig`中

```bash
cat ~/.gitconfig
[user]
	name = kaindy7633
	email = kaindy7633@gmail.com
[alias]
	co = checkout
	br = branch
	st = status
	ci = commit
[color]
	ui = true
```

## 搭建Git服务器

搭建一台Git服务器需要运行Linux，如Ubuntu或Debian。

### 第一步： 安装git

```bash
$ sudo apt-get install git
```

### 第二步： 创建一个git用户，用来运行git服务

```bash
$ sudo adduser git
```

### 第三步： 创建证书登录

将所有需要登录的用户的公钥（id_rsa.pub）文件导入到`/home/git/.ssh/authorized.keys`文件里，一行一个。

### 第四步： 初始化Git仓库

我们需要先选定一个目录为Git仓库，如：`/srv/sample.git`，在`/srv`目录下输入命令：

```bash
$ sudo git init --bare sample.git
```

这样Git就会创建一个裸仓库，它并没有工作区，因为服务器上的Git仓库是为了共享，所以不允许用户直接登录到服务器上去修改工作区，服务器上的Git仓库通常以.git结尾，然后把owner改为git

```bash
$ sudo chown -R git:git sample.git
```

### 第五步： 禁用shell登录

为安全考虑，我们可以通过修改`/etc/passwd`文件来禁止用户登录`shell`

找到下面这行：

```bash
git:x:1001:1001:,,,:/home/git:/bin/bash
```

改为：

```bash
git:x:1001:1001:,,,:/home/git:/usr/bin/git-shell
```

### 第六步： 克隆远程仓库

现在我们就可以使用`git clone`命令来克隆远程仓库了。

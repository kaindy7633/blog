<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

**Table of Contents** _generated with [DocToc](https://github.com/thlorenz/doctoc)_

- [GIT （分布式版本控制系统）](#git-%E5%88%86%E5%B8%83%E5%BC%8F%E7%89%88%E6%9C%AC%E6%8E%A7%E5%88%B6%E7%B3%BB%E7%BB%9F)
  - [Git 的自动完成](#git%E7%9A%84%E8%87%AA%E5%8A%A8%E5%AE%8C%E6%88%90)
  - [Git 的基本配置](#git%E7%9A%84%E5%9F%BA%E6%9C%AC%E9%85%8D%E7%BD%AE)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## GIT （分布式版本控制系统）

Git 是一款免费、开源的分布式版本控制系统，用于敏捷高效地处理任何或小或大的项目。

Git 是一个开源的分布式版本控制系统，用以有效、高速的处理从很小到非常大的项目版本管理。 Git 是 Linus Torvalds 为了帮助管理 Linux 内核开发而开发的一个开放源码的版本控制软件。

Torvalds 开始着手开发 Git 是为了作为一种过渡方案来替代 BitKeeper，后者之前一直是 Linux 内核开发人员在全球使用的主要源代码工具。开放源码社区中的有些人觉得 BitKeeper 的许可证并不适合开放源码社区的工作，因此 Torvalds 决定着手研究许可证更为灵活的版本控制系统。尽管最初 Git 的开发是为了辅助 Linux 内核开发的过程，但是我们已经发现在很多其他自由软件项目中也使用了 Git。例如 最近就迁移到 Git 上来了，很多 Freedesktop 的项目也迁移到了 Git 上。

（以上内容摘自百度百科，有兴趣的朋友可以移步到百度进行搜索）

Git 是什么？

Git 是目前世界上最先进的分布式版本控制系统（没有之一）。

Git 有什么特点？简单来说就是：高端大气上档次！

那什么是版本控制系统？

如果你用 Microsoft Word 写过长篇大论，那你一定有这样的经历：

想删除一个段落，又怕将来想恢复找不回来怎么办？有办法，先把当前文件“另存为……”一个新的 Word 文件，再接着改，改到一定程度，再“另存为……”一个新文件，这样一直改下去，最后你的 Word 文档变成了这样：

![](http://static.oschina.net/uploads/img/201603/14235500_0Ha1.jpg)

过了一周，你想找回被删除的文字，但是已经记不清删除前保存在哪个文件里了，只好一个一个文件去找，真麻烦。

看着一堆乱七八糟的文件，想保留最新的一个，然后把其他的删掉，又怕哪天会用上，还不敢删，真郁闷。

更要命的是，有些部分需要你的财务同事帮助填写，于是你把文件 Copy 到 U 盘里给她（也可能通过 Email 发送一份给她），然后，你继续修改 Word 文件。一天后，同事再把 Word 文件传给你，此时，你必须想想，发给她之后到你收到她的文件期间，你作了哪些改动，得把你的改动和她的部分合并，真困难。

于是你想，如果有一个软件，不但能自动帮我记录每次文件的改动，还可以让同事协作编辑，这样就不用自己管理一堆类似的文件了，也不需要把文件传来传去。如果想查看某次改动，只需要在软件里瞄一眼就可以，岂不是很方便？

这个软件用起来就应该像这个样子，能记录每次文件的改动：

| 版本 | 用户 | 说明                    | 日期        |
| ---- | ---- | ----------------------- | ----------- |
| 1    | 张三 | 删除了软件服务条款      | 57/12 10:38 |
| 2    | 张三 | 增加了 License 人数限制 | 7/12 18:09  |
| 3    | 李四 | 财务部门调整了合同金额  | 7/13 9:51   |
| 4    | 张三 | 延长了免费升级周期      | 7/14 15:17  |

这样，你就结束了手动管理多个“版本”的史前时代，进入到版本控制的 20 世纪。

（以上内容摘自廖雪峰的博客网站，地址是：http://www.liaoxuefeng.com/，有兴趣的朋友可以去查看他的git教程）

OK，我以自己的 MAC 为准，来记录我的学习过程。

首先，MAC 自带了 `git`，我们在命令行下输入`git`，会跳出一大堆帮助命令，再次输入 `git --version`，就会显示当前`git`版本。

接着我们从 git 的官方网站（git-scm.com）下载最新的`git`版本，官网会自动提示您下载当前您的系统适应版本，下载完成后直接安装，这里就不再赘述。

我们在命令行窗口输入命令来查看当前系统安装的`git`

```bash
localhost:~ liuzhen$ which -a git
/usr/local/git/bin/git
/usr/local/bin/git
/usr/bin/git
localhost:~ liuzhen$
```

我们看到有 3 个版本的`git`，那么我们如何来使用这些版本的`git`呢？在命令行窗口使用`vim`打开并编辑`.bash_profile`文件

并输入以下命令：

```bash
export PATH=/usr/local/git/bin:$PATH
```

保存、退出，并输入命令连接：

```bash
source .bash_profile
```

再次输入`git --version`命令来查看当前使用的`git`版本

```bash
localhost:~ liuzhen$ git --version
git version 2.6.4
```

### Git 的自动完成

`git`有自动完成功能，当我们记不住完整的命令时，可以使用`tab`键来完成输入，如果是在`windows`下，这个功能是集成的。但在 Mac 下需要进行配置

从 github.com/git/git 这个地址里下载 git 源码，解压缩后，进入`contrib/completion`目录，找到`git-completion.bash`和`git-prompt.sh`文件，将他们拷贝到根目录下即可，最后`source`一下

### Git 的基本配置

git 的基本配置很简单，需要配置用户名和 Email，命令如下：

```bash
git config --global user.name kaindy1976
git config --global user.email kaindy7633@gmail.com
```

这两个配置用来说明提交代码的人是谁，用来识别作者。

`git`配置的三个级别分别是`git config --system`、`git config --global`、 `git config --local`，从优先级来说，`local`级别最高，其次是`global`，最低是`system`

`git`文档的查看，`git`的命令很多，我们也不可能每个都记得，最好的方式就是学会查看`git`的文档，查看`git`文档有三种方式：

```bash
git config --help
git help config
man git-config
```

`git`添加，比如我们想给`git`添加一个`user`，那么我们可以像这样做

```bash
git config --global --add user.name lz
```

接下来我们可以使用下面的命令来获取

```bash
git config user.name
```

也可以这样获取

```bash
git config --get user.name
```

OK,如果我们需要获取所有的键值对信息呢？可以这样

```bash
git config --list --global
```

在`git`中，同一个键可以对应多个值，比如，我们可以再次指定一个`user.name`的值

```bash
git config --global --add user.name liuzhen
```

这时当我们需要删除时可以键入下面的命令

```bash
git config --global --unset user.name
```

但如果有多个值时，系统会提示`user.name`这个键有多个值，需要单独指定，这时，我们就可以指定要删除的值

```bash
git config --global --unset user.name liuzhen
```

那么我们如何来修改这些键值对呢？

```bash
git config --global user.name liuzhen
```

我们只需要像上面一样，重新指定键的值即可

下面我们来看看给 git 命令起别名

```bash
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.st status
git config --global alias.ci commit
```

以后我们就可以使用这些别名来启动 git 的命令了

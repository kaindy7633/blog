> 通常我们在软件开发使用的版本控制系统有两种，一种是集中式版本控制，如SVN，另一种就是分布式版本控制系统，如GIT。Git的特点就是分布式，不但可以在本地机器上做版本仓库，还可以将代码上传至远程Git服务器，方便团队协作，也实现了另外一个远程代码备份。

## 在github上创建自己的远程仓库

git服务器我们可以自己搭建，但那是没有必要的，因为有github这样的网站为我们提供了，而且只要不是必须的，你不需要去付费使用。

首先我们需要在github上去注册一个自己的账号，因为本地git仓库与github仓库之间的数据传输是加密的，所以我们需要先创建 `SSH KEY`.

在用户主目录下，看看有没有`.ssh`目录，如果有，再看看这个目录下有没有 `id_rsa` 和 `id_rsa.pub` 这两个文件，如果没有，打开终端，创建`SSH Key`。

在终端使用命令创建这个KEY： 

```bash
ssh-keygen -t rsa -C "youremail@example.com"
```

后面引号里的Email地址填写自己的，应该为在github上注册Email地址。一路回车之后，就创建成功了。

![](http://static.oschina.net/uploads/space/2016/0317/105415_yuVE_2399867.png)

其中`id_rsa`为私钥，这个不能泄露出去，而`id_rsa.pub`为公钥，可以放心的告诉别人。

接下来，我们登录github.com，在账号设置中，点击左边菜单栏中的`SSH keys`。

![](http://static.oschina.net/uploads/space/2016/0317/105911_fXJX_2399867.png)

点击右上角的 “New SSH key”

![](http://static.oschina.net/uploads/space/2016/0317/110022_62Mp_2399867.png)

在Title中填写标题，可随意填写，建议使用有意义的名称，比如这个项目的简称，然后将`id_rsa.pub`的内容粘贴到下面的key里，成功后显示如下：

![](http://static.oschina.net/uploads/space/2016/0317/110457_fGso_2399867.png)

OK，到现在，我们就可以正常使用github了。我们有了本地仓库，也有了github这样的远程仓库，就可以同步了，这样既可以有一个远程的代码备份，也方便团队进行协作开发。

现在我们需要在github上创建一个仓库，首先登陆github，在右上角点击 “+” 号，在弹出的菜单中选择 “New repository”。

![](http://static.oschina.net/uploads/space/2016/0317/112024_npKn_2399867.png)

在"Repository name" 中填写仓库名称，这里我填了gitTest，其他默认，然后点击下方的Create repository。

![](http://static.oschina.net/uploads/space/2016/0317/112940_b9VA_2399867.png)

现在这个gitTest仓库是空的，我们可以将已有的本地仓库与之关联，然后将本地仓库推送到远程仓库，也可以从远程仓库克隆项目到本地仓库。

我们现在将上一节的gitTest项目推送到这个远程仓库，首先使用下面的命令让本地git与远程github进行关联

```bash
$ git remote add origin git@github.com:kaindy733/gitTest.git
```

完成后没有提示错误，下一步我们使用下面的命令，将本地项目推送上去

```bash
$ git push -u origin master
```

中间会有提示是否继续，输入yes即可。

![](http://static.oschina.net/uploads/space/2016/0317/115603_RMNO_2399867.png)

下面我们来看下github上的项目情况

![](http://static.oschina.net/uploads/space/2016/0317/115720_fLGa_2399867.png)

可以看到，我们的项目已经推送到了github上，把本地仓库的内容推送到远程，我们使用  `git push`命令，也就是把当前分支 `master` 推送到远程。由于远程仓库是空的，我们第一次推送 `master` 分支时加上了 `-u` 参数，`git`不但把本地的`master`分支内容推送到远程新的`master`分支，还会把两者关联，在以后的推送或拉取时就可以简化命令。

好了，从现在起，如果本地做了代码修改，就可以直接使用下面的命令将项目推送到github上。

```bash
$ git push origin master
```

分布式版本系统的最大好处之一是在本地工作完全不需要考虑远程库的存在，也就是有没有联网都可以正常工作，而SVN在没有联网的时候是拒绝干活的！当有网络的时候，再把本地提交推送一下就完成了同步

## 从远程仓库克隆项目

上面介绍的是从本地仓库推送项目到远程仓库，我们还可以从远程仓库克隆项目到本地，以方便团队开发。首先，我们在github上创建项目仓库

![](http://static.oschina.net/uploads/space/2016/0317/151226_kD62_2399867.png)

填写仓库名称，勾选下面的Initialize this repository with a README，这个操作会为我们的项目自动创建一个README文件，然后点击下面的创建按钮。

![](http://static.oschina.net/uploads/space/2016/0317/151709_thrb_2399867.png)

我们可以编辑README.md文件，为项目添加说明

![](http://static.oschina.net/uploads/space/2016/0317/152043_hpYO_2399867.png)

好了，现在远程库已准备好，我们可以使用 `git clone` 从远程库克隆项目到本地

```bash
$ git clone git@github.com:kaindy7633/myProjectTest.git
```

![](http://static.oschina.net/uploads/space/2016/0317/152648_5zVD_2399867.png)

克隆成功，我们打开这个项目目录看下

![](http://static.oschina.net/uploads/space/2016/0317/152801_Y80n_2399867.png)
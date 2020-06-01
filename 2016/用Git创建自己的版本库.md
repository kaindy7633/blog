> 我们在上一节介绍了`git`及一些简单的配置，具体在各个平台上（如Linux、windows）的安装，可以参考廖雪峰老师的博客上的文章

## 一、创建自己的版本库

版本库，又名仓库，英文名：repository，我们可以把它当做是一个目录，`git`能管理这个目录里的所有文件，包括对这些文件的修改、删除的跟踪。

创建版本库很简单，假设我们需要新开发一个项目，那么我们首先创建一个新的目录，作为这个项目的工作区

![](http://static.oschina.net/uploads/space/2016/0316/115331_4oRX_2399867.png)

上面我们创建项目目录gitTest并进入这个目录。

![](http://static.oschina.net/uploads/space/2016/0316/115509_Tm38_2399867.png)

执行 `git init` 命令，在当前工作目录创建`git`，那么在当前目录下就会有一个隐藏的`.git`目录，所有的记录都会在这个目录中。

![](http://static.oschina.net/uploads/space/2016/0316/120033_dgdj_2399867.png)

接下来我们直接创建一个测试的html文件，并用vim进行编辑，写入html基本结构，保存后退出，现在这个`index.html`是没有被跟踪的

![](http://static.oschina.net/uploads/space/2016/0316/120243_gEFb_2399867.png)

我们使用 `git add index.html` 命令来讲刚创建的`index.html`文件添加到暂存区，这时我们还没有将新建的文件提交到仓库，只是放在了暂存区

![](http://static.oschina.net/uploads/space/2016/0316/120413_qL1R_2399867.png)

OK，接下来我们把这个新的文件提交到仓库

![](http://static.oschina.net/uploads/space/2016/0316/120629_pduw_2399867.png)

我们可以看到，`index.html`已成功提交到了仓库，在 `git commit` 后面加上了`-m`参数，后面写上此次提交的说明，这是非常有必要的。

好了，接下来我们对`index.html`做出修改，向HTML文件里添加一个p标签，并写入一些信息，然后我们使用 `git status` 来查看下当前文件状态，结果如下：

![](http://static.oschina.net/uploads/space/2016/0316/151640_NZG6_2399867.png)

上面第一排的`On branch master`表示我们正在`master`分支上，下面的红色部分说明`index.html`已被修改

现在我们把修改添加到暂存区，之后再次查看下当前状态

![](http://static.oschina.net/uploads/space/2016/0316/151921_jgEC_2399867.png)

红色部分没有了，这表示修改已提交到了暂存区，接着我们把它提交到仓库并附上说明

![](http://static.oschina.net/uploads/space/2016/0316/152153_7dzZ_2399867.png)

现在有个问题，如果我们对文件做了更改，但没有提交，而我们又想知道文件到底做了哪些更改呢？我们再次为`index.html`添加第二个p标签，并写入一些内容

当我们对`index.html`再次做出更改后，我们用 `git diff` 命令来查看最近有些更改

![](http://static.oschina.net/uploads/space/2016/0316/152659_0q9L_2399867.png)

从上图可以看出，第二个p标签前面有个+号，表示这段代码是我们后面加入的，但并没有提交，好了我们知道了上次对文件做了哪些更改，就可以对更改后的文件做提交了

## 二、版本回退

我们来试想下，上面显示了一个创建和两次对文件内容的更改（添加），而且内容都很少，如果我们在几个月内对一个或多个文件做了成百上千此更改呢？有谁会记得这些，好了，我们可以使用 `git log` 来查看历史修改记录

![](http://static.oschina.net/uploads/space/2016/0316/153345_BVEb_2399867.png)

可以看到我们每次在修改之后提交到仓库的动作，都记录在这里，不过好像有点不太清楚，OK，我们在命令后面加上参数 `--pretty=oneline`

![](http://static.oschina.net/uploads/space/2016/0316/153648_Mxxi_2399867.png)

这样就舒服多了，现在我们来做回退的工作，如果最近一次的修改你并不满意，但修改量很大，而且也记不清是哪些地方做了修改，我们就使用 `git reset`  来回退到上一个版本，那么要回退，必须要让`git`知道我们需要回退到那个版本，在`git`中，`HEAD` 用来表示当前版本，上一个版本使用 `HEAD^` 表示，上上一个版本使用`HEAD^^`表示，那100个呢？不是要写100个^?呵呵，像这样的情况我们使用 `HEAD~100` 来表示。好，我们现在来把index.html的内容回退到上一个版本，在做这个操作之前，我们先使用 `cat index.html` 来查看下当前index.html的内容是怎样的。

![](http://static.oschina.net/uploads/space/2016/0316/154446_yZZD_2399867.png)

接着我们使用 `git reset --hard HEAD^` 来回退到上一个版本

![](http://static.oschina.net/uploads/space/2016/0316/154621_LukV_2399867.png)

好了，没有错误提示，我们再次查看下index.html的内容，发现文件内容已回退到了上一个版本，也就是没有第二个P标签的时候

![](http://static.oschina.net/uploads/space/2016/0316/154813_W98m_2399867.png)

完成上面的操作后，我们回到了我们希望的版本，第二天一睡醒，完了，后悔了，这么办？这个好办，我们使用命令 `git reflog` 来查看我们的每次操作

![](http://static.oschina.net/uploads/space/2016/0316/162124_gJnW_2399867.png)

可以看到，我们做的第三次操作的commitid是：469e0de，好了，有这个就好办了，我们再次执行 `git reset --hard 469e0de`

![](http://static.oschina.net/uploads/space/2016/0316/162933_lU93_2399867.png)

再次cat一下index.html的内容

![](http://static.oschina.net/uploads/space/2016/0316/163018_m8Hr_2399867.png)

看到了吗？刚刚的第二个p标签又回来啦！

## 三、工作区和暂存区

### 工作区（Working Directory）

就是你在电脑里能看到的目录，比如我的gitTest文件夹就是一个工作区

### 版本库（Repository）

工作区有一个隐藏目录 `.git`，这个不算工作区，而是Git的版本库。

Git的版本库里存了很多东西，其中最重要的就是称为stage（或者叫index）的暂存区，还有Git为我们自动创建的第一个分支 `master`，以及指向 `master` 的一个指针叫HEAD

我们把文件往Git版本库里添加的时候，是分两步执行的：

第一步是用 `git add` 把文件添加进去，实际上就是把文件修改添加到暂存区；

第二步是用 `git commit` 提交更改，实际上就是把暂存区的所有内容提交到当前分支。

因为我们创建Git版本库时，Git自动为我们创建了唯一一支 `master` 分支，所以，现在，`git commit` 就是往 `master` 分支上提交更改。

你可以简单理解为，需要提交的文件修改通通放到暂存区，然后，一次性提交暂存区的所有修改。

## 四、管理修改

Git管理的是修改，而非文件，比如新增是一个修改，删除也是一个修改，更改了某些字符也是一个修改，删了一些又加了一些也是一个修改，甚至创建一个新文件也算一个修改。

比如有一个文件，我们第一次做了修改，然后 `git add` 了，这时我们再次做了一次修改，并没有`add`，而是直接 `git commit` 了，`git diff` 下就可以看到，`git commit` 是将暂存区的修改提交到了仓库，而第二次的修改并没有 `add` 到暂存区，所以看到的只是第一次修改的结果。

我们也可以使用 `git diff -- index.html` 这样的命令来查看工作区与仓库之间的文件差异，如果没有返回结果，那么这两处的结果是一样的。

## 五、撤销修改
当我们的工作量很大时，必须会在编写代码时出错，这时，我们来分析下下面的几种情况：

1. 我们写错了代码，并没有提交到暂存区，也就是没有执行 `git add` 操作，这时你发现了错误，OK，我们执行 `git checkout -- file` 命令，撤销工作区的修改，返回到跟暂存区版本一致。

2. 我们写错了代码，而且已经提交修改到了暂存区，但没有`commit`，这时，我们执行 `git reset HEAD file` ，丢弃暂存区的修改，这样就返回到了上面的阶段，然后再次执行上面的 `git checkout -- file` 就可以了。

3. 我们写错了代码，不但提交到了暂存区，而且已经`commit`了，这时，可以参看上面的版本回退部分，不过前提是没有提交到远程仓库。

## 六、删除文件

在Git中，删除也是一种修改操作，下面我们用一个实例来讨论下。首先我们创建一个test.txt文件，并把它提交到仓库

![](http://static.oschina.net/uploads/space/2016/0316/174300_rR1H_2399867.png)

这时，我们直接在工作区将这个文件删除

![](http://static.oschina.net/uploads/space/2016/0316/175026_FP2r_2399867.png)

我们使用 git status 来查看下

![](http://static.oschina.net/uploads/space/2016/0316/175845_qA4e_2399867.png)

`git` 告诉我们，test.txt已被删除了，因为它发现了工作区和版本库的不一致了，这时，我们有两个选择，一是直接删除版本库里的test.txt ，另外一种就是删错了，要从版本库里恢复

下面，我们首先来恢复被误删的test.txt，使用 `git checkout -- test.txt` 命令

![](http://static.oschina.net/uploads/space/2016/0316/180344_NCjq_2399867.png)

被删除后，项目目录里没有test.txt，当我们恢复文件后，就出现在目录里了

如果我们确定要删除，那么我们可以使用 `git rm` 命令来执行删除操作

![](http://static.oschina.net/uploads/space/2016/0316/180636_h3m1_2399867.png)

![](http://static.oschina.net/uploads/space/2016/0316/180700_adHX_2399867.png)
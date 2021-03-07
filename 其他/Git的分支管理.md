## 一、创建与合并分支

在上一节中，我们在本地创建了一个 Git 仓库，但只有一个分支，就是 `master` 分支，它是主分支，HEAD 指向 `master` ，`master`指向当前提交，所以，HEAD 指向的就是当前分支。

![](http://static.oschina.net/uploads/space/2016/0317/230433_sBsX_2399867.png)

每次提交，master 都会向前移动一步，随着不断的提交，这条分支线会越来越长

![](http://static.oschina.net/uploads/space/2016/0317/230842_2isc_2399867.png)

当我们创建了新的分支，比如叫 `myBranch` ，git 就会新建一个指针叫 `myBranch`，指向 `master` 相同的提交，在把 HEAD 指向 `myBranch`，就表示当前分支在 `myBranch` 上。

![](http://static.oschina.net/uploads/space/2016/0318/085105_uzHN_2399867.png)

从现在开始，对工作区的修改和提交都是针对 `myBranch` 分支了，如果我们修改后再提交一次，`myBranch`指针就会向前移动一步，而`master`指针不变

![](http://static.oschina.net/uploads/space/2016/0318/091522_OCoH_2399867.png)

当我们在`myBranch`分支上的工作完成后，就可以把`myBranch`合并到`master`，也就是把`master`指针移动到`myBranch`的当前提交。

![](http://static.oschina.net/uploads/space/2016/0318/092018_EFqC_2399867.png)

当合并完成后，我们就可以删除掉`myBranch`分支，也就是把`myBranch`指针删除掉，然后我们就只剩下`master`分支了

![](http://static.oschina.net/uploads/space/2016/0318/092159_f2Nu_2399867.png)

OK,我们现在通过实际的例子来说明上面分支的使用。我们先看看当前分支：

```bash
$ git branch        //查看分支
```

![](http://static.oschina.net/uploads/space/2016/0318/092618_XS70_2399867.png)

可以看到，目前我们只有一个`master`主分支，我们来创建一个`bra`分支：

```bash
$ git checkout -b bra
```

![](http://static.oschina.net/uploads/space/2016/0318/094544_ueDk_2399867.png)

`git checkout` 命令加上`-b`参数，表示创建分支并切换，它相当于下面的两个命令：

```bash
$ git branch dev        //创建分支
$ git checkout dev      //切换到创建的分支
```

我们再次查看下当前分支情况

![](http://static.oschina.net/uploads/space/2016/0318/095155_GUqd_2399867.png)

我们可以看到有两个分支，分别是`master`和`bra`，当前在`bra`分支上。

`git branch`命令会列出所有分支，当前分支前面会标注一个 `*` 号，现在我们在 bra 分支上对 index.html 做一些修改

![](http://static.oschina.net/uploads/space/2016/0318/095622_y3cl_2399867.png)

保存退出后，我们进行提交

![](http://static.oschina.net/uploads/space/2016/0318/095800_RdI2_2399867.png)

现在我们在`bra`分支上的工作完成，切换到`master`分支：

```bash
$ git checkout master
```

![](http://static.oschina.net/uploads/space/2016/0318/100303_SAJt_2399867.png)

我们发现，刚才添加的第三个 P 标签不见了，这是因为刚才的提交时在`bra`分支上，而`master`分支此刻的提交点没有变化

![](http://static.oschina.net/uploads/space/2016/0318/100525_MsEY_2399867.png)

现在我们可以使用 `git merge` 命令来将`bra`分支上的更改合并到`master`分支上：

```bash
$ git merge bra
```

![](http://static.oschina.net/uploads/space/2016/0318/101120_WiSL_2399867.png)

然后我们再次查看 index.html 的内容

![](http://static.oschina.net/uploads/space/2016/0318/101206_GcX1_2399867.png)

OK，在 bra 分支上添加的第三个 P 标签回来了，而当前我们是在`master`主分支上。大家可能注意到了在我们合并时，出现了 `'Fast-forward'`，它告诉我们这次合并是'快进模式'，也就是将`master`指针直接指向`bra`分支的提交，所以速度很快，当然除了这种模式，还有其他模式。

合并完成后，我们就可以删除`bra`分支了

```bash
$ git branch -d bra
```

![](http://static.oschina.net/uploads/space/2016/0318/101630_7i8l_2399867.png)

然后我们再次查看分支情况

![](http://static.oschina.net/uploads/space/2016/0318/101721_3SXS_2399867.png)

现在只剩下`master`分支了。GIT 鼓励我们使用分支来进行开发，下面我们来总结下上面使用过的命令：

- 查看分支： git branch

- 创建分支： git branch "branch name"

- 切换分支： git checkout "branch name"

- 创建并切换分支： git checkout -b "branch name"

- 合并某分支到当前分支： git merge "branch name"

- 删除分支： git branch -d "branch name"

## 二、 解决冲突

有时候我们在进行分支合并时，会遇到各种各样的问题，下面我们用实例来说明下。

我们先创建一个新的分支`fea`，在这个分支上对 index.html 再添加一个 p 标签，然后在这个分支上提交。

```bash
$ git checkout -b fea    //创建并切换到fea分支
//对index.html做出修改
$ git add index.html    //提交
$ git commit -m "modifyed and commit on fea branch"
```

![](http://static.oschina.net/uploads/space/2016/0318/104138_hj6m_2399867.png)

切换到 master 分支上

```bash
$ git checkout master
```

![](http://static.oschina.net/uploads/space/2016/0318/104304_9UPH_2399867.png)

上面的代码还提示我们当前的`master`分支比远程的`master`还要多 2 个提交，可以使用 `git push` 命令推送本地的提交

接下来，我们在`master`分支上对 index.html 做出修改，并提交修改

![](http://static.oschina.net/uploads/space/2016/0318/105422_MFpP_2399867.png)

现在，`master`分支和`fea`分支都有了各自的提交

![](http://static.oschina.net/uploads/space/2016/0318/110402_ko9e_2399867.png)

这个时候，git 是无法进行快速合并的，只能把各自的修改合并起来，但这种合并可能会造成冲突。下面我们尝试着合并一下

![](http://static.oschina.net/uploads/space/2016/0318/111043_6fgC_2399867.png)

看到了吗？ `Automatic merge failed`，合并失败了。git 告诉我们文件有冲突，必须手动解决，我们用 `git status` 来看下，也提示有问题

![](http://static.oschina.net/uploads/space/2016/0318/112354_Qk3p_2399867.png)

查看文件内容，也有提示

![](http://static.oschina.net/uploads/space/2016/0318/112533_GPGR_2399867.png)

我们进入 index.html 进行修改，保存退出后，提交。

![](http://static.oschina.net/uploads/space/2016/0318/113123_Rgiy_2399867.png)

最后，我们删除 fea 分支

![](http://static.oschina.net/uploads/space/2016/0318/113249_yZLQ_2399867.png)

当 git 无法自动合并分支时，就必须手动去解决问题，再进行合并。我们还可以使用 `git log --graph` 来查看分支合并图

## 三、分支管理

上面我们了解了合并分支，git 会使用 `Fast forward` 模式，在这种模式下合并，删除分支后，会丢失分支信息，所以我们强制禁用 `Fast forward` 模式，在合并分支的时候使用 `--on--ff`

现在我们新建并切换到`dev`分支上

![](http://static.oschina.net/uploads/space/2016/0318/114416_o7EY_2399867.png)

修改 index.html 文件并提交

![](http://static.oschina.net/uploads/space/2016/0318/114602_fnN7_2399867.png)

切换到 master 分支

![](http://static.oschina.net/uploads/space/2016/0318/114654_Z5Jq_2399867.png)

OK，关键在这里，我们合并`dev`分支， 使用`--no--ff`参数，表示禁用 `Fast forward`

```bash
$ git merge --no-ff -m "merge with no-ff" dev
```

![](http://static.oschina.net/uploads/space/2016/0318/114907_0DUo_2399867.png)

合并后，我们使用 `git log` 查看分支历史

![](http://static.oschina.net/uploads/space/2016/0318/115041_PfgP_2399867.png)

在实际的开发中，`master`分支是主分支，是非常稳定的，仅仅只能用来发布新的版本，平时不能在它上面工作。

在一个项目开始的时候，我们可以在 git 上新建一个`dev`分支，那么如果团队有 3 个人，分别是 A,B,C,那么他们都分别会有自己的分支，大家都在自己的分支上干活，完成之后都提交到 dev 分支上，但这是不稳定的，经过多次的测试，发现 bug，修改，再次合并到`dev`分支，经过很多次的迭代，版本稳定了，OK，现在可以把`dev`分支合并到`master`上进行发布了。

## 四、BUG 分支

我们在工作时会遇到各种各样的 BUG，有时候，有些 bug 需要立刻修复，但是你手上的任务还没有完成，怎么办？这时，Git 为我们提供了 `stash` 功能，它可以将我们当前分支上的任务存储起来，放在另外一个地方，我们就可以放心的切换到有 bug 的分支去进行修复。

当前有如下的情景，我在`dev`分支上工作，写了一些代码，但并没有提交

![](http://static.oschina.net/uploads/space/2016/0329/232244_hkn6_2399867.png)

这时，有任务来了，需要去 Fix 一个编号为 88 的 bug，我们可以在`master`分支上创建一个临时的分支来修复这个 bug，OK，我们利用 `stash` 功能将当前的工作保存起来。

![](http://static.oschina.net/uploads/space/2016/0329/232558_gRey_2399867.png)

我们在利用 `status` 来查看下当前工作区状态

![](http://static.oschina.net/uploads/space/2016/0329/232708_sr2M_2399867.png)

我们看到当前在`dev`分支上，而且工作区是干净的，而刚刚我们在`dev`分支上做的工作并没有提交。

好了，我们现在需要去`master`分支上创建一个`fix88`分支来修复 bug，先切换到`master`分支

![](http://static.oschina.net/uploads/space/2016/0329/232917_YIyw_2399867.png)

创建`fix88`分支来修复 bug

![](http://static.oschina.net/uploads/space/2016/0329/233121_yAzK_2399867.png)

![](http://static.oschina.net/uploads/space/2016/0329/233121_JyAx_2399867.png)

我们进入 index.html 修复 bug，并提交

![](http://static.oschina.net/uploads/space/2016/0329/233553_N55T_2399867.png)

切换到`master`分支，合并修改，并删除`fix88`分支

![](http://static.oschina.net/uploads/space/2016/0329/234104_QycK_2399867.png)

修复 bug 后的 index.html 内容如下，我们在最后一个 p 标签里，把原来的内容加上了一个 span 标签，并添加了另外一个 span 标签，插入了一些说明的内容

![](http://static.oschina.net/uploads/space/2016/0329/235330_Uw6g_2399867.png)

然后我们再来看看当前的分支状态和工作区状态

![](http://static.oschina.net/uploads/space/2016/0329/235709_9ynn_2399867.png)

![](http://static.oschina.net/uploads/space/2016/0329/235501_ac8M_2399867.png)

切换到我们原来的工作分支`dev`上，并查看工作区状态

![](http://static.oschina.net/uploads/space/2016/0329/235817_kahU_2399867.png)

![](http://static.oschina.net/uploads/space/2016/0329/235913_dJVo_2399867.png)

工作区是干净的，下面我们使用 `git stash list` 命令来查看下刚刚我们隐藏的工作场景

![](http://static.oschina.net/uploads/space/2016/0330/000048_IMWe_2399867.png)

OK，我们来恢复我们在`dev`分支上的工作场景 ，这里有两个方法可以来恢复

一是使用 `git stash apply`，这个方法恢复之后，并不会删除`stash`里的内容，还需要使用 `git stash drop`来删除 `stash` 里的内容

二是使用 `git stash pop` ，这个方法恢复之后，会直接删除`stash`里的内容

![](http://static.oschina.net/uploads/space/2016/0330/000502_oFqV_2399867.png)

可以看到工作场景恢复了，我们再来看看`stash`里的内容，`git stash list`

![](http://static.oschina.net/uploads/space/2016/0330/000630_xBLP_2399867.png)

没有了。

我们还可以多次使用`stash`，最后需要恢复的时候，使用下面的命令：

```bash
git stash apply stash@{0}
```

修复 bug 可能是我们会长期做的事，它会随时出现，而 bug 需要立刻解决，这时，我们就需要把现有的手上的工作`stash` 下，然后创建一个新的分支去修复 bug，提交合并后删除这个分支，最后再使用 `git stash pop` 来恢复我们的工作场景。

## 五、Feature 分支

我们在开发的过程中，可能随时会接到新的任务，为整个工程添加新的功能，这时，我们最好的做法就是新建一个`feature`分支，在这个分支上开发，合并，最后删除该分支

假设有这样一个场景，我们接到了 Boss 的一个任务，要在当前工程上开发一个新的功能，命名为 feature-new01，ok, let's go work...

创建新功能分支 feature-new01

![](http://static.oschina.net/uploads/space/2016/0330/002448_xXay_2399867.png)

在当前新功能分支上，我们对 index.html 添加一个新的东西

![](http://static.oschina.net/uploads/space/2016/0330/002730_ZsoM_2399867.png)

提交修改

![](http://static.oschina.net/uploads/space/2016/0330/002947_rQP7_2399867.png)

切换回`dev`分支，并准备进行合并。（新功能合并到`dev`工作分支上）

![](http://static.oschina.net/uploads/space/2016/0330/003107_3ryW_2399867.png)

这时，Boss 说新能取消，不再开发，所以我们必须删除，如果我们使用 `git branch -d feature-new01` ，这时`git`会提示我们，这个分支的内容还没有被合并，不能删除，所以，我们需要使用 `git branch -D feature-new01` 来强行删除这个分支。

![](http://static.oschina.net/uploads/space/2016/0330/003506_THIk_2399867.png)

![](http://static.oschina.net/uploads/space/2016/0330/003506_jN0s_2399867.png)

如果团队需要在现有工程上开发新的功能，请新建一个分支进行，完成后，提交，并切换回团队工作分支（不是`master`），进行合并，如果在合并之前需要删除，使用 `git branch -D <branch name>` 来强行删除，如果已合并，请参考前面的版本回退。

## 六、多人协作

当我们从远程仓库克隆项目时，实际上是把本地`master`分支和远程`master`分支对应起来了，远程仓库的默认名称是 `origin` ，要查看远程仓库的信息，使用 `git remote`

![](http://static.oschina.net/uploads/space/2016/0331/102402_cCC7_2399867.png)

或者我们可以使用 `git remote -v` 来显示更详细的信息

![](http://static.oschina.net/uploads/space/2016/0331/102452_rYdq_2399867.png)

推送分支，就是把该分支上的所有本地提交都推送到远程仓库，推送时，需要指定本地分支，比如我们需要推送`master`分支，使用 `git push origin master`

![](http://static.oschina.net/uploads/space/2016/0331/103045_tWJp_2399867.png)

如果要推送其他分支，如`dev`，则可以使用 `git push origin dev`

![](http://static.oschina.net/uploads/space/2016/0331/103221_08m2_2399867.png)

但不是所有的本地分支都需要推送到远程仓库

`master`分支是主分支，它是需要推送到远程的。

`dev`分支作为开发分支，也是需要推送到远程分支的。

处理 bug 的某些分支，因为处理完成之后会被删除，所以就么有必要了，除非团队需要，比如可以查看那些人在什么时候处理了哪些 bug

新功能的开发分支，如`feature`分支，视自己的团队情况而定。

所以，我们自己在本地的分支，是否推送，完全取决于我们自己，某些分支完全就可以放在自己的本地电脑上玩。

多人团队开发时，团队成员都会往`master`和`dev`分支上推送自己的修改，下面我们来模拟一个 2 人的团队开发，我在自己的 Mac 上的虚拟机中装了一个 Ubuntu，我们在这里来模拟。

在 Ubuntu 上装好 git，然后从 github 上克隆 gitTest 项目。（注意：在这之前必须把当前机器的 SSH Key 添加到 github）。

![](http://static.oschina.net/uploads/space/2016/0331/111507_1RG7_2399867.png)

创建用户

![](http://static.oschina.net/uploads/space/2016/0331/114623_vspo_2399867.png)

当前，我们在远程仓库中有两个分支，分别是`mastet`主分支和`dev`开发分支，但其他开发成员从远程克隆项目下来之后，会发现只有`master`分支，看刚才我们在 Ubuntu 上克隆的项目

![](http://static.oschina.net/uploads/space/2016/0331/112244_3ZG6_2399867.png)

我们看到只有一个`master`分支，如果团队成员 lz 需要在`dev`分支上进行开发，那么必须创建远程的`dev`分支到本地，可以使用 `git checkout -b dev origin/dev` 命令创建

![](http://static.oschina.net/uploads/space/2016/0331/115406_TnrD_2399867.png)

现在，团队成员 lz 就可以在`dev`分支上进行开发，并提交，push 到远程。我们来试试

![](http://static.oschina.net/uploads/space/2016/0331/145513_HNzV_2399867.png)

修改完成，最后一行的 div 是团队成员 lz 在本地`dev`分支上添加的。我们保存退出并提交，最后 push 到远程仓库

![](http://static.oschina.net/uploads/space/2016/0331/145833_HzNh_2399867.png)

OK，现在团队成员 lz 对 index.html 做了添加并推送到了远程，当另外一个成员也对这个文件做了修改，并推送，是一个怎么样的情况呢？我们来试试

![](http://static.oschina.net/uploads/space/2016/0331/151020_0Fff_2399867.png)

呀，提示推送失败了，原因是刚才 lz 已经对 index.html 文件做除了修改并推送到了`dev`分支，我再提交推送就会出现冲突，这时我们需要先把最新的修改 pull 下来到我的本地，合并修改后再推送

![](http://static.oschina.net/uploads/space/2016/0331/151349_tWyT_2399867.png)

pull 也失败了，原因是我们需要将本地`dev`和远程的`origin/dev`建立链接

![](http://static.oschina.net/uploads/space/2016/0331/151749_h8kD_2399867.png)

再次 pull

![](http://static.oschina.net/uploads/space/2016/0331/151921_VClb_2399867.png)

成功了，我们打开 inex.html 看看

![](http://static.oschina.net/uploads/space/2016/0331/152049_7kkY_2399867.png)

看到了吗？刚才成员 lz 的代码和我刚才写入的代码都在里面了，而且 git 也给我们做出了提示，如果现在合并会起冲突，我们需要手动调整代码，然后再提交推送

![](http://static.oschina.net/uploads/space/2016/0331/152832_oF7z_2399867.png)

通常情况下，在团队协作开发中，我们可以先推送自己的修改，使用 `git push origin <branch name>`

如果推送失败，说明远程的分支比本地更新，我们需要使用 `git pull` 来合并

如果 `git pull` 提示 “no tracking information”， 说明我们本地的分支没有和远程进行关联，我们需要使用

`git branch --set-upstream-to=origin/dev dev` 来进行关联，之后再次使用 `git pull`

如果存在冲突，在本地解决冲突的代码，最后 `git push origin <branch name>`。

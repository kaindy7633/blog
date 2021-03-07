<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [一、修改错误的提交信息（commit message）](#%E4%B8%80%E4%BF%AE%E6%94%B9%E9%94%99%E8%AF%AF%E7%9A%84%E6%8F%90%E4%BA%A4%E4%BF%A1%E6%81%AFcommit-message)
- [二、提交之前撤销 `git add`](#%E4%BA%8C%E6%8F%90%E4%BA%A4%E4%B9%8B%E5%89%8D%E6%92%A4%E9%94%80-git-add)
- [三、撤销最近一次代码提交](#%08%E4%B8%89%E6%92%A4%E9%94%80%E6%9C%80%E8%BF%91%E4%B8%80%E6%AC%A1%E4%BB%A3%E7%A0%81%E6%8F%90%E4%BA%A4)
- [四、Git仓库撤销至前一次提交时的状态](#%E5%9B%9Bgit%E4%BB%93%E5%BA%93%E6%92%A4%E9%94%80%E8%87%B3%E5%89%8D%E4%B8%80%E6%AC%A1%E6%8F%90%E4%BA%A4%E6%97%B6%E7%9A%84%E7%8A%B6%E6%80%81)
- [五、撤销合并（Merge）](#%E4%BA%94%E6%92%A4%E9%94%80%E5%90%88%E5%B9%B6merge)
- [六、从当前Git分支移除未追踪的本地文件](#%E5%85%AD%E4%BB%8E%E5%BD%93%E5%89%8Dgit%E5%88%86%E6%94%AF%E7%A7%BB%E9%99%A4%E6%9C%AA%E8%BF%BD%E8%B8%AA%E7%9A%84%E6%9C%AC%E5%9C%B0%E6%96%87%E4%BB%B6)
- [七、删除本地和远程Git分支](#%E4%B8%83%E5%88%A0%E9%99%A4%E6%9C%AC%E5%9C%B0%E5%92%8C%E8%BF%9C%E7%A8%8Bgit%E5%88%86%E6%94%AF)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

> 我们经常使用Git来保存自己的工作，在我们迷迷糊糊的犯下错误之后，就可以使用Git将代码返回到之前的状态。通常，大部分时间我们都只会用到`add`、`commit`、`branch`和`push/pull`这些命令。但如果自己往仓库中添加了错误的文件，或是将代码提交到了错误的分支，而且提交信息还写错了的话，自己怎样才能取消之前的操作？

## 一、修改错误的提交信息（commit message）

下面这个命令可以让你编辑最近一次的提交信息

```bash
$ git commit --amend -m ”YOUR-NEW-COMMIT-MESSAGE”
```

下面的命令强制推送这次的代码提交

```bash
$ git push <remote> <branch> --force
```

## 二、提交之前撤销 `git add`

如果你往暂存区`（staging area）`中加入了一些错误的文件，但是还没有提交代码。你可以使用一条简单的命令就可以撤销

```bash
$ git reset <文件名>
```

或者如果你想从暂存区移除所有没有提交的修改:

```bash
$ git reset
```

## 三、撤销最近一次代码提交

有时候你可能会不小心提交了错误的文件或一开始就遗漏了某些东西

```bash
$ git reset --soft HEAD~1
$ git add -A .
$ git commit -c ORIG_HEAD
```

行第一个命令时，`Git`会将`HEAD`指针后移到此前的一次提交，之后你才能移动文件或作必要的修改。

然后你就可以添加所有的修改，而且当你执行最后的命令时，`Git`会打开你的默认文本编辑器，其中会包含上一次提交时的信息

## 四、Git仓库撤销至前一次提交时的状态

“撤销”（`revert`）在许多情况下是非常有必要的——尤其是你把代码搞的一团糟的情况下

```bash
$ git checkout <SHA>
```

`<SHA>`是你想查看的提交拥有的哈希值（`Hash Code`）中前8至10个字符

这个命令会使`<HEAD>`指针脱离（`detach`），可以让你在不检出（`check out`）任何分支的情况下查看代码

## 五、撤销合并（Merge）

要想撤销合并，你可能必须要使用恢复命令（HARD RESET）回到上一次提交的状态。“合并”所做的工作基本上就是重置索引，更新working tree（工作树）中的不同文件，即当前提交（）代码中与HEAD游标所指向代码之间的不同文件；但是合并会保留索引与working tree之间的差异部分（例如那些没有被追踪的修改）

```bash
$ git checkout -b <SHA>
```

## 六、从当前Git分支移除未追踪的本地文件

假设你凑巧有一些未被追踪的文件（因为不再需要它们），不想每次使用`git status`命令时让它们显示出来

```bash
$ git clean -f -n #1  // 选项-n将显示执行下面的命令时将会移除哪些文件
$ git clean -f #2  // 该命令会移除所有上面的命令中显示的文件
$ git clean -fd #3  // 如果你还想移除文件件，请使用选项-d
$ git clean -fX #4  // 如果你只想移除已被忽略的文件，请使用选项-X
$ git clean -fx #5  // 如果你想移除已被忽略和未被忽略的文件，请使用选项-x
```

## 七、删除本地和远程Git分支

```bash
$ git branch --delete --force <branchName>  // 删除本地分支
$ git push origin --delete <branchName>  // 删除远程分支
```
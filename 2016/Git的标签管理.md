> 当我们需要提交一个软件版本时，可以往这个版本上打一个标签，以后可以按照某个标签来取回某个版本的代码，实际上标签就是一个软件版本的快照。

标签实际上是一个指向某个`commit`的指针，跟分支很像，但分支可以移动，而标签却不能。

## 创建标签

首先，我们应该切换到需要打标签的分支上

```bash
git branch
* dev
  master
git checkout master
Switched to branch 'master'
Your branch is up-to-date with 'origin/master'.
```

然后，我们可以使用`git tag v1.0`这样的命令来创建一个标签

```bash
git tag v1.0
```

使用`git tag`命令来查看所有标签

```bash
git tag
```

上面的操作是默认的，也就是当前最新的提交上，如果想要给历史版本打上标签，就必须找到历史提交的`commit id`

```bash
git log --pretty=oneline --abbrev-commit 
4b2bea2 merge fix88 branch's modifyed
601da8d 在fix88分支上修复了一个bug
3d3cc43 merge with no-ff
a75a84c modifyed on dev branch
d057d79 conflict fixed
08ae6f3 modifyed on master branch
cec715d modifyed and commit on fea branch
8d4576f test on bra branch
62a6606 delete test.txt
96d9332 add test.txt
469e0de 这是我第二次修改，向index.html里添加了一个p标签并写入内容
1fb9ecb 这是我第一次修改，向index.html里添加了一个p标签并写入内容
a1a356d 新建index.html文件，这是第一次提交到仓库
```

比如，我们想要在第二次修改的地方打上标签，那么它对应的`commit id`就是 `469e0de`，下面来敲入命令：

```bash
git tag v0.1 469e0de
```

我们再次使用`git tag`命令来查看标签列表

```bash
git tag
v0.1
v1.0
```

我们可以使用`git show <tagname>`命令来查看标签信息

```bash
git show v0.1
commit 469e0dee7484aecadc303dea96aca3b05fcab718
Author: kaindy7633 <kaindy7633@gmail.com>
Date:   Wed Mar 16 15:28:47 2016 +0800

    这是我第二次修改，向index.html里添加了一个p标签并写入内容

diff --git a/index.html b/index.html
index 00e3fba..de4f7cf 100644
--- a/index.html
+++ b/index.html
@@ -6,5 +6,6 @@
 
 <body>
   <p>这是我向这个HTML文件加入的第一个P标签。</p>  
+  <p>这是我向这个HTML文件加入的第二个p标签。</p>
 </body>
 </html>
```

我们还可以为标签打上一段说明，使用`-a`参数指定标签名，`-m`参数指定标签说明

```bash
git tag -a v0.2 -m "add for fea branch" cec715d
```

继续使用`git show <tagname>`查看

```bash
git show v0.2
tag v0.2
Tagger: kaindy7633 <kaindy7633@gmail.com>
Date:   Thu May 5 18:24:55 2016 +0800

add for fea branch

commit cec715de12320fe1169c083c722e572685750144
Author: kaindy7633 <kaindy7633@gmail.com>
Date:   Fri Mar 18 10:41:18 2016 +0800

    modifyed and commit on fea branch

diff --git a/index.html b/index.html
index bf6b036..b7720b4 100644
--- a/index.html
+++ b/index.html
@@ -8,5 +8,6 @@
   <p>这是我向这个HTML文件加入的第一个P标签。</p>  
   <p>这是我向这个HTML文件加入的第二个p标签。</p>
   <p>这条修改是在bra分支上进行的，添加了第三个p标签</p>
+  <p>这条修改是在fea分支上进行的，添加了第四个p标签</p>
 </body>
 </html>
```

## 操作标签

如果标签打错了，也是可以删除的，标签都是存储在本地的

```bash
git tag -d v0.1
Deleted tag 'v0.1' (was 469e0de)
```

如果想要把本地标签推送到远程，可以使用`git push origin <tagname>`命令

```bash
git push origin v1.0
Total 0 (delta 0), reused 0 (delta 0)
To git@github.com:kaindy7633/gitTest.git
 * [new tag]         v1.0 -> v1.0
```

或者，我们可以一次把所有未推送到远程的标签推送到远程，使用命令`git push origin --tags`

```bash
git push origin --tags
Counting objects: 1, done.
Writing objects: 100% (1/1), 161 bytes | 0 bytes/s, done.
Total 1 (delta 0), reused 0 (delta 0)
To git@github.com:kaindy7633/gitTest.git
 * [new tag]         v0.2 -> v0.2
```

如果标签已推送到远程，而又要删除，则会有点麻烦，先删除本地标签

```bash
git tag -d v0.2
Deleted tag 'v0.2' (was d6683cf)
```

然后从远程删除，命令也是使用`push`

```bash
git push origin :refs/tags/v0.2
Warning: Permanently added the RSA host key for IP address '192.30.252.120' to the list of known hosts.
To git@github.com:kaindy7633/gitTest.git
 - [deleted]         v0.2
```
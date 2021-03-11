# 如何发布Go公共模块

通常之前的学习，我们知道了在 `Go` 的项目中，可以 `import` 一个托管在远程仓库的模块，这个模块在我们使用 `go get` 的时候，会下载到本地。

既然是放在远程仓库上，意味着所有人都可以发布，并且所以人也都可以使用。

今天就来学习一下，如何发布一个开源的模块，并且使用它。

## 新建仓库

先在你的 `Github` 上新建一个仓库，记得选 `Public`（默认）

![](../images/5A1E33FF188C26616E5F69E89A32484C.webp)

然后你会得到一个仓库地址，在你的电脑上 使用 `git clone` 命令克隆下来

## 编写模块代码

使用前面学过的 `go mod init` 命令进行初始化，注意这里的模块名，填写我们的 `git` 仓库地址（但是要去掉 `.git` 哈）

```bash
$ git clone https://github.com/BingmingWong/goutils.git
$ go mod init github.com/BingmingWong/goutils
```

![](../images/DFCBEBEF1F6E8502B0F5E4BE9D9CDB26.webp)

然后新建一个 `hash` 文件夹，存放编写的一个计算 `md5` 值工具包，编辑 `md5.go`

```go
package hash

import (
    "crypto/md5"
    "encoding/hex"
    "errors"
    "fmt"
    "io"
    "os"
)

// get file md5
func FileMd5(filename string) (string, error) {
    file, err := os.Open(filename)
    if err != nil {
    return "", errors.New(
        fmt.Sprintf("md5.go hash.FileMd5 os open error %v", err))
    }
    h := md5.New()
    _, err = io.Copy(h, file)
    if err != nil {
        return "", errors.New(fmt.Sprintf("md5.go hash.FileMd5 io copy error %v", err))
    }

    return hex.EncodeToString(h.Sum(nil)), nil
}

// get string md5
func StringMd5(s string) string {
    md5 := md5.New()
    md5.Write([]byte(s))
    return hex.EncodeToString(md5.Sum(nil))
}
```

由于我们使用的都是内置包，没有引入第三方的包，所以接下来可以把你刚刚那些新增的文件，全部 `push` 到 `git` 仓库。

```bash
$ git add -A
$ git commit -m "Add a md5 function"
$ git push
```

## 发布版本

一切完成后，刷新我们的仓库，就可以看到我们的刚刚上传的项目代码了，点击 `release` 发布一个版本

![](../images/3F749EADD15E03808629399DC024299E.webp)

![](../images/D3F97C812182763B95EED7F74CC682F4.webp)

然后像下图一样，添加一些版本说明

![](../images/C23CBD18183C91A0B0DB50B1F5EAC103.webp)

最后点击一个 `Publish release`，就发布了一个版本

![](../images/2FF57B41725347AEC390FF5A7DF7FA06.webp)

## 如何使用？

使用 `go get` 命令下载我们的发布的模块

```bash
$ go get github.com/BingmingWong/goutils
```

![](../images/7E2FD1048371394B9CF43FC8F755A0B2.webp)

再使用 `tree` 命令，查看一下我们下载的包已经放入了 `$GOPATH/pkg/mod` 下。

有一点很有趣的是，我的 `Github` 用户名（`BingmingWong`）是有大写字母的，下载下来后，在目录中大写字母会对应变成 !小写字母，如下所示

![](../images/76429097535B1392F4C3DFEEB7701C31.webp)

这个用户名看起来有点非主流（大小混写），你要想改的话，也是可以的。如果你有其他的开源项目，`github` 并不会为你做重定向，你需要自己评估这个风险。

写完这篇文章后，我把自己的用户名也改了下，改成了 `iswbm` 。

![](../images/CA5352224CCC36FD654F2895BED1A64A.webp)

回过头来，我还是继续讲如何使用吧。

下载下来后，我们试着去调用一下他的函数，有一点需要注意的是，在这个示例里，你不能使用 `github.com/BingmingWong/goutils` 去导入，因为在这个目录下并没有 `package`，所以你必须导入 `github.com/BingmingWong/goutils/hash` 。

整个过程如下所示：

![](../images/7214714ADD07D5C8539B5CBA5D0AF571.webp)

本文参考学习自
https://studygolang.com/articles/22851
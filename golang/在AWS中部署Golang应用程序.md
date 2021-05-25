# 在 AWS 中部署 Golang 应用程序

以前，当我们构建完我们的应用程序后，我们会选择各种服务器资源，进行应用程序的部署上线，其实这中间会隐藏的各种各样的问题，况且，我们也不是专业的运维人员，固定的服务资源投入也增加了我们的投入，所以，`ServerLess` 来了，关于 `ServerLess` 的相关知识点，请移步 `BD` 或 `GG` 自行查询

这里，我来介绍一下如何在 `AWS` 中安装部署 `Golang` 应用程序，`AWS` 全称：`Amazon web service`(亚马逊网络服务)，是亚马逊公司旗下云计算服务平台，为全世界各个国家和地区的客户提供一整套基础设施和云解决方案。

说的直白一点，就是当我们完成应用程序开发后，完成部署上线运营的事，都是它干的，我们无需担心资源调用，服务负载等问题，关注到业务本身即可，国内的阿里、腾讯也有相应的服务，后面会有相关文章介绍如何使用它们来部署小程序或移动 `APP` 应用

对应的，官方有详尽的介绍如何在 `AWS` 上部署 `Golang` 应用程序，这里是链接：

[https://docs.aws.amazon.com/zh_cn/elasticbeanstalk/latest/dg/go-tutorial.html](https://docs.aws.amazon.com/zh_cn/elasticbeanstalk/latest/dg/go-tutorial.html)

(PS: 速度慢的同学自行搭梯子)

部署的过程其实就是将 `Go` 应用程序并将其部署到 `AWS Elastic Beanstalk` 环境的过程，`AWS Elastic Beanstalk` 是 `AWS` 提供的构建 `REST API` 的服务

我们不会使用 `AWS` 提供的控制台，转而使用 `AWS` 提供的命令行方式来部署，我们需要安装一个叫做 `EB` 的工具，故我们需要一个强大的 `SHELL` 来完成这事，`Linux` 或 `Mac` 的同学使用默认的命令行工具即可，`Windows` 的同学，强烈建议安装 `WSL`，在 `Ubuntu` 环境下安装 `EB`

在开始安装之前，我们先来把上线测试 `Go` 应用程序写出来

```go
package main

import (
	"fmt"
	"net/http"
)

func handler(w http.ResponseWriter, r *http.Request) {
	if r.URL.Path == "/" {
		fmt.Fprintf(w, "Hello World! Append a name to the URL to say hello. For example, use %s/Mary to say Hello to Mary", r.Host)
	} else {
		fmt.Fprintf(w, "Hello, %s!", r.URL.Path[1:])
	}
}

func main() {
	http.HandleFunc("/", handler)
	if err := http.ListenAndServe(":5000", nil); err != nil {
		fmt.Printf("%s", err)
	}
}
```

这个 `Go` 应用程序就是提供了一个 `GET` 服务，很简单，现在我们开始安装并部署我们的应用程序

第一步，我们需要在系统中安装 `EB CLI`，`EB CLI` 在 `Python` 中开发，需要 `Python` 版本 `2.7`、`3.4` 或更高版本，此外，还需要 `pip`，最终的 `awsebcli` 是由 `pip` 来安装的

如果你的系统中还没有安装 `Python`，请使用下面的命令来安装

```bash
$ sudo apt-get install python3.7
```

验证是否已正确安装 `Python`，打开终端或 `Shell`，并运行以下命令:

```bash
kaindy@LAPTOP-IF6KJL8R:~$ python3 --version
Python 3.8.5
```

下面开始安装 `pip`

从 `pypa.io` 下载安装脚本。

```bash
$ curl -O https://bootstrap.pypa.io/get-pip.py
```

使用 `Python` 运行脚本。

```bash
$ python3 get-pip.py --user
Collecting pip
  Downloading pip-8.1.2-py2.py3-none-any.whl (1.2MB)
Collecting setuptools
  Downloading setuptools-26.1.1-py2.py3-none-any.whl (464kB)
Collecting wheel
  Downloading wheel-0.29.0-py2.py3-none-any.whl (66kB)
Installing collected packages: pip, setuptools, wheel
Successfully installed pip setuptools wheel
```

这里需要特别注意，按照官方的做法，这里会找不到 `pip`，所以，我们需要手动将 `pip` 挂载到 `PATH` 上。（参考地址：[https://blog.csdn.net/r527665047/article/details/106295315](https://blog.csdn.net/r527665047/article/details/106295315)）

- 编辑文件 `/etc/sudoers`

  ```bash
  sudo vi /etc/sudoers
  ```

  将 `Defaults env_reset` , 改为 `Defaults !env_reset` (就是多一个感叹号，在保存退出的时候，必须`:wq!`才能强制保持退出)

- 编辑文件 `~/.bashers`

  ```bash
  sudo vi .bashrc
  ```

  在文档的最后一行添加 `alias sudo='sudo env PATH=$PATH'`

- 退出，再执行命令

  ```bash
  source ~/.bashrc
  ```

接下来验证 `pip` 是否正确安装

```bash
kaindy@LAPTOP-IF6KJL8R:~$ pip --version
pip 21.1.2 from /home/kaindy/.local/lib/python3.8/site-packages/pip (python 3.8)
```

使用 `pip` 安装 `EB CLI`。

```bash
$ pip install awsebcli --upgrade --user
```

验证 `EB CLI` 是否正确安装：

```bash
kaindy@LAPTOP-IF6KJL8R:~$ eb --version
EB CLI 3.19.4 (Python 3.8.5)
```

要升级到最新版本，执行下面的命令：

```bash
pip install awsebcli --upgrade --user
```

下面，我们使用 `EB CLI` 来部署 `Go` 应用程序

创建环境并部署 `Go` 应用程序

使用 `eb init` 命令，初始化 `EB CLI` 存储库。

```bash
~/eb-go$ eb init -p go go-tutorial --region us-east-2
Application go-tutorial has been created.
```

此命令创建名为 `go-tutorial` 的应用程序，并配置本地存储库，以最新的 `Go` 平台版本创建环境。

如果还没有配置秘钥 ID 和加密秘钥的话，会弹出对话框要求填入，这两个需要在控制台中生成，请自行登录 AWS 控制配置

创建环境并使用 `eb create` 将应用程序部署到此环境中。`Elastic Beanstalk `会自动为您的应用程序生成一个二进制文件，并在端口 `5000` 上启动该文件。

```bash
~/eb-go$ eb create go-env
```

运行大概几分钟后，就可以看到创建并部署成功，还有一个访问地址，我们也可以前往自己的控制台，选择 `Elastic Beanstalk`，就可以查看到对应的刚创建的应用。

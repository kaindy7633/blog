# 用 Gin 编写一个完整的博客后端应用（一）

`gin` 是用 `Go` 语言编写的一个 `HTTP Web` 框架，并使用了 `httprouter` 开源项目作为路由，性能很高。

## 项目初始化

执行以下命令进行项目的初始化操作

```bash
kaindy@liuzhendeMacBook-Pro project % mkdir -p $HOME/MyWorks/project/go-programming-tour-book/blog-service
kaindy@liuzhendeMacBook-Pro project % cd $HOME/MyWorks/project/go-programming-tour-book/blog-service
kaindy@liuzhendeMacBook-Pro blog-service % go mod init github.com/kaindy7633/go-programming-tour-book/blog-service
go: creating new go.mod: module github.com/kaindy7633/go-programming-tour-book/blog-service
```

完成初始化第一步，接下来我们安装 `gin`

```bash
go get -u github.com/gin-gonic/gin@latest
```

目前我的 `go` 版本是 `1.17.1`， 安装的 `gin` 版本是 `1.7.4`, 打开项目目录下的 `go.mod` 文件也可以查看 `gin` 框架的版本信息以及依赖项

## 快速启动

接下来，我们编写一个 `Demo`，来快速启动一个基于 `gin` 的 `HTTP` 服务，在 `blog-service` 目录下新建 `main.go` 文件

```go
package main

import "github.com/gin-gonic/gin"

func main() {
	r := gin.Default()
	r.GET("/ping", func(c *gin.Context) {
		c.JSON(200, gin.H{"message": "pong"})
	})
	_ = r.Run()
}
```

运行它

```bash
kaindy@liuzhendeMacBook-Pro blog-service % go run main.go
[GIN-debug] [WARNING] Creating an Engine instance with the Logger and Recovery middleware already attached.

[GIN-debug] [WARNING] Running in "debug" mode. Switch to "release" mode in production.
 - using env:   export GIN_MODE=release
 - using code:  gin.SetMode(gin.ReleaseMode)

[GIN-debug] GET    /ping                     --> main.main.func1 (3 handlers)
[GIN-debug] Environment variable PORT is undefined. Using port :8080 by default
[GIN-debug] Listening and serving HTTP on :8080
```

上面输出的调试信息很明确的表达了以下信息：

- 这是一个默认的 `Engine` 实例，表示默认使用官方提供的 `Logger` 和 `Recovery` 中间件创建
- 这是一个调试模式的运行模式，生产环境应切换为发布模式
- 这里注册了一个路由，`GET/ping`，并输出其调用方法名
- 以及女性信息，表示监听默认的 `8080` 端口

在这之后就可以通过命令行来验证该接口

```bash
kaindy@liuzhendeMacBook-Pro blog-service % curl http://localhost:8080/ping
{"message":"pong"}
```

---

下一节：[用 Gin 编写一个完整的博客后端应用（二）](https://github.com/kaindy7633/blog/blob/main/golang/%E7%94%A8Gin%E7%BC%96%E5%86%99%E4%B8%80%E4%B8%AA%E5%AE%8C%E6%95%B4%E7%9A%84%E5%8D%9A%E5%AE%A2%E5%90%8E%E7%AB%AF%E5%BA%94%E7%94%A8%EF%BC%88%E4%BA%8C%EF%BC%89.md)

在我们使用 `Ant Design Pro` 进行 `React` 工程创建的时候，按照官方的说明，会报一个错误：

![](https://s1.ax1x.com/2020/04/12/GqWIpR.png)

官方提供的创建工程的命令是：

新建一个空白的目录，然后执行如下命令：

```bash
yarn create umi

#or

npm create umi
```

但却得到如上的错误提示，无论如何选择都是这样，正确的方式应该是在你要创建的工程目录的父目录中执行命令

```bash
yarn create umi ant-design-app

# or

npm create umi ant-design-app
```

`ant-design-app` 是项目名称，可以自定义，这样就可以正确创建项目了
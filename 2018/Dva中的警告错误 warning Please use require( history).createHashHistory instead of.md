安装好 `dva`，启动后在浏览器控制台，有时候会报如下的错误：

![](https://s1.ax1x.com/2020/04/23/Jd38gK.jpg)

解决方案：

找到 `node_modules` 中的 `dva` 包

![](https://s1.ax1x.com/2020/04/23/Jd3336.png)

修改 `lib/index.js`

![](https://s1.ax1x.com/2020/04/23/Jd319x.jpg)

关闭编译器和服务 重新启动就好了
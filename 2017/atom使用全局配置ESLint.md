> ESLint是一个Javascript静态检查工具，它可以帮你养成良好的编程习惯，使你的javascript代码达到国际化的水准。

ESLint是所有Javascrpt静态检查工具里最晚诞生的一个，之前还曾经有过JSLint以及JSHint等工具，但JSLint和JSHint都是用的一套标准，在目前这个前端技术飞速发展的时代已经显得有点落伍。

ESLint的好处是既提供了国际大厂的标准，同时又给了你自定义标准的可能性。

ESLint的推荐设置方式是按项目设置，但是如果我们有很多个不同的javascript项目的话，一个一个去设置未免太麻烦，所以在这里介绍的是全局设置方法，一次设置，所有项目全部采用同一标准。

首先，在atom中安装`linter`插件和`linter-eslint`插件。安装完成之后，`linter-eslint`的缺省设置有2个地方需要修改：

1. 把`Disable when no ESLint config is found`的对钩去掉。这个选项的意思是说：如果你的javascript项目文件夹中没有`.eslintrc`这样的配置文件的话，那么ESLint就不起作用。在这里，我们要设置为全局`lint`，不需要在每个javascript文件夹中包含`.eslintrc`文件，所以要把它去掉，否则由于我们的项目文件夹中没有`.eslintrc`文件，ESLint会不起作用。

2. 把`Use global ESLint installation`的对钩勾上。因为我们使用的是全局的ESLint安装包。

下面，开始安装ESLint：

```bash
npm install eslint -g
```

ESLint是通过npm安装的，这里的`-g`选项代表全局，也就是说它不会把ESLint的可执行文件安装在你的项目文件夹或者说当前文件夹下。如果你没有设置这个`-g`选项的话，它会在你当前文件夹下安装ESLint可执行文件，那样就不是全局安装了。后面我们所有安装包都要用使用这个`-g`选项

```
eslint -v
```

安装完成之后，你可以先执行一下`eslint -v`这个命令来看一下`eslint`是否已经安装成功了，如果没有的话，你需要反复检查，直到确保`eslint`安装已经成功为止。

关于`eslint --init`可以不必执行，它主要的作用是在你当前文件夹下生成`.eslintrc`文件，但同时也会把eslint在你当前文件夹下重新安装一遍，并且如果你使用包的话，它还会要求必须要有`package.json`文件，总之会很麻烦。

但如果你是第一次使用的话，我建议你可以执行一下试试，它主要提供3种预安装包：Google标准、Airbnb标准和Standard标准。这3个标准里，Google就是Google公司的标准，Airbnb是Airbnb公司的标准，Standard就是一些前端工程师自定的标准。

目前来看，公认的最好的标准是Airbnb标准（互联网发展日新月异，永远是年轻人颠覆老年人，连Google都老了）。它对于ES6要求最严格，比如禁止使用`var`定义变量，必须使用`le`t或者`const`等等。既然采用最新标准，当然就让你的代码一次性向最高标准看齐，省得以后麻烦。

```bash
npm install eslint-config-airbnb -g
```

精彩的重头戏来了：看到漂亮的airbnb了吗？我们就里就是要安装Airbnb的标准了。注意`-g`，还是全局化安装。

```bash
npm install eslint-plugin-jsx-a11y -g
```

a11y是accessibility（无障碍环境）的缩写，从第一个字母a到最后一个字母y，中间一共是11个字母，所以就叫a11y了，类似于i18n表示internationalization（国际化）一样。JSX主要是React会用到，虽然我们的项目里可能并不会用React，但是这个Airbnb标准必须要用到它，所以必须安装。

```bash
npm install eslint-plugin-import -g
```

同上，Airbnb标准必需。

最后，编写我们自己的全局`.eslintrc`文件：

```bash
vi ~/.eslintrc.json
```

前面讲过了，为项目服务的`.eslintrc.json`文件是放在项目文件夹下的，全局的`.eslintrc.json`文件则放在当前用户的根目录下，类Unix系统的当前用户目录是`~`，而Windows系统的话则是类似于`C:\Windows\Users\Username`这样的地方。 把以下代码放入`.eslintrc.json`，就做好了你的全局ESLint配置文件。

```
{
    "extends": "airbnb",
    "installedESLint": true,
    "plugins": [
        "react"
    ]
}
```

在atom中打开你的某一个js文件，随便改几个字符看看效果吧，不出所料的话，应该会出现一堆红色的错误。如果没有出现，不是你的代码没有问题，而是你没有安装对。

Airbnb的缺省标准是每行的缩进字符是2个空格键，而我一般喜欢使用4个空格键作缩进，所以这里需要一点小小的定制。另外，我缺省会大量使用`jQuery`，不想让它总是报告什么`jQuery`这个变量未定义等错误。所以增加了几行，最终的`.eslintrc.json`如下：

```
{
    "extends": "airbnb",
    "installedESLint": true,
    "plugins": [
        "react"
    ],
    "env": {
        "jquery": true
    },
    "rules": {
        "indent": ["error", 4]
    }
}
```

这样你在任何项目中的js文件都会按照这同一套标准去检查。好了，现在可以开始改你的代码了，解决那一大堆红叉子吧，我相信一定不少。



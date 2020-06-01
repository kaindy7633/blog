## 一、搭建自动化的前端开发、调试和测试环境

我们先来看一个完整的项目实例，这是AngularJS官方为我们提供的Phonecat项目。在AngularJS的官方网站上有详细的指导，有兴趣的朋友可以去看看，地址：http://docs.angularjs.org/tutorial。

Phonecat项目源码托管在GitHub上，我们通过git来下载源码：

```bash
git clone --depth=14 https://github.com/angular/angular-phonecat.git
```

如果不能下载，请将命令中的https替换成ssh。

Phonecat项目运行在Nodejs上，请确保你的系统里有NodeJS环境，下载完成后我们进入Phonecat目录，运行下面的命令安装项目依赖。

```bash
npm install
```

运行该命令后，会在angular-phonecat项目路径下安装以下依赖包：

Bower . 包管理器

Http-Server . 轻量级Web服务器

Karma . 用于运行单元测试

Protractor . 用于运行端到端测试

完成上述操作之后，我们在angular-phonecat目录里执行下面的命令

```bash
npm start
```

PhoneCat运行后，可以在浏览器中打开 http://localhost:8000/app/index.html 来访问该Web应用

OK，现在我们可以通过protractor来自动运行测试，protractor是一款自动测试工具，它可以自动打开本机的浏览器，运行当前项目，模拟用户的选择、输入、滑动等操作来测试项目。

```bash
npm run protractor
```

通过这个项目我们可以看出自动化的构建和测试对前端来说尤其重要，但有时我们在想，我们到底需要一个什么样的前端开发环境呢？

1、首先我们需要一个款强大的代码编辑工具

2、一款易用的断点调试工具，尤其是在做JS调试时

3、一款拉风的版本管理工具，说到这里大家会想到的是就是Git，像SVN就不要了吧

4、一款代码合并和混淆工具

5、依赖管理工具

6、单元测试工具，以前我们的代码只能在浏览器环境里跑，所以每次的测试都离不开浏览器，过程也很繁琐，现在我们可以依赖NodeJS环境，来跑单元测试，这样就脱离的浏览器，做到自动的单元测试

7、集成测试工具，当我们完成整个项目的开发后，进入测试阶段，我们需要一款足够强大的全面的测试工具来帮我们完成整个项目的测试。

## 二、常用工具的介绍

1、代码编辑工具：

说到代码编辑工具，前端的朋友都会推荐Sublime了，是的，这是一款前端轻量级的强大的代码编辑工具，支持多种编程语言，其使用方法和插件的安装在百度上会找的很多。

代码编辑工具除了上面说到的Sublime之外呢，还有一款重量级的，Webstorm，这款工具比较大，但功能确实很强大，插件里首先就支持了AngularJS，如果你的电脑比较好，可以考虑使用这款工具。

2、断点调试工具：

chrome插件Batarang，我们可以在chrome的设置里安装这个断点调试工具

3、版本管理工具

在这个技术日新月异的年代，我们当然要用上比较高大上的工具，版本管理，自然我们会使用Git这样强大的分布式版本管理工具，具体使用方法，在我的博客里有比较详细的讲解。

4、开发和调试工具：

我们用的很多这样的工具都依赖一个环境，这就是NodeJS，所以首先我们需要在自己的电脑上安装并配置好NodeJS，其次就是npm，这是NodeJS的一个包管理器，使用npm我们可以解决很多依赖包的安装和配置工作。

5、代码合并和混淆工具：

Grunt，这款工具也是在NodeJS环境下安装的，我们可以使用npm来安装grunt，然后我们在项目中，使用npm来安装一些grunt会使用到的插件，基本的包括uglify（代码混淆）、concat（合并文件）、watch（监控文件变化）。

6、依赖管理工具

Bower，这款工具可以自动安装依赖的组建，包括对这些依赖的检测和版本之间兼容性的检测，关于Bower的具体使用可以参考百度。

7、轻量级Server

http-server，这是一款基于NodeJS的http-server工具，它可以把你电脑上的任意一个目录变成Web服务目录。我们可以通过npm把它安装到全局，然后在需要测试的项目目录里运行http-server即可。

8、单元测试runner

我们先来看下单元测试神器：Karma，它只是用来跑测试用例的容器，并没有提供一套用来编写测试用例的语法，所以我们需要另外一款工具来配合，那就是Jasmine，它提供了一套比较简洁的语法，来编写测试用例。

Jasmine的四个核心概念：分组、用例、期望、匹配，它们分别对应Jasmine的四个函数：

- `describe(string,function)` 这个函数表示分组，也就是一组测试用例

- `it(string,function)` 这个表示单个的测试用例

- `expect(expression)` 表示期望expression这个表达式会返回某个值或具有某种行为

- `to***(arg)` 这个表示匹配

下面我们通过一个例子来看下这个单元测试的过程。首先我们需要在测试目录里安装必要的模块，这里我们新建并进入karmaTets目录，在此目录下通过npm或cnpm安装`karma`、`karma-chrome-launcher`、`karma-coverage`和`karma-jasmine`，安装过程这里就不再赘述了。

上述的安装完成之后，我们在目录中新建src目录，在这里个目录里新建一个index.js文件，写上一个简单的函数，这个函数的作用是把传入的参数字符串进行反转，如abc返回cba，js代码如下：

```javascript
function reverse(name) {
    return name.split("").reverse().join("");
}
```

接下来我们再新建一个目录test，表示是测试目录，里面分别有两个目录，一个是unit，单元测试，一个是e2e，表示是集成测试目录。我们在unit目录新建一个测试文件，叫testCase.js，输入以下内容

```javascript
describe("A suite", function(){
	it("contains spec with an expectation", funtion(){
		console.log("This is msg from log...");
		expect(true).toBe(true);
	});
});

describe("A suite of basic functions", function(){
	it("reverse word", function(){
		expect("DCBA").toEqual(reverse("ABCD"));
		expect("damo").toEqual(reverse("omad"));
	});
});
```

然后我们在命令行下，执行`karma init`来初始化`karma`，并配置`karma.conf.js`文件，完成之后我们就可以使用`karma start`来启动测试，结果会在命令行打印出来。

9、专为AngularJS定制的测试工具 -- Protractor

Protractor是一款集成测试工具，专门为ANgularJS应用而设计的，它是基于WebDriverJS的，原理就是利用WebDriverJS，借助NodeJS直接调用浏览器的接口。我们可以通过下面的地址去了解这款工具

https://github.com/angular/protractor

https://code.google.com/p/selenium/wiki/WebDriverJs

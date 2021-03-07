## 一、`grunt` 简介

`grunt` 是什么？

`grunt` 是 Javascript 世界的构建工具，我们的项目在创建初期，会很小，但经过很多版本的迭代，越来越大，CSS 和 JS 都不太好管理了，这时我们需要工具来帮助我们管理，`grunt` 就是做这个的。它主要的工具就是编译、压缩、单元测试等，以减少我们的工作量。

`grunt` 已有很多可供我们使用的插件，帮助我们实现各种工业自动化，那如何使用 `grunt` 呢？

## 二、安装 grunt

`grunt` 和其插件都是通过 `npm` 安装的，所以，系统中必须安装 `npm` ，`npm` 是 NodeJS 的包管理器。

```bash
liuzhendeMacBook-Air:gruntTest liuzhen$ npm -v
2.14.12
```

安装 `grunt` 之前必须先将 `grunt-cli` 安装到全局中（我这里使用了 sudo 命令来安装）

```bash
liuzhendeMacBook-Air:gruntTest liuzhen$ sudo npm install -g grunt-cli
Password:
npm WARN deprecated lodash@2.4.2: lodash@<3.0.0 is no longer maintained. Upgrade to lodash@^4.0.0
/usr/local/bin/grunt -> /usr/local/lib/node_modules/grunt-cli/bin/grunt
grunt-cli@0.1.13 /usr/local/lib/node_modules/grunt-cli
├── resolve@0.3.1
├── nopt@1.0.10 (abbrev@1.0.7)
└── findup-sync@0.1.3 (lodash@2.4.2, glob@3.2.11)
liuzhendeMacBook-Air:gruntTest liuzhen$
```

安装好 `grunt-cli` 并不是安装了 `grunt` ，`grunt-cli` 的作用就是调用与 `grunfile` 同目录的 `grunt`，这样做的好处就是不同的项目里可以存放不同版本的 `grunt`。

## 三、`package.json`和 `gruntfile`

在项目中安装 `grunt` 之前，一般都需要两个文件，`package.json` 和 `gruntfile`

`package.json`：

此文件被 `npm` 用于存储项目的元数据，以便将此项目发布为 `npm` 模块进入项目目录，使用 `npm init` 命令来创建一个基本的 `package.json`，在创建完 `gruntfile` 之后，就可以在项目目录中使用

```bash
sudo npm install grunt --save-dev
```

来安装项目 `grunt`，也可以使用

```bash
sudo npm install grunt-contrib-jshint --save-dev
```

来安装 grunt 插件

`gruntfile`：

此文件可被定义为 `gruntfile.js` 或者 `gruntfile.coffee`，用来配置或定义任务（task），并加载 `grunt` 插件。

一般它可以由以下几个部分组成：

1. “wrapper”函数，它包含整个 grunt 配置信息

   ```javascript
   module.exports = function (grunt) {};
   ```

   在这个函数中初始化 `configuration` 对象

   ```
   grunt.initConfig({});
   ```

   接下来就可以从 `package.json` 中读取配置信息，并存入 pkg 属性中

   ```javascript
   pkg: grunt.file.readJSON("package.json");
   ```

   好了，到目前为止我们可以看到如下的代码：

   ```javascript
   module.exports = function (grunt) {
     grunt.initConfig({
       pkg: grunt.file.readJSON("package.json"),
     });
   };
   ```

   接下来，我们就可以为每个任务定义相应的配置

2. 项目与任务配置

   首先，我们来配置 `concat`，也就是文件合并任务，如下代码：

   ```javascript
   concat: {
     options: {
       //定义一个用于插入合并输出文件之间的字符
       separator: ';';
     },
     dist: {
       //将要被合并的文件
       src: ['src/**/*.js'],
       //合并后的JS文件的存放位置
       dest: 'dist/<%= pkg.name %>.js'
     }
   }
   ```

   接下来，我们配置 `uglify` 插件，也就是文件压缩

   ```javascript
   uglify: {
     options: {
       //此处定义的banner注释将插入到输出文件的顶部
       banner: '/* <%= pkg.name %> <%= grunt.template.today("dd-mm-yyyy") %> */\n'
     },
     dist: {
       files: {
         'dist/<%= pkg.name %>.min.js': ['<%= concat.dist.dest %>']
       }
     }
   }
   ```

   `QUnit` 插件用于测试文件，只要提供文件位置即可

   ```javascript
   qunit: {
     files: ['test/**/*.html']
   },
   ```

   `JShint` 插件用于检查 JS 代码的合法性，配置也很简单

   ```javascript
   jshint: {
     //定义需要检查的文件的位置
     files: ['gruntfile.js', 'src/**/*.js', 'test/**/*.js'],
     //JSHint默认配置
     options: {
       globals: {
         jQuery: true,
         console: true,
         module: true
       }
     }
   }
   ```

   最后，来配置 `watch` 插件，它是用来监视当前文件变化，如果有变化，则 grunt 会自动执行代码检查

   ```javascript
   watch: {
     files: ['<%= jshint.files %>'],
     tasks: ['jshint', 'qunit']
   }
   ```

3. 加载 grunt 插件和任务

```javascript
grunt.loadNpmTasks("grunt-contrib-uglify");
grunt.loadNpmTasks("grunt-contrib-jshint");
grunt.loadNpmTasks("grunt-contrib-qunit");
grunt.loadNpmTasks("grunt-contrib-watch");
grunt.loadNpmTasks("grunt-contrib-concat");
```

以上的 `grunt` 插件需要通过 npm 进行安装，如以下代码：

```bash
sudo npm install grunt-contrib-jshint --save-dev
```

4. 自定义任务

最后，我们需要设置 `task` ，重要的是 `default` 任务：

```javascript
//在命令行输入“grunt test”，test task就会被执行
grunt.registerTask("test", ["jshint", "qunit"]);
//在命令行上输入“grunt”，就会被执行的default task
grunt.resisterTask("default", ["jshint", "qunit", "concat", "uglify"]);
```

下面，是最终完成的 `gruntfile` 文件代码：

```javascript
module.exports = function (grunt) {
  //初始化
  grunt.initConfig({
    //读取配置信息
    pkg: grunt.file.readJSON("package.json"),
    //定义文件合并
    concat: {
      options: {
        separator: ";",
      },
      dist: {
        src: ["src/**/*.js"],
        dest: "dist/<%= pkg.name %>.js",
      },
    },
    //文件压缩
    uglify: {
      options: {
        banner:
          '/*! <%= pkg.name %> <%= grunt.template.today("dd-mm-yyyy") %> */\n',
      },
      dist: {
        files: {
          "dist/<%= pkg.name %>.min.js": ["<%= concat.dist.dest %>"],
        },
      },
    },
    //文件测试
    qunit: {
      files: ["test/**/*.html"],
    },
    //JS代码检查
    jshint: {
      files: ["gruntfile.js", "src/**/*.js", "test/**/*js"],
      options: {
        //这里覆盖JSHint默认配置选项
        globals: {
          jQuery: true,
          console: true,
          module: true,
          document: true,
        },
      },
    },
    //文件变化监听
    watch: {
      files: ["<%= jshint.files %>"],
      tasks: ["jshint", "qunit"],
    },
  });

  //加载插件
  grunt.loadNpmTasks("grunt-contrib-uglify");
  grunt.loadNpmTasks("grunt-contrib-jshint");
  grunt.loadNpmTasks("grunt-contrib-qunit");
  grunt.loadNpmTasks("grunt-contrib-watch");
  grunt.loadNpmTasks("grunt-contrib-concat");

  //设置任务
  grunt.registerTask("test", ["jshint", "qunit"]);
  grunt.registerTask("default", ["jshint", "qunit", "concat", "uglify"]);
};
```

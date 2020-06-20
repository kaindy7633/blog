<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [第一步，创建`package.json`](#%E7%AC%AC%E4%B8%80%E6%AD%A5%E5%88%9B%E5%BB%BApackagejson)
- [第二步，安装模块](#%E7%AC%AC%E4%BA%8C%E6%AD%A5%E5%AE%89%E8%A3%85%E6%A8%A1%E5%9D%97)
- [第三步，创建`gulpfile.js`文件](#%E7%AC%AC%E4%B8%89%E6%AD%A5%E5%88%9B%E5%BB%BAgulpfilejs%E6%96%87%E4%BB%B6)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

> 利用gulp搭建本地服务器，实现自动打开页面，自动刷新，模拟ajax操作

用到的模块如下：

- gulp
- gulp-webserver
- gulp-livereload

## 第一步，创建`package.json`

```bash
npm init
```

## 第二步，安装模块

```bash
npm install gulp --save-dev
npm install gulp-webserver --save-dev
npm install gulp-livereload --save-dev
```

## 第三步，创建`gulpfile.js`文件

```javascript
var url = require('url');
var fs = require('fs');
var path = require('path');

gulp = require('gulp');
livereload = require('gulp-livereload');
webserver = require('gulp-webserver');

//web服务器
gulp.task('webserver', function() {
  gulp.src('./www') // 服务器目录（./代表根目录）
  .pipe(webserver({ // 运行gulp-webserver
    port: 8000, //端口，默认8000
    livereload: true, // 启用LiveReload
    open: true, // 服务器启动时自动打开网页
    directoryListing: {
        enable: true,
        path: './www'
    },
    middleware: function(req, res, next) {
      //mock local data
      var urlObj = url.parse(req.url, true),
          method = req.method;


      if (!urlObj.pathname.match(/^\/api/)) { //不是api开头的数据，直接next
          next();
          return;
      }
      var mockDataFile = path.join(__dirname, urlObj.pathname) + ".js";
      //file exist or not
      fs.access(mockDataFile, fs.F_OK, function(err) {
        if (err) {
            res.setHeader('Content-Type', 'application/json');
            res.end(JSON.stringify({
                "status": "没有找到此文件",
                "notFound": mockDataFile
            }));
            return;
        }
        var data = fs.readFileSync(mockDataFile, 'utf-8');
        res.setHeader('Content-Type', 'application/json');
        res.end(data);
      });
      next();
    },
    proxies: []
  }));
});


// 默认任务
gulp.task('default', ['webserver']);
```
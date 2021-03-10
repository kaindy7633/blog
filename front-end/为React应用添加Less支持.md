<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Eject](#eject)
- [安装less](#%E5%AE%89%E8%A3%85less)
- [配置webpack.config.js](#%E9%85%8D%E7%BD%AEwebpackconfigjs)
- [第二种配置方式](#%E7%AC%AC%E4%BA%8C%E7%A7%8D%E9%85%8D%E7%BD%AE%E6%96%B9%E5%BC%8F)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

`create-react-app` 在 `webpack` 上封装了一层 `react-scripts`，一方面是可以使得不习惯 `eslint`，`babel` 和 `webpack` 的新手只需关注于组件的编写，另一方面是可以不断的更新和改进默认选项，而不会影响到业务代码。

可见，`react-scripts` 的作用就是通过将一些底层配置封装起来，从而向上屏蔽了众多细节，使得业务开发者只需关注业务代码的开发。

> create-react-app 脚手架中已经添加了 `sass-loader` 的支持，所以只需要安装 `node-sass` 插件即可，这里不再赘述，下面来看看如何添加`Less`支持

## Eject

首先，我们使用 `eject` 把配置文件暴露出来（**注意：这个过程是不可逆的**）

```bash
npm run eject
# 或者
yarn eject
```

## 安装less

`less` 和 `less-loader` 都要安装。`less` 是支持`less`语法的，`less-loader`是`webpack`使用来编译`less`的。

```bash
npm install less less-loader --save
```

## 配置webpack.config.js

修改`config/webpack.config.js`

新增`less`配置变量

```javascript
const cssRegex = /\.css$/;
const cssModuleRegex = /\.module\.css$/;
const sassRegex = /\.(scss|sass)$/;
const sassModuleRegex = /\.module\.(scss|sass)$/;
const lessRegex = /\.less$/;  // 新增less配置
const lessModuleRegex = /\.module\.less$/; // 新增less配置，这个其实不配置也行
```

增加`module`下面`rule`规则，可以`copy cssRegex`或者`sassRegex`的配置。

```json
{
    test: sassModuleRegex,
    use: getStyleLoaders({
            importLoaders: 2,
            sourceMap: isEnvProduction && shouldUseSourceMap,
            modules: true,
            getLocalIdent: getCSSModuleLocalIdent
        },
        "sass-loader"
    )
},
{
    test: lessRegex,
    exclude: lessModuleRegex,
    use: getStyleLoaders({
            importLoaders: 1,// 值是1
            modules: true, // 增加这个可以通过模块方式来访问css
            sourceMap: isEnvProduction && shouldUseSourceMap
        },
        "less-loader"
    ),
    sideEffects: true
},
// 这个测试删了也不影响
{
    test: lessModuleRegex,
    use: getStyleLoaders({
            importLoaders: 1,
            sourceMap: isEnvProduction && shouldUseSourceMap,
            modules: true,
            getLocalIdent: getCSSModuleLocalIdent
        },
        "less-loader"
    )
},
// "file" loader makes sure those assets get served by WebpackDevServer.
```

需要注意一下几个地方：

- `lessRegex`中`importLoaders`的值为`1`

	当然这个是`2`也能使用，但是它的值是根据`lessRegex`变量后面正则中匹配的`loader`数来决定的，比如`const cssRegex = /\.css$/`只是处理`css`一种类型的文件，那应该就是`1`；`const sassRegex = /\.(scss|sass)$/;`对应的是`scss`和`sass`两种类型，那就应该是`2`.

- `lessRegex`的`use`中增加`modules`配置

	`modules`可以不设置，不设置的话，`less`只能通过字符串名的方式使用，比如定义了一个`.title`,引用时`import './index.less'`，使用时：`<div className="title"></div>`

	如果需要通过模块的方式调用，则需要把`modules`设置成`true`，就可以通过`styles.title`方式使用了。`import styles from './index.less'`,使用`<div className={styles.title}></div>`

## 第二种配置方式

可以不增加新的变量，把`css`的配置包含`less`

```javascript
const cssRegex = /\.(css|less)$/; //增加less
const cssModuleRegex = /\.module\.(css|less)$/;

{
    test: cssRegex,
    exclude: cssModuleRegex,
    use: getStyleLoaders({
            importLoaders: 2,// 改成2
            modules: true,//使用模块方式访问样式
            sourceMap: isEnvProduction && shouldUseSourceMap
        },
        "less-loader" //增加loader
    ),
    // Don't consider CSS imports dead code even if the
    // containing package claims to have no side effects.
    // Remove this when webpack adds a warning or an error for this.
    // See https://github.com/webpack/webpack/issues/6571
    sideEffects: true
}
```

最后，当安装完成后，启用`CSS Module`，你会发现`TS`报错了，原因是它找不到`Less`的声明文件，这时，如果在根目录下有一个名叫：`react-app-env.d.ts`的声明文件，就可以打开，你会发现，所有图片和样式文件类型的声明都在这里，OK，添加一个`Less`的声明即可：

```typescript
...

declare module '*.module.css' {
  const classes: { readonly [key: string]: string };
  export default classes;
}

declare module '*.module.scss' {
  const classes: { readonly [key: string]: string };
  export default classes;
}

declare module '*.module.sass' {
  const classes: { readonly [key: string]: string };
  export default classes;
}

// 把Less的声明添加到这里
declare module '*.module.less' {
  const classes: { readonly [key: string]: string };
  export default classes;
}
```


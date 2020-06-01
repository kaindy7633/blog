# 团队开发中ESLint的使用及其相关规范介绍

> 在目前的团队开发中，前端团队的代码规范问题是很让人头痛的。如果让你去看一个你不熟悉的代码风格，其实是非常耗时且效率低下的事。那有什么方法可以规范团队中每个成员的代码书写风格呢？答案是肯定的，使用ESLint可以很方便的，或者说可以强制性的规范每个人的代码书写风格，在中小团队中，我们可以不去自定义风格，而去使用ESLint官方推荐的代码风格(Standard)，这篇博文简单的介绍了如何使用ESLint去做这些事，甚至我们可以通过一些方法在Git中加入钩子，强制不规范的代码不能提交。

在这里，我在Vue代码中做一些例子的示范，其他的如React，可参照网上其他的教程做相应的修改，或参看官方推荐。

在我们的项目中加入ESLint，好处不言而喻，首先可以防止一些低级的错误，导致在编译时出现一些莫名其妙的问题，其次就是在团队协作时，能保持所有成员的开发风格一致，这样在参看别人的代码时就显得非常的方便，从而提高效率。

## ESLint的安装

首先，我们应该在自己的项目中安装ESLint及其相关的依赖包，ESLint是遵循一定的规则的，在中小团队中，就没有必要去自定义了，可以使用官方的 `Standard` 标准，当然，其配置文件中也可以对部分规则进行修改，以满足团队的特殊需求.

下面来看看需要安装的包：

- `eslint`
- `eslint-config-standard`
- `eslint-plugin-standard`
- `eslint-plugin-promise`
- `eslint-plugin-import`
- `eslint-plugin-node`

```bash
npm i -D eslint eslint-config-standard eslint-plugin-standard eslint-plugin-promise eslint-plugin-import eslint-plugin-node
```

安装完成后，在项目根目录下创建文件 `.eslintrc`

这是ESLint的配置文件，它是一个JSON格式的文件

```js
{
  "extends": "standard"
}
```

这里有个问题，因为我们的JS代码都写在了Vue中，ESLint是无法识别Vue文件的，所以这里还需要安装一个工具包 `eslint-plugin-html`

```bash
npm i -D eslint-plugin-html
```

安装完成后，在配置文件 `.eslintrc` 中加入 `plugins` 选项

```js
{
  "extends": "standard",
  "plugins": [
    "html"
  ]
}
```

## 如何使用

上述的安装和配置完成之后，我们就可以在 `package.json` 中增加 `script` 选项来使用ESLint了。

```js
{
  "scripts": {
    "lint": "eslint --ext .js --ext .jsx --ext .vue src/"
  }
}
```

这里解释一下上面的 `lint` 命令，运行的是 `npm run lint` 来检查当前开发目录 `src` 中所有的需要检查的文件代码。 `--ext` 参数指定我们需要检查哪些后缀名的文件，最后的 `src/` 表示要检查那个目录里的文件。

如果当项目一开始没有使用ESLint来规范代码书写的话，这时候会在控制台打印出很多错误，如果一条一条的去修复很麻烦，很幸运的是，ESLint为我们提供了修复的命令：

```js
{
  "scripts": {
    "lint": "eslint --ext .js --ext .jsx --ext .vue src/",
    "lint-fix": "eslint --fix --ext .js --ext .jsx --ext .vue src/"
  }
}
```

上面在 `scripts` 中加入了另外一条命令 `lint-fix`， 这条命令里增加了一个 `--fix` 的参数，表示运行此命令，如果遇到错误就自动修复。

## 如何即时发现错误

通过上面的操作，我们可以发现并修复我们代码中不符合ESLint规范的错误，但这种方法并不好，因为这样团队成员就无法养成规范书写的习惯，每次都要去重新修复一次，所以我们希望的是在书写代码的时候能即时发现错误并提示修改。

要做到这一点，我们还需要安装两个包，`eslint-loader` 和 `babel-eslint`

```bash
npm i -D eslint-loader babel-eslint
```

安装完成后，首先要去修改 `.eslintrc` 这个配置文件，增加 `parser` 选项

```js
{
  "extends": "standard",
  "plugins": [
    "html"
  ],
  "parser": "babel-eslint"
}
```

那为什么我们需要增加这个选项呢？ 因为我们的项目都是经过Webpack进行打包的，代码是通过 `babel` 进行处理的，在这个过程中，`babel`可能会与ESLint有所冲突，所以使用这个方法来解决这些问题。

然后，我们就可以修改我们的 `Webpack` 的配置文件

```js
{
  module: {
    rules: [
      {
        test: /\.(vue|js|jsx)$/,
        loader: 'eslint-loader',
        exclude: /node_modules/,
        enforce: 'pre'
      }
    ]
  }
}
```

上面的配置中，需要特别注意是最后一项 `enforce`， 为什么要配置它呢？ 是因为在 `rules` 中会有其他的配置选项，比如单独对 `vue` 文件进行处理的 `vue-loader`, 所以这里需要指定，预先对vue文件使用 `eslint-loader` 进行代码风格检查，如果这里都过不了，就无需进行下去，直接报错并提示。

通过上述的安装和配置，我们就可以在实际的代码开发中，当发现有不符合ESLint规则的时候就会报错。这样，团队成员都会按照既定的风格进行代码书写，以达到统一开发的目的。

## 关于 editorconfig 的设置

在编辑器方面，我们还可以配置 `editorconfig` 来进一步规范代码书写，首先我们的编辑器要安装相应的插件，在vscode中，直接搜索并安装 `EditorConfig for VS Code`

然后在项目根目录下新建 `editorconfig` 文件，并写入配置项

```
root = true

[*]
charset = utf-8
end_of_line = lf
indent_size = 2
indent_style = space
insert_final_newline = true
trim_trailing_whitespace = true
```

## 进一步的优化

通过上面的配置，我们基本上可以做到统一团队的代码开发风格了，那还有没有更进一步的优化呢？ 是有的。 我们还可以在 Git 中使用钩子，在成员进行代码提交时对代码风格进行检查，如果不符合则禁止其提交代码。

首先我们需要安装一个包 `husky`

```bash
npm i -D husky
```

**注意**：在安装之前，我们要使用 `git init`初始化本地仓库，因为在安装完这个包之后，会在本地 git 目录下生成一个hook，如果没有 git 目录，就会初始化失败。这个hook会读取我们的 `package.json` 文件里的内容。

随后，我们就可以在 `scripts` 里添加一个选项 `precommit`，内容就是进行 ESLint 代码检查

```js
{
  "scripts": {
    "lint": "eslint --ext .js --ext .jsx --ext .vue src/",
    "lint-fix": "eslint --fix --ext .js --ext .jsx --ext .vue src/",
    "precommit": "npm run lint"
  }
}
```

每次当我们进行代码提交时，这个hook都会自动调用 `precommit` ，进行代码检查，如果有错误，则停止后面的提交，并显示错误.


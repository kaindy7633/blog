> 对于`Typescript`项目的编码规范而言，主要有两种选择`ESLint`和`TSLint`。`ESLint`不仅能规范js代码，通过配置解析器，也能规范TS代码。此外由于性能问题，`TypeScript` 官方决定全面采用`ESLint`，甚至把仓库作为测试平台，而 `ESLint` 的 `TypeScript` 解析器也成为独立项目，专注解决双方兼容性问题。

- 用`ESLint`来规范`Typescript`代码

- 用`ESLint`来规范`React`代码

- 结合`Prettier`和`ESLint`来规范代码

- 在`VSCode`中使用`ESLint`

- `husky`和`lint-staged`构建代码工作流

- `gitlab`的 CI/CD 来规范代码

## 用ESLint来规范Typescript代码

安装依赖：

```bash
npm i -d eslint @typescript-eslint/parser @typescript-eslint/eslint-plugin
```

- `eslint`: `ESLint`的核心代码

- `@typescript-eslint/parser`：`ESLint`的解析器，用于解析`typescript`，从而检查和规范`Typescript`代码

- `@typescript-eslint/eslint-plugin`：这是一个`ESLint`插件，包含了各类定义好的检测`Typescript`代码的规范

在根目录下新建`.eslintrc.js`文件，该文件中定义了`ESLint`的基础配置，一个最为简单的配置如下所示：

```javascript
module.exports = {

    parser:  '@typescript-eslint/parser',                    //定义ESLint的解析器
    extends: ['plugin:@typescript-eslint/recommended'],      //定义文件继承的子规范
    plugins: ['@typescript-eslint'],                         //定义了该eslint文件所依赖的插件
    env:{                                                    //指定代码的运行环境
        browser: true,
        node: true,
    }
}
```

- 在ts项目中必须执行解析器为`@typescript-eslint/parser`，才能正确的检测和规范TS代码

- `env`环境变量配置，形如`console`属性只有在`browser`环境下才会存在，如果没有设置支持`browser`,那么可能报`console is undefined`的错误。

## 用ESLint来规范React代码

如果在你的TS项目中同时使用了`React`，那么为了检测和规范`React`代码的书写必须安装插件`eslint-plugin-react`，然后增加配置：

```javascript
module.exports = {

    parser:  '@typescript-eslint/parser',
    extends: [
    'plugin:react/recommended'  
    'plugin:@typescript-eslint/recommended'
    ],                              //使用推荐的React代码检测规范
    plugins: ['@typescript-eslint'],
    env:{
        browser: true,
        node: true,
    },
    settings: {             //自动发现React的版本，从而进行规范react代码
        "react": {
            "pragma": "React",
            "version": "detect"
        }
    },
    parserOptions: {        //指定ESLint可以解析JSX语法
        "ecmaVersion": 2019,
        "sourceType": 'module',
        "ecmaFeatures":{
            jsx:true
        }
    }
    rules: {
		// 自定义的React规范
    }
}
```

在`Rules`中可以自定义你的`React`代码编码规范。

## 结合Prettier和ESLint来规范代码

`Prettier`中文的意思是漂亮的、美丽的，是一个流行的代码格式化的工具，我们来看如何结合`ESLint`来使用。首先我们需要安装三个依赖：

```bash
npm i -g prettier eslint-config-prettier eslint-plugin-prettier
```

其中：

- `prettier`：`prettier`插件的核心代码

- `eslint-config-prettier`：解决`ESLint`中的样式规范和`prettie`r中样式规范的冲突，以`prettier`的样式规范为准，使`ESLint`中的样式规范自动失效

- `eslint-plugin-prettier`：将`prettier`作为`ESLint`规范来使用

然后在项目的根目录下创建`.prettierrc.js`文件：

```javascript
module.exports =  {
    "printWidth": 120,
    "semi": false,
    "singleQuote": true,
    "trailingComma": "all",
    "bracketSpacing": false,
    "jsxBracketSameLine": true,
    "arrowParens": "avoid",
    "insertPragma": true,
    "tabWidth": 4,
    "useTabs": false
  };
```

接着修改`.eslintrc.js`文件，引入`prettier`：

```javascript
module.exports = {
    parser:  '@typescript-eslint/parser',
    extends:[
    'prettier/@typescript-eslint',
    'plugin:prettier/recommended'
    ],
    settings: {
        "react": {
            "pragma": "React",
            "version": "detect"
        }
    },
    parserOptions: {
        "ecmaVersion": 2019,
        "sourceType": 'module',
        "ecmaFeatures":{
            jsx:true
        }
    },
    env:{
        browser: true,
        node: true,
    }
```

上述新增的`extends`的配置中：

- `prettier/@typescript-eslint`：使得`@typescript-eslint`中的样式规范失效，遵循`prettier`中的样式规范

- `plugin:prettier/recommended`：使用`prettier`中的样式规范，且如果使得`ESLint`会检测`prettier`的格式问题，同样将格式问题以`error`的形式抛出

## 在VSCode中集成ESLint配置

为了开发方便我们可以在`VSCode`中集成`ESLint`的配置，使得代码在保存或者代码变动的时候自动进行`ESLint`的`fix`过程。

首先需要安装`VSCode`的`ESLint`插件，安装插件完毕后，在`settings.json`文件中修改其配置文件为：

```javascript
{
       "eslint.enable": true,  //是否开启vscode的eslint
       "eslint.autoFixOnSave": true, //是否在保存的时候自动fix eslint
       "eslint.options": {    //指定vscode的eslint所处理的文件的后缀
           "extensions": [
               ".js",
               ".vue",
               ".ts",
               ".tsx"
           ]
       },
       "eslint.validate": [     //确定校验准则
           "javascript",
           "javascriptreact",
           {
               "language": "html",
               "autoFix": true
           },
           {
               "language": "vue",
               "autoFix": true
           },
           {
               "language": "typescript",
               "autoFix": true
           },
           {
               "language": "typescriptreact",
               "autoFix": true
           }
       ]
}
```

主要注意的有两点：

- `eslint.options`中可以通过`configFile`属性来执行`eslint`规范的绝对路径，默认会向上查找，在根路径中指定

- `eslint.validate`中必须通过`{ language: XXX }`的形式来指定`typescript`和`typescriptreact`

## husky和lint-staged构建代码工作流

首先来看`husky`,`Husky` 能够帮你阻挡住不好的代码提交和推送,首先我们在`package.json`中定义如下的`script`:

```json
"scripts": {
   "lint": "eslint src --fix --ext .ts,.tsx "
}
```
接着在`package.json`定义`husky`的配置：

```json
 "husky": {
   "hooks": {
      "pre-commit": "npm run lint"
    }
}
```

我们在`git`的`hook`的阶段来执行相应的命令，比如上述的例子是在`pre-commit`这个`hook`也就是在提交之前进行`lint`的检测。

接着来看`lint-staged`，上述我们通过在`husky`的`pre-comit`这个`hook`中执行一个`npm`命令来做`lint`校验。除了定义个`npm lint`命令外，我们也可以直接通过使用`lint-staged`，来在提交前检测代码的规范。

使用`lint-staged`来规范代码的方式如下，我们修改`package.json`文件为：

```json
{
  "husky": {
    "hooks": {
      "pre-commit": "lint-staged"
    }
  },
  "lint-staged": {
    "*.{.ts,.tsx}": [
      "eslint",
      "git add"
    ]
  }
}
```

同样在`git commit`的时候会做`lint`的检测。

## gitlab的CI/CD来规范代码

仅仅通过`git`的`hook`来执行代码的规范检测有一个问题，我们可以在`git commit`的时候通过`--no-verify`来跳过代码的规范检测。但是某些情况下，我们对于某一个重要分支，该分支上的代码必须完整通过代码的规范检测，此时我们可以使用`gitlab`的`CI/CD`。

同样在`package.json`中增加一个`lint`的`npm` 命令：

```json
"scripts": {
	"lint": "eslint src --fix --ext .ts,.tsx "
}
```

然后在根目录增加`.gitlab-ci.yml`文件，该文件中的配置为：

```json
stages:
  - lint

before_script:
  - git fetch --all
  - npm install 

lint:
  stage: lint
  script:
    - npm run lint
  only
    - 特定分支1
    - 特定分支2
```


然后配置相应的`gitlab runner`，这里不具体详描，最后的结果就是在我们指定的分支上的提交或者`merge`都会进行所配置的命令检测。这样保证了特定分支不受`git commit`跳过操作`--no-verify`的影响。
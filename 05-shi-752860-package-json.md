# 使用\`package.json\`

管理局部安装最好的方式就是去创建一个`package.json`（译者注：在里面进行版本管理的依赖）

一个`package.json`文件会给你提供一些不错的东西：

1. 它提供一个你的项目依赖了哪些模块的文档
2. 它允许你通过[语义化版本规则](https://docs.npmjs.com/getting-started/semantic-versioning)来指定你的项目中依赖的模块的特定版本。
3. 让你可以创建可复用的代码。这是一种非常方便与其他开发者共享代码的方式。

## 要求

作为最小化要求，一个`package.json`必须有以下几个属性：

* "name"
  * 全小写
  * 一个单词，不能有空格
  * 破折号（-）和下划线（\_）可以。
* "version"
  * 以`x.x.x`的形式
  * 遵守[语义化规范](https://docs.npmjs.com/getting-started/semantic-versioning)（译者注：无法做到强制，有些包确实就没有遵守，所以给版本依赖带来一些问题，比如依赖的一个包修改了一个api，但是只修改了小版本号。）

举例：

```
{
    "name": "my-awesome-package",
    "version": "1.0.0"
}
```

## 创建package.json

创建一个`package.json`文件可以通过以下方式：

```
> npm init
```

这样做会初始化一系列命令行交互问题，并且会你运行这个命令的目录创建一个包含了根据你回答信息生成`package.json`文件。

### --yes 初始化命令

那些扩展的命令行问题并不是为所有人准备的，并且如果你经常使用`package.json`的话，你可以加速这个过程。

你可以通过在运行`npm init`的时候，增加一个`--yes`或者`-y`标示，来得到一个默认配置的`package.json`。

```
> npm init --yes
```

这将不会询问你任何问题，而是会从当前目录信息中抓取一些，产生一个默认的`package.json`。

```
> npm init -yes
```

写入到`/home/ag_dubs/my_package/package.json`（译者注：注意这个目录结构）的内容会是以下样子：

```json
{
  "name": "my_package",
  "description": "",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "repository": {
    "type": "git",
    "url": "https://github.com/ashleygwilliams/my_package.git"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "bugs": {
    "url": "https://github.com/ashleygwilliams/my_package/issues"
  },
  "homepage": "https://github.com/ashleygwilliams/my_package"
}
```

* name：当前目录的名字
* version：永远是`1.0.0`
* description：从当前目录的`readme`文件中提取，如果没有会是一个空字符串`""`
* main：永远是`index.js`
* scripts：默认创建一个空的`test`脚本命令
* keywords：空
* author：空
* license：[ISC](https://opensource.org/licenses/ISC)
* bugs：信息提取自当前目录，如果存在
* homepage：信息提取自当前目录，如果存在

你同样也可以给`init`命令设置一些配置选项，几个比较有用：

```
> npm set init.author.email "sinoon1218@gmail.com"
> npm set init.author.name "sinoon"
> npm set init.license "MIT"
```

### 提示：

如果在`package.json`中没有`description`这一属性（译者注：指在发布时），`npm`会使用`README.md`或者`README`的第一行来替代。`description`帮助人们在`npm`中搜索到你的包，所以一个自定义的`description`是非常有用的，它可以让你的包更容易被找到。

## 自定义init过程

同样可以完全自定义创建的信息以及在创建过程中的问题。通过创建一个`.npm-init.js`来完成。默认情况下，`npm`会检查你的`home`目录下有没有这个文件，`~/.npm-init.js`

一个简单的`.npm-init.js`文件看起来是这个样子的：

```js
module.exports = {
    customField: 'Custom Field',
    otherCustomField: 'This field is really cool'
}
```

在设置好这个文件之后，运行`npm init`，会产生一个下面内容的package.json文件：

```json
{
  customField: 'Custom Field',
  otherCustomField: 'This field is really cool'
}
```

同样，你也可以自定义问题，通过prompt函数：

```js
modele.exports = prompt("你最喜欢的av女友是谁？","我喜欢苍老师");
```

了解更多进一步自定义的方法，请看这里**占位符**。

## 指定依赖的包

为了指定你项目中依赖的包，你需要在package.json中列出你需要的那些包。这里有两种类型的包你可以列出：

* "dependencies"：列在这里的包，是用来在生产环境中依赖的。
* "devDependencies"：列在这里的包，仅仅为了开发和测试中需要用到。

## 手动编辑你的package.json

你可以手动编辑你的package.json文件。你需要创建一个叫做`dependencise`属性，它是一个对象（译者注：指`json`中的一种数据类型）。这个对象用来保存你将要用到的包，这里需要指出的是，它是通过[`semver`](https://docs.npmjs.com/getting-started/semantic-versioning)\(语义化版本\)表达式来指定符合你项目依赖的模块版本的。

如果你需要依赖的包，只是在开发或者测试的时候才会用到，那么你可以用上面的方式来指定依赖以及版本，唯一不同的是，存在一个叫`devDependencies`属性中。

举个栗子：下面的项目用到了一个主版本号为1，并且名字叫mydep的包，在生产环境使用，然后在开发环境依赖了一个主版本号为3，名字叫`mytext_framework`的包：

```json
{
  "name": "my_package",
  "version": "1.0.0",
  "dependencies": {
    "my_dep": "^1.0.0"
  },
  "devDependencies" : {
    "my_test_framework": "^3.1.0"
  }
}
```

### --save 和 --save-dev install标示

更简单（也更流弊）的一个增加依赖到`package.json` 的方式是通过命令行来操作的时候，在`npm install`后面增加`--save`或者`--save-dev`，选择哪个取决于你希望它是哪种依赖了。

在`package.json`中的`dependencies`增加一条依赖：

`npm install <package_name> --save`

在`devDependencies`增加哦一条依赖：

`npm install  <package_name> --save-dev`

### 管理版本依赖

就像我们经常说的那样，`npm`使用语义化版本或者叫`SemVer`，来进行版本管理和版本的范围限制。

如果你有一个package.json在目录下，你可以运行npm install，之后，`npm`会依据在`package.json`文件中列出的依赖，依据semver rules（语义化规则）来下载最新的版本。

学习关于更多语义化版本的内容，请看我们的**跳转**
















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

在设置好这个文件只有，运行`npm init`，


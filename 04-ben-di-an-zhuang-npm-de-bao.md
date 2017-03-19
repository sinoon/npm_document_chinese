# 本地安装npm包

有两种方式来安装`npm`的包：局部（译者注：当前目录） 或者 全局（译者注：全局目录）。选择何种方式安装，是基于你想如何使用它。

如果你想在你自己的模块中依赖包，就像`Node.js`中使用`require`，那么你会想使用局部安装，这也正是`npm install`的默认方式。另一方面，如果你想把这个包当做命令行工具来使用，就像`grunt`的CLI（command line interface），那么你应该全局安装它。

了解更多关于`install` 命令的行为，请看这里`CLI doc page`。

## 安装

一个包可以通过以下方式来安装：

```
npm install <包名>
```

它将会在当前目录下创建一个`node_modules`目录（如果不存在的话），并且会下载模块到这个目录。

### 测试安装

为了确认npm install是否运行成功，确认nodemodules目录存在，并且目录下包含了你下载的包的名字。你可以通过ls nodemodules的方式来确认（在Unix系统上），比如，OSX，Debian，或者在windows上运行dir node\_modules。

### 举例

安装一个叫lodash的包。通过列出node\_modeles里面所有的文件夹看是不是有叫loadsh的，来判断是否安装成功。

> npm install lodash  
> ls node\_modules        \# 在Windows系统上使用 `dir`

```
#=> lodash
```

## 什么版本的包被安装了呢？

如果没有存在`package.json`文件在当前目录下，最新的版本会被安装。

如果存在`package.json`文件，那么在`package.json`中按照[语义化规则](https://docs.npmjs.com/getting-started/semantic-versioning)的最新版本会被安装。

## 使用被安装的包

一旦一个包被安装在了node\_modules中，你就可以在你的代码中使用它了。举例来说，如果你正在开发一个Node.js模块，你可以require它。

### 举例：

创建一个叫`index.js`的文件，里面有如下代码：

```javascript
// index.js
var lodash = require('lodash');

var output = lodash.without([1,2,3], 1);
console.log(output);
```

使用`node index.js`来运行这段代码，它将输出`[2, 3]`。

如果你没有正确的安装`lodash`，那么你将会收到以下错误：

```
module.js:340
    throw err;
    
Error: Cannot find module 'lodash'
```

要修复它的话，运行`npm install lodash`在`index.js`的同级目录下。




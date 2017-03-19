# 02 - 安装Node.js，升级npm

## 安装Node.js

如果你使用的是`OS X` 或者 `Windows`，那么最好的安装Node.js方式是从[Node.js下载页面](https://nodejs.org/en/download/)下载对应的安装包。如果你使用的`Linux`系统，你可以使用系统自带的安装工具\(yun,apt-get等\)，或者你可以去检查下[Node源码分发平台](https://github.com/nodesource/distributions) s，看看那里有没有最近可以运行在你当前操作系统上的版本。

测试是否安装成功：node -v在命令行运行，会显示当前的node版本。这个提示的版本信息应该大于`v0.10.32`。

## 更新npm

`Node`的安装，都会携带好一个`npm` 版本（译者注：这个`npm`的版本一般取决于当时`node`发布时候的`npm`版本。）然后，`npm`的发布速度一般都比`node`的发布速度要快，所以你安装好`node`之后，`npm`的版本通常都是落后的，因此你会想确认安装`npm`的最新版本。

```
npm install npm@latest -g
```

测试是否安装成功：在命令行运行`npm -v`。显示的版本信息应该大于`2.1.8`。



## 手动安装

针对进阶用户。

`npm`模块可以从以下地址进行下载

```
https://registry.npmjs.org/npm/-/npm-{VERSION}.tgz
```






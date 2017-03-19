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

为了确认`npm install`是否运行成功，确认`node_modules`目录存在，并且目录下包含了你下载的包的名字。你可以通过`ls node_modules`的方式来确认（在Unix系统上），比如，`OSX`，`Debian`，或者\`dir node\


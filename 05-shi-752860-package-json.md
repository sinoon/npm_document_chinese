# 使用\`package.json\`

管理局部安装最好的方式就是去创建一个`package.json`（译者注：在里面进行版本管理的依赖）

一个package.json文件会给你提供一些不错的东西：

1. 它提供一个你的项目依赖了哪些模块的文档
2. 它允许你通过[语义化版本规则](https://docs.npmjs.com/getting-started/semantic-versioning)来指定你的项目中依赖的模块的特定版本。
3. 让你可以创建可复用的代码。这是一种非常方便与其他开发者共享代码的方式。

## 要求

作为最小化要求，一个package.json必须有以下几个属性：

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






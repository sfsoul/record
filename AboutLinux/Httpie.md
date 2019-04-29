[TOC]

### Httpie简介

[HTTPie官网](https://github.com/jakubroztocil/httpie#usage)

`HTTPie`是一个 HTTP 命令行客户端。

`HTTPie`工具是现代的 HTTP 命令行客户端，它能通过命令行界面与 Web 服务进行交互。它提供一个简单的`http`命令，允许使用简单而自然的语法发送任意的 HTTP 请求，并会显示彩色的输出。

`HTTPie`能用于测试、调试以及与 HTTP 服务器交互。

### 使用HTTPie请求URL

`HTTPie`的基本用法就是将网站的URL作为参数。

```
http https://juejin.im/timeline
```

### 使用HTTPie下载文件

**使用带`--download`参数的HTTPie命令下载文件。类似于`wget`命令。**

```
http --down http://wx2.sinaimg.cn/mw690/b05fa026gy1g0ogg6vh8sj21400u07cq.jpg
```

**使用`-o`参数用不同的名称保存输出文件。**

```
http --down http://wx2.sinaimg.cn/mw690/b05fa026gy1g0ogg6vh8sj21400u07cq.jpg -o drink.png
```

### 使用HTTPie恢复部分下载

**使用带`-c`参数的HTTPie继续下载。**

### 使用HTTPie上传文件

**使用带有`<`的HTTPie命令上传文件**

```
http https://transfer.sh < avatar.jpg
```

**使用带有重定向符号`>`下载文件**

```
http https://tvax2.sinaimg.cn/crop.597.0.1066.1066.180/b05fa026ly8fp7mgs05gsj21hc0u0gty.jpg > /Users/jing_zhang/Desktop/avatar.png
```

### 发送一个HTTP GET请求

**可以在请求中发送HTTP GET方法。GET方法会使用给定的URI，从给定服务器检索信息。**

```
http GET https://juejin.im/timeline
```

### 发送一个HTTP POST请求

```

```

### 提交表单

### 参考文章

- [HTTPie官方文档中文翻译版](https://keelii.com/2018/09/03/HTTPie/)
- []()


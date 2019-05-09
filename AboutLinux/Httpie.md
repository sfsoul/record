[TOC]

### Httpie简介

[HTTPie官网](https://github.com/jakubroztocil/httpie#usage)

`HTTPie`是一个 HTTP 命令行客户端。

`HTTPie`工具是现代的 HTTP 命令行客户端，它能通过命令行界面与 Web 服务进行交互。它提供一个简单的`http`命令，允许使用简单而自然的语法发送任意的 HTTP 请求，并会显示彩色的输出。

`HTTPie`能用于测试、调试以及与 HTTP 服务器交互。

### 使用

最简单的使用：

```
http httpie.org
```

语法：

```
http [flags] [METHOD] URL [ITEM [ITEM]]
```

### 使用HTTPie请求URL

`HTTPie`的基本用法就是将网站的URL作为参数。

```
http https://juejin.im/timeline
```

**使用一个输出参数`-v`来查看请求信息（默认不显示请求信息）：**

```
http -v https://juejin.im/timeline
```

### 使用HTTPie下载文件

**使用`--download, -d`参数的HTTPie命令下载文件。类似于`wget`命令。**

```
http --download http://wx2.sinaimg.cn/mw690/b05fa026gy1g0ogg6vh8sj21400u07cq.jpg
```

```
// 显示下载的过程
HTTP/1.1 200 OK
Access-Control-Allow-Origin:
Age: 0
Cache-Control: max-age=7776000
Connection: keep-alive
Content-Length: 57997
Content-Type: image/jpeg
Date: Mon, 29 Apr 2019 01:17:13 GMT
Expires: Sun, 28 Jul 2019 01:17:13 GMT
LB_HEADER: wbtngx.34.wbg1.shx.lb.sinanode.com
Last-Modified: Mon, 08 Jul 2013 18:06:40 GMT
Pragma: public
Server: nginx
Via: http/1.1 gwbn.guangzhou.ha2ts4.27 (ApacheTrafficServer/6.2.1 [cMsSfW])
X-Cache: MISS.27
X-Request-ID: g2.114-1556500633.615000-2671994505
X-Via-CDN: f=edge,s=gwbn.guangzhou.ha2ts4.13.nb.sinaedge.com,c=219.133.170.204;f=Edge,s=gwbn.guangzhou.ha2ts4.27,c=124.42.245.13
X-Via-Edge: 1556500633603ccaa85db1ef52a7c1b491caf
x-debug-hit: sto(244638,0.121)

Downloading 56.64 kB to "b05fa026gy1g0ogg6vh8sj21400u07cq.jpg"
Done. 56.64 kB in 0.07850s (721.51 kB/s)
```



**使用`--output， -o`参数用不同的名称保存输出文件。**

```
http -do drink.png http://wx2.sinaimg.cn/mw690/b05fa026gy1g0ogg6vh8sj21400u07cq.jpg
```

### 下载文件的文件名

**如果没有指定参数`--output, -o`,文件名将由`Content-Disposition`决定，或者通过URL及其`Content-Type`，如果名字已占用，HTTPie会添加唯一后缀。**

### 使用HTTPie恢复部分下载

**如果指定`--output, -o`，可以使用`--continue, -c`恢复部分下载。不过仅当服务器支持`Range`请求而且响应返回`206 Partial Content`才可以，若服务器不支持这个功能，那就只会下载整个文件。**

```
http -dco file.zip example.org/file
```

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
- [HTTPie:替代Curl和Wget的现代HTTP命令行客户端](https://juejin.im/post/5cbdd241e51d456e4f4d2a1c)
- []()


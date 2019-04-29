[TOC]

### 介绍

`curl`命令：是一个利用URL规则在命令行下工作的文件传输工具。它支持文件的上传和下载，所以是综合传输工具，按照传统习惯称curl为下载工具。curl支持包括HTTP、HTTPS、ftp等众多协议，还支持POST、cookies、认证、从指定偏移处下载部分文件、用户代理字符串、限速、文件大小、进度条等特征。

### 查看网页源码

`curl 网站地址`

### 保存网页

`curl -o [文件名] 网站地址`

### 自动跳转(针对301永久重定向的网站)

`curl -L 网站地址`

### 显示头信息

`curl -i 网站地址`：显示 **http response**的头信息，连同网页代码一起。

`curl -I 网站地址`：只显示**http response**的头信息。

### 显示通信过程

`curl -v 网站地址`：显示一次**http**通信的整个过程，包括端口连接和**http request**头信息。

`curl --trace [output.txt] 网站地址`：详细的通信过程会被输出到 output.txt文本中。

`curl --trace-ascii [output.txt] 网站地址`：同上。

### 发送表单信息

**发送表单信息有`GET`和`POST`两种方法。**

```
// GET方法只需要把数据附在网址后面就行。
curl example.com/form.cgi?data=xxx

// POST方法必须把数据和网址分开，curl就要用到 --data参数
curl -X POST --data "data=xxx" example.com/form.cgi

// 若数据没有经过表单编码，可以让curl为你编码，参数为“--data-urlencode”
curl -X POST--data-urlencode "data=April 1" example.com/form.cgi

```

### HTTP动词

**`curl`默认的HTTP动词是 GET，使用'-X'参数可以支持其他动词。**

```
curl -X POST 网站地址

curl -X DELETE 网站地址
```

### 文件上传

### 参考文章

- [Linux命令行：cURL的十种常见用法](https://juejin.im/post/5915204b44d904006c463c61)
- [Web 开发者需要知道的12个终端命令](https://www.oschina.net/translate/12-terminal-commands-every-web-developer-should-know?lang=chs)
- [学会使用curl命令](https://juejin.im/post/5c1da55b6fb9a049c84f709b)
- 
### 如何从终端直接打开webstorm
- 先在Webstorm编辑器中配置终端命令行的打开命令。`Tools => Create Command-line Launcher`.
- 设置完成后在终端输入`cd /usr/local/bin`命令，可以看到在`bin`文件夹下面有`webstorm`.
- 此时只需要先切换到你想要打开项目的路径下，然后输入`webstorm .`，即可用Webstorm编辑器打开当前目录文件了。

### 设置webstorm别名快捷键
- 编辑 .zshrc 文件。`vim .zshrc`
- 为Webstorm添加别名。`alias ws="webstorm"`
- 然后`source .zshrc`即可生效。

```
// 先切换到工作目录
cd /Users/username/yzj/forumweb
// 然后直接执行 webstorm . 即可。
webstorm .
// 或者直接使用别名
ws .
```

### 在终端快速的用Webstorm编辑器打开项目文件
一般情况下，我们想要在当前的一个webstorm项目窗口打开（新开一个窗口）另外一个项目文件，需要
点击Webstorm中的 **File=>Open**,然后在到显示出来的文件系统中去找对应想打开的文件。若文件存放在
较深的目录，会导致每次这样的操作很痛苦。那有没有简单而又快速的方法来实现上面的操作呢？
答案是有的，**只需要进行一些简单的配置，就可以通过输入两条命令来完成上面的需求。**

#### 1.为常用的工作目录设置别名（alias）
以我自身为例，公司的项目都会存放在当前用户的某个文件下面。
```
vim .zshrc
// 设置别名 lapp
alias lapp="cd /Users/username/yzj/connecterp-lapp"
```
#### 2.通过输入别名切换到对应要打开的工作目录
```
// 跳转到 /Users/username/yzj/connecterp-lapp目录
lapp
// 用webstorm打开当前目录
ws .
```
通过以上两步就可以超快速的在终端用webstorm打开工作目录啦。


### 参考文章
- [如何从终端打开webstorm](https://cloud.tencent.com/developer/ask/112420)
- [mac终端快速启动Sublime/WebStrom/VS Code/Atom等编辑器](https://www.jianshu.com/p/5ced5876cba4)
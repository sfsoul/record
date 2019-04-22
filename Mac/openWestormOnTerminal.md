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

### 参考文章
- [如何从终端打开webstorm](https://cloud.tencent.com/developer/ask/112420)
- [mac终端快速启动Sublime/WebStrom/VS Code/Atom等编辑器](https://www.jianshu.com/p/5ced5876cba4)
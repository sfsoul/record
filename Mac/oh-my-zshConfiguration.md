### 前言
主要介绍 oh-my-zsh中用到的插件与主题以及如何进行配置。
### oh-my-zsh下载与基本介绍
关于下载 oh-my-zsh，可以直接在[oh-my-zsh官网](https://ohmyz.sh/)进行命令下载，官网给出了两条不同的下载命令。

下载完 oh-my-zsh后，在终端的当前用户下（/Users/username）会新生成几个隐藏文件。
- .oh-my-zsh
- .zshrc   // 进行oh-my-zsh的相关配置，修改完成后记得执行`source .zshrc`命令才能生效。
- .zsh_history
### 关于oh-my-zsh的theme
关于 oh-my-zsh中的主题列表清单以及相关配置可以从[这里](https://github.com/robbyrussell/oh-my-zsh/wiki/Themes)获取。

#### 如何设置主题（修改 .zshrc文件中的ZSH_THEME字段即可）
**In order to enable a theme, set `ZSH_THEME` to the name of the theme in your `~/.zshrc`, before
sourcing Oh My Zsh; for example：`ZSH_THEME=robbyrussell`。**

#### oh-my-zsh内置的主题
oh-my-zsh中会内置很多主题，可通过命令`cd ~/.oh-my-zsh/themes`来查看目前拥有的主题。

#### 配置agnoster主题
![agnoster主题信息](https://i.loli.net/2019/04/22/5cbdab05bf327.jpg)
因为oh-my-zsh已经内置了agnoster主题，所以我们不需要去下载agnoster主题，而只需要进行简单的配置就可以啦。
##### 1.修改ZSH_THEME
将`.zshrc`文件中的`ZSH_THEME`值修改为`agnoster`。
##### 2.Install Powerline fonts
**Install Powerline fonts for the special characters。**

看[官网](https://github.com/powerline/fonts)进行安装。
```
# clone
git clone https://github.com/powerline/fonts.git --depth=1
# install
cd fonts
./install.sh
# clean-up a bit
cd ..
rm -rf fonts
```
**最终字体是被安装到了`/Users/username/Library/fonts`目录下面，感兴趣的可以自己去看`install.sh`脚本做了什么事情。**

最后到终端（iTerm2）中进行字体font的设置即可。
**Preferences=>Profiles=>Text=>Change Font(我选择的是All Fonts下面的Meslo LG M DZ Bold for Powerline字体)。**

##### 3.set DEFAULT_USER
![show](https://i.loli.net/2019/04/22/5cbdd9da54c8a.jpg)
其实完成上面的1、2两步后已经能够正常的使用 agnoster主题啦。但是从上面的截图可以看到每条命令
前面都有那么长的前缀（user@hostname）很不美观，那有没有办法去掉呢？当然是有的，看下面那段英文介绍。

**Optionally set `DEFAULT_USER` to your regular username followed by prompt_context(){} in
`~/.zshrc` to hide the "user@hostname" info when you're logged in as yourself on your local machine.**

从上面的话中不难理解，只要我们在`~/.zshrc`文件配置一个`DEFAULT_USER`信息就可以达到隐藏前缀的效果啦。
```
// 修改.zshrc文件，配置DEFAULT_USER= usernamer(这里我以xx为例)，然后source .zshrc即可
DEFAULT_USER= 'xxxx'

source .zshrc
```
![隐藏前缀](https://i.loli.net/2019/04/22/5cbddc805be49.jpg)

### oh-my-zsh好用的插件
首先oh-my-zsh中的插件存放位置分为两种：
- 1.标准插件位置：`~/.oh-my-zsh/plugins/*`
- 2.用户自定义插件位置：`~/.oh-my-zsh/custom/plugins/`

插件的配置也很简单，只需要在`.zshrc`文件中将想用的插件配置进入plugins这个变量中即可。
```
vim .zshrc

// 编辑plugins变量，加入插件
plugins = (
    git
    autojump
    zsh-autosuggestions
    zsh-syntax-highlighting
)

source .zshrc
```
#### git（默认已开启）
**作用：可以使用各种`git`命令缩写。**
```
// 例如：
git add ===> ga
git log --pretty=oneline ===> gsl
```
**查看所有`git`命令缩写**

`cat ~/.oh-my-zsh/plugins/git/git.plugin.zsh`

**或者筛选对应的命令，如和`git`有关的命令。**

`alias | grep git`

#### autojump
[autojump官网](https://github.com/wting/autojump)

> autojump is a faster way to navigate your filesystem. It works by maintaining a database of
the directories you use the most from the command line. Directories must be visited first before they can be jumped to.

以上内容是 **autojump官网**对 `autojump`的描述，可以大概分为两点理解：
- autojump能够快速的导航跳转到我们的文件系统，它的工作原理是维护一个数据库，数据库中记录了用户使用多次的命令行。
- 目录文件要能够被autojump跳转过去，需要在之前有访问过。（因为它的原理储存用户输入过的命令行）

#### git-open
[git-open官网](https://github.com/paulirish/git-open)

> Type `git-open` to open the repo website（Github，Gitlab，Bitbucket）in your browser.

作用：**当你在自己的本地机器上将代码提交到远程库（github）上时，输入`git-open`就会立马在浏览器中打开此项目的github地址。**

##### Installation
因为我的终端下载了Oh-My-Zsh,所以这块的下载我只介绍跟Oh-My-Zsh相关，其他下载方式可以到官网上看。
- `git clone https://github.com/paulirish/git-open.git $ZSH_CUSTOM/plugins/git-open`
- Add git-open to your plugin list - edit ~/.zshrc and change plugins=(...) to plugins=(... git-open)
- `source .zshrc`

只需要简单的三步就可以在终端使用`git-open`命令啦。

**特别注意：`git-open`命令是要在当前目录属于一个`git repository`时才生效的，否则会提示失败。**
![失败的git-open场景](https://i.loli.net/2019/04/24/5cc07b28b8d35.jpg)


### 其他插件
#### trash
[trash官网](https://github.com/sindresorhus/trash)
> Move files and folders to the trash. In contrast to `fs.unlink`,`del`, and `rimraf` which permanently
delete files, this only moves them to the trash, which is much safer and reversible.

**Install through CLI**
```
// To install the trash command, run：
npm install --global trash-cli
```

#### bat
[bat官网](https://github.com/sharkdp/bat)
> A cat(1) clone with syntax highlighting and Git integration

**Installation**

`brew install bat`

**effect**

- Syntax highlighting：`bat` supports syntax highlighting for a large number og programming and markup languages。
- Git integration：`bat` communicates with `git` to show modifications with respect to the index。
- Show non-printable characters：use the `-A/--show-all` option to show and highlight non-printable characters。
- Automatic paging：`bat` can pipe its own output to `less` if the output is too large for one screen。
### 参考文章
- [zsh oh-my-zsh 插件推荐](https://hufangyun.com/2017/zsh-plugin/)
- []()
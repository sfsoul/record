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

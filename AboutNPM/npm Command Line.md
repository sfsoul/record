 [TOC]

### npm-install

#### npm install(in package directory, no arguments)

> Install the dependencies in the local node_modules folder.
>
> By default, `npm install` will install all modules listed as dependencies in `package.json`
>
> With the `--production` flag(or when the `NODE_ENV` environment variable is set to `production`), npm will not install modules listed in `devDependencies`

#### npm install [<@scope>/]<name>

> In most cases, this will install the version of the modules tagged as `latest` on the npm registry.

```
npm install sax
```

> `npm install` saves any specified packages into `dependencies` by default. Additionally, you can control where and how they get saved with some additional flags:

- -P,  —save-prod:Package will appear in your `dependencies`. This is the default unless -D or -O are present.
- -D, —save-dev:Package will appear in your `devDependencies`.
- -O, —save-optional:Package will appear in your `optionalDependencies`.
- —no-save:Prevents saving to `dependencies`.

#### npm install [<@scope>/]<name>@<tag>

> Install the version of the package that is referenced by the specified tag. If the tag does not exist in the registry data for that package, then this will fail.

```
npm i sax@latest
npm i @myorg/mypackage@latest
```

#### npm install [<@scope>/]<name>@<version>

> Install the specified version of the package. This will fail if the version has not been published to the registry.

```
npm i sax@0.1.1
npm i @myorg/privatepackage@1.5.0
```

#### npm install [<@scope>/]<name>@<version range>

> Install a version of the package matching the specified version range. This will     follow the same rules for resolving dependencies described in `package.json`.
>
> Note that most version ranges must be  put in quotes so that your shell will treat it as a single argument.

```
npm i sax@">=0.1.0 <0.2.0"
npm i @myorg/privatepackage@">=0.1.0 <0.2.0"
```

### npm-folders

```
cd /usr/local/bin
// 通过npm install -g 下载的包
cd /usr/local/lib/node_modules
```



#### tl;dr

### npm-bin

> 列出npm安装可执行文件的文件夹

```
npm bin [-g | --global]
```

### npm install <package_name> -g 怎么能使得某命令全局范围生效？

**查看系统环境变量：**

```
env
输出：PATH=/Users/jing_zhang/.oh-my-zsh/custom/plugins/git-open:/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin
```

**再看对应的 /usr/local/bin 下有哪些程序链接：**

```

```

**全局包最终的安装原地址：`/usr/local/lib/node_modules/` 下的文件（其实就是超链接）。**

#### 如何使本地安装的modules和全局安装的相同效果(通过npm来实现和系统环境一样的逻辑)

- 了解`npm bin`的作用。

```
// 在当前项目目录下
npm bin

// 查看全局
npm bin -g
```



### 参考文章

- [npm依赖包bin文件路径问题](https://blog.csdn.net/qq_29956875/article/details/75433976)
- [npm脚本执行](https://eminoda.github.io/2019/01/12/npm-bin/)
- 


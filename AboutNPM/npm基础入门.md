[TOC]

### npm

### 更新npm

> When you install node.js,npm is automatically installed.However, npm gets updated more frequently than Node.js, so be sure that you have the latest version.

**This will install the latest official, tested version of npm**

```
npm install npm@latest -g
```

**To install a version that will be released in the future**

```
npm install npm@next -g
```

```
/usr/local/bin/npm -> /usr/local/lib/node_modules/npm/bin/npm-cli.js
/usr/local/bin/npx -> /usr/local/lib/node_modules/npm/bin/npx-cli.js
```

### NVM

### How to Prevent Permissions Errors

### 如何安装本地包

**两种方式来安装npm包：本地安装和全局安装。**

- 若自己的模块依赖于某个包，并通过Node.js的`require`加载，应该选择本地安装，此方式也是`npm install`命令的默认行为。
- 若想将包作为一个命令行工具(如grunt CLI)，应该选择 全局安装。

#### 安装一个包

```
npm install <package_name>
```

**上述命令会在当前的目录下创建一个`node_module`的目录（若不存在的话），然后将下载的包保存到这个目录下。**

#### 哪个版本的包会被安装？

**在本地目录中若没有`package.json`此文件，那么最新版本的包会被安装。若存在`package.json`文件，则会在`package.json`文件中查找针对这个包所约定的语义化版本规则，然后安装符合此规则的最新版本。**

### Working with package.json

#### How to Customize the package.json questionnaire

> If you expect to create many package.json files,you might wish to customize the questions asked during the init process, so that the files always contain key information that you expect. You can customize the fields as well as the questions that are asked.

#### Specifying Dependencies

> to specify the packages your project depends on, you need to list the packages you'd like to use in your `package.json` file. There are 2 types of packages you can list:

- `"dependencies"`: These packages are required by your application in production.
- `"devDependencies"`: These packages are only needed for development and testing.

#### The —save and —save-dev install flags

> The easier(and more awesome) way to add dependencies to your `package.json` is to do so from the command line, flagging the `npm install` command with either `--save` or `--save-dev`, depending on how you'd like to use the dependency.

**To add an entry to your `package.json's dependencies`:**

```
npm install <package_name> --save
```

**To add an entry to your `package.json's devDependencies`:**

```
npm install <package_name> --save-dev
```

### 如何更新本地安装的包

- 在`package.json`文件所在的目录中执行`npm update`命令。
- 执行`npm outdated`命令。不应该有任何输出。

### 如何卸载本地安装的包

**如需删除node_module目录下面的包，执行：**

```
npm uninstall <package_name>
```

**如需从`package.json`文件中删除依赖，需要在命令后添加参数 —save：**

```
npm uninstall --save <package_name>
```

**若将安装的包作为`devDependency`,必须通过 —save-dev参数将其卸载。**

```
npm uninstall --save-dev <package_name>
```

### 如何安装全局包

**将其作为一个命令行工具，就应该将其安装到全局。**

```
npm install -g <package_name>
```

### 如何更新全局安装的包

**To update global packages, type:**

```
npm update -g <package_name>
```

**To find out which packages need to be updated, type:**

```
npm outdated -g --depth=0
```

**To update all global packages, type:**

```
npm update -g
```

### 如何卸载全局安装的包

```
npm uninstall -g <package_name>
```

### 如何创建 Node.js 模块

- 将包发布到npm。
- 在你的项目外新建一个目录。
- 然后 `cd` 进入这个新目录。
- 执行 `npm install <package>` 命令。
- 创建一个 test.js 文件，require 这个包，并调用其中的方法。
- 执行 `node test.js` 命令。

### How to Publish & Update a Package

#### How to Publish a Package

##### Create a User Account

> To publish, you must be a user on the npm registry. If you aren't a user, create an account by using `npm adduser`. If you created a user account on the site, use `npm login` to access your account from your terminal.

##### Publish!

> Go to `https://npmjs.com/package/<package_name>`. You should see a page all about your new package.

**Use `npm publish` to publish the package.**

#### How to Update a Package

##### How to Update the Read Me File

> The README displayed on the site will not be updated unless a new version of your package is published, so you need to run `npm version patch` and `npm publish` to update the documentation displayed on the site.

##### How to Update the Version Number

> When you make changes, you can update the package using `npm version <update_type>`. This command will change the version number in `package.json`. After updating the version number, run `npm publish` again.

### 如何使用语义化版本

### How to Work with Scoped Packages

> Scopes are used to group related packages together, and to create a namespace, like a domain, for npm modules.

**If a package's name begins with @, then it is a `scoped package`. The scope is everything in between the @ and the slash.**

```
@scope/project-name
```

**Each npm user has their own scope.**

```
@username/project-name
```

#### How to Initialize a Scoped Package

> To create a scoped package, you simply use a package name that starts with your scope.

```
{
	"name": "@username/project-name"
}
```

**If you use `npm init`, you can add your scope as an option to that command.**

```
npm init --scope=username
```

**If you use the same scope all the time, you will probably want to see this option in your `.npmrc` file.**

````
npm config set scope username
````

#### Publishing a Scoped Package

> By default, scoped packages are private. To publish private modules, you need to be a paid private modules user. Public scoped modules are free and don't require a paid subscription. To publish a public scoped module, set the access option when publishing it. This option will remain set for all subsequent publishes.

```
npm publish --access=public
```

#### Using a Scoped Package

> To use a scoped package, simply include the scope wherever you use the package name.

```
// In package.json
{
	"dependencies": {
		"@username/project-name": "^1.0.0"
	}
}
```

**On the command line:**

```
npm install @username/project-name --save
```

**In a `require` statement:**

```
var projectName = require("@username/project-name")
```

### How to Label Packages with Dist-tags

#### Adding tags

#### Publishing with tags

#### Installing with tags

### How to Use Two-Factor Authentication

### How to Work with Security Tokens

### How to change profile settings from the CLI

> To view and set profile properties from the Command Line Interface(CLI), use these commands:

```
npm profile get
npm profile set <prop> <value>
```

#### Viewing & Setting Profile Values

> To see your current profile setting, type:

```
npm profile get
```

> npm displays your profile settings in a table:

**搞张截图**

#### How to Set a Password from the Command Line

> To set a password, type:

```
npm profile set password
```

#### How to Set Other Profile Properties

> To set other values, append them to the end of the line as shown:

```
npm profile set fullname nori pat marsupial
```

### Understanding Packages and Modules

#### What is a package?

**A package is any of the following:**

- A folder containing a program described by a `package.json` file.
- A gzipped tarball containing.
- A url that resolves to.
- A `<name>@<version>` that is published on the registry with.
- A `<name>@<tag>` that points to.
- A `<name>` that has a `latest` tag satisfying.
- A `git` url that, when cloned, results in.

#### What is a module?

**A mdoule is anything that can be loaded with `require()` in a Node.js program. The following are all examples of things that can be loaded as modules:**

- A folder with a `package.json` file containing a `main` field.
- A folder with an `index.js` file in it.
- A JavaScript file








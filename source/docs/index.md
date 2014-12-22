title: 文档
---
欢迎阅读 Hexo 的文档。本文档将帮助您快速上手。如果您在使用 Hexo 时出现任何问题，你可以在 [Q&A](troubleshooting.html) 寻找答案，或者你可以在我的 [GitHub上](https://github.com/hexojs/hexo/issues) 或 [谷歌小组](https://groups.google.com/group/hexo) 中询问我。

## 什么是 Hexo?

Hexo 是一个快速，简单，强大的博客框架。 它使用 [Markdown](http://daringfireball.net/projects/markdown/)  (或者其他的渲染引擎)转换你的文章并结合一个漂亮的主题生成静态文件，而这一切都在数秒之内完成。

## 安装

准备好 Hexo 只需要花费几分钟时间。如果你在安装过程中遇到问题并且在这个文档中不能找到解决方法, 请 [提交问题](https://github.com/hexojs/hexo/issues) ，我会试着解决你的问题。

### Requirements

Installing Hexo is quite easy. However, there are some things required before you get started:

- [Node.js](http://nodejs.org/)
- [Git](http://git-scm.com/)

If your computer already has the requirements above, congratulations! Just install Hexo with npm.

``` bash
$ npm install -g hexo
```

If not, please follow the following instructions to install all the requirements.

{% note warn For Mac users %}
You may encounter some problems when compiling. Please install Xcode from App Store first. After Xcode is installed, open Xcode and go to **Preferences -> Download -> Command Line Tools -> Install** to install command line tools.
{% endnote %}

### Install Git

- Windows: Download & install [msysgit](http://code.google.com/p/msysgit/).
- Mac: Install it with [Homebrew](http://mxcl.github.com/homebrew/), [MacPorts](http://www.macports.org/) or [installer](http://code.google.com/p/git-osx-installer/).
- Linux (Ubuntu, Debian): `sudo apt-get install git-core`
- Linux (Fedora, Red Hat, CentOS): `sudo yum install git-core`

### Install Node.js

The best way to install Node.js is installing with [nvm](https://github.com/creationix/nvm).

cURL:

``` bash
$ curl https://raw.github.com/creationix/nvm/master/install.sh | sh
```

Wget:

``` bash
$ wget -qO- https://raw.github.com/creationix/nvm/master/install.sh | sh
```

Once installed, restart the terminal and run the following command to install Node.js.

``` bash
$ nvm install 0.10
```

Or you can download the [installer](http://nodejs.org/) and install it.

### Install Hexo

Once all the requirements are installed, you can install Hexo with npm.

``` bash
$ npm install -g hexo
```

title: 开始
---
安装好 Hexo 后，运行下面的命令，Hexo 会在目标文件夹下建立所有的文件。

``` bash
$ hexo init <folder>
$ cd <folder>
$ npm install
```

建立文件之后，文件夹结构看起来是这样的：

``` plain
.
├── _config.yml
├── package.json
├── scaffolds
├── scripts
├── source
|   ├── _drafts
|   └── _posts
└── themes
```

### _config.yml

查看 [配置](configuration.html) 说明，那你可以在这里配置一些选项。

### package.json

应用程序数据，如果你了解 Node.js 你应当知道它的作用。[EJS](http://embeddedjs.com/), [Stylus](http://learnboost.github.io/stylus/) 和 [Markdown](http://daringfireball.net/projects/markdown/) 
Application data. [EJS](http://embeddedjs.com/), [Stylus](http://learnboost.github.io/stylus/) and [Markdown](http://daringfireball.net/projects/markdown/) 默认会被安装，稍后你可以卸载他们。

``` json package.json
{
  "name": "hexo-site",
  "version": "",
  "private": true,
  "dependencies": {
    "hexo-renderer-ejs": "*",
    "hexo-renderer-stylus": "*",
    "hexo-renderer-marked": "*"
  }
}
```

### scaffolds

[scaffolds](writing.html) 文件夹. 当你新建一篇文章时， Hexo 会在 scaffolds 的基础上创建这篇文章。

### scripts

[scripts](plugins.html) 文件夹. 这些脚本是扩展 Hexo 最简单的方式。这个文件夹下的 Javascript 文件会被自动执行。

### source

你可以将你写的内容放在 Source 文件夹里。除了 `_posts` 其他以 `_` （下划线）开头命名的文件或文件夹和隐藏文件会被忽略。Markdown 和 HTML 文件会被处理并放到 `public` 文件夹，其他文件会被复制过去。

### themes

[Theme](themes.html) 文件夹。 Hexo 会基于主题创建静态文件。

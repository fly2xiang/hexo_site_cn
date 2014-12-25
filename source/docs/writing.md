title: 撰写
---
## 创建一篇新文章

你可以自己创建或者使用下面的命令一篇新文章。如果不提供 `layout` 参数，会使用 [_config.yml](configuration.html) 中配置的 `default_layout` 。如果标题中包含空格，需要使用双引号。

``` bash
$ hexo new [layout] <title>
```

### 布局

Hexo 有两种默认布局： `post` 和 `page`。其他布局默认会被保存在 `source/_posts` 。

布局 | 目录
--- | ---
`post` (Default) | source/_posts
`page` | source

{% note tip 我不想文章被应用一个布局! %}
如果你不想文章应用一个布局，你可以在文章前面设置 `layout: false` 。
{% endnote %}

### 例子

``` bash
$ hexo new "New Post"
# => 会在 source/_posts/new-post.md 创建一个新文件

$ hexo new page "New Page"
# => 会在 source/new-page/index.html 创建一个新文件
```

### 文件名

你可以修改 `new_post_name` 设置来修改文件名。

变量 | 描述
--- | ---
`:title` | 转义过的文章标题 (小写字母和中划线)
`:year` | 文章创建的年 (4位数字)
`:month` | 文章创建的月 (1位数字)
`:i_month` | 文章创建的月 (没有前导零)
`:day` | 文章创建的日 (2位数字)
`:i_day` | 文章创建的日 (没有前导零)

{% note tip 以日期组织你的文章 %}
你可以将 `new_post_name` 设置为 `:year-:month-:day-:title.md` 可以将你的文章设置为按日期排序。
{% endnote %}

## Front-matter 前置数据

Front-matter 是一个放在文件前面被 `---` 包裹的区块。例如:

``` yaml
title: Hello World
date: 2013/7/13 20:46:25
---
```

你可以在 front-matter 中配置所有文章的配置项。下面是预定义的设置。

设置 | 描述 | 默认值
--- | --- | ---
`layout` | 布局 | post/page
`title` | 标题 |
`date` | 发布时间 | 文件创建日期
`updated` | 最后修改时间 | 文件的最后时间
`comments` | 对这篇文章开启评论 | true
`tags` | 标签 (对于独立页面不可用) |
`categories` | 分类 (对于独立页面不可用) |
`permalink` | 对于这篇文章覆盖默认的链接规则 | 文件名

{% note warn YAML front-matter %}
编写 front-matter 使用 YAML 格式。在 front-matter 不能使用制表符而要使用空格进行缩进，在冒号后面有一个空格。
{% endnote %}

## 分类和标签

Hexo 支持分类和标签。分类和标签只在文章中支持并且必须在 front-matter 中设置。例如:

``` yaml
categories:
- Diary
tags:
- PS3
- Games
```

分类和标签在其他系统中听起来是很相似的，但是他们在 Hexo 中是完全不同的。分类是分层的、有序的，这意味着 `Foo, Bar` 和 `Bar, Foo` 是不同的。 而标签是无序的、扁平的。

## 摘要

你可以在你文章中添加 `<!-- more -->` 来隐藏部分内容。列表页面只会显示第一个 `<!-- more -->` 和第二个  `<!-- more -->`  之间的内容。

``` markdown
...

<!-- more -->

...
```

## 代码高亮

有两种方式高亮你的文章中的代码片段： **Backtick code block** 与 **Swig code block**。它们都是从 Octopress 移植过来的。

### Backtick Code Block

{% code %}
``` [language] [title] [url] [link text]
code snippet
```
{% endcode %}

### Swig Code Block

{% raw %}
<figure class="highlight"><pre>{% code [title] [lang:language] [url] [link text] %}
code snippet
{% endcode %}
</pre></figure>
{% endraw %}

## 模版

Hexo 会基于对应的模版创建新的文章。例如：

``` bash
$ hexo new photo "My Gallery"
# => 文件将会被创建到 source/_posts/my-gallery.md
```

Hexo 会使用 `scaffolds` 文件夹下以 `photo` 命名的模版文件，如果模版不存在，会使用文章的模版。

### 例子

变量会被两个大括号包裹。例如：

``` plain
layout: {% raw %}{{ layout }}{% endraw %}
title: {% raw %}{{ title }}{% endraw %}
date: {% raw %}{{ date }}{% endraw %}
---
```

### 变量

变量 | 描述
--- | ---
`layout` | 布局名称
`title` | 文章标题
`date` | 文件创建时间

## 资源文件夹

如果你将所有图片和其他资源放在 `source` 文件夹。你可以开启 `post_asset_folder` 设置。

``` yaml
post_asset_folder: true
```

开启此设置后，当你在新建一篇文章时会创建一个文件夹。你可以将所有这篇文章需要的资源文件放在这个文件夹里。这让在文章中使用图片变得非常简单。

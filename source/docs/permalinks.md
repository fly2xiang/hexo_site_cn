title: 链接格式
---
你可以在 `_config.yml` 或在每篇文章的前置数据中指定链接格式。 

### 变量

Besides the following variables, you can use any attributes in the permalink since Hexo 2.5.
在Hexo 2.5以上版本中，你可以在链接格式中使用以下变量。

变量 | 描述
--- | ---
`:year` | 文章的发表年份 (4位数字)
`:month` | 文章的发表月份 (2位数字)
`:i_month` | 文章的发表月份 (不含前导零)
`:day` | 文章的发表日 (2位数字)
`:i_day` | 文章的发表日 (不含前导零)
`:title` | 文件名
`:id` | 文章ID
`:category` | 文章分类。 如果文章没有分类，它将会是 `category_dir` 设置项。

你可以在 `permalink_defaults` 设置项中定义每个变量的默认值：

``` yaml
permalink_defaults:
  lang: en
```

### 示例

Given a post named `hello-world.md` in `source/_posts` folder with the following content.
给定一篇在 `source/_posts` 目录下，文件名为 `hello-world.md` 的文章，内容如下：

``` yaml
title: Hello World
date: 2013-07-14 17:01:34
categories:
- foo
- bar
```

设置 | 结果
--- | ---
`:year/:month/:day/:title/` | 2013/07/14/hello-world
`:year-:month-:day-:title.html` | 2013-07-14-hello-world.html
`:category/:title` | foo/bar/hello-world

### 多语言支持

想创建一个多语言的站点，你可以修改 `new_post_name` 和 `permalink` 设置如下：

``` yaml
new_post_name: :lang/:title.md
permalink: :lang/:title/
```

当你新建一篇文章时，会被保存到：

``` bash
$ hexo new "Hello World" --lang tw
# => source/_posts/tw/Hello-World.md
```
文章地址将会是：

``` plain
http://localhost:4000/tw/hello-world/
```
title: 配置
---
你可以在 `_config.yml` 进行大部分的配置。

## 配置

### Site 站点

配置项 | 描述
--- | ---
`title` | 网站的标题
`subtitle` | 网站的副标题
`description` | 网站的描述
`author` | 你的名字
`email` | 你的邮箱地址
`language` | 你的网站使用的语言。使用 [IETF 格式](http://www.w3.org/International/articles/language-tags/). (例如: 简体中文: `zh-CN`)

### URL

配置项 | 描述 | 默认值
--- | --- | ---
`url` | 你网站的网址 |
`root` | Hexo 相对于你网站的根目录 |
`permalink` | 文章的 [permalink](permalinks.html) 格式 | :year/:month/:day/:title/
`tag_dir` | 标签文件夹 | tags
`archive_dir` | 文章文件夹 | archives
`category_dir` | 分类文件夹 | categories
`code_dir` | 包含代码文件夹 | downloads/code

{% note info 将网站放在子目录中 %}
如果你将网站放置在一个子目录中，类似于 `http://yoursite.com/blog` ，请将 `url` 设置为 `http://yoursite.com/blog` ，将 `root` 设置为 `/blog/`。
{% endnote %}

### Writing 撰写

设置项 | 描述 | 默认值
--- | --- | ---
`new_post_name` | 新文章的命名格式 | :title.md
`default_layout` | 默认的布局 | post
`auto_spacing` | 在东方字符和西方字符之间加入空格 | false
`titlecase` | 将标题转换为合适的 | false
`external_link` | 在新标签页打开外部链接 | true
`filename_case` | 将文件名转换为小写或大写，1.小写，2.大写，0.不转换 | 0
`render_drafts` | 渲染草稿 | false
`post_asset_folder` | 开启 [Asset 文件夹](writing.html#Asset_Folder) | false
`relative_link` | 使用相对路径 | false
`highlight` | 代码块设置 |

### Category & Tag 分类和标签

配置项 | 描述 | 默认值
--- | --- | ---
`default_category` | 默认分类 | uncategorized
`category_map` | 分类云 |
`tag_map` | 标签云 |

### Archives 文章

配置项 | 描述 | 默认值
--- | --- | ---
`archive` | 2: 开启分页, 1: 禁用分页, 0: 全局禁用 | 2
`category` | 2: 开启分页, 1: 禁用分页, 0: 全局禁用 | 2
`tag` | 2: 开启分页, 1: 禁用分页, 0: 全局禁用 | 2

### Server 服务器

配置项 | 描述 | 默认值
--- | --- | ---
`port` | 服务端口 | 4000
`logger` | 在控制台显示请求日志，在调试模式下默认启用 | false
`logger_format` | 日志格式 |
`server_ip` | 自定义服务器IP | 0.0.0.0

### Date / Time format 日期时间格式

Hexo 使用 [Moment.js](http://momentjs.com/) 来转换和显示日期和时间。

配置项 | 描述 | 默认值
--- | --- | ---
`date_format` | 日期格式 | MMM D YYYY
`time_format` | 时间格式 | H:mm:ss

### Pagination 分页

配置项 | 描述 | 默认值
--- | --- | ---
`per_page` | 每页显示的文章数 (0 = 禁用分页) | 10
`pagination_dir` | Pagination directory | page

### Comment 评论

配置项 | 描述
--- | ---
`disqus_shortname` | [Disqus](http://disqus.com/) shortname

### Extensions 扩展

配置项 | 描述
--- | ---
`theme` | 当前使用的主题
`exclude_generator` | 不生成的 (archive, category, home, page, post, tag)

{% note warn YAML 格式 %}
在配置文件中不可使用制表符，只能使用空格缩进。在冒号后要加上一个空格。配置文件不能正确解析可能导致 Hexo 不能运行。
{% endnote %}

## Default Configuration 默认配置

``` yaml _config.yml
title: Hexo
subtitle:
description:
author: John Doe
email:
language:

url: http://yoursite.com
root: /
permalink: :year/:month/:day/:title/
tag_dir: tags
archive_dir: archives
category_dir: categories
code_dir: downloads/code

new_post_name: :title.md
default_layout: post
auto_spacing: false
titlecase: false
filename_case: 0
render_drafts: false
post_asset_folder: false
relative_link: false
highlight:
  enable: true
  line_number: true
  tab_replace:

default_category: uncategorized
category_map:
tag_map:

archive: 2
category: 2
tag: 2

port: 4000
logger: false
logger_format:

date_format: MMM D YYYY
time_format: H:mm:ss

per_page: 10
pagination_dir: page

disqus_shortname:

theme: light
exclude_generator:

deploy:
  type:
```

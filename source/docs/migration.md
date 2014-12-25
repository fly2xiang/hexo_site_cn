title: 迁移
---
## RSS

首先，安装 `hexo-migrator-rss` 插件。

``` bash
$ npm install hexo-migrator-rss --save
```

插件安装之后，运行下面的命令将所有的文章从 RSS 迁移。 `source` 参数是文件路径或者 URL 地址。

``` bash
$ hexo migrate rss <source>
```

## Jekyll

将所有文件从 `_posts` 文件夹移动到 `source/_posts` 文件夹并修改 `_config.yml` 文件中的 `new_post_name` 配置。

``` yaml
new_post_name: :year-:month-:day-:title.md
```

## Octopress

将 Octopress  `source/_posts` 文件夹下的所有文件移动到 Hexo 的 `source/_posts` 文件夹并修改 `_config.yml` 文件中的 `new_post_name` 配置。

``` yaml
new_post_name: :year-:month-:day-:title.md
```

## WordPress

首先安装 `hexo-migrator-wordpress` 插件。

``` bash
$ npm install hexo-migrator-wordpress --save
```

插件安装之后，运行下面的命令将所有的文章从 RSS 迁移。 `source` 参数是文件路径或者 URL 地址。

``` bash
$ hexo migrate wordpress <source>
```
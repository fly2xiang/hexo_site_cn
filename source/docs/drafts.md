title: 草稿
---
## 创建

你可以使用 `hexo new` 命令创建一个草稿。例如：

``` bash
$ hexo new draft <title>
```

这将会在 `source/_drafts` 文件夹下创建一个文件。

## 预览

想要和草稿一起预览你的网站，你可以在 `_config.yml` 中开启 `render_drafts` 设置：

``` yaml
render_drafts: true
```

或者在运行 `hexo server` 命令时带上 `-d` 或 `--drafts` 参数。

``` bash
$ hexo server --drafts
```

## 发布

当你的草稿完成后，你可以使用 `hexo publish` 发布它。

``` bash
$ hexo publish [layout] <filename>
```

文件会被移动到 `source/_posts` 文件夹下并追加你指定的布局。
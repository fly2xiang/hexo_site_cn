title: 命令
---
## init

``` bash
$ hexo init [folder]
```

初始化一个网站。如果不提供 `folder` 参数，Hexo 会在当前目录下初始化一个网站。

## new

``` bash
$ hexo new [layout] <title>
```

新建一篇文章，如果不提供 `layout` 参数，会使用 [_config.yml](configuration.html) 中配置的 `default_layout` 。如果标题中包含空格，需要使用双引号。

**别名:** n

## generate

``` bash
$ hexo generate
```

生成静态文件。

**别名**: g

参数 | 描述
--- | ---
`-d`, `--deploy` | 生成后部署
`-w`, `--watch` | 监控文件修改

## publish

``` bash
$ hexo publish [layout] <filename>
```

发布一个草稿。

**别名**: p

## server

``` bash
$ hexo server
```

启动服务器。

**别名:** s

参数 | 描述
--- | ---
`-p`, `--port` | 覆盖默认端口
`-s`, `--static` | 只使用静态文件
`-l`, `--log` | 开启日志，覆盖默认的日志格式
`-d`, `--drafts` | 将草稿显示为文章

## deploy

``` bash
$ hexo deploy
```

部署网站。

**别名:** d

参数 | 描述
--- | ---
`--setup` | 配置而不部署
`-g`, `--generate` | 部署前生成
`-m`, `--message` | 自定义提交信息

## render

``` bash
$ hexo render <file1> [file2] ...
```

渲染文件

参数 | 描述
--- | ---
`-o`, `--output` | 输出目录

## migrate

``` bash
$ hexo migrate <type>
```

从其他博客系统 [合并](migration.html) 内容。

## clean

``` bash
$ hexo clean
```

清理缓存文件 (`db.json`) 和生成的文件 (`public`) 。

## list

``` bash
$ hexo list <type>
```

列出所有的路由

## version

``` bash
$ hexo version
```

显示版本信息

## 参数

### 安全模式

``` bash
$ hexo --safe
```

在安全模式下插件和脚本不会被加载。当你在新安装了一个插件后出现问题时，你可以使用这个参数。

### 调试模式

``` bash
$ hexo --debug
```

在终端中显示详细的信息并保存到 `debug.log` 文件。当你遇到问题时，你可以尝试在调试模式下运行 Hexo 并 [将问题提交到 Github ](https://github.com/hexojs/hexo/issues/new)。

### 安静模式

``` bash
$ hexo --silent
```

在终端中隐藏输出。

### 自定义配置文件路径

``` bash
$ hexo --config custom.yml
```

使用自定义的配置文件路径替代 `_config.yml`。

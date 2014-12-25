title: 服务器
---
## 内建服务器

Hexo 使用 [Connect] 作为内建服务器。想要开启服务器，运行下面的命令：

``` bash
$ hexo server
```

你的网站会运行在 `http://localhost:4000`。你可以在 `_config.yml` 中修改使用的端口或者使用命令行参数覆盖默认的设置。例如：

``` bash
$ hexo server -p 5000
```

服务器会监控文件的修改并自动更新他们。但是，服务器不会更新 `public` 文件夹中的文件。你可以运行 `hexo generate` 来替代他们。

{% note info 在更改配置文件后重启 Hexo %}
Hexo 不能监控配置文件的更改。你必须重启 Hexo 来保证新的配置有效果。
{% endnote %}

### 静态文件模式

在静态文件模式中，只有 `public` 文件夹中的文件会被查看到，并且文件尽快被禁用，你必须在启动服务器之前运行 `hexo generate` 。在生产环境中这是非常有用的。

``` bash
$ hexo server -s
```

### 自定义 IP

Hexo 默认在 `0.0.0.0` 运行。你可以覆盖默认的 IP 设置，例如：

``` bash
$ hexo server -i 192.168.1.1
```

### 草稿

在草稿模式中，草稿会被保存为普通文章。你可以在服务器上预览你的草稿。你对草稿的修改会马上被更新。

``` bash
$ hexo server -d
```

### 日志

想要记录服务器请求，你可以在 `_config.yml` 开启日志。日志在调试模式下是默认开启的。你可以查看 [morgan] 了解更多信息。

``` yaml
logger: true
logger_format: default
```

或者使用命令行参数覆盖默认设置。例如：

``` bash
$ hexo server -l default
```

**预定义的格式:**

格式 | 描述
--- | ---
`default` | `:remote-addr - - [:date] ":method :url HTTP/:http-version" :status :res[content-length] ":referrer" ":user-agent"`
`short` | `:remote-addr - :method :url HTTP/:http-version :status :res[content-length] - :response-time ms`
`tiny` | `:method :url :status :res[content-length] - :response-time ms`
`dev` | concise output colored by response status for development use

**令牌:**

令牌 | 描述
--- | ---
`:req[header]` | 请求头 (例如： `:req[Accept]`)
`:res[header]` | 响应头 (例如： `:res[Content-Length]`)
`:http-version` | HTTP 版本
`:response-time` | 响应时间
`:remote-addr` | 客户端 IP
`:date` | 请求时间
`:method` | 请求方法
`:url` | 请求 URL
`:referrer` | 引用页
`:user-agent` | 用户代理
`:status` | 状态

## Pow

[Pow](http://pow.cx/) 是一个 Mac 平台基于 Node.js 的零配置服务器。

### 安装

运行下面的命令:

``` bash
$ curl get.pow.cx | sh
```

### 配置

在 `~/.pow` 创建符号链接

``` bash
$ cd ~/.pow
$ ln -s /path/to/myapp
```

你的网站会运行在 `http://myapp.dev`。URL 是基于你符号链接的名称。

## Forever / PM2

想保持 Hexo 服务器运行，你可以使用 [Forever] 或 [PM2]。

Hexo 从 2.5 版本可以编程运行。所以你可以在 Javascript 中启动 Hexo 来替代命令行。

**1. 在你的网站目录中安装 Hexo 。**

``` bash
$ npm install hexo --save
```

**2. 添加一个 Javascript 文件并加入以下内容。**

``` js app.js
require('hexo').init({command: 'server'});
```

**3. 使用 [Forever] 或 [PM2] 运行你刚才创建的 Javascript 文件。**

PM2 有一个 [已知的问题](https://github.com/Unitech/pm2#known-bugs-and-workarounds) 就是当脚本停止时端口不会被释放，除非 PM2 被杀死。你必须在 fork 模式下运行这个脚本。

``` bash
$ forever start app.js
$ pm2 start app.js -x
```

[Connect]: https://github.com/senchalabs/connect
[morgan]: https://github.com/expressjs/morgan
[Forever]: https://github.com/nodejitsu/forever
[PM2]: https://github.com/Unitech/pm2
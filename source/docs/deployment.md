title: 发布
---
发布 Hexo 网站，你只需要一条命令。

``` bash
$ hexo deploy
```

## 发布到 GitHub Pages

编辑 `_config.yml`.

``` yaml
deploy:
  type: github
  repo: <repository url>
  branch: [branch]
  message: [message]
```

配置项 | 描述
--- | ---
`repo`, `repository` | GitHub 仓库的地址 URL (最好使用 HTTPS)
`branch` | 发布器会自动检测正确的分支，你也可以自定义分支。
`message` | 自定义提交信息 (默认是 `Site updated: {% raw %}{{ now('YYYY-MM-DD HH:mm:ss') }}{% endraw %}`)

### 移除

移除 `.deploy` 文件夹。

``` bash
$ rm -rf .deploy
```

### 自定义域名

在 `source` 文件夹下创建一个 `CNAME` 文件，填入以下内容。

``` plain
example.com
```

- **顶级域名:** 添加一个 A 记录: `192.30.252.153`, `192.30.252.154`.
- **子域名**: 添加一个 CNAME 记录： `blog.example.com`.

查看 [GitHub Pages](https://help.github.com/articles/setting-up-a-custom-domain-with-pages) 获得更多信息。

## 发布到 Heroku

编辑 `_config.yml`.

``` yaml
deploy:
  type: heroku
  repo: <repository url>
  message: [message]
```

配置项 | 描述
--- | ---
`repo`, `repository` | Heroku 仓库 URL
`message` | 自定义提交信息 (Default is `Site updated: {% raw %}{{ now('YYYY-MM-DD HH:mm:ss') }}{% endraw %}`)

### 移除

移除 `.git`, `app.js` 和 `Procfile`.

## 发布到 Rsync

编辑 `_config.yml`.

``` yaml
deploy:
  type: rsync
  host: <host>
  user: <user>
  root: <root>
  port: [port]
  delete: [true|false]
  verbose: [true|false]
  ignore_errors: [true|false]
```

配置项 | 描述 | 默认值
--- | --- | ---
`host` | 远端主机地址 |
`user` | 用户名 |
`root` | 远端主机的根目录 |
`port` | 端口 | 22
`delete` | 删除远端主机的旧文件 | true
`verbose` | 显示详细信息 | true
`ignore_errors` | 忽略错误 | false

## 发布到 OpenShift DIY Cartridge

编辑 `_config.yml`.

``` yaml
deploy:
  type: openshift
  remote: <upstream git remote>
  branch: [upstream git branch] # Default is master
```

配置项 | 描述 | 默认值
--- | --- | ---
`remote` | Upstream Git remote |
`branch` | Upstream Git branch | master

## 发布到 Git

编辑 `_config.yml`.

``` yaml
deploy:
  type: git
  message: [message]
  repo:
    github: <repository url>,[branch]
    gitcafe: <repository url>,[branch]
```

配置项 | 描述
--- | --- | ---
`repo`, `repository` | 仓库 URL 和分支. 使用逗号分割 (`,`) 。 默认是 `master` 分支。
`message` | 自定义提交信息 (默认是 `Site updated: {{ now('YYYY-MM-DD HH:mm:ss') }}`)

## 批量部署

你可以将你的网站部署到多个目标。

``` yaml
deploy:
- type: github
  repo: ...
- type: heroku
  repo: ...
```

## 提交信息

你可以在 **github**, **heroku**, **git** 发布器中自定义提交信息.

提交信息是支持 Swig 的。 你可以使用 `now(format)` 来显示部署时间。例如，默认的提交信息是 `Site updated: {% raw %}{{ now('YYYY-MM-DD HH:mm:ss') }}{% endraw %}`:

``` js
Site updated: {% raw %}{{ now('YYYY-MM-DD HH:mm:ss') }}{% endraw %}
// Site updated: 2014-05-12 00:02:25
```

提交信息也可以在终端中设置

``` bash
$ hexo deploy -m "Commit message"
```

或者在 `_config.yml` 中。

``` yaml
deploy:
  type: github
  repo: ...
  message: "Commit message"
```

## 其他方法

所有的生成的文件被保存在 `public` 文件夹中。你可以将它拷贝到任何你喜欢的地方。

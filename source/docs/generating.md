title: 生成
---

使用 Hexo 生成静态文件是相当简单与快速的。

``` bash
$ hexo generate
```

### 监控文件修改

Hexo 可以监控文件修改并马上重新生成。

``` bash
$ hexo generate --watch
```

{% note info 在更改配置文件后重启 Hexo %}
Hexo 不能监控配置文件的更改。你必须重启 Hexo 来保证新的配置有效果。
{% endnote %}

### 生成后发布

想要在生成后发布，你可以运行下面命令中的任何一个，效果都是相同的。

``` bash
$ hexo generate --deploy
$ hexo deploy --generate
```
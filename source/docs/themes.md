title: 主题
---
## 文件结构

``` plain
.
├── _config.yml
├── languages
├── layout
├── scripts
└── source
```

### _config.yml

主题配置文件，被改动时会自动更新，你无须重新启动服务器。

### languages

语言文件夹。Hexo 提供一个简单的内置国际化模块。想要开启这个功能，可以编辑 `language` 设置。语言代码必须写为[IETF 格式]。如：

``` yaml
language: zh-TW
```

语言文件夹必须含有一个名为 `default.yml` 的文件。语言文件可以些微 YAML 格式或者 JSON 格式。

你可以使用 `__` 和 `_p` 工具获取局部的字符串。你甚至还可以使用[printf format](https://github.com/alexei/sprintf.js)。例如：

``` yaml default.yml
index:
  title: Home
  add: Add
  video:
    zero: No videos
    one: One video
    other: %d videos
```

``` js
<%= __('index.title') %>
// Home

<%= _p('index.video', 3) %>
// 3 videos
```

### layout

布局文件夹。以 `_` 为前缀的文件或文件夹，隐藏文件将会被忽略。

Hexo 提供内置的 [EJS] 和 [Swig] 模版引擎。你可以安装一些渲染插件来提供 [Haml]、 [Jade] 支持。Hexo 基于文件的扩展名选择模板引擎。例如：

``` plain
EJS: layout.ejs
Swig: layout.swig
```

每一个模版都至少提供 `index` 布局。

布局 | 描述 | 依赖
--- | --- | ---
`index` | 首页布局 |
`post` | 文章页布局 | `index`
`page` | 单页布局 | `index`
`archive` | 归档布局 | `index`
`category` | 分类布局 | `archive`
`tag` | 标签布局 | `archive`

### scripts

脚本文件。当 Hexo 启动时 Javascript 文件将会被加载（Hexo 2.4 及以上）。

更多信息请查看[插件](plugins.html)页。

### source

源文件夹。CSS、Javascript文件等将会被放在这个文件夹里。以 `_` 文件或文件夹和隐藏文件将会被忽略。

Files which are able to rendered by renderer plugins will be rendered, such as Stylus files. Hexo provides built-in [Stylus] renderer plugin (with [nib] support). You can install some renderer plugins for [Less], [CoffeeScript] support.
可以被渲染的文件将会被渲染。Hexo 提供内置的 [Stylus] 渲染器插件 (包含 [nib] 支持)。你可以安装一些插件来提供[Less], [CoffeeScript] 支持。

{% note info 在文件中获取配置信息 %}
在文件中，你可以用 `hexo-config(key)` 获取全局配置和主题配置信息。
{% endnote %}

## 布局

Layout wraps a template to another layout template. A layout must contain `<%- body %>` so that it can show the contents of the template. For example:
布局包含一个模版和其他的布局模版。一个布局必须提供 `<%- body %>` 用来显示模版的内容。例如：

``` html index.ejs
index
```

``` html layout.ejs
<!DOCTYPE html>
<html>
  <body><%- body %></body>
</html>
```

yields:

``` html
<!DOCTYPE html>
<html>
  <body>index</body>
</html>
```

默认的，每个模版文件使用 `layout.ejs` 作为布局。你可以在前置数据中指定其他的布局。你还可以使用其他的布局来创建一个嵌套布局。

## Partial

Partial 帮助你在模版之间共享组件，例如：

``` html _partial/header.ejs
<header></header>
```

``` html index.ejs
<%- partial('_partial/header') %>
<div id="content"></div>
```

yields:

```
<header></header>
<div id="content"></div>
```

你可以转换数据到 partials 用定义的本地变量：

``` js
<%- partial('_partial/header', {title: 'Hello World'}) %>
```

更多信息请查看 [partial helper](helpers.html#partial).

## 优化

如果你的主题太复杂，有很多源文件需要创建。生成的性能会降低不少。除了简化你的主题，在Hexo 2.7 中你也可以尝试 **片段缓存** 。

这个特性是从[Ruby on Rails](http://guides.rubyonrails.org/caching_with_rails.html#fragment-caching) 借鉴而来。它保存内容中的一个片段并在下一个请求到来时使用缓存。这可以减少数据库查询并且更快地生成文件。

它可以被用在页头、页尾、侧边栏或者在你的模版中不会被修改的静态内容。例如：

``` js
<%- fragment_cache('header', function(){
  return '<header></header>';
});
```

它比 partial 要简单：

``` js
<%- partial('header', {}, {cache: true});
```

## 发布

你可以将你的主题发布到wiki上的 [主题列表](https://github.com/hexojs/hexo/wiki/Themes)。在发布之前，你应当使用 [Theme Unit Test](https://github.com/hexojs/hexo-theme-unit-test) 进行测试。

[IETF format]: http://www.w3.org/International/articles/language-tags/
[EJS]: https://github.com/visionmedia/ejs
[Swig]: http://paularmstrong.github.com/swig/
[Haml]: https://github.com/hexojs/hexo-renderer-haml
[Jade]: https://github.com/hexojs/hexo-renderer-jade
[Stylus]: http://learnboost.github.com/stylus/
[nib]: http://visionmedia.github.com/nib/
[Less]: https://github.com/hexojs/hexo-renderer-less
[CoffeeScript]: https://github.com/hexojs/hexo-renderer-coffeescript
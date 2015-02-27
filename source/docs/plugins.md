title: 插件
---
## 概述

Hexo 有一个强大的插件系统。很多内置插件是 Hexo 的扩展。它是你简单的编写你的代码。

### 脚本

如果你的代码是简单的，推荐你使用脚本。你需要做的就是将 Javascript 文件放到 `scripts` 文件夹中，它们会在 Hexo 初始化的时候被加载。

### 插件

如果你的代码很复杂或者你想要将它发布到 NPM ，推荐你使用插件。首先，在 `node_modules` 文件夹下创建一个文件夹。文件夹名称必须以 `hexo-` 开头才能被 Hexo 加载。文件夹中至少要包含两个文件：一个是主程序文件，另一个是 `package.json` 用来描述插件的目的和依赖。

``` plain
.
├── index.js
└── package.json
```

你应当在 `package.json` 中写入 `name`, `version`, `main` 描述信息。例如：

``` json package.json
{
  "name": "hexo-my-plugin",
  "version": "0.0.1",
  "main": "index"
}
```

### 发布

你可以将插件发布到wiki上的 [插件列表](https://github.com/hexojs/hexo/wiki/Plugins)。

## 生成器

生成器被用来处理源文件生成静态文件。

### 语法

``` js
hexo.extend.generator.register(name, function(locals, render, callback){
  // ...
});
```

参数 | 描述
--- | ---
`name` | Generator name
`fn` | Generator function

`fn` is invoked with 3 arguments:

Argument | Description
--- | ---
`locals` | [Site variables](variables.html)
`render` | Render function
`callback` | Callback function

### Render Function

To render contents with templates, use the render function.

``` js
render(path, layout, locals)
```

Argument | Description
--- | ---
`path` | URL without root URL
`layout` | Theme layout to use. This value can be an array or a string. When it's an array, Hexo'll use the first matched layout.
`locals` | Page variables

If you don't need to render contents with templates. You can bind contents on routes directly:

``` js
hexo.route.set('feed.xml', content);
```

### Example

``` js
hexo.extend.generator.register(function(locals, render, callback){
  render('archive.html', ['archive', 'index'], locals);
  callback();
});
```

## Renderer

Renderers are used to render contents. You can find available renderers in [plugin list](https://github.com/hexojs/hexo/wiki/Plugins#renderer).

### Syntax

``` js
hexo.extend.renderer.register(name, output, function(data, options, callback){
  // ...
}, sync);
```

Parameter | Description
--- | ---
`name` | Input file extension (lowercase, without prefixing `.`)
`output` | Output file extension (lowercase, without prefixing `.`)
`fn` | Render function
`sync` | Sync mode (`false` by default)

`fn` is invoked with 3 arguments:

Argument | Description
--- | ---
`data` | `data` contains 2 properties: `path` (File path) and `text` (File content). `path` doesn't always exist in sync mode.
`options` | Options.
`callback` | Callback function. Only used in async mode.

### Example

**Sync mode:**

``` js
var ejs = require('ejs');

hexo.extend.renderer.register('ejs', 'html', function(data, options){
  options.filename = data.path;
  return ejs.render(data.text, options);
}, true);
```

**Async mode:**

``` js
var stylus = require('stylus');

hexo.extend.renderer.register('styl', 'css', function(data, options, callback){
  stylus(data.text).set('filename', data.path).render(callback);
});
```

## Helper

Helpers are used in templates to help you insert snippets quickly. It's recommended to put complicated or often used code in helpers instead of templates. (Don't repeat yourself, right?)

### Syntax

You can get all local variables from `this`.
``` js
hexo.extend.helper.register(name, function(){
  // ...
});
```

Parameter | Description
--- | ---
`name` | Helper name
`fn` | Helper function

### Example

``` js
hexo.extend.helper.register('js', function(path){
  return '<script type="text/javascript" src="' + path + '"></script>';
});
```

``` js
<%- js('script.js') %>
// <script type="text/javascript" src="script.js"></script>
```

## Deployer

Deployer plugin helps you deploy your site on web without complicated commands.

### Syntax

``` js
hexo.extend.deployer.register(name, function(args, callback){
  // ...
});
```

Parameter | Description
--- | ---
`name` | Deployer name
`fn` | Deployer function

`fn` is invoked with 2 arguments:

Argument | Description
--- | ---
`args` | Deployer options and [Minimist] arguments.
`callback` | Callback function

## Processor

Processors are used to process raw data in `source` folder.

{% note info Hidden files will be ignored %}
Hexo won't process hidden files.
{% endnote %}

### Syntax

``` js
hexo.extend.processor.register(rule, function(file, callback){
  // ...
});
```

Paramter | Description
--- | ---
`rule` | File path matching rule. This value can be a [Backbone-style route](http://backbonejs.org/#Router), a regular expression or a function.
`fn` | Processor function

`fn` is invoked with 2 arguments:

Argument | Description
--- | ---
`file` | File data (see below)
`callback` | Callback function

### File data

You can check [Box.File](/api/classes/Box.File.html) for more info.

Property | Description
--- | ---
`source` | File source
`path` | File relative path
`type` | File event. The value can be `create`, `update`, `delete` or `skip`.
`read` | Reads the file
`readSync` | Reads the file synchronizedly
`stat` | Gets the file status
`statSync` | Gets the file status synchronizedly
`render` | Renders the file
`renderSync` | Renders the file synchronizedly

**Reads the file:**

``` js
file.read([options], callback);
file.readSync([options]);
```

Option | Description | Default
--- | --- | ---
`cache` | Enables cache | false
`encoding` | File encoding | utf8

**Gets the file status:**

``` js
file.stat(callback);
file.statSync();
```

**Renders the file:**

``` js
file.render([options], callback);
file.renderSync([options]);
```

## Tag

Tags are used in posts to help your insert snippets quickly.

### Syntax

``` js
hexo.extend.tag.register(name, function(args, content, options){
  // ...
}, options);
```

Parameter | Description
--- | ---
`name` | Tag name
`fn` | Tag function
`options` | Options (See below)

`fn` is invoked with 3 arguments:

Argument | Description
--- | ---
`args` | Arguments
`content` | Content (Only available when `options.end` is true)
`options` | Swig options

### Options

Option | Description | Default
--- | --- | ---
`ends` | Whether a tag must have an end tag | false
`escape` | Escape contents in a tag | true

### Example

**Without end tag:** Inserts a Youtube video.

``` js
hexo.extend.tag.register('youtube', function(args, content, options){
  var id = args[0];
  return '<div class="video-container"><iframe width="560" height="315" src="http://www.youtube.com/embed/' + id + '" frameborder="0" allowfullscreen></iframe></div>';
});
```

**With end tag:** Inserts a pull quote.

``` js
hexo.extend.tag.register('pullquote', function(args, content, options){
  var className = args.length ? ' ' + args.join(' ') : '';
  return '<blockquote class="pullquote' + className + '">' + content + '</blockquote>';
}, true);
```

## Console

Consoles are the interface between Hexo and you.

### Syntax

``` js
hexo.extend.console.register(name, desc, options, function(args, callback){
  // ...
});
```

Parameter | Description
--- | ---
`name` | Console name (must be in lowercase)
`desc` | Console description
`options` | Options
`fn` | Console function

`fn` is invoked with 2 arguments:

Argument | Description
--- | ---
`args` | [Minimist] arguments
`callback` | Callback function

### Options

Option | Description
--- | ---
`init` | Whether the console plugin should display in a non-Hexo folder.
`debug` | Only display in debug mode.
`alias` | The alias for the console plugin.

### Example

``` js
hexo.extend.console.register('config', 'Display configuration', function(args, callback){
  console.log(hexo.config);
  callback();
});
```

## Migrator

Migrators are used to migrate from other system to Hexo.

### Syntax

``` js
hexo.extend.migrator.register(name, function(args, callback){
  // ...
});
```

Parameter | Description
--- | ---
`name` | Migrator name
`fn` | Migrator function

`fn` is invoked with 2 arguments:

Argument | Description
--- | ---
`args` | [Minimist] arguments
`callback` | Callback function

## Filter

Filters are used to modify certain data. Hexo passes data through filters and you can modify everything as long as it's provided. This concept is stolen from [WordPress](http://codex.wordpress.org/Plugin_API#Filters). Filter API is rewritten in 2.6 and more filter types are added.

### Syntax

``` js
hexo.extend.filter.register(type, function(){
  // ...
}, priority);
```

Parameter | Description
--- | ---
`type` | Filter type (See below)
`fn` | Filter function (Arguments are depend on the filter type)
`priority` | Priority of the filter (Default is 10)

### Post Filter

**before_post_render**

Runs before posts are rendered by Markdown. For example, transform a title into titlecase:

``` js
hexo.extend.filter.register('before_post_render', function(data, callback){
  data.title = hexo.util.titlecase(data.title);
  callback(null, data);
});
```

**after_post_render**

Runs after posts are rendered by Markdown. For example, replace `@username` to a Twitter profile link.

``` js
hexo.extend.filter.register('after_post_render', function(data, callback){
  data.content = data.content.replace(/@(\d+)/, '<a href="http://twitter.com/$1">#$1</a>');
  callback(null, data);
});
```

**new_post_path**

Runs when creating a post. Used to determine the file path of a post.

``` js
hexo.extend.filter.register('new_post_path', function(data, replace, callback){
  // ...
});
```

**post_permalink**

Used to determine the permalink of a post.

``` js
hexo.extend.filter.register('post_permalink', function(data){
  // ...
});
```

**server_middleware**

Adds a middleware to the server. `app` is an instance of the [Connect] server.

``` js
hexo.extend.filter.register('server_middleware', function(app){
  app.use(function(req, res, next){
    res.setHeader('X-Powered-By', 'Hexo');
    next();
  });
});
```

[Minimist]: https://github.com/substack/minimist
[Connect]: https://github.com/senchalabs/connect
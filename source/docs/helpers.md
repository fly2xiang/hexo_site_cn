title: 帮助
---
帮助工具帮助你在模版中快速插入片段。你可以查看 [插件](plugins.html#Helper) 来学习如何创建一个帮助插件。

### url_for

Returns a url with the root path prefixed. You should use this helper instead of `config.root + path` since Hexo 2.7.
返回一个包含根路径的URL，从 Hexo 2.7 开始你可以使用这个助手代替 `config.root + path`。

``` js
<%- url_for(path) %>
```

### relative_url

返回从 `from` 到 `to` 的相对路径

``` js
<%- relative_url(from, to) %>
```

### css

加载CSS文件。`path` 可以是数组或者字符串。如果 `path` 没有 `/` 前缀或者其他协议将会被添加根路径。如果你没有在 `path` 之后添加扩展名 `.css` ，将会被添加。

``` js
<%- css(path, ...) %>
```

**例子:**

``` js
<%- css('style.css') %>
// <link rel="stylesheet" href="/style.css" type="text/css">

<%- css(['style.css', 'screen.css']) %>
// <link rel="stylesheet" href="/style.css" type="text/css">
// <link rel="stylesheet" href="/screen.css" type="text/css">
```

### js

加载 Javascript 文件。`path` 可以是数组或者字符串。如果 `path` 没有 `/` 前缀或者其他协议将会被添加根路径。如果你没有在 `path` 之后添加扩展名 `.css` ，将会被添加。

``` js
<%- js(path, ...) %>
```

**例子:**

``` js
<%- js('script.js') %>
// <script type="text/javascript" src="/script.js"></script>

<%- js(['script.js', 'gallery.js']) %>
// <script type="text/javascript" src="/script.js"></script>
// <script type="text/javascript" src="/gallery.js"></script>
```

### 条件标签

条件标签帮助你检查当前页面的状态。

助手 | 描述
--- | ---
`is_current(path, [strict])` | 检查 `path` 是否匹配当前页面
`is_home()` | 检查是否作为首页显示
`is_post()` | 检查是否作为文章页显示
`is_archive()` | 检查是否作为归档页显示
`is_year()` | 检查是否作为年归档页显示
`is_month()` | 检查是否作为月归档页显示
`is_category()` | 检查是否作为分类页显示
`is_tag()` | 检查是否作为标签页显示

### gravatar

插入一个头像

``` js
<%- gravatar(email, [size]);
```

**例子:**

``` js
<%- gravatar('a@abc.com') %>
// http://www.gravatar.com/avatar/b9b00e66c6b8a70f88c73cb6bdb06787

<%- gravatar('a@abc.com', 40) %>
// http://www.gravatar.com/avatar/b9b00e66c6b8a70f88c73cb6bdb06787?s=40
```

### trim

清除字符串中的所有空白

``` js
<%- trim(string) %>
```

### strip_html

清楚字符串中的HTML标签

``` js
<%- strip_html(string) %>
```

**例子:**

``` js
<%- strip_html('It's not <b>important</b> anymore!') %>
// It's not important anymore!
```

### titlecase

转换字符串的大小写到合适

``` js
<%- titlecase(string) %>
```

**例子:**

``` js
<%- titlecase('this is an apple') %>
# This is an Apple
```

### partial

记载其他模版文件。你可以在 `locals` 下里定义局部变量。

``` js
<%- partial(layout, [locals], [options]) %>
```

选项 | 描述 | 默认值
--- | --- | ---
`cache` | 缓存内容 | `false`
`only` | 严格的局部变量 | `false`

### fragment_cache

在片段中缓存内容。保存内容片段，在下次请求到来时使用缓存的内容。

``` js
<%- fragment_cache(id, fn);
```

**例如:**

``` js
<%- fragment_cache('header', function(){
  return '<header></header>';
}) %>
```

### tagcloud

插入标签云

``` js
<%- tagcloud([tags], [options]) %>
```

选项 | 描述 | 默认值
--- | --- | ---
`min_font` | 最小字体大小 | 10
`max_font` | 最大字体大小 | 20
`unit` | 字体大小单位 | px
`amount` | 标签总数 | 40
`orderby` | 标签排序依据 | name
`order` | 排序方式. `1`或者`sac`升序; `-1`或者`desc`降序 | 1
`color` | 为标签云上色 | false
`start_color` | 起始颜色. 你可以使用16进制 (`#b700ff`), rgba (`rgba(183, 0, 255, 1)`), hsla (`hsla(283, 100%, 50%, 1)`) 或者 [color keywords]. 这个选项在 `color` 选项为 `true` 时才工作。 |
`end_color` | 结束颜色. 你可以使用16进制 (`#b700ff`), rgba (`rgba(183, 0, 255, 1)`), hsla (`hsla(283, 100%, 50%, 1)`) 或者 [color keywords]. 这个选项在 `color` 选项为 `true` 时才工作。 |

### paginator

插入一个分页

``` js
<%- paginator(options) %>
```

选项 | 描述 | 默认值
--- | --- | ---
`base` | 基础URL | /
`format` | URL格式 | page/%d/
`total` | 每页的文章数 | 1
`current` | 当前页码 | 0
`prev_text` | 上一页的链接文字. 仅当 `prev_next` 被设置为 true 时才工作。 | Prev
`next_text` | 上一页的链接文字. 仅当 `prev_next` 被设置为 true 时才工作。 | Next
`space` | 空白文字 | &hellp;
`prev_next` | 显示上一页、下一页链接 | true
`end_size` | 在开始和结束部分显示的页码数 | 1
`mid_size` | 在中间显示的页码数（不包含当前页） | 2
`show_all` | 显示所有页码。 如果被设置为 true, `end_size` 和 `mid_size` 将不会工作。 | false

### date

插入格式化的日期。 `date` 可以是 UNIX 时间戳，ISO时间，date 对象，或者  moment.js 对象。`format` 默认是 `date_format` 设置。

``` js
<%- date(date, [format]) %>
```

**例子:**

``` js
<%- date(Date.now()) %>
// Jan 1, 2013

<%- date(Date.now(), 'YYYY/M/D') %>
// 2013/1/1
```

### date_xml

插入XML格式的日期。`date` 可以是 UNIX 时间戳，ISO时间，date 对象，或者  moment.js 对象。`format` 默认是 `date_format` 设置。

``` js
<%- date_xml(date) %>
```

**例子:**

``` js
<%- date_xml(Date.now()) %>
// 2013-01-01T00:00:00.000Z
```

### time

插入格式化的时间。`date` 可以是 UNIX 时间戳，ISO时间，date 对象，或者  moment.js 对象。`format` 默认是 `date_format` 设置。

``` js
<%- time(date, [format]) %>
```

**例子:**

``` js
<%- time(Date.now()) %>
// 13:05:12

<%- time(Date.now(), 'h:mm:ss a') %>
// 1:05:12 pm
```

### full_date

插入格式化的日期和时间。`date` 可以是 UNIX 时间戳，ISO时间，date 对象，或者  moment.js 对象。`format` 默认是 `date_format + time_format` 设置。

``` js
<%- full_date(date, [format]) %>
```

**例子:**

``` js
<%- full_date(new Date()) %>
// Jan 1, 2013 0:00:00

<%- full_date(new Date(), 'dddd, MMMM Do YYYY, h:mm:ss a') %>
// Tuesday, January 1st 2013, 12:00:00 am
```

### moment

[Moment.js] library.

### search_form

插入一个 Google 搜索表单。

``` js
<%- search_form(options) %>
```

选项 | 描述 | 默认值
--- | --- | ---
`class` | 表单的class值 | search-form
`text` | 搜索框的占位符 | Search
`button` | 显示搜索按钮，可以是字符串或者是布尔值，是字符串时显示为按钮文字 | false

### markdown

渲染一个 Markdown 字符串。

``` js
<%- markdown(str) %>
```

**例子:**

``` js
<%- markdown('make me **strong**') %>
// make me <strong>strong</strong>
```

### word_wrap

自动换行文字，每行不超过 `length` 。`length` 默认是 80。

``` js
<%- word_wrap(str, [length]) %>
```

**例子:**

``` js
<%- word_wrap('Once upon a time', 8) %>
// Once upon\n a time
```

### truncate

截断 `length` 后的字符串。

``` js
<%- truncate(text, length) %>
```

**例子:**

``` js
<%- truncate('Once upon a time in a world far far away', 16) %>
// Once upon a time
```

### truncate_words

截断 `length` 后的单词。

``` js
<%- truncate_words(text, length) %>
```

**例子:**

``` js
<%- truncate_words('Once upon a time in a world far far away', 4) %>
// Once upon a time
```

### link_to

插入一个链接。

``` js
<%- link_to(path, [text], [options]) %>
```

选项 | 描述 | 默认值
--- | --- | ---
external | 新标签页中打开 | false
class | class名称 |
id | ID |

**例子:**

``` js
<%- link_to('http://www.google.com') %>
// <a href="http://www.google.com" title="http://www.google.com">http://www.google.com</a>

<%- link_to('http://www.google.com', 'Google') %>
// <a href="http://www.google.com" title="Google">Google</a>

<%- link_to('http://www.google.com', 'Google', {external: true}) %>
// <a href="http://www.google.com" title="Google" target="_blank" rel="external">Google</a>
```

### mail_to

插入一个邮件链接。

``` js
<%- mail_to(path, [text], [options]) %>
```

选项 | 描述
--- | ---
class | class名称
id | ID
subject | 邮件主题
cc | CC
bcc | BCC
body | 邮件内容

**例子:**

``` js
<%- mail_to('a@abc.com') %>
// <a href="mailto:a@abc.com" title="a@abc.com">a@abc.com</a>

<%- mail_to('a@abc.com', 'Email') %>
// <a href="mailto:a@abc.com" title="Email">Email</a>
```

### image_tag

插入图片

``` js
<%- image_tag(path, [options]) %>
```

选项 | 描述
--- | ---
alt | 替代文字
class | class名称
id | ID
width | 图片宽度
height | 图片高度

### favicon_tag

插入一个favicon。

``` js
<%- favicon_tag(path) %>
```

### feed_tag

插入一个 feed link。

``` js
<%- feed_tag(path, [options]) %>
```

选项 | 描述 | 默认值
--- | --- | ---
title | Feed标题 |
type | Feed类型 | atom

### list_categories

插入所有分类列表。

``` js
<%- list_categories([options]) %>
```

选项 | 描述 | 默认值
--- | --- | ---
`orderby` | 排序依据 | name
`order` | 排序方式， `1`或者`asc`升序; `-1`或者`desc`降序 | 1
`show_count` | 显示每个分类的文章数 | true
`style` | 分类列表的显示样式 `list` 显示为无序列表  | list
`separator` | 分类间的分隔符 (当 `style` 为 `none` 时工作) | ,
`depth` | 分类的显示层级 `0` 显示所有分类和子分类; `-1` 与 `0` 相同但是没有树状结构; `1` 只显示一级分类 | 0
`class` | 分类列表的class | category

### list_tags

插入所有标签列表。

``` js
<%- list_tags([options]) %>
```

选项 | 描述 | 默认值
--- | --- | ---
`orderby` | 排序依据 | name
`order` | 排序方式， `1`或者`asc`升序; `-1`或者`desc`降序 | 1
`show_count` | 显示每个标签的文章数 | true
`style` | 标签列表的显示样式 `list` 显示为无序列表 | list
`separator` | 标签间的分隔符 (当 `style` 为 `none` 时工作) | ,
`class` | 标签列表的class | tag
`amount` | 显示的标签数目 (0 = 不限制) | 0

### list_archives

插入一个归档列表。

``` js
<%- list_archives([options]) %>
```

选项 | 描述 | 默认值
--- | --- | ---
`type` | 类型。 `yearly` 或者 `monthly`. | monthly
`order` | 排序方式， `1`或者`asc`升序; `-1`或者`desc`降序 | 1
`show_count` | 显示每一个归档的文章数 | true
`format` | 日期格式 | MMMM YYYY
`style` | 归档列表的显示样式 `list` 显示为无序列表 | list
`separator` | 归档间的分隔符 (当 `style` 为 `none` 时工作) | ,
`class` | 归档列表的class | category

### list_posts

插入一个文章列表

``` js
<%- list_posts([options]) %>
```

Option | Description | Default
--- | --- | ---
`ulClass` | 列表的class |
`liClass` | 每一个列表项的class |
`style` | 文章列表的显示样式 `list` 显示为无序列表 | list
`separator` | 文章间的分隔符 (当 `style` 为 `none` 时工作) | ,
`class` | 文章列表的class | post

### get_posts

获得多个文章内容

``` js
<% get_posts([options]) %>
```

选项 | 描述 | 默认值
--- | --- | ---
`count` | 文章个数 | 6
`orderby` | 排序依据 | date
`order` | 排序方式， `1`或者`asc`升序; `-1`或者`desc`降序 | -1
`query` | 查询条件 |

### number_format

格式化数字

``` js
<%- number_format(number, [options]) %>
```

选项 | 描述 | 默认值
--- | --- | ---
`precision` | 数的精度。 `false` 或者是一个非负整数 | false
`delimiter` | 千分符 | ,
`separator` | 小数点 | .

**例子:**

``` js
<%- number_format(12345.67, {precision: 1}) %>
// 12,345.68

<%- number_format(12345.67, {precision: 4}) %>
// 12,345.6700

<%- number_format(12345.67, {precision: 0}) %>
// 12,345

<%- number_format(12345.67, {delimiter: ''}) %>
// 12345.67

<%- number_format(12345.67, {separator: '/'}) %>
// 12,345/67
```

### open_graph

Inserts open graph data.

``` js
<%- open_graph([options]) %>
```

Option | Description | Default
--- | --- | ---
`title` | Page title (`og:title`) | `page.title`
`type` | Page type (`og:type`) | blog
`url` | Page URL (`og:url`) | `url`
`image` | Page cover (`og:image`) | First image in the content
`site_name` | Site name (`og:site_name`) | `config.title`
`description` | Page description (`og:desription`) | Page excerpt or first 200 characters of the content
`twitter_card` | Twitter card type (`twitter:card`) | summary
`twitter_id` | Twitter ID (`twitter:creator`) |
`twitter_site` | Twitter Site (`twitter:site`) |
`google_plus` | Google+ profile link |
`fb_admins` | Facebook admin ID |
`fb_app_id` | Facebook App ID |

### toc

Parses all heading tags (h1~h6) in the content and inserts a table of contents.

``` js
<%- toc(str, [options]) %>
```

Option | Description | Default
--- | --- | ---
`class` | Class name | toc
`list_number` | Displays list number | true

**Examples:**

``` js
<%- toc(page.content) %>
```

[color keywords]: http://www.w3.org/TR/css3-color/#svg-color

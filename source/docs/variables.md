title: 变量
---
### 全局变量

变量 | 描述
--- | ---
`site` | 站内信息
`page` | 页面的具体信息和前置数据里的变量
`config` | 站点设置
`theme` | 主题设置，继承站点设置
`_` (单个下划线) | [Lodash](http://lodash.com/) 库
`__` (双下划线) | 国际化 (i18n) 工具. 参阅下面的详细信息。
`path` | 当前页面的路径
`url` | 当前页面的完整URL

{% note tip 自定义变量 %}
你也可以在布局中使用前置数据就像在写文章时一样！
{% endnote %}

### 站点变量

下面所有的变量都是数据模型

变量 | 描述
--- | ---
`site.posts` | 所有文章
`site.pages` | 所有单页
`site.categories` | 所有分类
`site.tags` | 所有标签

### 页面变量

**文章 (这里的文章包括博文和单页等)**

变量 | 描述
--- | ---
`page.title` | 文章标题
`page.date` | 文章创建时间 ([Moment.js] object)
`page.updated` | 文章最后更新时间 ([Moment.js] object)
`page.categories` | 文章的所有分类
`page.tags` | 文章的所有标签
`page.comments` | 文章评论是否开启
`page.layout` | 布局名称
`page.content` | 文章全部处理的内容
`page.excerpt` | 文章的摘要内容
`page.source` | 源文件路径
`page.full_source` | 源文件的完整路径
`page.path` | 文章的URL. 在主题中使用 `url_for(page.path)` 得到.
`page.permalink` | 文章的完整URL
`page.prev` | 上一篇文章。如果这是第一篇文章那么它是 `null`。
`page.next` | 下一篇文章。如果这是最后一篇文章那么它是 `null`。
`page.raw` | 文章的原始数据
`page.photos` | 文章的图片 (Used in gallery posts)
`page.link` | 文章的外部链接 (Used in link posts)

{% note info 自定义前置数据 %}
前置数据可以在 `page` 中使用.
{% endnote %}

**首页 (index)**

变量 | 描述
--- | ---
`page.per_page` | 每页显示的文章数
`page.total` | 文章总数
`page.current` | 当前页码
`page.current_url` | 当前页的URL
`page.posts` | 当前页的文章 ([数据模型])
`page.prev` | 上一页的页码。 如果是第一页为 `0`。
`page.prev_link` | 上一页的URL。如果是第一页为 `''` 。
`page.next` | 下一页的页码。 如果最后一页为 `0`。
`page.next_link` | 下一页的URL。如果是最后一页为 `''` 。
`page.path` | 当前页面的URL（不包含根URL）。在主题中通过 `url_for(page.path)` 得到。

**归档 (archive):** 与 `index` 布局类似但是添加了以下变量。

变量 | 描述
--- | ---
`archive` | 固定为 `true`
`year` | 归档年份 (4位数字)
`month` | 归档月份 (2位数字，不含前导零)

**分类 (category):** 与 `index` 布局类似但是添加了以下变量。

变量 | 描述
--- | ---
`category` | 分类名称

**标签 (tag):** 与 `index` 布局类似但是添加了以下变量。

变量 | 描述
--- | ---
`tag` | 标签名称

[Moment.js]: http://momentjs.com/
title: 模型
---
Hexo 使用 [Warehouse](https://github.com/tommy351/warehouse) 来保存所有数据。你可以查看 [API](/api/warehouse/classes/Database.html) 和查看下面的数据模型内容。

### 博文

名称 | 描述
--- | ---
`id` | 博文ID (用户设置)
`title` | 博文标题
`date` | 博文日期 ([Moment.js] 对象)
`updated` | 博文最后更新日期 ([Moment.js] 对象)
`categories` | 博文的所有分类
`tags` | 博文的所有标签
`comments` | 博文的所有评论
`layout` | 布局名称
`content` | 完整的处理过的内容
`excerpt` | 摘要
`source` | 源文件路径
`full_source` | 完整源文件路径
`path` | 不包含根目录的URL
`permalink` | 完整URL
`raw` | 原始内容
`photos` | 文章图片 (Used in gallery posts)
`link` | 文正外部链接 (Used in link posts)

### 单页

标题 | 描述
--- | ---
`title` | 文章标题
`date` | 文章日期 ([Moment.js] 对象)
`updated` | 文章最后更新时间 ([Moment.js] 对象)
`comments` | 评论是否打开
`layout` | 布局名称
`content` | 完整的处理过的内容
`excerpt` | 摘要
`source` | 源文件路径
`full_path` | 完整源文件路径
`path` | 不包含根目录的URL
`permalink` | 完整URL
`raw` | 原始内容

### 分类

名称 | 描述
--- | ---
`name` | 分类名称
`slug` | Category slug
`posts` | 分类中的所有文章
`path` | 不包含根目录的URL
`permalink` | 完整URL
`length` | 分类中的文章数
`parent` | 父级分类

### 标签

名称 | 描述
--- | ---
`name` | 标签名称
`slug` | Tag slug
`posts` | 标签中的所有文章
`path` | 不包含根目录的URL
`permalink` | 完整URL
`length` | 标签中的文章数

[Moment.js]: http://momentjs.com/
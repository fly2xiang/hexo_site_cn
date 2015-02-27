title: 分页
---
在你博客中的文章增多之后，分页是非常有用的。Hexo 支持分页，下面介绍在Hexo中如何使用分页。

Before we start, you have to enable pagination. Edit `per_page` setting to change how many posts displayed in a single page. To disable pagination, just set it to `0`.
开始之前，你必须开启分页。编辑 `per_page` 设置来更改一个页面中显示的文章的个数。想要禁用分页，把它设置为 `0` 即可。

``` yaml
per_page: 10
```

你可以编辑下面的设置来启用或禁用分页。

- 2: 开启分页
- 1: 禁用分页
- 0: 全面禁用

``` yaml
archive: 2
category: 2
tag: 2
```

## 基础

The most basic pagination is just two links: "Previous page" & "Next page". For example:
最基本的分页就是两个链接："上一页" & "下一页"。例如：

```
<% if (page.prev){ %>
  <a href="<%- url_for(page.prev_link) %>">上一页</a>
<% } %>
<% if (page.next){ %>
  <a href="<%- url_for(page.next_link) %>">下一页</a>
<% } %>
```

## 分页助手

想要在分页中显示数字，你可以使用分页助手（paginator helper）。它帮助你快速插入分页。

```
<%- paginator() %>
```

更多信息请查看：[Helpers](/docs/helpers.html#paginator).

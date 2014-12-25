title: 标签插件
---
标签插件与文章中的标签是不同的。他们是从 Octopress 移植过来可以帮助你在文章中插入具体的内容。

## 区块引用

插入引用到文章中，连同作者、来源以及标题。

**别名:** quote

{% raw %}
<figure class="highlight"><pre>{% blockquote [author[, source]] [link] [source_link_title] %}
content
{% endblockquote %}
</pre></figure>
{% endraw %}

### 例子

**没有参数，输出块引用**

{% raw %}
<figure class="highlight"><pre>{% blockquote %}
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Pellentesque hendrerit lacus ut purus iaculis feugiat. Sed nec tempor elit, quis aliquam neque. Curabitur sed diam eget dolor fermentum semper at eu lorem.
{% endblockquote %}
</pre></figure>
{% endraw %}

{% blockquote %}
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Pellentesque hendrerit lacus ut purus iaculis feugiat. Sed nec tempor elit, quis aliquam neque. Curabitur sed diam eget dolor fermentum semper at eu lorem.
{% endblockquote %}

**引用一本书中的段落**

{% raw %}
<figure class="highlight"><pre>{% blockquote David Levithan, Wide Awake %}
Do not just seek happiness for yourself. Seek happiness for all. Through kindness. Through mercy.
{% endblockquote %}
</pre></figure>
{% endraw %}

{% blockquote David Levithan, Wide Awake %}
Do not just seek happiness for yourself. Seek happiness for all. Through kindness. Through mercy.
{% endblockquote %}

**引用 Twitter 内容**

{% raw %}
<figure class="highlight"><pre>{% blockquote @DevDocs https://twitter.com/devdocs/status/356095192085962752 %}
NEW: DevDocs now comes with syntax highlighting. http://devdocs.io
{% endblockquote %}
</pre></figure>
{% endraw %}

{% blockquote @DevDocs https://twitter.com/devdocs/status/356095192085962752 %}
NEW: DevDocs now comes with syntax highlighting. http://devdocs.io
{% endblockquote %}

**引用网上的一篇文章**

{% raw %}
<figure class="highlight"><pre>{% blockquote Seth Godin http://sethgodin.typepad.com/seths_blog/2009/07/welcome-to-island-marketing.html Welcome to Island Marketing %}
Every interaction is both precious and an opportunity to delight.
{% endblockquote %}
</pre></figure>
{% endraw %}

{% blockquote Seth Godin http://sethgodin.typepad.com/seths_blog/2009/07/welcome-to-island-marketing.html Welcome to Island Marketing %}
Every interaction is both precious and an opportunity to delight.
{% endblockquote %}

## 代码块

在文章中插入代码块

**别名:** code

{% raw %}
<figure class="highlight"><pre>{% codeblock [title] [lang:language] [url] [link text] %}
code snippet
{% endcodeblock %}
</pre></figure>
{% endraw %}

### 例子

**一般的代码块**

{% raw %}
<figure class="highlight"><pre>{% codeblock %}
alert('Hello World!');
{% endcodeblock %}
</pre></figure>
{% endraw %}

{% codeblock %}
alert('Hello World!');
{% endcodeblock %}

**指定语言的代码块**

{% raw %}
<figure class="highlight"><pre>{% codeblock lang:objc %}
[rectangle setX: 10 y: 10 width: 20 height: 20];
{% endcodeblock %}
</pre></figure>
{% endraw %}

{% codeblock lang:objc %}
[rectangle setX: 10 y: 10 width: 20 height: 20];
{% endcodeblock %}

**带标题的代码块**

{% raw %}
<figure class="highlight"><pre>{% codeblock Array.map %}
array.map(callback[, thisArg])
{% endcodeblock %}
</pre></figure>
{% endraw %}

{% codeblock Array.map %}
array.map(callback[, thisArg])
{% endcodeblock %}

**带 URL 的代码块**

{% raw %}
<figure class="highlight"><pre>{% codeblock _.compact http://underscorejs.org/#compact Underscore.js %}
_.compact([0, 1, false, 2, '', 3]);
=> [1, 2, 3]
{% endcodeblock %}
</pre></figure>
{% endraw %}

{% codeblock _.compact http://underscorejs.org/#compact Underscore.js %}
_.compact([0, 1, false, 2, '', 3]);
=> [1, 2, 3]
{% endcodeblock %}

## 反引号代码块

这个插件是一个类似的代码块，只是使用单引号样式。

{% code %}
``` [language] [title] [url] [link text]
code snippet
```
{% endcode %}

## Pull Quote

这个插件帮助你在文章中插入一个 pull quote。

{% raw %}
<figure class="highlight"><pre>{% pullquote [class] %}
content
{% endpullquote %}
</pre></figure>
{% endraw %}

## jsFiddle

在文章中嵌入一段 jsFiddle 片段。

{% raw %}
<figure class="highlight"><pre>{% jsfiddle shorttag [tabs] [skin] [width] [height] %}
</pre></figure>
{% endraw %}

## Gist

在文章中嵌入一段 Gist 片段。

{% raw %}
<figure class="highlight"><pre>{% gist gist_id [filename] %}
</pre></figure>
{% endraw %}

## iframe

在文章中嵌入 iframe 片段。

{% raw %}
<figure class="highlight"><pre>{% iframe url [width] [height] %}
</pre></figure>
{% endraw %}

## 图片

在文章中插入指定大小的图片。

{% raw %}
<figure class="highlight"><pre>{% img [class names] /path/to/image [width] [height] [title text [alt text]] %}
</pre></figure>
{% endraw %}

## 链接

插入一个包含 `target="_blank"` 属性的链接。

{% raw %}
<figure class="highlight"><pre>{% link text url [external] [title] %}
</pre></figure>
{% endraw %}

## 包含代码

插入 `source` 文件夹中的代码片段。

{% raw %}
<figure class="highlight"><pre>{% include_code [title] [lang:language] path/to/file %}
</pre></figure>
{% endraw %}

## Youtube

在文章中插入一个 Youtube 视频。

{% raw %}
<figure class="highlight"><pre>{% youtube video_id %}
</pre></figure>
{% endraw %}

## Vimeo

在文章中插入一个 Vimeo 视频。

{% raw %}
<figure class="highlight"><pre>{% vimeo video_id %}
</pre></figure>
{% endraw %}

## 原始内容

如果你不想让一些内容被处理，你可以用 `rawblock` 标签包裹。

{% raw %}
<figure class="highlight"><pre>{% rawblock %}
content
{% endrawblock /%}
</pre></figure>
{% endraw %}
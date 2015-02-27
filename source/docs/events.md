title: 事件
---
## 概述

Hexo 继承了 Node.js 的 EventEmitter。你可以订阅或者发布指定事件。例如：

``` js
hexo.on('ready', function(){
  console.log('Hexo is ready to go!');
});
```

## 事件

### ready

Hexo 初始化完成后被调用一次。

### generateBefore

生成之前被调用。

### generateAfter

生成之后被调用。

### processBefore

处理之前被调用。

参数 | 描述
--- | ---
`path` | Base path of the processor

### processAfter

处理之后被调用。

参数 | 描述
--- | ---
`path` | Base path of the processor

### new

新的博文文件被创建后被调用。

参数 | 描述
--- | ---
`path` | 绝对路径
`content` | 文件内容

### server

服务器开启之后被调用。

### exit

Hexo 退出之后被调用。

### deployBefore

发布之前被调用。

### deployAfter

发布之后被调用。
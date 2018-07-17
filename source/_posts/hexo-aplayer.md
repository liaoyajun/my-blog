---
title: hexo 中插入音频
date: 2018-07-16 21:38:16
tags:
  - hexo
  - 插件
  - audio
---
## 插入音频的方法

### 安装插件

``` bash
npm install hexo-tag-aplayer  --save
```

### 手动创建缺失的文件

- 在 node_modules\aplayer\dist 目录下手动创建 `font` 文件夹
- 在 node_modules\aplayer\dist 目录下手动创建 `APlayer.min.css` 文件

### 测试aplayer

[aplayer 参数文档](https://github.com/liaoyajun/hexo-tag-aplayer)
``` plain
{% aplayer title author url [picture_url, narrow, autoplay, width:xxx, lrc:xxx] %}
```
{% aplayer "爱要怎么说出口" "赵传" "./赵传 - 爱要怎么说出口.mp3" "赵传 - 爱要怎么说出口.jpeg" "autoplay" "width:100%" "lrc:爱要怎么说出口-赵传.lrc" %}

### 直接在 Markdown 插入

Markdown 是兼容 html 语法的，所以我们可以直接在 Markdown 文档中使用 html 语法。

iframe 标签
``` html
<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width=330 height=86 src="//music.163.com/outchain/player?type=2&id=189164&auto=1&height=66"></iframe>
```
<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width=330 height=86 src="//music.163.com/outchain/player?type=2&id=189164&auto=1&height=66"></iframe>

embed 标签
``` html
<embed src="//music.163.com/style/swf/widget.swf?sid=189164&type=2&auto=1&width=320&height=66" width="340" height="86"  allowNetworking="all"></embed>
```
<embed src="//music.163.com/style/swf/widget.swf?sid=189164&type=2&auto=1&width=320&height=66" width="340" height="86"  allowNetworking="all"></embed>




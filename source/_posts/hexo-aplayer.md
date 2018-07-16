---
title: hexo中插入音频
date: 2018-07-16 21:38:16
tags:
  - hexo
  - 插件
  - audio
---
## 插入音频的方法

### 1、安装插件

``` bash
npm install hexo-tag-aplayer  --save
```

### 2、手动创建node_modules中缺失的文件

- 在node_modules\aplayer\dist目录下手动创建`font`文件夹
- 在node_modules\aplayer\dist目录下手动创建`APlayer.min.css`文件

### 3、测试aplayer

``` plain
{% aplayer "歌名" "歌手" "http://win.web.ra01.sycdn.kuwo.cn/1604c198d8615bb5e52cfbb8f9ed4dfb/5b4c9ad7/resource/n3/320/68/81/877593876.mp3" "autoplay" %}
```
{% aplayer "歌名" "歌手" "http://win.web.ra01.sycdn.kuwo.cn/1604c198d8615bb5e52cfbb8f9ed4dfb/5b4c9ad7/resource/n3/320/68/81/877593876.mp3" "autoplay" %}

### 4、Markdown 插入

Markdown 是兼容 html 语法的，所以我们可以直接在 Markdown 文档中使用 html 语法。

iframe 标签
``` html
<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width=330 height=86 src="//music.163.com/outchain/player?type=2&id=30251317&auto=1&height=66"></iframe>
```
<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width=330 height=86 src="//music.163.com/outchain/player?type=2&id=30251317&auto=1&height=66"></iframe>

embed 标签
``` html
<embed src="//music.163.com/style/swf/widget.swf?sid=30251317&type=2&auto=1&width=320&height=66" width="340" height="86"  allowNetworking="all"></embed>
```
<embed src="//music.163.com/style/swf/widget.swf?sid=30251317&type=2&auto=1&width=320&height=66" width="340" height="86"  allowNetworking="all"></embed>




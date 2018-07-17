---
title: hexo 中插入视频
date: 2018-07-16 21:38:24
tags:
  - hexo
  - 插件
  - video
---
## 插入视频的方法

### 安装插件

``` bash
npm install hexo-tag-dplayer  --save
```

### 手动创建缺失的文件

- 在 node_modules\dplayer\dist 目录下手动创建 `DPlayer.min.css` 文件

### 测试 dplayer

[dplayer 参数文档](https://github.com/liaoyajun/hexo-tag-dplayer)
``` plain
{% dplayer key=value ... %}
```
{% dplayer "url=夜曲.mp4" "loop=yes" "theme=#FADFA3" "autoplay=false" %}

### 直接在 Markdown 插入

Markdown 是兼容 html 语法的，所以我们可以直接在 Markdown 文档中使用 html 语法。

vedio 标签
``` html
<video src="./红玫瑰.mp4" id="video" controls="controls" preload="auto" webkit-playsinline="true" x5-video-player-type="h5" x5-video-player-fullscreen="true" playsinline></video>
```
<video src="./红玫瑰.mp4" id="video" controls="controls" preload="auto" webkit-playsinline="true" x5-video-player-type="h5" x5-video-player-fullscreen="true" playsinline></video>

iframe 标签
``` html
<iframe src="//player.bilibili.com/player.html?aid=24185473&cid=40540394&page=1" width=680 height=556 scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"> </iframe>
```
<iframe src="//player.bilibili.com/player.html?aid=24185473&cid=40540394&page=1" width=680 height=556 scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"> </iframe>

embed 标签
``` html
<embed src="https://imgcache.qq.com/tencentvideo_v1/playerv3/TPout.swf?max_age=86400&v=20161117&vid=j0689lrdcjs&auto=0" allowFullScreen="true" quality="high" width="670" height="377" align="middle" allowScriptAccess="always" type="application/x-shockwave-flash"></embed>
```
<embed src="https://imgcache.qq.com/tencentvideo_v1/playerv3/TPout.swf?max_age=86400&v=20161117&vid=j0689lrdcjs&auto=0" allowFullScreen="true" quality="high" width="670" height="377" align="middle" allowScriptAccess="always" type="application/x-shockwave-flash"></embed>

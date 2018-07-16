---
title: hexo笔记
date: 2018-07-16 18:22:00
share: true
tags:
  - hexo
  - 笔记
---
使用[Hexo](https://hexo.io/)和[github](https://github.com/liaoyajun)搭建个人博客，博客主题选择了[Yelee主题](http://moxfive.coding.me/yelee/)。

## step 1

### 安装hexo脚手架

``` bash
npm install hexo-cli -g
```

### 初始化博客

``` bash
hexo init  # 或者简写 hexo i
```

### 生成静态页面

``` bash
hexo generate  # 或者简写 hexo g
```

### 本地启动

``` bash
hexo server  # 或者简写 hexo s
```

### 配置github

1、建好名为[user_name.github.io](https://github.com/liaoyajun/liaoyajun.github.io)的代码仓库

2、安装hexo部署git依赖模块
``` bash
npm install hexo-deployer-git --save
```

3、修改项目根目录`_config.yml`文件[deploy](https://hexo.io/docs/deployment.html)参数
``` bash
deploy:
  type: git
  repo: <repository url>
  branch: [branch]
  message: [message]
```

### 部署到github

``` bash
hexo clean && hexo generate && hexo deploy  # 或者简写 hexo clean && hexo g && hexo d
```

### 其他常用指令

``` bash
hexo new postName # 新建文章
hexo new page postName # 新建页面
```

## step 2

### 设置标签云

1、安装插件
``` bash
npm install hexo-tag-cloud --save
```

### 自定义站点内容搜索

1、安装插件
``` bash
npm install hexo-generator-search --save
```

2、修改项目根目录`_config.yml`文件[search](https://github.com/wzpan/hexo-generator-search)参数
``` bash
search:
  path: search.xml
  field: post
```

### 博文插入图片

1、安装插件
``` bash
npm install hexo-asset-image --save
```

2、修改项目根目录`_config.yml`文件post_asset_folder参数
``` bash
post_asset_folder: true
```

3、再运行hexo n "xxxx"来生成md博文时，/source/\_posts文件夹内除了xxxx.md文件还有一个同名的文件夹

4、在xxxx.md中想引入图片时，先把图片复制到xxxx这个文件夹中，然后只需要在xxxx.md中按照markdown的格式引入图片
``` bash
![替代文字](xxxx/图片名.jpg)
```

---
title: CentOS 上搭建 Git 服务器
date: 2018-07-26 17:28:18
tags:
  - centos
  - git
---
- 1、安装 `git`

``` bash
yum install git
```

- 2、创建一个 `git` 用户组和用户

``` bash
groupadd git
adduser git -g git
```

- 3、禁止 `git` 用户登录

``` bash
# 打开 /etc/passwd 文件夹
vi /etc/passwd
# 将
git:x:???:???::/home/git:/bin/bash
# 改为
git:x:???:???::/home/git:/bin/git-shell
```

- 4、创建证书登录

``` bash
mkdir /home/git/.ssh
chmod 700 /home/git/.ssh
touch 700 /home/git/.ssh/authorized_keys
chmod 600 /home/git/.ssh/authorized_keys
```

- 5、将 `/home/git/.ssh/` 的 `owner` 设置为 `git`

``` bash
sudo chown -R git:git /home/git/.ssh/
```

- 6、编辑 `/home/git/.ssh/authorized_keys` ，把客户端的公钥放进去，每个公钥占一行

``` bash
vi /home/git/.ssh/authorized_keys
```

- 7、初始化 `git` 仓库

``` bash
cd /srv
mkdir gitrepo
chown git:git gitrepo/
cd gitrepo
# 创建一个空的 git 仓库，服务器上的 git 仓库通常都以 .git 结尾
git init --bare project.git
# 将仓库所属用户改为 git
chown -R git:git project.git
```

- 8、克隆仓库到本地

``` bash
git clone ssh://username@yourServer:Port/srv/gitrepo/project.git
# ssh 端口为 22 时可简写为
git clone git@yourServer:/srv/gitrepo/project.git
```



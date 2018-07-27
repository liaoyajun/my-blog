---
title: Linux 修改 ssh 端口
date: 2018-07-26 17:01:19
tags:
  - Linux
  - vps
  - ssh
---
### 修改默认 ssh 端口

``` bash
vi /etc/ssh/sshd_config
# 修改
# # Port 22
# 为
# Port new_port
```
<!--more-->

### 防火墙上打开 new_port

``` bash
iptables -I INPUT -p tcp -m state --state NEW -m tcp --dport new_port -j ACCEPT
```

### 查看 new_port 是否开放

``` bash
iptables -nL --line-number
# 显示
# 1    ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            state NEW tcp dpt:new_port
```

### 重启 ssh 服务

``` bash
systemctl restart sshd.service
```

### 设置免密登录

``` bash
ssh-copy-id -i ~/.ssh/id_rsa.pub root@ip -p ssh_port
```

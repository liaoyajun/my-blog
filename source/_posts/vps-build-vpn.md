---
title: 搬瓦工VPS搭建VPN
date: 2018-07-19 16:13:44
tags:
  - 搬瓦工
  - vps
  - vpn
  - kcptun
---
## 安装shadowsocks server

1. 登录 [搬瓦工](https://bwh1.net/clientarea.php)

2. 打开 [KiwiVM](https://kiwivm.64clouds.com/main.php)

3. `Main controls` 中停止运行系统

4. `Install new OS` ，选择 `centos-6-x86` 系统，记下 `ssh` 的 `password` 和 `port`

5. 本地终端登录
``` bash
ssh -l root -p ssh_port IP
```

6. 一键安装 [shadowsocks](https://kiwivm.64clouds.com/preloader.php?load=/main-exec.php?mode=extras_shadowsocks) (不推荐)

7. 手动安装 `shadowsocks`
``` bash
# 更新 `yum`
yum -y update

# 安装 `wget`
yum -y install wget

# 安装 `shadowsocks`
wget –no-check-certificate https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocks.sh

# 修改文件权限
chmod +x shadowsocks.sh

# 配置参数(密码、端口、加密方式等)
./shadowsocks.sh 2>&1 | tee shadowsocks.log

# 安装完成
```

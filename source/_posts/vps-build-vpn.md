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

# 配置参数(密码******、端口443、加密方式aes-256-cfb等)
./shadowsocks.sh 2>&1 | tee shadowsocks.log

# 安装完成
```
## 安装kcptun

``` bash
# 新 https://github.com/kuoruan/shell-scripts/raw/master/kcptun/kcptun.sh
wget https://raw.githubusercontent.com/kuoruan/kcptun_installer/master/kcptun.sh

# 修改权限
chmod +x ./kcptun.sh

# 配置参数 加速端口和ss输出端口对应
./kcptun.sh

# 完成

# 通过 supervisor 管理 kcptun 状态
# {启动|关闭|重启|查看状态}
supervisorctl {start|stop|restart|status} kcptun<id>

```
[kcptun 作者 blog](https://blog.kuoruan.com/)

## 客户端使用

1. 下载[ kcptun 客户端文件](https://github.com/xtaci/kcptun/releases/tag/v20170315) `client_darwin`

2. 运行 `kcptun`
``` bash
sudo ./client_darwin_386 -l local_ip:local_port -r remote_ip:remote_port -mode 加速模式 -key "password"
```

3. 运行 `shadowsocks` 客户端
  - 地址 ip : 客户端运行的 `kcptun` 的 `local_ip`
  - 地址 port : 客户端运行的 `kcptun` 的 `local_port`
  - 密码: 远程 `shadowsocks` 的密码









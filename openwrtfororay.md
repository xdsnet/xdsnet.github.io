# OpenWrt使用花生壳脚本

OpenWrt作为常见路由器系统，提供了较强的`sh`环境，这使得其可以很好的利用花生壳提供的网页版实现公网环境下的动态域名解析支持。


## `sh`脚本(文件名：OpenWrtForOray)
```sh
#!/bin/sh -
# filename:OpenWrtForOray
# USER值为花生壳用户名
USER="nameid"
# PASS值为花生壳对应登录密码
PASS="password"
# DOMAIN值为该用户下可使用的域名
DOMAIN="hostname.vicp.cc"
# IPPORT值是在OpenWrt上配置的可获取公网IP地址的网口，家用一般是 pppoe-wan
IPPORT="pppoe-wan"

# 下面的代码获取到实际的公网 IP 地址
IP=$(ifconfig ${IPPORT} |awk -F "[: ]+" '/inet addr/{print $4}')

# 下面生成完整的花生壳网页版调用URL地址
URL="http://${USER}:${PASS}@ddns.oray.com:80/ph/update?hostname=${DOMAIN}&myip=${IP}"

# 下面的代码检测是否发生IP地址变化，如果没有变化就不产生实际调用
if [ -f /tmp/oray ];then
        OLD_IP=$(cat /tmp/oray | awk '{print $2}')
        if [ "${OLD_IP}" = "${IP}" ];then
                exit
        fi
fi
wget -q -O /tmp/oray -q ${URL}
```
## 脚本的放置与处理

把脚本放置到 `/etc/hotplug.d/iface/` 目录下，执行

```bash
chmod a+x /etc/hotplug.d/iface/OpenWrtForOray
```

再编辑 `/etc/crontabs/root`文档，添加重复执行的命令，比如可以执行下面的命令：

```bash
echo */1 * * * * /etc/hotplug.d/iface/OpenWrtForOray start >> /etc/crontabs/root
```

再重新启动路由器的定时任务服务

```bash
/etc/init.d/cron restart
```

正确的话可通过命令

```bash
ps | grep cron
```

查看`cron`是否启动成功，一般显示为：

```
2999 root 1508 S /usr/sbin/crond -c /etc/crontabs -l 6
3000 root 1495 S grep cront
```

## 多个域名的处理

因为一个花生壳用户可以管理多个域名，如果想在这个路由器上绑定多个域名，有两个方法

1. 按前述步骤制作多份脚本，命名为不同的名字，并添加到循环执行中去
2. 修改脚本，主要修改涉及 `DOMAIN` 值的地方，比如修改为  `DOMAIN1` `DOMAIN2` ... `DOMAINN` ，对应产生 `URL1` `URL2` ... `URLN`，然后后面 `wget`语句处改为多个：

```bash
wget -q -O /tmp/oray -q ${URL1}
wget -q -O /tmp/oray -q ${URL2}
...
wget -q -O /tmp/oray -q ${URLN}
```

即可。

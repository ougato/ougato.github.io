---
layout: post
title: "VMWare 安装 CentOS 没有 eth0 网卡"
date: 2022-05-30 17:01:38 +0800
categories: VMWare
tags: VMWare CentOS
author: ougato
mathjax: true
---

* content
{:toc}




# VMWare 安装 CentOS 没有 eth0 网卡

## 只存在 ens33 和 lo 网卡 解决方案

1. **NAME** 和 **DEVICE** 字段改为 **eth0**

```shell
vi /etc/sysconfig/network-scripts/ifcfg-ens33
```

2. 重命名网卡 

```shell
mv /etc/sysconfig/network-scripts/ifcfg-ens33 /etc/sysconfig/network-scripts/ifcfg-ens0
```

3. 插入 `net.ifnames=0 biosdevname=0` 配置到 **GRUB_CMD_LINE_LINUX** 字段中（以空格区分）

```shell
vi /etc/default/grub
```

4. 更新配置

```shell
grub2-mkconfig -o /boot/grub2/grub.cfg
```

5. 重启

```shell
reboot
```
---
title: Ubuntu for Win10 编译K3 syncdial 单线多拨
date: 2018-01-20 01:37:15
tags:
---

K3刷了LEDE想单线多拨，发现软件源内没有syncdial。手动设置感觉麻烦(没设置过啊，一键多好)
![脸上笑嘻嘻,心里MMP](lede-k3-compile-syncdial/1516378730321.png)

编译需要在Linux环境下，虚拟机不想折腾了。。懒得装的，所以用Ubuntu for Win10来试试（在微软商店下载），然后 控制面板 > 程序 > 启动或关闭Windows功能
勾上`适用于Linux的Windows子系统`

## 下载LEDE K3 SDK
> 可以在windows下载, 也可以在ubuntu wget

中国科大提供了openwrt镜像和代理连接[	openwrt.proxy.ustclug.org](	openwrt.proxy.ustclug.org)
SDK地址:[lede-sdk-17.01.4-bcm53xx_gcc-5.4.0_musl-1.1.16_eabi.Linux-x86_64](http://openwrt.proxy.ustclug.org/releases/17.01.4/targets/bcm53xx/generic/lede-sdk-17.01.4-bcm53xx_gcc-5.4.0_musl-1.1.16_eabi.Linux-x86_64.tar.xz)
```bash
# 切换到D盘目录并建立文件夹lede
cd /mnt/d/ && mkdir lede
#下载SDK
wget http://openwrt.proxy.ustclug.org/releases/17.01.4/targets/bcm53xx/generic/lede-sdk-17.01.4-bcm53xx_gcc-5.4.0_musl-1.1.16_eabi.Linux-x86_64.tar.xz
# 解压SDK 到lede-sdk目录
tar xvJf lede-sdk-17.01.4-bcm53xx_gcc-5.4.0_musl-1.1.16_eabi.Linux-x86_64.tar.xz -C lede-sdk
# 切换到sdk目录
cd lede-sdk
# 安装依赖软件
sudo apt-get update
sudo apt-get install build-essential asciidoc binutils bzip2 gawk gettext git libncurses5-dev libz-dev patch unzip zlib1g-dev lib32gcc1 libc6-dev-i386 subversion flex uglifyjs git-core gcc-multilib p7zip p7zip-full msmtp libssl-dev texinfo libglib2.0-dev
```

## 编译luci-app-syncdial 

```


> MARK 软件包来自[https://github.com/coolsnowwolf/lede](https://github.com/coolsnowwolf/lede/)
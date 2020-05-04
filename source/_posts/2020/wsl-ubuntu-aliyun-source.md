---
title: WSL-Ubuntu-18.04 阿里云源
date: 2020-05-04 22:05:39
categories: 
- 折腾
tags:
- WSL
---

windows subsystem linux ubuntu安装的版本默认源仓库在国外,此文为替换国内源一个记录,同时适用于所有Ubuntu-18.04系统

阿里云源地址:[https://developer.aliyun.com/mirror/](https://developer.aliyun.com/mirror/)

#### 查看现有ubuntu软件源信息

```bash
cat /etc/apt/sources.list
```

**结果：**

```sh
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu/ bionic main restricted
# deb-src http://archive.ubuntu.com/ubuntu/ bionic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ bionic-updates main restricted
# deb-src http://archive.ubuntu.com/ubuntu/ bionic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ bionic universe
# deb-src http://archive.ubuntu.com/ubuntu/ bionic universe
deb http://archive.ubuntu.com/ubuntu/ bionic-updates universe
# deb-src http://archive.ubuntu.com/ubuntu/ bionic-updates universe
....
```

#### 更换软件源

```bash
# 先备份
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak  

# 在替换
sudo sed -i "s/security.ubuntu/mirrors.aliyun/g" /etc/apt/sources.list
sudo sed -i "s/archive.ubuntu/mirrors.aliyun/g" /etc/apt/sources.list

# 后更新
sudo apt update
```

---
layout: post
title: "Mac 下制作 ubuntu 安装 U 盘"
date: 2016-07-06 19:41:48 +0800
comments: true
categories: Mac
---

测试环境版本：Mac 10.8.4 ubuntu 13.04

1.将ISO转换成IMG:

```bash
hdiutil convert -format UDRW -o ubuntu-13.04-desktop-i386.img ubuntu-13.04-desktop-i386.iso
```
<!--more-->

2.查看磁盘设备名，找到U盘的设备名

```bash
diskutil list
```

3.卸载U盘

```bash
diskutil umountDisk /dev/disk1
```

4.使用dd将ubuntu的img写入U盘

```bash
sudo dd if=ubuntu-13.04-desktop-i386.img.dmg of=/dev/disk1 bs=1m
```

5.完成！
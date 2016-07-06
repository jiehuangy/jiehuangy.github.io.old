---
layout: post
title: "Ubuntu 14.10 安装 ffmpeg"
date: 2016-07-06 23:46:05 +0800
comments: true
categories: Linux
---

#### 1.安装命令：
```sh
sudo add-apt-repository ppa:kirillshkrogalev/ffmpeg-next
sudo apt-get update
sudo apt-get install ffmpeg
```
<!--more-->

#### 2.Using ffmpeg

Syntax

```sh
ffmpeg [[infile options][-i infile]]... {[outfile options] outfile}...
```

FFmpeg Examples

```sh
ffmpeg -i input.avi -b:v 64k -bufsize 64k output.avi
```

强制视频为 24 帧

```sh
ffmpeg -i input.avi -r 24 output.avi
```

To force the frame rate of the input file (valid for raw formats only) to 1 fps and the frame rate of the output file to 24 fps

```sh
ffmpeg -r 1 -i input.m2v -r 24 output.avi
```

[完整文档](https://www.ffmpeg.org/ffmpeg.html)
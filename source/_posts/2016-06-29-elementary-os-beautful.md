---
layout: post
title: Elementary OS 美化
date: 2016-06-29 19:25:35 +0800
comments: true
categories: Linux
---
### Contents
{:.no_toc}
* a random unordered list with only one item
{:toc}

### 1. 安装 `tweak`

```
sudo apt-add-repository ppa:versable/elementary-update
sudo apt-get update
sudo apt-get install elementary-tweaks
```
<!-- more -->

### 2. 修改 Terminal 字体大小

#### 方法一：安装 dconf-editor

```
$ sudo apt-get install dconf-tools
```

只针对终端设置字体类型：org -> pantheon -> terminal -> settings -> font 输入要设置的值语法同上。

#### 方法二：使用 gsettings 命令设置

```
$ gsettings set org.pantheon.terminal.settings font 'Droid Sans Mono 12'
```

### 3. 修改 Terminal 主题
uncomment `~/.bashrc` 中的 `force_color_prompt=yes:`

主题 Gogh [Github](https://github.com/Mayccoll/Gogh)

```
$ wget -O xt  http://git.io/v3D4o && chmod +x xt && ./xt && rm xt
```

### 4. 安装oh-my-zsh “agnoster” 主题依赖的 “powerline” 字体
下载字体 [Github](https://github.com/powerline/fonts)，将相应字体拷贝到`～/.local/share/fonts/`文件夹下

```
$ cp Droid\ Sans\ Mono\ for\ Powerline.otf  ～/.local/share/fonts/
```
修改`tweaks`->`fonts`->`Monospace`成`Powerline`字体 

### 5. 添加最小化按钮
 在`tweaks`->`appearence`->`Windows Controls`中选择`Minimize Left`

```
gconftool-2 --set /apps/metacity/general/button_layout --type string "close,minimize,maximize"
```


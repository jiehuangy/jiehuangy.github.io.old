---
layout: post
title: "ubuntu install latex"
date: 2016-07-07 00:04:30 +0800
comments: true
categories: Linux
---

可以在 Ubuntu 安装很多 LaTeX 的分发版，其中一个是 TeX Live。

- 使用下面命令可以在 Ubuntu 上安装 Tex Live

{% coderay lang:shell %}
sudo apt-get install texlive-full
{% endcoderay %}

<!--more-->

- 要编辑 LaTeX 文档需要一个编辑器，你可以找到很多编辑器，这里我们推荐 Texmaker


{% coderay lang:shell %}
sudo apt-get install texmaker
{% endcoderay %}

- 在 Ubuntu 下执行下面命令可以打开 Texmaker 编辑器：

{% coderay lang:latex %}
texmaker
{% endcoderay %}


- 现在让我们用 Texmaker 创建一个简单的文档，点击 File -> New 然后在新文档中插入如下内容：

{% coderay lang:latex %}
\documentclass{article}
\begin{document}
Hello oschina!
\end{document}
{% endcoderay %}


- 接下来使用 File -> Save 将文档保存为一个扩展名为 tex 的文件，然后点击 Quick Build 来编译文档：

{% imgcap center {{ root_url }}/images/2016-07-07-ubuntu-install-latex.jpg 800 800 %}

[OSCHINA](http://www.oschina.net/question/12_63776?fromerr=9YSLPyM7)原创翻译
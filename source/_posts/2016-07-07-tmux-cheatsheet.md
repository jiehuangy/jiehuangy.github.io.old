---
layout: post
title: "Tmux Cheatsheet"
date: 2016-07-07 00:12:52 +0800
comments: true
categories: tmux
---

{% coderay lang:shell %}
tmux ls    // 列出已有 windows
{% endcoderay %}

<!--more-->

#### Session:

{% coderay lang:shell %}
tmux new -s name          // 创建 session
tmux detach                // 挂起 session
C-b s                      // 切换 session
C-b $                      // 改名 session
tmux attach -t name        // 接入 session
tmux kill-session -t name  // 关闭 session
{% endcoderay %}

#### Window:

{% coderay lang:shell %}
C-b c          // 创建  window
C-b ,          // 重命名 window
C-b w          // 切换  window
C-b &          // 关闭  window
{% endcoderay %}

#### Pane:

{% coderay lang:shell %}
C-b %        // 水平分割成 pane
C-b "        // 竖直分割成 pane
C-b x        // 关闭 pane
{% endcoderay %}
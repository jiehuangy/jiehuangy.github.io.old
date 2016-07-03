---
layout: post
title: "Hello World"
date: 2015-04-15 19:32:16 +0800
comments: true
categories: 编程
---

$$
f'\left( x\right) = \lim _{x\rightarrow 0}\dfrac {f\left( x+\Delta x\right) - f\left( x\right)}{\Delta x}
$$

好吧，这应该就是第一篇文章了。

Jekyll 不支持 GFM 实在是蛋碎，不知道有没有什么变通的方法。

```js
// 这是一段 GFM 才有的代码块
var date = new Date();
window.alert(date)
```

```http
GET / HTTP/1.1
Host: my.server.com
```

{% codeblock %}
Awesome code snippet
{% endcodeblock %}

{% codeblock Javascript Array Syntax lang:js http://j.mp/pPUUmW MDN Documentation %}
var arr1 = new Array(arrayLength);
var arr2 = new Array(element0, element1, ..., elementN);
{% endcodeblock %}


`inline`

a `common inline code` that needn't parse.

秘诀[在此](http://xingrz.us/assets/themes/xingrz/js/fenced-code-blocks.js)。
---
layout: post
title: "Markdown Examples"
date: 2016-07-06 11:24
comments: false
categories: "Markdown"
---

- list element with functor item
{:toc}

### Insert image.

{% coderay lang:ruby %}{% raw %}
{% img [left|right|center] {{ root_url }}/images/test.jpg [width] [height] [title text [alt text]] %}
OR
{% imgcap {{ root_url }}/images/test.jpg 256 256 This is a image test %}{% endraw %}
{% endcoderay %}

{% imgcap {{ root_url }}/images/test.jpg 256 256 This is a image test %}

<!--more-->

### Info & Warn
This is information.
{:.info}

This is warning.
{:.warning}


### Citation
{% coderay %}
> This is
> 
> Citation.
{% endcoderay %}

> This is
> 
> Citation.

### Footnote
{% coderay %}
[^1]This is footnote.
[^1]: Explain for footnote.
{% endcoderay %}

[^1]This is footnote.

### Hyperlink
{% coderay %}
[Github](https://github.com/)
{% endcoderay %}
[Github](https://github.com/)

### Equation
{% coderay %}
$$
f'\left( x\right) = \lim _{x\rightarrow 0}\dfrac {f\left( x+\Delta x\right) - f\left( x\right)}{\Delta x}
$$
{% endcoderay %}
$$
f'\left( x\right) = \lim _{x\rightarrow 0}\dfrac {f\left( x+\Delta x\right) - f\left( x\right)}{\Delta x}
$$


### Code
{% coderay %}
This <code>is </code> in `line` code.
{% endcoderay %}
This <code>is </code> in `line` code.

{% coderay lang:ruby %}{% raw %}
{ % coderay [lang:lang] [linenos:true|false(default)] [title] [url] [link text] % }
code fragment
{ % endcoderay % }{% endraw %}
{% endcoderay %}

{% coderay lang:ruby %}{% raw %}
{% codeblock lang:python caption %}
rv = conn.validateaddress(foo)
if rv.isvalid:
    print "The address that you provided is valid"
else:
    print "The address that you provided is invalid, please correct"
{% endcodeblock %}{% endraw %}
{% endcoderay %}

{% codeblock lang:python caption %}
rv = conn.validateaddress(foo)
if rv.isvalid:
    print "The address that you provided is valid"
else:
    print "The address that you provided is invalid, please correct"
{% endcodeblock %}

{% coderay lang:ruby %}{% raw %}
{% coderay lang:python caption %}
rv = conn.validateaddress(foo)
if rv.isvalid:
    print "The address that you provided is valid"
else:
    print "The address that you provided is invalid, please correct"
{% endcoderay %}{% endraw %}
{% endcoderay %}


{% coderay lang:python caption %}
rv = conn.validateaddress(foo)
if rv.isvalid:
    print "The address that you provided is valid"
else:
    print "The address that you provided is invalid, please correct"
{% endcoderay %}


[^1]: Explain for footnote.
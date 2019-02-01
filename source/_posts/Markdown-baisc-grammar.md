---
title: Markdown基本语法
date: 2019-01-29 22:40:30
sticky: 0
mathjax: true
tags:
  - Markdown
categories:
  - 博文书写规范
photos: 
  - /images/Local-Gallery/markdown.jpg
---

{% cq %}
    第一篇正式博客，因为对Markdown语法不熟悉，就打算专门写个关于Markdown语法的博客
    **注意：本博客仅仅是总结其他博客的用法，末尾会给出所有的链接**
{% endcq %}

<!-- more -->

## Quick Start

### Create a new post

{% note default no-icon %}
    $$\begin{bmatrix}
        {a_{11}}&{a_{12}}&{\cdots}&{a_{1n}}\\
        {a_{21}}&{a_{22}}&{\cdots}&{a_{2n}}\\
        {\vdots}&{\vdots}&{\ddots}&{\vdots}\\
        {a_{m1}}&{a_{m2}}&{\cdots}&{a_{mn}}\\
    \end{bmatrix}$$
    $$\begin{array}{c|lll}
    {↓}&{a}&{b}&{c}\\
    \hline
    {R_1}&{c}&{b}&{a}\\
    {R_2}&{b}&{c}&{c}\\
    \end{array}$$
{% endnote %}

``` bash
$ hexo new "My New Post"
```

More info: [Writing](https://hexo.io/docs/writing.html)

### Run server

``` bash
$ hexo server
```

More info: [Server](https://hexo.io/docs/server.html)

### Generate static files

``` bash
$ hexo generate
```

More info: [Generating](https://hexo.io/docs/generating.html)

### Deploy to remote sites

``` bash
$ hexo deploy
```

More info: [Deployment](https://hexo.io/docs/deployment.html)

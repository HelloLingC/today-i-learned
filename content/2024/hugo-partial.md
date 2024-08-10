---
title: 'Hugo Partial'
date: 2024-08-10T14:04:26+08:00
draft: false
categories:
tags: [hugo]
---

# Partial

```
{{ partial "footer.html" }}
```

我看到有的hugo模板调用partial方法会传入上下文参数，但是不传也不会报错。

然而 partialCached 就必须传入上下文，否则会报错：

```
Error: error building site: render: failed to render pages: render of "home" failed: "/home/lingc/Documents/today-i-learned/themes/sim/layouts/_default/baseof.html:10:11": execute of template failed: template: _default/list.html:10:11: executing "_default/list.html" at <partialCached>: wrong number of args for partialCached: want at least 3 got 1
```

```
{{ partialCached "footer.html" . }}
```

不过这里挺奇怪的，`want at least 3 got 1`，最终给了2个参数依旧没有报错。

# {{- -}}

Use {{ }} when you want to keep the whitespace intact.
Use {{- }} or {{ -}} when you want to trim whitespace before or after the template action, respectively.


# IsHome

https://gohugo.io/methods/page/ishome/

hugo中页面有三种类型：Page, Section, Home

```
content/
├── books/
│   ├── book-1/
│   │   └── index.md  <-- kind = page
│   ├── book-2.md     <-- kind = page
│   └── _index.md     <-- kind = section
└── _index.md         <-- kind = home
```

(taxonomony 的页面，如`/tag/1`也是page)

使用 `{{ if .IsHome }}` 就可以判断当前页面是否是主页


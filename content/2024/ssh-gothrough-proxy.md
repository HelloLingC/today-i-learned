---
title: 'SSH 协议不走代理解决方法'
date: 2024-08-11T14:09:25+08:00
draft: false
categories:
tags: ssh]
---

在我用ssh连接服务器的时候，每次使用代理就会出现EOF。我本来以为是我代理服务器的问题，结果每个代理服务器都是一致的导致连接出现EOF。我突然想到，会不会是因为ssh连接没有走代理呢？我看到有人用ssh连接git也会出现不走代理的情况，不过由于我用https连接git，所以我就没有遇到。

而因为地域问题，我如果直连服务器速度是很慢很慢的。我是完全忍受不了龟速的终端输入，所以这个问题必须要解决了。

即使终端设置了代理，ssh客户端也依旧很有特色地走自己的路。

使用这个命令即可让ssh客户端走代理。

```
$ ssh -o ProxyCommand="nc -X 5 -x 127.0.0.1:1080 %h %p" root@server
```

`nc` 命令中 `-X `是指定代理协议，4是socks4协议，5是socks5协议。

不过如果使用类似Termius的应用，也可以选择修改ssh配置文件（不过有的ssh客户端提供了修改代理的选项）。

我是Linux系统，ssh客户端配置是`~/.ssh/config`

只需要添加如下：

```
Host *
    ProxyCommand nc -X 5 -x 127.0.0.1:1080 %h %p
```

----

Refs

https://kuokuo.io/2019/07/01/ssh-over-http-or-socks/

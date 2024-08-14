---
title: 'Pacman Mirrorlist更新'
date: 2024-08-13T17:17:43+08:00
draft: false
categories:
tags: [linux]
---

```
$ sudo pacman -Sy
```

出现了：

```
error: failed retrieving file 'core.db' from mirror.f4st.host : Operation too slow. Less than 1 bytes/sec transferred the last 10 seconds
error: failed retrieving file 'extra.db' from mirror.f4st.host : Operation too slow. Less than 1 bytes/sec transferred the last 10 seconds
error: failed retrieving file 'multilib.db' from mirror.f4st.host : Operation too slow. Less than 1 bytes/sec transferred the last 10 seconds
warning: too many errors from mirror.f4st.host, skipping for the remainder of this transaction
error: failed retrieving file 'core.db' from mirror.f4st.host : SSL connection timeout
error: failed retrieving file 'extra.db' from mirror.f4st.host : SSL connection timeout
```

而`mirror.f4st.host`已经在2024.6.30关闭力：https://lists.archlinux.org/archives/list/arch-mirrors@lists.archlinux.org/message/VQAMXLF6RIZHXQF6O3UO3AWWPSEQFCB7/


先看以下镜像列表都有哪些：

```
$ cat /etc/pacman.conf

$ ls /etc/pacman.d/
```

arch的都在`/etc/pacman.d/mirrorlist`里了。去https://archlinux.org/mirrorlist/生成一个新的文件再替换掉就好。

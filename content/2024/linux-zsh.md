---
title: 'Linux 使用zsh'
date: 2024-08-12T06:35:43+08:00
draft: false
categories:
tags: [docker]
---

先查看当前的shell：

```
$ echo $SHELL
/bin/bash

```

安装zsh:

```
$ sudo pacman -S zsh zsh-completions
```

# Making zsh the default shell

List all installed shell:

```
$ chsh -l
```

将`/bin/zsh`设为默认：

```
$ chsh -s /bin/zsh
```

docker run -d \
    --name artalk \
    -p 8080:23366 \
    -v $(pwd)/data:/data \
    -e "ATK_LOCALE=zh-CN" \
    -e "ATK_SITE_DEFAULT=Mooblab" \
    -e "ATK_TRUSTED_DOMAINS=https://moonlab.top" \
    artalk/artalk-go

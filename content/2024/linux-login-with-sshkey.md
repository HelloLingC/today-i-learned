---
title: '服务器配置ssh仅允许使用pubkey验证'
date: 2024-08-11T15:32:43+08:00
draft: false
categories:
tags: [linux]
---

本地要有keypair，可以是rsa也可以是ed25519。

```
$ ssh-keygen
```

将本地的pubkey复制到服务器的`~/.ssh/authorized_keys`中：

```
$ ssh-copy-id username@host
```

然后修改服务器的ssh服务器配置：

```
$ sudo nano /etc/ssh/sshd_config
```

```
PubkeyAuthentication yes
PasswordAuthentication no
AuthorizedKeysFile      .ssh/authorized_keys
PasswordAuthentication no
```

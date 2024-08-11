---
title: 'ssh-keygen'
date: 2024-08-11T15:50:43+08:00
draft: false
categories:
tags: [linux]
---

When i used systemctl status sshd, i saw:

```
Aug 11 03:41:35 NekoPara01 sshd[1045]: error: Could not load host key: /etc/ssh/ssh_host_ecdsa_key
Aug 11 03:41:35 NekoPara01 sshd[1045]: error: Could not load host key: /etc/ssh/ssh_host_ed25519_key
```

Use `sudo ssh-keygen -A` to generate all missing host keys.

---
title: git commit sign失败 windows
date: 2025-02-23T00:13:59+08:00
draft: false
categories: 
tags:
  - git
---
```
gpg --list-secret-keys --keyid-format LONG
```

```
gpg: skipped "name <name@mail.com>": secret key not available
gpg: signing failed: secret key not available
error: gpg failed to sign the data
fatal: failed to write commit object
```

解决方法：

```
git config --global gpg.program "C:\Program Files (x86)\GnuPG\bin\gpg.exe"
```

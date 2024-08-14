---
title: 'Vim Configuration'
date: 2024-08-13T21:27:37+08:00
draft: false
categories:
tags: [vim]
---

I dont know its a good idea or bad idea to decide to use vim.

I just wanna give it a try...

List all the .vim files that Vim loads:

```
:scriptnames
```

In default, vim dont automaticalyy create `~/.vimrc`

`:e $MYVIMRC` open & edit the current .vimrc that you are using, then use Ctrl + G to view the path in status bar.

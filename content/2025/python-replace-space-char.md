---
title: Python Replace Space Char
date: 2025-02-14T15:28:59+08:00
draft: false
categories: 
tags:
  - python
---

```python
def _trim(s: str):
    return s.replace(' ', '').replace('.', '').strip()
```
`s.replace(' ', '')`的确删除了句中的空格，但并没有把字符串末尾的空格删去，所以我不得不加了一个`strip()`


https://stackoverflow.com/questions/31210985/python-3-cant-delete-a-space-in-a-string-using-replace
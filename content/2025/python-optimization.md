---
title: 'Python Replace Space Char'
date: 2025-02-14T15:23:39+08:00
draft: false
categories:
tags: [python]
---

python包或模块的全局代码会在导入时自动运行。比如，包中的类、函数或者任何变量在导入时都会被初始化。

如果在包的根目录下有 `__init__.py` 文件，Python 还会执行这个文件里的代码。

```python
# 假设有一个包叫 mypackage，其中有一个 __init__.py 文件 
# mypackage/__init__.py
print("Initializing mypackage") 
# mypackage/module.py
print("Initializing module")

# main.py 
import mypackage
```

就会输出：
```
Initializing mypackage
Initializing module
```

计算每个包的导入时间：

```python
import time

# 包名列表
packages = ['numpy', 'pandas', 'matplotlib', 'scipy']

for package in packages:
    start_time = time.time()
    try:
        __import__(package)
        elapsed_time = time.time() - start_time
        print(f'{package} 导入时间: {elapsed_time:.6f}秒')
    except ImportError:
        print(f'{package} 无法导入')
```



![[Pasted image 20250214161541.png]]

## Python 的模块缓存（`sys.modules`）

Python 会查找并执行该模块的代码，之后将模块对象保存在 `sys.modules` 中。下次导入相同模块时，Python 会直接从 `sys.modules` 中获取已经加载的模块，而不会再次执行模块代码。
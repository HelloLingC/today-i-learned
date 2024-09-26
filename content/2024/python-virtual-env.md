---
title: 'Python Virtual Environment'
date: 2024-09-25T20:28:43+08:00
draft: false
categories:
tags: [python]
---

因为有时候需要不同的python的版本来运行程序，所以就出现了版本管理器pyenv，类似于nodejs nvm。

而pip包管理器则是通过 pypi(Python Package Index)

# Venv

python 的虚拟环境其实就是环境变量在进程之间的隔离。
一般的进程会共享操作系统的环境变量。

```
lingc@lap: $
(.venv) lingc@lap: $
```

前面带上`(.venv)`就代表当前环境是虚拟环境。

python3.3之后venv模块就代替了virtualenv。

```
pip install virtualenv
```

# 创建虚拟环境

```
virtualenv myvenv
```

or

```
python -m venv myenv
```

# Activate venv

```
$ source myenv/bin/activate
```

# 退出虚拟环境

```
deactivate
```

退出虚拟环境相当于将 `PATH` 环境变量还原到创建虚拟环境之前的状态。

# 删除虚拟环境

```
rm -rf myvenv
```


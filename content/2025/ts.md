---
title: TS
date: 2025-02-21T00:25:59+08:00
draft: false
categories: 
tags:
  - TypeScript
---
```ts
import { Link } from "next/link"
```

在项目中用加上curly braces会导致报错：


```
React.jsx: type is invalid -- expected a string (for built-in components) or a class/function (for composite components) but got: undefined. You likely forgot to export your component from the file it's defined in, or you might have mixed up default and named imports.
```

因为next/link已经有default export了，所以不需要加上两个花括号。

```ts
import Link from "next/link"

```
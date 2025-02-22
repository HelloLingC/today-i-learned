---
title: TS
date: 2025-02-21T00:25:59+08:00
draft: false
categories: 
tags:
  - TypeScript
---
安装 prisma client

```
pnpm install @prisma/client
```

###  **生成 Prisma Client**

安装 `@prisma/client` 后，需要生成 Prisma Client。运行以下命令：

npx prisma generate

这会根据你的 `schema.prisma` 文件生成 Prisma Client。生成的文件通常位于 `node_modules/.prisma/client` 目录中。



npx prisma migrate dev --name init

This will create the `dev.db` file (if it doesn’t exist) and apply the schema defined in `prisma/schema.prisma`.
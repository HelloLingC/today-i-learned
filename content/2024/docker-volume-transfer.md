---
title: 'Docker Volume迁移'
date: 2024-08-11T18:48:43+08:00
draft: false
categories:
tags: [docker]
---

其实我一直都用不好docker，因为我的经验很少，直到现在我也没有遇到非使用docker不可的情况，所以其实我就没有什么动力去用docker。而且我一直在怀疑，在低配的个人服务器上，运行docker的性能究竟如何。

Docker中有两种Volume（在刚刚我发现它们的存在，并上网查询之前，我称这两者为Independent Volume和Hidden Volume）：

- Named Volumes

- Anonymous Volumes

`Named Volumes` 是通过 `docker volume create` 命令或在 `docker-compose.yml` 中声明的。

Persistence: Named volumes are stored in a Docker-managed directory (/var/lib/docker/volumes/ by default) and are not tied to the lifecycle of a container.

`Anonymous Volumes` 则是由 `docker run` 的 `-v` flag创建的。

Persistence: They are still stored in Docker’s volume directory, but they are harder to manage directly because they don’t have a user-defined name.

# 迁移Volume

接着就可以步入正题，转移Volume了。因为我所搭建是服务是有公共image的，我也没有修改任何代码，所以不需要备份image。

## Create tarball

```
$ docker exec memos tar czf /tmp/memos_backup.tar.gz -C /var/opt/memos .

$ docker cp memos:/tmp/memos_backup.tar.gz ~/memos_backup.tar.gz
```

之后就需要把备份迁移到另一台服务器中，服务器要先装好镜像。

```
docker run -d \
  --init \
  --name memos \
  --publish 5230:5230 \
  --volume ~/.memos/:/var/opt/memos \
  neosmemo/memos:stable
```

（这里 `--volume ~/.memos/:/var/opt/memos` 会把`/var/opt/memos` mount 到host的文件夹中。同时也可以命名卷，如` --volume my_volume:/var/opt/memos` ）

在进行导入的时候，容器要保持开启。

```
$ docker cp ~/memos_backup.tar.gz memos:/tmp/memos_backup.tar.gz

Successfully copied 9.73kB to memos:/tmp/memos_backup.tar.gz

$ docker exec memos tar xzf /tmp/memos_backup.tar.gz -C /var/opt/memos
```

这个时候需要重启一下容器才能完成迁移。（我也不知道为什么）


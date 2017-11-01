---
title: Docker 学习笔记（一）
tags: [Programming, Docker]
date: 2017-10-03 10:12:10
---


## Concepts

### Image
`Image` 是轻量级的集合，包含了自定义的配置文件、依赖库、环境变量等。

### Container
`Container` 是 `Image` 的运行状态。独立存在于内存中，与宿主机器隔离，只通过 _port_ 进行通信。一个 `Image` 可以运行产生多个 `Container`, 每个都具有独立的内存与进程。你可以使用 `docker ps` 查看进程。

## Container vs. Virtual Machine

### VM Diagram
![VM Diagram](https://www.docker.com/sites/default/files/VM%402x.png)

### Container diagram
![Container diagram](https://www.docker.com/sites/default/files/Container%402x.png)

## Hello world
测试 Docker 环境

```
$ docker run hello-world
```

国内会报错 timeout。可以参考 [这篇文章](https://my.oschina.net/nevermissing/blog/760954)更新镜像源。
国内可使用的镜像源：
- [Docker 中国官方镜像加速](https://www.docker-cn.com/registry-mirror)

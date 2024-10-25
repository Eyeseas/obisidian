---
title: Heroku部署RSSHub并配置自动SSL证书
share: "true"
date: 2024-10-25 23:17
updated: 2024-10-25 23:17
tags:
  - Docker
  - SaaS
categories:
  - tech
  - docker
---
> 之前Edu送的Heroku免费额度一直没怎么用过, 最近心血来潮, 想着利用起来, 但是感觉没什么应用部署, 感觉食之无味弃之可惜, 突然想到最近大火的Follow带起来RSS的热潮, 于是部署上一个配套的RSSHub应用, 顺便看看Heroku如何部署Docker应用


<!-- more -->
## Heroku CLI

首先应该安装[`Heroku CLI`](https://devcenter.heroku.com/articles/heroku-cli), 由Heroku官方提供的命令行工具, 比较全能, 基本上你所有在控制台页面能操作的事情, 都能通过命令行完成.

## 项目准备

可以通过heroku网页创建应用, 或者使用`heroku cli`通过命令行创建应用.

- 设置应用类型为Container

```shell
heroku stack:set container
```

## 配置文件

- `Dockerfile`, 可以直接指定使用什么镜像, 也可以自己二次打包

```yaml
FROM diygod/rsshub:chromium-bundled
```

- `heroku.yml`, heroku的配置文件, 指定heroku的行为

```yaml
build:
	docker:
		web: Dockerfile

# 下面还应该指定web相关的启动指令,但是不指定好像也可以, 会默认使用原镜像的启动指令
```

## 自动证书

```shell
heroku certs:auto:enable
```

```shell
# 查看证书状态
heroku certs:auto
```
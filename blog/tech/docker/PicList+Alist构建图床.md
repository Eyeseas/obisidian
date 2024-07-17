---
share: "true"
categories:
  - tech
  - docker
title: PicList+Alist构建图床
date: 2024-07-16
tags:
  - Docker
  - Alist
  - 图床
---
> 私有化部署Alist图床, 使用PicList-core + Picgo-plugin-alist插件


## 前期准备工具

- Alist
- 以下选一个你会用的
	- PicGo / PicList (有图形化界面, `PicGo` 需要手动安装 [picgo-plugin-alist](https://github.com/jinzhi0123/picgo-plugin-alist))
	- PicGo-Core / PicList-Core(无图形化界面 )


## Alist 准备

### 1. 关闭签名

![image.png](https://alist.kong.vision/d/r2/_imageStore/2024/07/1720240717232721.png)


### 2. 获取令牌

> picgo-plugin-alist 也可以直接填入用户名密码

![image.png](https://alist.kong.vision/d/r2/_imageStore/2024/07/1720240717232750.png)


## PicGo / PicList

> 图形化界面可以直接在应用里面配置, core版本自行对照文档编辑config.json, 配置的字段基本都一样

```json
{
	"url": "https://xxxx.xxx.xxx",
	"token": "alistxxxxxxxxxxxxxxc",
	"username": "",
	"password": "",
	"uploadPath": "/r2/_imageStore",
	"webPath": "",
	"customUrl": ""
}
```











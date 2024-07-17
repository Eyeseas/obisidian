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


## 前期准备

- Alist
- PicGo / PicList (有图形化界面)
- PicGo-Core / PicList-Core(无图形化界面)


## 需要的问题

1. 在使用PicList-Core过程中，通过[obisidian-image-auto-upload-image](https://github.com/renmu123/obsidian-image-auto-upload-plugin)自动上传剪贴板图片，图片名不会触发renameFn，导致一直传的都是同一个文件名 `image.png`，一直在覆盖相同的图片

---
share: "true"
categories:
  - tech
  - hexo
title: Hexo+Obisidian解决方案
date: 2024-07-15T13:00:00
tags:
  - Hexo
  - Obisidian
---
## 需求分析

- [x] icloud同步vault
- [x] hexo图片路径解决不了，像图床方案妥协
- [ ] 跨平台同步ios/android/windows

<!-- more -->

## 解决方案

1. obisidian文档 icloud同步
2. obisidian publisher推送文档仓库
3. 文档仓库触发push事件
4. 文档脱离hexo仓库，以子模块引入
5. 图床外链, 因为无法找到合适hexo的图片路径方案
6. 子模块更新自动化推送到hexo仓库
7. github action 同步submodule与hexo仓库
8. cloudflare pages自动部署
9. 绑定自定义域名

## 1. icloud同步

vault存储目录选icloud内的目录就原生支持了icloud同步

## 2. 同步到git仓库

Obisidian插件[Enveloppe](https://github.com/Enveloppe/obsidian-enveloppe)

## 3. github action监听push事件

Obisidian仓库收到push事件后，推送了自定义的 `update-submodule` 事件到 blog仓库，触发blog仓库的对应事件

```yaml
name: Dispatch Update Submodule
on:
  push:
    branches:
      - main
jobs:
  dispatch:
    runs-on: ubuntu-latest
    steps:
      - name: Dispatch update to Git Blog Project
        uses: peter-evans/repository-dispatch@v3
        with:
          token: ${{ secrets.PAT }}
          repository: Eyeseas/blog
          event-type: update-submodule
```

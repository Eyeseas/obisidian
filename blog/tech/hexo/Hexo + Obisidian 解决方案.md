---
share: "true"
categories:
  - tech
  - hexo
title: Hexo+Obisidian解决方案
date: 2024-07-16
tags:
  - Hexo
  - Obisidian
---
## 需求分析

- [x] icloud同步vault
- [x] hexo图片路径解决不了，像图床方案妥协
- [ ] 跨平台同步ios/android/windows

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

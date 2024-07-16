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
核心前提: 
1. icloud同步
2. 文档脱离hexo仓库，以子模块引入
3. 图床外链, 因为无法找到合适hexo的图片路径方案
4. 子模块更新自动化推送到hexo仓库
5. github action 同步submodule与hexo仓库
6. cloudflare pages自动部署

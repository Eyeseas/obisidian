---
title: ollama 部署大模型 并接入各类ai服务
share: "true"
date: 2024-08-05 00:11
updated: 2024-08-05 00:11
tags: 
categories:
  - tech
  - ai
description: ollama一键安装及调用openai compatible接口用于各类服务
---
## ollama 安装

[官网下载](https://ollama.com/download)

## 大模型获取

支持一键部署的[模型库](https://ollama.com/library)

例如阿里的qwen2, 内网RTX3060下跑一个7B的模型非常舒服

![image.png](https://alist.kong.vision/d/r2/_imageStore/2024/08/05/20240805001515.png)

## 常用指令

- `ollama start` 运行ollama服务, 与客户端程序冲突, 需要重任务栏退出羊驼图标后使用
- `ollama list` 列出可用模型
- `ollama pull xxx-model` 拉取指定模型 
- `ollama run xxx-model` 启动指定模型的命令行交互

## 常用环境变量

- `OLLAMA_ORIGINS` 不考虑安全问题,方便调用的情况下直接设置`*`
- `OLLAMA_HOST` 一般设置为`0.0.0.0:11434`, 根据实际情况来定




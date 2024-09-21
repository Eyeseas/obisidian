---
title: 给开源的Perplexity项目加上ONE-API支持
share: "true"
date: 2024-09-21 11:52
updated: 2024-09-21 11:52
tags:
  - AI
  - Perplexity
  - Perplexica
categories:
  - tech
  - ai
---
> [Perplexica](https://github.com/ItzCrazyKns/Perplexica)目前已经有13k的star, 号称开源版的Perplexity

## 开发背景

原版`Perplexica`是支持在项目启动后, 通过**页面上的配置项**去配置第三方接口+密钥, 通过配置下来虽然没有难度, 但是会增加分享给朋友测试使用的难度, 特别是在移动端, 页面不会出现配置的按钮, 根本无法进行配置

<!-- more -->

![原版的配置页面](https://alist.kong.vision/d/r2/_imageStore/2024/09/21/20240921120049.png)


## 修改后实现效果

在原有代码上新增了`ONE-API`的Provider, 支持直接从`ONE-API`接口获取所有模型, 以及自动过滤出`Embedding`相关的模型

![取出one-api的所有模型](https://alist.kong.vision/d/r2/_imageStore/2024/09/21/20240921120130.png)

![取出Embedding模型](https://alist.kong.vision/d/r2/_imageStore/2024/09/21/20240921120255.png)


## 修改版项目地址

https://github.com/gptkong/Perplexica

## 说明

所有改动代码由`Cursor`实现
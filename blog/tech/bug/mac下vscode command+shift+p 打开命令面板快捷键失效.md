---
title: mac下vscode command+shift+p 打开命令面板快捷键失效
share: "true"
date: 2024-08-11 00:17
updated: 2024-08-11 00:17
tags:
  - Bug
  - vscode
categories:
  - tech
  - bug
---
在mac下突然发现vscode的`command+shift+p`无法触发了, 开始排查问题

<!-- more -->

1. ~~vscode插件冲突情况~~

通过查看现有的`键盘快捷方式` 发现并没有插件快捷键跟vscode冲突, 排除vscode内部问题

2. ~~mac 系统快捷键~~

设置里面没看到明显的冲突快捷键, macOS官网有关finder的一个`command+shift+p`的快捷键, 不过也不是罪魁祸首

3. 系统内某个软件

通过一顿查找[解决方案](https://github.com/microsoft/vscode/issues/182834#issuecomment-1822218334), 总算找到一个好使的, 通过安装brew安装这个shotcutdetective软件`brew install --cask shortcutdetective`, 启动后查看是哪个软件劫持了你的快捷键,直接找出内鬼`picList`的自带快捷键
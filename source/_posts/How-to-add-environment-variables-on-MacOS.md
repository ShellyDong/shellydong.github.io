layout: post
title: 如何为MacOS添加新的环境变量
tags:
  - Mac
  - Apple
  - iOS
categories:
  - Apple
date: 2015-11-19 16:38:04
description: 
---
具体步骤如下：
1. 打开Terminal，输入`sudo vim /etc/profile`，此时将进入vi编辑界面
2. 按下[i]键进入Insert模式，插入如下代码
	`ANDROID_HOME=/Users/xxx/desktop/sdk`
3. 按Esc键进入Command模式， 输入`:wq!`保存并强制退出。
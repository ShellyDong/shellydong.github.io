layout: post
title: 如何在MacOS搭建Android开发环境
tags:
  - Mac
  - Apple
  - Android
categories:
  - Apple
date: 2015-11-20 15:40:30
description:
---
###准备安装包
1. 由于eclipse使用的是Java 6，因此需要从苹果官网下载[支持包](https://support.apple.com/kb/DL1572?locale=zh_CN&viewlocale=zh_CN)。
2. 下载JDK，可以选择从Oracle官网或者[AndroidDevTools](http://www.androiddevtools.cn)下载，选择Mac OSX的1.8u5版本即可。
3. 下载Android SDK，这里我是从[AndroidDevTools](http://www.androiddevtools.cn)下载ADT Bundle，选择Mac OSX的64位23.0.2即可。
<!--more-->
###环境变量配置

1. 查看Java安装路径: `/usr/libexec/java_home -V`
![](http://7xkfin.com1.z0.glb.clouddn.com/QQ截图20151120160216.png)
2. 添加Java环境变量
	- 全局配置
	```bash
	sudo vi /etc/profile
	#配置JAVA_HOME，此处路径根据自己的版本填写
	JAVA_HOME="/System/Library/Java/JavaVirtualMachines/1.8.0_05.jdk/Contents/Home/"
	CLASS_PATH="$JAVA_HOME/lib"
	#把JAVA添加到到环境变量PATH中
	PATH=".:$PATH:$JAVA_HOME/bin"
	#设置tomcat的主目录
	#CATALINA_HOME="/usr/local/tomcat"（tomcat需自行提前安装好）
	#将JAVA_HOME和CATALINA_HOME设置为环境变量
	#export JAVA_HOME CATALINA_HOME
	export JAVA_HOME
	```
	- 针对用户配置
	```bash
	#进入用户主目录，然后看一下有没有.bash_profile文件
	cd ~
	ls -all
	#编辑.bash_profile文件(没有则新建，命令touch .bash_profile)
	vim .bash_profile
	#英文模式下，按一下i键进入编辑模式，输入以下内容，路径部分自己粘贴自己的
	export JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk1.8.0_05.jdk/Contents/Home
	#输完后，按esc，输入:wq!保存
	#source命令使profile立即生效
	source .bash_profile
	```
3. 添加Android SDK环境变量
	- 全局配置
	```bash
	sudo vi /etc/profile
	#配置ANDROID_HOME，此处路径根据自己的版本填写
	ANDROID_HOME=/Users/blue/Downloads/adt-bundle/sdk
	export ANDROID_HOME
	export PATH=$PATH:$ANDROID_HOME/tools:$ANDROID_HOME/platform-tools	
	```
	- 针对用户配置
	```bash
	#进入用户主目录，然后看一下有没有.bash_profile文件
	cd ~
	ls -all
	#编辑.bash_profile文件(没有则新建，命令touch .bash_profile)
	vim .bash_profile
	#英文模式下，按一下i键进入编辑模式，输入以下内容，路径部分自己粘贴自己的
	ANDROID_HOME=/Users/blue/Downloads/adt-bundle/sdk
	export ANDROID_HOME
	export PATH=$PATH:$ANDROID_HOME/tools:$ANDROID_HOME/platform-tools
	#输完后，按esc，输入:wq!保存
	#source命令使profile立即生效
	source .bash_profile
	```
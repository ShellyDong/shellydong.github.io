title: Appium环境搭建
tags: [Appium, Android, IOS, Automation, Test]
date: 2015-11-17 17:24:15
categories: 
- Android
---
Appium目前较流行移动自动化测试框架。
##Windows
安装依赖库

1. 安装 nodejs v0.10 版本及以上，可通过官方的安装程序来安装。
	测试安装是否成功：运行cmd，输入node -v 
<!--more-->
2. 安装android的SKD
	安装android的sdk包(http://developer.android.com/sdk/index.html),运行依赖sdk中的 'android'工具。并确保你安装了Level17或以上的版本api。

	设置ANDROID_HOME 系统变量为你的 Android SDK 路径，并把tools和platform-tools两个目录加入到系统的 Path路径里。

         变量： ANDROID_HOME

           值： D:\android-sdk

         设置： Path

           值： %ANDROID_HOME%\platform-tools;%ANDROID_HOME%\tools;

3. 安装Apache Ant（可选）
	安装Apache Ant（http://ant.apache.org/bindownload.cgi）

	解压缩文件夹，并把路径加入环境变量。

         变量： ANT_HOME

           值： D:\apache-ant-1.8.2

         设置： Path

           值： %ANT_HOME%\bin 

	测试ant环境安装成功：运行cmd，输入ant，如果没有指定build.xml就会输出：

	 Buildfile: build.xml does not exist!

	 Build failed

4. 安装JDK

	下载解压文件夹 并且设置 M2HOME 和 M2 环境变量，把 M2 环境变量添加到你的系统PATH变量中。 

         变量： JAVA_HOME

           值： C:\Program Files (x86)\Java\jdk1.7.0_01

         变量： classpath

           值： %JAVA_HOME%\lib;

         设置： Path

           值： %JAVA_HOME%\bin;%JAVA_HOME%\jre\bin;

   测试环境安装成功：运行cmd，输入java -version 如果成功则出现java信息。

5. 安装Apache Maven
	安装Maven（http://maven.apache.org/download.cgi）

	下载解压文件夹 并且设置 M2HOME 和 M2 环境变量，把 M2 环境变量添加到你的系统PATH变量中。 

         变量： MAVEN_HOME

           值： D:\apache-maven-3.1.1

         设置： Path:

           值： %MAVEN_HOME%\bin 

   测试环境安装成功：运行cmd，输入mvn -v 如果成功则出现maven信息。

Appium提供两种方式进行安装:
- 下载 AppiumForWindows，解压后即完成安装，[下载地址](https://bitbucket.org/appium/appium.app/downloads/)
- 命令行输入相关命令安装

	`运行 npm install -g appium 安装 appium `

验证 appium：在命令行输入appium-doctor,如果结果如下，证明 环境搭建成功
![appium-doctor result](http://7xkfin.com1.z0.glb.clouddn.com/20151117001.png)

##Mac OS (待后补)

#参考资料
1. [Appium官网](http://appium.io/)
2. [TesterHome Appium中文教程](https://appium.testerhome.com/)
3. [Github Appium开源项目代码](https://github.com/appium/appium)
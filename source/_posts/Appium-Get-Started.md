title: Appium使用指引
tags: [Appium, Android, IOS, Automation, Test]
date: 2015-11-17 18:24:15
categories: 
- Android
---
1. 启动程序
![启动成功](http://7xkfin.com1.z0.glb.clouddn.com/QQ截图20151117175555.png)
<!--more-->
2. 设置capabilities
![设置参数](http://7xkfin.com1.z0.glb.clouddn.com/QQ截图20151117175634.png)
3. 启动Server
![启动中](http://7xkfin.com1.z0.glb.clouddn.com/QQ截图20151117175706.png)
4. 启动Inspector
![启动中](http://7xkfin.com1.z0.glb.clouddn.com/QQ截图20151117175831.png)
![启动成功](http://7xkfin.com1.z0.glb.clouddn.com/QQ截图20151117175848.png)
5. 刷新界面
![刷新成功](http://7xkfin.com1.z0.glb.clouddn.com/QQ截图20151117175930.png)
6. 开始测试
	- 从Android Studio直接开始测试

	![右键菜单选择测试](http://7xkfin.com1.z0.glb.clouddn.com/QQ截图20151117180018.png)

	- 使用命令行启动测试

	![启动单个测试](http://7xkfin.com1.z0.glb.clouddn.com/QQ截图20151117181042.png)

需要注意Appium每一个测试都会清除data & cache，保证各个case之间不会互相干扰。测试完成后会在命令行输出测试结果。


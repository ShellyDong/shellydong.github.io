title: Android应用集成友盟页面路径统计
date: 2015-07-13 17:46:22
categories:
- Android
tags:
- Umeng
- Android
---
##1.  集成准备

###1.1  获得Appkey
首先需要到友盟官网注册并且添加新应用，获得Appkey
不同平台的应用禁止使用相同的Appkey，友盟后台的应用名与实际应用名和包名无关，建议命名为“应用名+平台”。
<!--more-->
###1.2  下载SDK

###1.3  导入SDK
将下载包中的libs 文件夹合并到本地工程libs子目录下；


##2.  基本功能集成

###2.1  配置manifest
manifest的配置主要包括添加权限，填写Appkey和填写渠道id三部分，代码示例如下：
```xml
<manifest……>
<uses-sdk android:minSdkVersion="4"></uses-sdk>
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"></uses-permission>
<uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />
<uses-permission android:name="android.permission.INTERNET"></uses-permission>
<uses-permission android:name="android.permission.READ_PHONE_STATE"></uses-permission>
<application ……>
……
<activity ……/>
<meta-data android:value="YOUR_APP_KEY" android:name="UMENG_APPKEY"></meta-data>
<meta-data android:value="Channel ID" android:name="UMENG_CHANNEL"/>
</application>    
</manifest>
```

###2.2  session的统计
在每个Activity的onResume方法中调用 MobclickAgent.onResume(Context), onPause方法中调用 MobclickAgent.onPause(Context)

确保在所有的Activity中都调用 MobclickAgent.onResume() 和MobclickAgent.onPause()方法，这两个调用将不会阻塞应用程序的主线程，也不会影响应用程序的性能。

>注意 
>如果您的Activity之间有继承或者控制关系请不要同时在父和子Activity中重复添加onPause和onResume方法，否则会造成重复统计，导致启动次数异常增高。(eg.使用TabHost、TabActivity、ActivityGroup时)。
>当应用在后台运行超过30秒（默认）再回到前端，将被认为是两个独立的session(启动)，例如用户回到home，或进入其他程序，经过一段时间后再返回之前的应用。可通过接口：MobclickAgent.setSessionContinueMillis(long interval) 来自定义这个间隔（参数单位为毫秒）。
>如果开发者调用Process.kill或者System.exit之类的方法杀死进程，请务必在此之前调用MobclickAgent.onKillProcess(Context context)方法，用来保存统计数据。

###2.3  页面的统计
页面统计集成正确，才能够获取正确的页面访问路径、访问深度（PV）的数据。
页面访问路径的数据为全量统计。开发过程中查看测试数据，可以使用友盟集成测试服务。

<span id = "jump"></span>
####2.3.1  只由Activity构成的应用

在Activity中添加

```java
public void onResume() {
super.onResume();
MobclickAgent.onResume(this);
}
public void onPause() {
super.onPause();
MobclickAgent.onPause(this);
}
```

####2.3.2  包含Activity、Fragment或View的应用
1. 管理Fragment的Activity不能继承BaseActivity，而是直接在Activity的onCreate中调用 `MobclickAgent.openActivityDurationTrack(false);`禁止默认的页面统计方式，这样将不会再自动统计该Activity。
2. 在Activity中如[2.3.1](#jump)一样使用 onResume 和 onPause 方法统计时长
3. 在每个Fragment中添加如下代码

```java
public void onResume() {
    super.onResume();
    MobclickAgent.onPageStart("FragmentName"); //统计页面
}
public void onPause() {
    super.onPause();
    MobclickAgent.onPageEnd("FragmentName"); 
}
```

###2.4  发送策略
在程序的入口 Activity 中添加

```java
MobclickAgent.updateOnlineConfig( mContext );
```

Android平台的数据发送策略有两种方式：
* 启动时发送：APP启动时发送当次启动数据和上次的使用时长等缓存数据，当次使用过程中产生的自定义事件数据缓存在客户端，下次启动时发送
* 按间隔发送：按特定间隔发送数据，间隔时长介于90秒与1天之间，可以在后台自定义发送间隔。

在没有取到在线配置的发送策略的情况下，会使用默认的发送策略：启动时发送。

> 注意：打开调试模式（debug）后，在集成测试模式中，数据实时发送，不受发送策略控制
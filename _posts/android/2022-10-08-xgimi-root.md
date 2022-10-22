---
layout: post
title: 极米投影仪刷机及精简
date: 2022-10-08 19:39:49 +0800
tags: [android]
toc:  true
---

- 把固件放在U盘根目录下  
- 一直按住机身的电源键，开机会自动升级固件  
- 进入系统后，进入系统信息，一直按住遥控器左键，进入工厂模式，打开adb  
- 打开路由器的防火墙开关，禁止设备外网，防止升级  

		iptables -I FORWARD  -m mac --mac-source 80:0b:51:0a:74:28 -j DROP

### adb命令
- 安装adb  

		sudo apt-get update
		sudo apt-get install android-tools-adb android-tools-fastboot


#### 本机ADB命令

|adb device|显示安卓设备
|adb kill-server|关闭ADB服务
|adb start-server|开启ADB服务
|adb shell pm list packages|列出所有的App
|adb shell pm list packages -s ***|查找App
|adb shell pm uninstall --user 0 ****|删除系统app
|adb root|root权限
|adb remount|加载读写
|adb shell rm -rf /system/app/*|删除系统应用
|adb push * /system/app|把桌面和ES文件浏览器传到系统应用

#### 远程adb连接

- 首先安卓设备打开 usb 调试
- 设备连接电脑
- 执行下列指令

		adb tcpip 5555
		adb connect <手机IP>:5555
		adb disconnect /断开wifi连接
		adb usb /切换到usb模式


#### 需保留的程序

```
drwxr-xr-x root     root              2018-12-04 19:30 BasicDreams
drwxr-xr-x root     root              2018-12-04 19:37 Bluetooth
drwxr-xr-x root     root              2018-12-04 19:20 Bluetooth3DService
drwxr-xr-x root     root              2018-12-04 19:30 BluetoothMidiService
drwxr-xr-x root     root              2018-12-04 19:31 BluetoothService
drwxr-xr-x root     root              2018-12-04 19:30 HTMLViewer
drwxr-xr-x root     root              2018-12-04 19:27 HoloSpiralWallpaper
drwxr-xr-x root     root              2018-12-04 19:30 MTvFactory
drwxr-xr-x root     root              2018-12-04 19:30 MTvHotkey
drwxr-xr-x root     root              2018-12-04 19:30 MTvMisc
drwxr-xr-x root     root              2018-12-04 19:32 MTvPlayer
drwxr-xr-x root     root              2018-12-04 19:30 MTvProvider
drwxr-xr-x root     root              2018-12-04 19:30 MTvService
drwxr-xr-x root     root              2018-12-04 19:30 MTvTest
drwxr-xr-x root     root              2018-12-04 18:42 MiniTvFactory
drwxr-xr-x root     root              2018-12-04 19:30 Provision
drwxr-xr-x root     root              2018-12-04 18:42 SogouIME
drwxr-xr-x root     root              2018-12-04 19:30 SounderModeService
drwxr-xr-x root     root              2018-12-04 18:42 XgimiBootwizard
drwxr-xr-x root     root              2018-12-04 18:42 XgimiManager
drwxr-xr-x root     root              2018-12-04 19:30 XgimiService
drwxr-xr-x root     root              2018-12-04 18:42 XgimiStreamPlayer
drwxr-xr-x root     root              2018-12-04 18:42 XgimiVoice
-rw-r--r-- root     root        19480 2020-04-13 17:05 app-debug.apk
drwxr-xr-x root     root              2018-12-04 18:42 burn_in_program
drwxr-xr-x root     root              2018-12-04 18:42 camera_test_Z5X
-rw-r--r-- root     root     17682317 2020-04-15 17:22 dbsc.apk
drwxr-xr-x root     root              2018-12-04 18:42 mediaPlayer
drwxr-xr-x root     root              2018-12-04 18:42 misckey
drwxr-xr-x root     root              2018-12-04 18:42 resManager
drwxr-xr-x root     root              2018-12-04 18:42 setting
drwxr-xr-x root     root              2018-12-04 18:42 systwind
drwxr-xr-x root     root              2018-12-04 18:42 vcontrol
drwxr-xr-x root     root              2018-12-04 19:38 webview
drwxr-xr-x root     root              2018-12-04 18:42 wirelessscreen
drwxr-xr-x root     root              2018-12-04 18:42 xgimipaysdk
drwxr-xr-x root     root              2018-12-04 18:42 xgimiweather
```


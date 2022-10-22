---
title: Pve安装openwrt
layout: post
date: '2022-10-08 19:39:49 +0800'
tags:
- openwrt
- linux
- pve
toc: true
---

## 登陆按以下设置  

- 创建虚拟机
- 填写虚拟机名称
- 高级-开机自动启动-下一步
- 类别-Linux（版本5.x-2.6kemel）-不使用任何介质
- cpu核心数量（2个）
- 内存大于256Mb，一般不超过2Gb
- 网卡-VirtIO（半虚拟化），
- VirtIO模型在Openwrt内会显示“Unknown!半双工”，但实测是千兆全双工，不影响使用。
- 把下载好的 openwrt 的 img 文件转化成硬盘文件
	
``` 
		chmod +x img2kvm
		./img2kvm op.img 111 vm-111-disk-1
```

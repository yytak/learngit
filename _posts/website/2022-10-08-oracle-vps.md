---
layout: post
title: Oracle主机安装一键脚本
date: 2022-10-08 19:39:49 +0800
tags: [vps,linux]
toc:  true
---

- 新建一台 vps, arm 架构, ubuntu 20, 保存私钥。

- vnic-ipv4地址-编辑-没有公共IP-更新-编辑-临时公共IP

- windows-xshell-新建会话-IP-public key-设置-用户密钥-浏览-导入-保存的私钥-确定-连接-用户名:ubuntu

- 连接到VPS后更改设置，打开ssh登陆

		sudo su
		nano /etc/ssh/sshd_config

	更改以下语句


		PermitRootLogin yes
		passwordAutoentication yes

- 重启sshd

		systemctl restart sshd.service

- 系统升级

		apt-get update
		apt-get upgrade
	
- 更改时区及更改时间
	
		rm -rf /etc/localtime	
		ln -s /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
		date -s "当前时间"
		apt-get install ntpdate
		ntpdate us.pool.ntp.org

- 关闭防火墙1
	
		iptables -P INPUT ACCEPT
		iptables -P FORWARD ACCEPT
		iptables -P OUTPUT ACCEPT
		iptables -F
	
		apt-get purge netfilter-persistent
		reboot
	
- 关闭防火墙2

		apt-get remove usw
		systemctl stop ufw.service

- 安装脚本

		wget -P /root -N --no-check-certificate "https://raw.githubusercontent.com/mack-a/v2ray-agent/master/install.sh" && chmod 700 /root/install.sh && /root/install.sh

- 先设置BBR



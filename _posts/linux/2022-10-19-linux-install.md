---
layout: post
title:  linux 安装软件几种方式
date:   2022-10-19 21:12:49 +0800
tags: 
- linux
toc:  true
---

### apt 命令安装

|apt update|列出所有可更新的软件清单命令
|apt upgrade|升级软件包
|apt list --upgradeable|列出可更新的软件包及版本信息
|apt full-upgrade|升级软件包，升级前先删除需要更新软件包
|apt install \<package_name>|安装指定的软件命令
|apt install \<package_1> \<package_2> \<package_3>|安装多个软件包
|apt update \<package_name>|更新指定的软件命令
|apt show \<package_name>|显示软件包具体信息,例如 版本号，安装大小，依赖关系
|apt remove \<package_name>|删除软件包命令
|apt autoremove|清理不再使用的依赖和库文件
|apt purge \<package_name>|移除软件包及配置文件
|apt search \<keyword>|查找软件包命令
|apt list \--installed|列出所有已安装的包
|apt list \--all-versions|列出所有已安装的包的版本信息

### Snap 命令安装

snap是在Ubuntu 16 新添加的一种软件包格式。这种格式把软件运行所需的依赖全部打包到软件包里面， 运行的时候持载到一个虚拟的环境里面运行。所有这种格式的软件包安装时不会破坏系统现有的软件包依赖。

|snap list|列出所有 snap 安装情况
|snap find 包名|在应用商店查找软件包
|snap install 包名|安装软件包
|snap refresh 包名|更新软件包
|snap refresh all|更新所有软件包
|snap revert 包名|将 snap 还原到以前安装的版本
|snap remove 包名|卸载软件  

### Dpkg 命令安装 deb 包

dpkg命令来自于英文词组“Debian package”的缩写，其功能是用于管理软件安装包，在Debian系统中最常用的软件安装、管理、卸载的实用工具。像网易云音乐、百度网盘这些并没有在软件源里面，而是在官网提供deb后缀的软件包下载，这种软件我们就要用到dpkg命令来安装了。

|dpkg -i|手动安装软件包,如果在遇到了软件依赖的问题,可以用apt-get -f install解决
|dpkg \--info|列出软件包解包后的包名称.
|dpkg -l|列出当前系统中所有的包.可以和参数less一起使用在分屏查看
|dpkg -l|查询软件包的信息
|dpkg -c|显示软件包内文件列表
|dpkg -s|查询已安装的包的详细信息.
|dpkg -L|查询系统中已安装的软件包所安装的位置. (类似于rpm -ql)
|dpkg -S|查询系统中某个文件属于哪个软件包. (类似于rpm -qf)
|dpkg -I|查询deb包的详细信息
|dpkg -r|卸载软件包.不是完全的卸载,它的配置文件还存在.
|dpkg -P|全部卸载
|dpkg -reconfigure|重新配置

### Rpm 命令安装

RPM包默认安装路径

|/etc/|配置文件安装目录
|/usr/bin/|可执行的命令安装目录
|/usr/lib/|程序所使用的函数库保存位置
|/usr/share/doc/|基本的软件使用手册保存位置
|/usr/share/man/|帮助文件保存位置

<br>

|rpm -ivh|安装包，-i 安装， -v 显示详细信息， -h 显示进度
|-nodeps|不检测依赖性安装，强制安装。注意，这样不检测依赖性安装的软件基本上是不能使用的。
|-replacefiles|替换文件安装。包中的部分文件已经存在，导致无法安装。这个选项可以覆盖安装。
|-replacepkgs|替换软件包安装。如果软件包已经安装，那么此选项可以把软件包重复安装一遍。
|-force|强制安装。不管是否已经安装，都重新安装。也就是 -replacefiles 和 -replacepkgs 的综合。
|-test|测试安装。不会实际安装，只是检测一下依赖性。
|-prefix|指定安装路径，而不使用默认安装路径。
|rpm -Uvh|升级软件，-U 没安装过直接装，安装过升最新版
|rpm -Fvh|只能升级，没安装则不安装
|rpm -e|删除软件

### Yum 方式安装 rpm 包

rpm 只能安装已经下载到本地机器上的rpm 包. yum能在线下载并安装rpm包,能更新系统,且还能自动处理包与包之间的依赖问题,这个是rpm 工具所不具备的。

### Bundle 文件的安装

Bundle 文件是可执行文件，首先给予可执行权限，再直接执行这个命令。

		sudo chmod +x *.bundle
		./*.bundle


### tar.gz 源代码包安装

		cd ***.tar.gz
		tar -xzvf ***.tar.gz
		cd ***
		./configure
		make
		make install
		
### tar.bz2 源代码包安装




### Bin 文件安装

下载到的软件名是soft.bin，一般情况下是个可执行文件

		chmod +x soft.bin
		./soft.bin
		


---
layout: post
title: Docker 安装 Halo 博客 
date: 2022-10-13 21:34:49 +0800
tags: [docker, linux, blog]
toc:  true
---



### 创建工作目录

		mkdir ~/.halo && cd ~/.halo
		
### 下载配置文件到工作目录

		wget https://dl.halo.run/config/application-template.yaml -O ./application.yaml

### 修改配置文件，配置数据库或者端口等

		vim application.yaml
		
### 拉取blog镜像源

		docker pull halohub/halo:1.4.13
		
### 创建容器

		docker run -it -d --name halo -p 8090:8090 -v ~/.halo:/root/.halo --restart=unless-stopped halohub/halo:1.4.13
		
	- 参数解释

		-it：开启输入功能并连接伪终端
		-d：后台运行容器
		--name：为容器指定一个名称
		-p：端口映射，格式为​​主机(宿主)端口:容器端口​​​ ，可在​​application.yaml​​ 配置。
		-v：工作目录映射。形式为：-v 宿主机路径:/root/.halo，后者不能修改。
		--restart：建议设置为​​unless-stopped​​，在 Docker 启动的时候自动启动 Halo 容器。


### 打开 http://ip:端口号 

安装引导界面，比如我的服务公网IP是:81.71.136.94,那么我访问的地址就是:​ ​http://81.71.136.94:8090/​​  
填写完信息之后，点击安装，安装完成之后，会跳转到登录页面。  
输入账号密码，点击登录会进入到博客后台管理界面。  
点击跳转到首页，可以直达到博客首页。   

### 访问测试

访问：​ ​http://*.*.*.*:8090/​​（需要更换为你自己的服务器IP地址噢~）


---
layout: post
title:  ubuntu 脚本命令，crontab命令, 桌面快捷方式
date:   2022-10-19 19:14:49 +0800
tags: 
- linux
- ubuntu
toc:  true
---

### 可执行脚本

1. 在桌面新建脚本 *.sh  

		#!/bin/bash
		command

2. 给脚本加可执行权限，右键默认运行程序

### Crontab 命令

1. 所在目录  

	|/var/spool/cron/|每个用户的 crontab 任务 
|/etc/crontab|这个文件负责调度各种管理和维护任务
|/etc/cron.d/|存放任何要执行的 crontab 文件或脚本
|/etc/cron.hourly|每小时执行一次，daily, weekly, monthly

2. crontab 命令与参数

	crontab [-u username]  //省略用户表表示操作当前用户  
-e      (编辑工作表)  
-l      (列出工作表里的命令)  
-r      (删除工作作)  

3. crontab 文件构成

	crontab的命令构成为 时间+动作，其时间有分、时、日、月、周五种.  
	分钟(0-59) 小时(0-23) 几号(1-31) 月份(1-12) 星期几(0-6) 执行的命令
 
|*|取值范围内的所有数字
|/|每过多少个数字
|-|从X到Z
|,|散列数字

<br>

|* * * * * command|每分钟执行一次
|3,15 * * * * command|第小时第3和第15分钟执行
|3,15 8-11 * * * command|每天上午8-11点第3和第15分钟执行
|3,15 8-11 */2 * * command|每隔2天上午8-11点第3和第15分钟执行
|3,15 8-11 * * 1 command|每周一上午8-11点第3和第15分钟执行
|30 21 * * * command|每天21:30执行
|45 4 1,10,22 * * command|每月1号10号22号4:45执行
|10  1  *  *  6,0 command|每周六，周日1:10分执行
|0,30  18-23  *  *  * command|每天18-23点，每半个小时执行
|*  */1  *  *  * command|每天整点执行
|*  23-7/1  *   *   * command|每天23点-第二天7点每小时执行
|0  11  4  *  mon-wed command|每个月4号和每周一到周三11:00执行
|@reboot command|每次重启执行

### 桌面快捷方式

/usr/share/applications/

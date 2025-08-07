---
title: 【持续更新】Windows系统实用bat命令大全
date: '2022-01-02 17:08'
permalink: /44.html
index_img: /img/article/44.jpg
categories:
  - 计算机
  - Windows
tags:
  - 计算机
  - 电脑知识
---

#### **一、服务类**

##### **启动系统服务命令**


	@echo off
	net start 服务名称
	exit


##### **结束系统服务命令**


	@echo off
	net stop 服务名称
	exit


##### **结束并重启服务命令**


	@echo off
	echo STOP
	net stop 服务名称
	timeout 5
	echo START
	net start 服务名称
	pause


`timeout 5` 表示等待5秒后再打开服务

##### **设置服务启动类型**


	@echo off
	sc config 服务名称 start= auto（自动）/demand（手动）/disabled（禁用）
	exit


#### **二、关闭exe程序**

##### **强制关闭程序**


	taskkill /f /im 程序名称

##### **强制关闭所有程序**


	taskkill /F /FI "USERNAME eq 账户名" /FI "IMAGENAME ne explorer.exe" /FI "IMAGENAME ne dwm.exe


#### **三、关机、重启**

##### **关机、重启**


	shutdown -s -t 10


-s（关机）
-r（重启）
10（10秒后关机）

#### **四、删除文件**

##### **删除文件夹下所有文件**


	del 文件目录\*.* /F/S/Q/A


`*.*`中第一个`*`是文件名，第二个`*`是文件后缀，直接写`*.*`代表所有文件名所有后缀，即删除当前目录下所有文件，也可以删除指定文件


	（不区分大小写）
	/P            删除每一个文件之前提示确认。
	/F            强制删除只读文件。
	/S            删除所有子目录中的指定的文件。
	/Q            安静模式。删除全局通配符时，不要求确认。
	/A            根据属性选择要删除的文件
	属性           R  只读文件                    S  系统文件
	              H  隐藏文件                    A  存档文件
	              I  无内容索引文件               L  重分析点
	              -  表示“否”的前缀


##### **删除文件夹**


	rmdir 文件目录 /S/Q
---
	（不区分大小写）
	/S            删除所有子目录中的指定的文件。
	/Q            安静模式。删除全局通配符时，不要求确认。






**待更新...**
---
title: 将电脑程序用Windows服务运行
date: '2022-02-14 19:34'
permalink: /157.html
index_img: /img/article/157.jpg
categories:
  - 计算机
  - Windows
tags:
  - 计算机
  - 电脑知识
---

此方法可以开机时不登录系统自动运行Windows程序

#### **1. 下载**

instsrv.exe和srvany.exe [点我下载](https://200408.lanzout.com/iy7cE27507da)

将两个文件放到C盘某个文件夹中，这里为`C:\fuwu`
![](https://img.w6wg.cn/i/2022/07/15/mdmyy7.png)

#### **2. 以管理员身份运行命令提示符**

![](https://img.w6wg.cn/i/2022/07/15/mdqo6v.png)
命令里面输入以下内容并回车，其中两个引号里面分别是上面下载的两个程序的路径


	"C:\fuwu\instsrv.exe" 服务名称 "C:\fuwu\srvany.exe"


提示下面内容就表示成功了
![](https://img.w6wg.cn/i/2022/07/15/mdtr4l.png)

#### **3. 打开注册表**

按Win+R打开运行输入`redegit`

![](https://img.w6wg.cn/i/2022/07/15/me5dpa.png)
找到目录`HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\（你的服务名称）`
右键单击你的服务名称文件夹选择新建项，名称为"Parameters"
![](https://img.w6wg.cn/i/2022/07/15/me8hfw.png)

选中"Parameters"，在右边新建一个字符串值，名称为"Application"
![](https://img.w6wg.cn/i/2022/07/15/mebhk1.png)
数值数据里填写你要做成服务的程序的完整路径（带程序名称+后缀)
例如：


	E:\QQ\Bin\QQ.exe


![](https://img.w6wg.cn/i/2022/07/15/meegkg.png)
再次创建一个字符串值，名称为"AppDirectory"，数值数据里填写你要做成服务的程序所在的目录
例如：


	E:\QQ\Bin


![](https://img.w6wg.cn/i/2022/07/15/mehmwe.png)

#### **4. 打开服务**

Win+R打开运行输入`services.msc`打开服务，可以找到创建的服务，启动这个服务就可以了，双击服务可以设置启动方式
![](https://img.w6wg.cn/i/2022/07/15/mettb7.png)

#### **5. 删除服务**

如果想删除这个服务，删除注册表中创建的服务名称的文件夹，然后重启电脑即可。
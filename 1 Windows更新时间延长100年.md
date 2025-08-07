---
title: Windows更新时间延长100年
date: '2024-08-23 14:42'
permalink: /1.html
index_img: /img/article/1.jpg
categories:
  - 计算机
  - Windows
tags:
  - 计算机
  - 电脑知识

---

 

# **方式一：一键添加注册表（推荐）**

1. 下载FlightSettingsMaxPauseDays.reg[点我下载](https://www.123pan.com/s/mzurVv-edh63)，双击运行，选择”是“添加到注册表中。

2. 打开设置，找到Windows更新，可以任意选择延长的时间。

# **方式二：手动添加注册表**

## **1. 添加注册表**

Win+R打开运行，输入`regedit`回车打开注册表编辑器

地址栏中输入`计算机\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\WindowsUpdate\UX\Settings`后回车

   ![](https://img.w6wg.cn/imgs/Snipaste_2024-08-23_14-54-09.jpg)

在下方空白处单击右键新建选择**DWORD(32位)值(D)**

名称为`FlightSettingsMaxPauseDays`

![](https://img.w6wg.cn/imgs/20240823145826.png)

双击新建的`FlightSettingsMaxPauseDays`选择基数为**十进制**

数值数据为36500，代表最高可延长100年

   ![](https://img.w6wg.cn/imgs/20240823150612.png)

## **2. 打开设置**

找到Windows更新，可以任意选择延长的时间

![](https://img.w6wg.cn/imgs/20240823150809.png)


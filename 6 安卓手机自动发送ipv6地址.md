---
title: 安卓手机自动发送ipv6地址到企业微信
date: '2025-02-14 21:06'
permalink: /6.html
index_img: /img/article/6.jpg
categories:
  - 手机
tags:
  - 安卓
  - root
  - Magisk
  - ipv6
---



{% note success %}

**为什么要自动发送ipv6？**
	由于公网ipv4资源短缺，不好申请，而ipv6几乎都有，与ipv4一样可以公网访问，但ipv6并不是固定的，所以需要自动发送新ipv6地址

{% endnote %}







# 方式一、无root使用

1. 使用[双卡助手](https://www.coolapk.com/apk/com.cozylife.smshelper)软件
2. 使用maccrodroid软件，教程：[查看链接](https://www.coolapk.com/feed/47952314?shareKey=M2UzYTE2ODU2OWY4NjdkMGRjODA~&shareUid=3557589&shareFrom=com.coolapk.market_15.0.3)





# 方式二、有root+magisk使用



## **方法一：**

​	使用ddns-go模块，ipv6地址更新时自动通知，但是好像需要有自己的域名才可以推送



## **方法二：**

### 1. 获取企业微信webhook

​	注册一个企业微信，全新创建企业-其他-创建，创建完成后消息页面有一个全员标志的群，进去点右上角，选择群机器人-添加机器人-新建-添加，有一个Webhook地址，复制下来



### **2. 下载文件**

​	本脚本作用是每隔30分钟检查一次ipv6地址，如果ip地址不相同则发送ipv6地址到企业微信

​	https://www.123912.com/s/mzurVv-cJ963 提取码:`nPoE`

​	将两个文件放到`/data/adb/service.d`目录中，用[MT文件管理器](https://mt2.cn/)将两个文件权限都改成777



### **3. 编辑文件send_ip_0.sh和send_ip_1.sh**

​	两个文件都需要更改以下两处

​	第24行双引号中填入步骤一中复制的Webhook地址

![](https://img.w6wg.cn/Screenshot_2025-02-14-22-01-34-464_bin.mt.plus.canary.png)

​	第4行双引号中填入日志文件保存的路径

![](https://img.w6wg.cn/Screenshot_2025-02-14-22-06-07-247_bin.mt.plus.canary.png)

执行脚本`send_ip_0.sh`，勾选使用root执行，如果企业微信收到信息就表示成功了，接下来配置定时执行



### **4. 定时执行**

​	创建目录`/system/cron/crontab`，在`crontab`文件夹中新建`root`文件，里面填写以下代码，表示每半小时运行一次，也可自己更改时间，[Cron - 在线Cron表达式生成器](https://cron.ciding.cc/)


	*/30 * * * *	/data/adb/service.d/send_ip_0.sh

​	配置完后执行`send_ip_1.sh`脚本，不然不会定时执行

​	配置完后执行`send_ip_1.sh`脚本，不然不会定时执行

​	配置完后执行`send_ip_1.sh`脚本，不然不会定时执行

### **5. 手机锁屏休眠问题**

​	有些手机锁屏后一段时间会自动休眠，导致脚本不会定时执行	

​	关于如何知道锁屏后有没有休眠，以上步骤配置完后等待一段时间或一晚上，查看日志文件每隔半小时是否有日志输出，如果有就表示手机不会休眠或没有影响，如果没有就需要开启唤醒锁，在`send_ip_1.sh`文件中将第22行前面的`#`删除，再执行此脚本，手机锁屏后就不会休眠

![](https://img.w6wg.cn/Screenshot_2025-02-14-22-11-35-453_bin.mt.plus.canary.png)



### **6. 其它**

​	其它地方也可以自己看着改，都标注了注释，不过鉴于大佬不看小白不会，建议还是别乱动[doge]



### **其它**

​	关于开机自动开启usb调试和usb安全模式，可以直接加在`send_ip_1.sh`文件`#!/system/bin/sh`下方


	until [ $(getprop sys.boot_completed) -eq 1 ] ; do
	  sleep 5
	done
	settings put global adb_enabled 1
	setprop persist.security.adbinput 1



# 参考文章



[**教程-安卓Root使用crontab定时任务执行sh脚本或shell命令**](https://www.coolapk.com/feed/42982745?shareKey=Zjg2Mjk5NzJiYTc2NjdhZjVmYjE~&shareUid=3557589&shareFrom=com.coolapk.market_15.0.3)

[**安卓Root默认开机启用adb调试和无线调试固定5555端口**](https://www.coolapk.com/feed/42956384?shareKey=NmM2YjczNDAwOTRhNjdhZjYwZWE~&shareUid=3557589&shareFrom=com.coolapk.market_15.0.3)


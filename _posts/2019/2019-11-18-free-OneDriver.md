---
layout: post
title: "申请 免费OneDrive 5T 网盘教育邮箱, rclone raiDriver 挂在硬盘"
subtitle: '申请 免费OneDrive 5T 网盘教育邮箱, rclone raiDriver 挂在硬盘'
author: "panmg"
header-style: text
catalog:    true
tags:
  - OneDriver 
  - 免费资源
---


## OneDriver 在国内速度很好, 所以网上有很多羊毛教程

> 申请最重要的是 通过 微软认证的 教育邮箱, 有了这个邮箱就可以申请免费教育版的 OneDriver

这里 记录一下 网上可用的 临时教育邮箱odmail 我自己用的, 教程也很详细

* [odmail](https://search.cocook.cn/redirect?url=https://t.odmail.cn/)   验证可用, 5T 无 office365
* [xkx](https://search.cocook.cn/redirect?url=http://xkx.me/)   未验证
* [readmail](https://search.cocook.cn/redirect?url=http://onedrive.readmail.net/)   未验证
* [chacuo](https://search.cocook.cn/redirect?url=http://24mail.chacuo.net/)   未验证

>特别提醒：chacuo 这个邮箱只需复制邮箱ID，不需要复制@chacuo.net，注册的时候请使用邮箱ID+@stu.mao.office.gy 即可！
如：ifkbdp74390@stu.mao.office.gy
申请成功后需要加入N软的组（NRuan.com）内，否则会被删除：https://account.activedirectory.windowsazure.com/r#/groups



## 使用 rclone raiDriver 挂在硬盘

### raiDriver windows 上用

https://www.xiaoz.me/archives/10397

`raiDriver` 挂在硬盘 的优点是 直接虚拟一个盘符出来, 不用占用自己 磁盘的空间, 直接安装就可以, 可以挂载的 很多应用盘
下载 客户端 直接安装即可, windows版本适用  [raiDriver下载地址](https://search.cocook.cn/redirect?url=https://www.raidrive.com/Download) 
直接应用授权即可
这是我自己挂的oneDriver 

![image](https://cocook.cn/img/raidriver.jpg)


### rclone 可用于 window 或 linux

具体安装教程 [点这里](https://search.cocook.cn/redirect?url=https://www.xiaoz.me/archives/10397)

>服务器上CentOS大部分未安装图形界面，但是Rclone必须要在有内置浏览器的电脑才能正常完成授权，因此这里使用的办法是先在本地Windows电脑安装Rclone并获取授权后的token，再将其复制到CentOS的服务器上。

**1.安装rclone, 先 安装windows版的 获取 token**
	
[win64下载地址 ](https://downloads.rclone.org/v1.41/rclone-v1.41-windows-amd64.zip)

 安装后 使用 rclone config 获取 token 

**2. 安装centos 版的 rclone config , 填入 windows 获取到token**
	
安装 curl https://rclone.org/install.sh | sudo bash
	
**3. 继续挂载**
```nginx

	#安装fuse
	yum -y install fuse
	#创建挂载目录
	mkdir -p /home/onedrive
	#挂载
	rclone mount remote:path/to/files /home/onedrive
	#如果需要后台保持运行，使用下面的命令
	nohup rclone mount remote:path/to/files /home/onedrive &
	
	rclone mount onedrive:ServerBackUp/backup /home/onedrive  --umask 0000  --default-permissions  --allow-non-empty  --allow-other  --transfers 4  --buffer-size 32M  --low-level-retries 200 &
	
	//国外使用googledriver 速度快, 国内申请到的 onedriver大部分在香港参考地址
	//https://www.moerats.com/archives/877/
	rclone mount google:/DB /home/ggdrive --umask 0000 --default-permissions --allow-non-empty --allow-other --transfers 4 --buffer-size 32M --low-level-retries 200
	
```
	
![image](https://cocook.cn/img/rclone.jpg)

### oneindex 一个php 写的 可用于 oneDriver上传 浏览工具

 [github地址](https://github.com/donwa/oneindex), 有兴趣的可以捣鼓一下
 

### multcloud  可以连接 onedrive googledriver 还有 百度云盘等工具

官网地址： [multcloud](https://search.cocook.cn/redirect?url=https://www.multcloud.com)
有免费流量,可以在网盘中互转 备份, 主要是可以轻松　使用`googleDriver`, 不用翻墙，　可以用来备用一下

![image](https://cocook.cn/img/multCloud.jpg)


> 开开车, 注意打开方式 [JAV高清名优](https://www.xkspp.com)
推廣 每日熱點   [cncknews](https://www.cncknews.com/)


---
layout: post
title: "修改hosts 文件 github clone 加速 访问 github 加速"
subtitle: 'Modify the hosts file github clone speed up access github acceleration'
author: "panmg"
header-style: text
tags:
  - github
---

### 修改hosts 文件 github clone 加速 访问 github 加速

我们可以通过修改hosts文件来提速,获取github的IP地址

### 1.手动访问：https://www.ipaddress.com/ 网址，然后依次获取以下三个网址的IP

	github.com
	github.global.ssl.fastly.net
	codeload.github.com

	这是我获取的IP
	192.30.253.113 github.com
	
	151.101.25.194 github.global.ssl.fastly.net

	192.30.253.121 codeload.github.com


### 2 修改系统本地的hosts文件，添加内容，

	Windows系统的hosts文件路径：C:\Windows\System32\drivers\etc\hosts

### 3. 打开cmd 界面

	C:\Users\tomsun>ipconfig /flushdns
	Windows IP 配置
	已成功刷新 DNS 解析缓存。


### 4. 最后, 到底有没有用, 只能自己体会了





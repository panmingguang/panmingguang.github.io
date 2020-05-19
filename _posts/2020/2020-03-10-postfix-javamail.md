---
layout: post
title: "linux 安装 postfix 邮件服务"
subtitle: 'javamail 连接 postfix 发送邮件'
author: "panmg"
header-style: text
catalog:    true
tags:
  - postfix
  - javamail
---


## 主要安装依赖

```	

	[root@mail ~]# yum -y install postfix.x86_64 dovecot.x86_64  cyrus-sasl
	
	yum install cyrus-sasl-plain
	
	（postfix主要是为发件服务25，devocot为收件服务110、145， cyrus-sasl登陆验证服务）
```


步骤,安装 改配置  建用户, 测试 发送邮件, 最后使用 javamail 连接, 注意开发端口 25, 或改端口

添加 解析, MX A 记录 

添加 SPF(否则gmail qq等监测会退信)   txt   v=spf1 ip4:107.150.37.60 ip4:107.150.37.61 ~all

## 参考 

https://blog.csdn.net/cbuy888/article/details/83212810

https://www.cnblogs.com/chris-cp/p/4843407.html

## 主要错误

fatal: no SASL authentication mechanisms 

解决方法  yum install cyrus-sasl-plain









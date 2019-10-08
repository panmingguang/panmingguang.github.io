---
layout: post
title: "使用caddy 部署 Typecho 免费https"
subtitle: '使用caddy 部署 Typecho 免费https'
author: "panmg"
header-style: text
catalog:    true
tags:
  - centos
  - caddy
  - typecho
---

## 安装 caddy
`wget -N --no-check-certificate https://raw.githubusercontent.com/ToyoDAdoubiBackup/doubi/master/caddy_install.sh && chmod +x caddy_install.sh && bash caddy_install.sh`
`#备用地址`
`wget -N --no-check-certificate https://www.moerats.com/usr/shell/Caddy/caddy_install.sh && chmod +x caddy_install.sh && bash caddy_install.sh`

## 修改配置文件
`cd /usr/local/caddy` 新建 Caddyfile
编辑 Caddyfile 加入以下配置

```bash
	http://47.97.156.168 { # 修改域名, 如果没有先写ip
	    gzip
	    #tls admin@moerats.com   # 自动 https, 有域名后放开,加自己邮箱
	    root /data/typecho
	    fastcgi / 127.0.0.1:9000 php
	    rewrite {
	        if {path} not_match ^\/admin
	        to {path} {path}/ /index.php?{query}
	     }
	}
	#重定向
	#http://www.cocook.cn {
	#redir https://www.cocook.cn{url}
	#}
	```bash
	
## 常用caddy 备忘
```java
	启动：/etc/init.d/caddy start
	停止：/etc/init.d/caddy stop
	重启：/etc/init.d/caddy restart
	查看状态：/etc/init.d/caddy status
	查看Caddy启动日志：tail -f /tmp/caddy.log
	安装目录：/usr/local/caddy
	Caddy配置文件位置：/usr/local/caddy/Caddyfile
	Caddy自动申请SSL证书位置：/.caddy/acme/acme-v01.api.letsencrypt.org/sites/xxx.xxx(域名)/
```java

## 启动失败 , 查看是否安装其他的 web服务

`netstat -nlpt`
```sh
	Active Internet connections (only servers)
	Proto Recv-Q Send-Q Local Address               Foreign Address             State       PID/Program name   
	tcp        0      0 127.0.0.1:9000              0.0.0.0:*                   LISTEN      465/php-fpm         
	tcp        0      0 0.0.0.0:3306                0.0.0.0:*                   LISTEN      22251/mysqld        
	tcp        0      0 0.0.0.0:80                  0.0.0.0:*                   LISTEN      7169/caddy          
	tcp        0      0 0.0.0.0:22                  0.0.0.0:*                   LISTEN      1369/sshd           
	tcp        0      0 127.0.0.1:25                0.0.0.0:*                   LISTEN      1471/master  
```sh



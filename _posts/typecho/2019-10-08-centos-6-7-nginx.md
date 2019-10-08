---
layout: post
title: "centos6 centos7 yum 安装  nginx  和一些配置"
subtitle: 'centos6 centos7 yum 安装  nginx  和一些配置'
author: "panmg"
header-style: text
catalog:    true
tags:
  - centos
  - nginx
  - typecho
---


http://www.nginx.cn/doc/  (很多的教程)
http://nginx.org/en/docs/

## centos7
```nginx
rpm -Uvh http://nginx.org/packages/centos/7/noarch/RPMS/nginx-release-centos-7-0.el7.ngx.noarch.rpm
yum install nginx
systemctl start nginx.service
systemctl stop nginx.service
systemctl enable nginx.service
```nginx

## centos6
```nginx
	rpm -ivh http://nginx.org/packages/centos/6/noarch/RPMS/nginx-release-centos-6-0.el6.ngx.noarch.rpm
	yum info nginx
	yum install nginx
	service nginx start restart stop reload
```

# 查看版本
`nginx -v `
# 查看端口占用 80
`netstat -nlpt`

## typecho 配置
```nginx
	server {
		listen       80;
		#定义使用www.xx.com访问
		server_name 47.97.156.168;
		root /data/typecho/;
		index index.html index.htm index.php;
	        if (!-e $request_filename) {
	            rewrite ^(.*)$ /index.php$1 last;
	        }
	        location ~ .*\.php(\/.*)*$ {
	            include fastcgi.conf;
	            fastcgi_pass  127.0.0.1:9000;
	        }
		access_log off;
		expires 24h;
	}
```


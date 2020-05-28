---
layout: post
title: "k8s 部署nginx 使用configMap"
subtitle: 'k8s 部署nginx 使用configMap'
author: "panmg"
header-style: text
catalog:    true
tags:
  - k8s nginx
  - configMap

---

### nginx 部署在 k8s 上, 并使用 configMap 修改 nginx配置
https://kubesail.com

kubectl 客户端使用, 下载windows k8s 客户端

### 1. 创建configmap 从本地文件 nginx.conf 从附件, 使用自定义nginx 生效

* kubectl create configmap nginx-conf --from-file nginx.conf
* kubectl delete configmap nginx-conf
* kubectl get configmap
* kubectl create -f nginx-conf.yaml
* kubectl delete -f nginx-conf.yaml

### 2. kubesail.com deployment 从 附件deployment.yaml

获取节点 kubectl get pod

进入, 进入查看  kubectl exec -it nginx-b568d9f55-cgc88 bash

	```yaml
	   
	apiVersion: apps/v1
	kind: Deployment
	metadata:
	  name: nginx
	spec:
	  selector:
	    matchLabels:
	      app: nginx
	  replicas: 1
	  template:
	    metadata:
	      labels:
	        app: nginx
	    spec:
	      containers:
	        - name: nginx
	          image: nginxinc/nginx-unprivileged
	          imagePullPolicy: Always
	          resources:
	            requests:
	              cpu: '20m'
	              memory: '10Mi'
	            limits:
	              cpu: '1000m'
	              memory: '512Mi'
	          ports:
	            - containerPort: 8080
	          volumeMounts:
	            - mountPath: /etc/nginx/nginx.conf
	              name: nginx-conf
	              subPath: nginx.conf
	      volumes:
	      - configMap:
	          name: nginx-conf
	        name: nginx-conf
	   
	
	
	``` yaml


### 3. 配置域名即可


参考 
https://www.orchome.com/1940  看这一个
https://gist.github.com/petitviolet/d36f33d145d0bbf4b54eb187b79d0244
http://www.bubuko.com/infodetail-3358084.html
https://www.cnblogs.com/xiangyu5945/p/11121055.html

http://docs.kubernetes.org.cn/618.html
https://kubernetes.io/zh/docs/tasks/configure-pod-container/configure-pod-configmap/

>> 开开车, 注意打开方式 [JAV高清名优](https://www.xkspp.com)

>推廣 每日熱點   [cocook 每日熱點](https://blog.cocook.cn/)


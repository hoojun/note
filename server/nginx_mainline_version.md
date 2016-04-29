# Ubuntu安装Pre-Built Packages for Mainline version

这篇博客里面记录怎么在ubuntu下面安装最新版本的nginx,nginx在今年(2015)年提供了对http2的支持。作为一个web开发者,需要对这种新的知识加以了解。

本文参考了nginx官网安装教程(http://nginx.org/en/linux_packages.html)

1. 添加nginx_signing.key

```
# 下载nginx签名文件
$ wget http://nginx.org/keys/nginx_signing.key 
$ sudo apt-key add nginx_signing.key
```

2. 添加镜像源

把下面两行文件添加到`/etc/apt/sources.list`下面 

```
deb http://nginx.org/packages/mainline/ubuntu/ codename nginx
deb-src http://nginx.org/packages/mainline/ubuntu/ codename nginx
```

3. 安装

```
apt-get update
apt-get install nginx
```

经过上面几步就可以安装最新的nginx了
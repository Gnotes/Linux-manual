# Nginx

1. 安装编译工具

```bash
$ yum -y install make zlib zlib-devel gcc-c++ libtool openssl openssl-devel pcre
```

2. 查看 [NGINX版本](http://nginx.org/en/download.html)

3. 下载源码

```bash
$ wget http://nginx.org/download/nginx-1.14.0.tar.gz
```

4. 解压

```bash
$ tar -zxvf nginx-1.14.0.tar.gz -C /usr/local
```

5. 编译安装

```bash
$ ./configure
$ make
$ make install # /usr/local/nginx
```

6. 添加环境变量

> 修改 `~/.bash_profile`

```bash
NGINX_HOME=/usr/local/nginx
PATH=$PATH:$HOME/bin:$NGINX_HOME/sbin

export PATH
```

立即生效

```bash
$ source ~/.bash_profile
```

7. 启动

```bash
$ nginx
```

8. 查看是否启动

```bash
$ ps -ef | grep nginx
```

## 其他

```bash
nginx -t # 验证配置是否正确
nginx -s reload # 重启服务
```

## 参考

- [Linux下NGINX安装](https://blog.csdn.net/yejiyueshang/article/details/78697224)
- [linux/centOS 下安装 ngnix](https://blog.csdn.net/qq_30038111/article/details/79410354)
# Redis

[下载](http://redis.io/download) 最新稳定版本

1. 下载并解压
```bash
$ wget http://download.redis.io/releases/redis-4.0.11.tar.gz
$ tar xzf redis-4.0.11.tar.gz -C /usr/local
```

2. 编译安装

```bash
$ cd /usr/local/redis-4.0.11
$ make # 编译Redis
$ make test # 测试Redis 是否正常
$ make install # 安装到默认目录 /usr/local/bin
```

3. 启动

```bash
redis-server
```

## WARNING

1. WARNING: The TCP backlog setting of 511 cannot be enforced because /proc/sys/net/core/somaxconn is set to the lower value of 128

> TCP  backlog设置值，511没有成功，因为 `/proc/sys/net/core/somaxconn` 这个设置的是更小的128.

解决方式：`vim /etc/sysctl.conf`，添加如下配置

```bash
net.core.somaxconn = 1024 # 指定为更大的值
```

并执行如下命令

```bash
$ sysctl -p # read values from file
```

2. WARNING overcommit_memory is set to 0! Background save may fail under low memory condition. To fix this issue add 'vm.overcommit_memory = 1' to /etc/sysctl.conf and then reboot or run the command 'sysctl vm.overcommit_memory=1' for this to take effect.

> overcommit_memory参数设置为0！在内存不足的情况下，后台程序save可能失败。建议在文件 /etc/sysctl.conf 中将overcommit_memory修改为1

解决方式：`vim /etc/sysctl.conf`，添加如下配置

```bash
vm.overcommit_memory = 1
```

并执行如下命令

```bash
$ sysctl -p # read values from file
```

3. WARNING you have Transparent Huge Pages (THP) support enabled in your kernel. This will create latency and memory usage issues with Redis. To fix this issue run the command 'echo never > /sys/kernel/mm/transparent_hugepage/enabled' as root, and add it to your /etc/rc.local in order to retain the setting after a reboot. Redis must be restarted after THP is disabled

> 你使用的是透明大页，可能导致redis延迟和内存使用问题。执行 echo never > /sys/kernel/mm/transparent_hugepage/enabled 修复该问题

解决方式：`vim /etc/rc.local`，添加如下配置，并在当前命令行执行这条命令(本次开机也生效)

```bash
echo never > /sys/kernel/mm/transparent_hugepage/enabled
```

## 参考

- [make & make install](https://zhidao.baidu.com/question/1609799056285524187.html)
- [Redis学习记录](https://www.jianshu.com/p/da69edda2a43)



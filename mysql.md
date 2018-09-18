# MySql

所有平台的 [MySQL](https://dev.mysql.com/downloads/mysql/) 挑选你需要的 MySQL Community Server 版本及对应的平台

> 注意：安装过程我们需要通过开启管理员权限来安装，否则会由于权限不足导致无法安装。

**Linux平台上推荐使用 [`RPM包`](http://man.linuxde.net/rpm) 来安装Mysql**

1. 检查是否已安装 MySQL

```bash
$ rpm -qa | grep mysql

# rpm -e mysql # 普通删除模式
# rpm -e --nodeps mysql # 强力删除模式，如果使用上面命令删除时，提示有依赖的其它文件，则用该命令可以对其进行强力删除
```

2. 查找 [安装源](https://dev.mysql.com/downloads/repo/yum/)

**选择el7**

> EL `RedHat Enterprise Linux` 的简写

- EL5软件包用于在 `RedHat5.x`,`CentOS5.x`,`CloudLinux5.x` 的安装
- EL6软件包用于在 `RedHat6.x`,`CentOS6.x`,`CloudLinux6.x` 的安装
- EL7软件包用于在 `RedHat7.x`,`CentOS7.x`,`CloudLinux7.x` 的安装

3. 下载源

```bash
$ wget https://dev.mysql.com/get/mysql80-community-release-el7-1.noarch.rpm
```

3. 添加 MySql 源

```bash
$ sudo yum localinstall mysql80-community-release-el7-1.noarch.rpm
```

4. 检查MySql启用的源

```bash
$ yum repolist enabled | grep "mysql.*-community.*"
```

5. 安装 MySql

```bash
$ sudo yum install mysql-community-server
```

6. 启动服务

```bash
sudo service mysqld start
```

7. 查看是否启动成功

```bash
$ sudo service mysqld status
```

8. 查看初始密码

> 初始用户 `'root'@'localhost` 的密码被保存在 `/var/log/mysqld.log` 中

```bash
$ sudo grep 'temporary password' /var/log/mysqld.log
```

9. 登录

```bash
$ mysql -uroot -p
Enter password:
```

10. 修改初始密码

> 默认的密码校验规则为 `至少` 一个大写字母，一个小写字母，一个数字，一个符号，并且至少 8 位

```bash
$ ALTER USER 'root'@'localhost' IDENTIFIED BY 'Password4Mysql!';
Query OK, 0 rows affected (0.16 sec)

# FLUSH PRIVILEGES; # 有些需要刷新权限
```

## 其他

```bash
$ sudo service mysqld stop # 关闭服务
$ sudo service mysqld restart # 重启服务
```

## 参考

- [MySQL 安装](http://www.runoob.com/mysql/mysql-install.html)
- [Installing MySQL on Linux Using the MySQL Yum Repository](https://dev.mysql.com/doc/refman/5.7/en/linux-installation-yum-repo.html)
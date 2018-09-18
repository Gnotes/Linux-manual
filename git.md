# Git

> Git安装方式，主要分为两种:

- 使用为特定平台预编译好的安装包
- 通过编译源代码来安装

## 安装包安装

```bash
$ sudo yum install git
```

*删除Git*

```bash
yum remove git # yum erase git # 这俩是同一个
```

## 源码安装

1. Git 的工作需要调用 curl，zlib，openssl，expat，libiconv 等库的代码，所以需要先安装这些依赖工具

```bash
$ yum install curl-devel expat-devel gettext-devel openssl-devel zlib-devel
```

*如果提示没有 `CC` 命令，请安装 [`gcc`](http://man.linuxde.net/gcc)*

```bash
$ yum install gcc
```

2. [下载](https://github.com/git/git/releases) 最新版本源代码并解压

```bash
$ wget https://github.com/git/git/archive/v2.19.0.tar.gz

$ tar -zxf v2.19.0.tar.gz
```

3. 编译

```bash
$ cd git-2.19.0
$ make prefix=/usr/local all
$ sudo make prefix=/usr/local install
```

- [Git 源码安装](https://git-scm.com/book/zh/v1/%E8%B5%B7%E6%AD%A5-%E5%AE%89%E8%A3%85-Git)
- [Git 安装包安装](https://git-scm.com/book/zh/v2/%E8%B5%B7%E6%AD%A5-%E5%AE%89%E8%A3%85-Git)
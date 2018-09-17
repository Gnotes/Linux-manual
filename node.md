# Node 环境安装

在 [官网中文网站](https://nodejs.org/zh-cn/download/) 查看最新版本

1. 下载安装包

    ```bash
    $ wget https://npm.taobao.org/mirrors/node/v10.8.0/node-v10.8.0-linux-x64.tar.xz
    ```

2. 解压到指定目录

    ```bash
    $ tar xf node-v10.8.0-linux-x64.tar.xz -C /usr/local/node-v10.8.0
    ```

3. 指定全局变量

    3.1 使用软连接的方式

    ```bash
    $ ln -s /usr/local/node-v10.8.0/bin/node /usr/local/bin/node

    $ ln -s /usr/local/node-v10.8.0/bin/npm /usr/local/bin/npm
    ```

    创建连接后查看

    ```bash
    $ ls -l /usr/local/bin

    $ node -> /usr/local/node-v10.8.0/bin/node
    $ npm -> /usr/local/node-v10.8.0/bin/npm
    ```

    3.2 指定环境变量的方式

      1) 修改当前用户的 `.bash_profile` 文件，`对单一用户生效（永久的）`  
      2) 修改 `/etc/profile` 文件， `对所有用户生效（永久的）`

      ```bash
      $ vim ~/.bash_profile # vim /etc/profile
      ```

      ```bash
      # 添加如下环境变量
      NODE_HOME=/usr/local/node-v10.8.0
      # 添加到PATH中
      PATH=$PATH:$NODE_HOME/bin
      # 导出
      export PATH
      ```

      ```bash
      # 修改后立即生效
      $ source ~/.bash_profile # source /etc/profile
      ```

4. 查看是否安装成功

    ```bash
    $ node -v
    v10.8.0
    $ npm -v
    6.2.0
    ```
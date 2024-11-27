---
title: 'MySQL日常操作'
date: 2024-11-27
permalink: /posts/2024/11/blog-post-7/
tags:
  - 命令记录
---

# 日常操作记录

 重启操作

```bash
service mysqld restart
```

修改配置（端口、数据库位置等）

```bash
nano /etc/my.cnf
vim /etc/my.cnf
```

```my.cnf
# For advice on how to change settings please see

# http://dev.mysql.com/doc/refman/8.4/en/server-configuration-defaults.html

[mysqld]
#

# Remove leading # and set to the amount of RAM for the most important data

# cache in MySQL. Start at 70% of total RAM for dedicated server, else 10%.

# innodb_buffer_pool_size = 128M

# 

# Remove the leading "# " to disable binary logging

# Binary logging captures changes between backups and is enabled by

# default. It's default setting is log_bin=binlog

# disable_log_bin

# 

# Remove leading # to set options mainly useful for reporting servers.

# The server defaults are faster for transactions and fast SELECTs.

# Adjust sizes as needed, experiment to find the optimal values.

# join_buffer_size = 128M

# sort_buffer_size = 2M

# read_rnd_buffer_size = 2M

#datadir=/var/lib/mysql
#socket=/var/lib/mysql/mysql.sock
#----------------newPath
datadir=/home/MySQL\ Server\ 8.0/Data
socket=/home/MySQL\ Server\ 8.0/Data/mysql.sock

log-error=/var/log/mysqld.log
pid-file=/var/run/mysqld/mysqld.pid

port = 3306
```

    修改mysql配置文件，修改MySQL启动脚本/etc/init.d/mysqld

```bash
vim /etc/init.d/mysqld
```

centos7:

```bash
sudo less /usr/lib/systemd/system/mysqld.service
```

sudo less /usr/lib/systemd/system/mysqld.service

登录

```bash
mysql -u root -p
```

### python连接Mysql

基于ssh连接Mysql可以查看sshtunnel的文档，里面有一些案例

```python
pip install pymysql
pip install sshtunnel
```

```python
sshp = os.getenv("ssh_password")
sshn = os.getenv("ssh_username")
mysqlrootpassword = os.getenv("mysqlrootpassword")
mysqljyhpassword = os.getenv("mysqljyhpassword")

def get_ssh_tunnel():
    '''创建SSH连接，传入连接参数'''
    server = SSHTunnelForwarder(
        ssh_address_or_host=('ip', 22),  # ip填写自己的服务器ip，样例连接的端口为22，自己做调整
        ssh_username=sshn,  # SSH用户名
        ssh_password=sshp,  # SSH密码
        remote_bind_address=('ip', 3306),
    )
    server.start()
    return server

def get_db_conn(sshserver):
    dbport = sshserver.local_bind_port
    return pymysql.connect(
        host='127.0.0.1',  # 默认本地IP
        port=dbport,
        user='root',
        passwd=mysqlrootpassword,
        db='数据库名',
        charset='utf8',
    )

```

```python

```

### 修改mysql数据库存储位置

```bash
nano /etc/my.cnf
```

```bash
nano /etc/init.d/mysqld
```

两个地方的datadir都改 socket也改

然后把新数据存储位置的文件夹文件所属和权限改一下

```bash
sudo chown -R mysql:mysql /home/mysqldata/mysql
sudo chcon -R -t mysqld_db_t /home/mysqldata/mysql
sudo chmod -R 755 /home/mysqldata/mysql
```

```bash
sudo chown -R mysql:mysql /home/MySQLdata
sudo chcon -R -t mysqld_db_t /home/MySQLdata
sudo chmod -R 755 /home/MySQLdata
```

检查两个位置的权限信息是否一致

```bash
ls -ldZ /home/mysqldata/mysql
ls -ldZ /var/lib/mysql
```

最后：

1. **设置文件的默认权限**：
   
   ```bash
   setfacl -m u::rwx,g::r-x,o::r-x /home/mysqldata/mysql
   ```

2. **设置目录的默认权限**：
   
   ```bash
   setfacl -m d:u::rwx,d:g::r-x,d:o::r-x /home/mysqldata/mysql
   ```

### mysql创建新用户并分配sql权限

在MySQL中创建用户并分配权限

首先，登录到MySQL数据库：

```bash
mysql -u root -p
```

输入MySQL root用户的密码。

然后，在MySQL中创建一个新的数据库用户：

```sql
CREATE USER 'jyh'@'localhost' IDENTIFIED BY '20010628@Jyh';
```

将`username`替换为Linux子用户的用户名，`password`替换为你想为MySQL用户设置的密码。

接下来，为这个MySQL用户分配权限。例如，如果你想让这个用户拥有对特定数据库的读取使用但不修改，可以使用：

```sql
GRANT SELECT ON test_gdelt.* TO 'jyh'@'localhost';
```

将`database_name`替换为你想要分配权限的数据库名称。

最后，应用权限更改并退出MySQL：

```sql
FLUSH PRIVILEGES;
EXIT;
```

这样，成功在MySQL中创建了一个对应的数据库用户，并分配了权限。

### 系统的非root用户在数据库位置被修改后无法进入mysql命令行的问题和解决办法

😴我将数据库存储位置放在`/home`下，非root用户在终端无法进入mysql命令行

#### 报错如下：

```bash
(base) [jyh@45h229 ~]$ mysql -u root -p
Enter password: 
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/home/MMmysqldata/mysql/mysql.sock' (13)
```

原因：`/home/MMmysqldata/mysql/mysql.sock`文件非root用户jyh无法访问，没有权限，这个文件夹被设置成mysql组内的了，只有root和mysql组内的有权限访问

#### 解决办法：

把用户加入到mysql组中

```bash
sudo usermod -a -G mysql jyh
id jyh
```

如果还有问题 将mysql组放到更前面

```ba
sudo usermod -g mysql jyh
```

检查：

```bash
id jyh
```

保险起见可以注销重新登录一下

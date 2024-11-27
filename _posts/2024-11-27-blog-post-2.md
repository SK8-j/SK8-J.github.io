---
title: 'MySQL刚下完就不能运行 报错MySQL Daemon failed to start'
date: 2024-11-27
permalink: /posts/2024/11/blog-post-8/
tags:
  - 解决问题
---

# 当MySQL刚下完就不能运行 报错MySQL Daemon failed to start.

```bash
[root]# sudo service mysqld start
MySQL Daemon failed to start.
正在启动 mysqld：                      [失败]
```

建议在完全匹配`MySQL刚下完就不能运行`的情况的条件下尝试：(这相当于把文件信息都删了)

```bash
  rm -fr /var/lib/mysql/*  
  rm /var/lock/subsys/mysqld   
  killall mysqld
```

如果没有`/var/lock/subsys/mysqld`，就试试改成

```bash
  rm -fr /var/lib/mysql/*  
  rm /var/lock/subsys/mysql  
  killall mysqld
```

之后再

```bash
[root@0h subsys]# service mysqld start
初始化 MySQL 数据库：                           [确定]
正在启动 mysqld：                              [确定]
[root]# service mysqld status
mysqld (pid  12183) 正在运行...
```

成功！

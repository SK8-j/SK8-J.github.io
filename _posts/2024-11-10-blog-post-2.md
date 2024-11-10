---
title: '在指定位置创建MySQL数据库'
date: 2024-11-10
permalink: /posts/2024/11/blog-post-2/
tags:
  - 问题解决记录
---
mysqld配置文件是MySQL服务器的配置文件。在Linux和Unix系统上，它通常位于`/etc/mysql`或`/etc`目录下。在Windows系统上，它通常位于MySQL安装目录的`bin`子目录中。C:\ProgramData\MySQL\MySQL Server 8.0

使用你喜欢的文本编辑器打开mysqld配置文件，并找到一个名为`datadir`的参数。如果找不到该参数，你可以在文件中添加一个新的行来指定它，如下所示：

登录后复制 

```plaintext
datadir = /path/to/custom/datadir
```

确保将`/path/to/custom/datadir`替换为你的自定义数据目录的实际路径。

```plaintext
datadir=G:/MySQL Server 8.0/Data
#datadir=C:/ProgramData/MySQL/MySQL Server 8.0/Data
```

**禁用 `--secure-file-priv`（不推荐在生产环境）**：
如果您有服务器权限并能修改 MySQL 配置文件，可以编辑 `my.cnf`（或 `my.ini`）文件，将 `secure-file-priv` 设置为 `NULL` 或将其删除来禁用该选项。

ini

复制代码

`[mysqld] secure-file-priv=""`
---
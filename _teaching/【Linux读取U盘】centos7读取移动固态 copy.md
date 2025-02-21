---
title: "Linux读取U盘：centos7版本服务器读取移动固态"
collection: teaching
type: "Server course/服务器教程"
permalink: /teaching/centos7-reading-usb/
venue: "西安交通大学"
date: 2024-11-27
location: "xi'an, China"
---

## 代码记录

### 更换yum源，安装适配exfat工具，挂载并读取

```bash
cp /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.bak #备份

wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-7.repo

yum clean all
yum makecache
# 接下来下载epel库
命令：yum install -y epel-release
再次运行
yum clean all 
清除缓存，
运行 
yum makecache 
生成新的缓存

# 安装exfat文件配套工具
yum install exfat-utils fuse-exfat

yum install -y http://li.nux.ro/download/nux/dextop/el7/x86_64/nux-dextop-release-0-5.el7.nux.noarch.rpm

sudo yum install -y exfat-utils
#查看U盘名称
sudo lsblk
sudo blkid
输出：/dev/sdc1: LABEL="GDELTM-fM-^UM-0M-fM-^MM-.M-gM-^[M-^X" UUID="E002-47B9" TYPE="exfat" PARTLABEL="Elements" PARTUUID="f9eb11b0-0120-47b6-8a80-c7e1235a58d3" 

以sdc1为例
sudo mkdir -p /mnt/my_ssd

sudo mount -t exfat /dev/sdc1 /mnt/my_ssd
```

### 清理挂载

在完成数据复制后，如果您不再需要访问移动固态硬盘，可以安全地卸载它：

```bash
sudo umount /mnt/my_ssd
```

在复制大量文件时，确保文件传输的稳定性和监控进度非常重要。以下是一些方法和工具，可以帮助您在复制过程中保持监控并确保传输的完整性：

### 使用 `rsync` 命令实时复制粘贴查看进度

`rsync` 是一个强大的文件传输工具，适合用于复制大量文件。它不仅可以显示传输进度，还可以在传输中断时恢复传输。使用 `rsync` 命令的基本格式如下：

bash

```bash
rsync -avh --progress /mnt/my_ssd/xxxx文件 /home/
rsync -avh --progress /mnt/my_ssd/MySQL\ Server\ 8.0 /home/
```

- `-a`：归档模式，保留文件属性。
- `-v`：详细输出。
- `-h`：以人类可读的格式显示文件大小。
- `--progress`：显示传输进度。

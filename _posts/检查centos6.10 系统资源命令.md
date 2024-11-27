---
title: 'centos6.10 系统常用命令'
date: 2024-11-27
permalink: /posts/2024/11/centos6.10 系统常用命令/
tags:
  - 命令记录
---

# centos6.10 系统常用命令

### 1. 查看 CPU 信息

```bash
cat /proc/cpuinfo
```

这将显示 CPU 的详细信息，包括型号、核心数等。

### 2. 查看内存信息

```bash
free -m
```

这将显示内存的总量、已用、空闲以及 Swap 分区的使用情况。

### 3. `df`查看磁盘空间

```bash
df -h
```

这将显示文件系统的磁盘空间使用情况，包括每个挂载点的总空间、已用空间和可用空间。

如果你只想查看特定目录的磁盘空间，可以使用：

```bash
df -h /path/to/directory
```

将 `/path/to/directory` 替换为你想要检查的实际目录路径。

### 4. 查看磁盘 I/O 统计

```bash
iostat
```

这将显示 CPU 使用率和磁盘 I/O 统计信息。

### 5. 查看网络状态

```bash
ifconfig
```

或者使用 `ip addr`（如果你的系统中可用）来查看网络接口的配置。

```bash
netstat -tulnp
```

这将显示 TCP 和 UDP 端口的使用情况，以及监听这些端口的服务。

### 6. 查看进程信息

```bash
ps aux
```

这将显示系统中所有运行的进程及其详细信息。

```bash
top
```

这是一个实时的系统监控工具，显示进程和资源使用情况。

### 7. 查看文件描述符限制

```bash
ulimit -a
```

这将显示当前用户可以打开的文件描述符的数量限制。

### 8. 查看系统负载

```bash
uptime
```

这将显示系统的负载平均值，以及当前时间、用户数、空闲内存等信息。

### 9. 查看系统日志

```bash
tail -f /var/log/messages
```

或者

```bash
tail -f /var/log/syslog
```

### 10.`top` 命令

`top` 提供了一个动态的实时视图，显示系统中的进程和它们的资源使用情况，包括 CPU 和内存。

```bash
top
```

在 `top` 界面中，你可以按 `M` 键来根据内存使用量对进程进行排序。

### 11.`reboot`重启服务器

这是重启系统的标准命令。你可以使用以下命令立即重启服务器：

```bash
sudo reboot
```

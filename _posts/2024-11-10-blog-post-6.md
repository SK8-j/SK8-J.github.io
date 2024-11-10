---
title: 'Pipenv 使用指南'
date: 2024-11-10
permalink: /posts/2024/11/blog-post-6/
tags:
  - 库应用
---
# 安装 Pipenv

使用以下命令安装 Pipenv：

```bash
pip3 install pipenv
```

或者在 macOS 上使用 Homebrew：

```bash
brew install pipenv
```

安装后，执行以下命令确认安装成功：

```bash
pipenv --version
```

# Pipenv 使用指南

## 创建虚拟环境

在项目目录下执行以下命令以创建虚拟环境：

```bash
python3 -m pipenv install
```

如果没有 `Pipfile` 和 `Pipfile.lock`，将自动生成这两个文件。

## 指定 Python 版本

要指定 Python 版本，可以使用：

```bash
pipenv install --python 3.8
```

## 安装包

安装某个包：

```bash
pipenv install [包名]
```

安装指定版本的包：

```bash
pipenv install package_name==***.**
```

## 开发环境依赖

安装仅用于开发环境的包：

```bash
pipenv install --dev
```

## 卸载包

卸载某个包：

```bash
pipenv uninstall [包名]
```

## 查看依赖

查看已安装的依赖关系：

```bash
pipenv graph
```

## 启动虚拟环境

在有 `Pipfile` 的目录下启动虚拟环境：

```bash
pipenv shell
```

## 清理未使用依赖

卸载未在 `Pipfile.lock` 中指定的依赖：

```bash
pipenv clean
```

## 显示虚拟环境路径

查看虚拟环境的路径：

```bash
pipenv --venv
```

## 删除虚拟环境

删除虚拟环境及其依赖：

```bash
pipenv --rm
```

这样，你就可以使用 Pipenv 来管理你的 Python 项目和依赖了。

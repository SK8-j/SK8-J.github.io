---
permalink: /
title: "欢迎来到吉宇豪的website"
author_profile: true
redirect_from: 
  - /about/
  - /about.html
---

我是吉宇豪，目前管理科学与工程研二在读。我目前的研究方向是产业链安全风险事件识别，主要关注大语言模型与新闻事件数据的结合等方向。我在东北大学工商管理学院信息管理与信息系统系就读本科，目前在西安交通大学管理学院管理科学与工程系学位。我的导师是[冯耕中](https://som.xjtu.edu.cn/info/1712/11864.htm)教授。

A data-driven personal website
======
像许多其他基于 Jekyll 的 GitHub Pages 模板一样，Academic Pages 让你将网站的内容与形式分开。你的网站内容和元数据在结构化的 markdown 文件中，而各种其他文件构成了主题，指定如何将这些内容和元数据转换为 HTML 页面。你将这些各种 markdown (.md)、YAML (.yml)、HTML 和 CSS 文件保存在一个公共的 GitHub 仓库中。每次你提交并推送更新到仓库时，[GitHub Pages](https://pages.github.com/) 服务会基于这些文件创建静态 HTML 页面，并免费托管在 GitHub 的服务器上。

许多动态内容管理系统（如 Wordpress）的功能可以通过这种方式实现，使用的计算资源只是其中的一小部分，并且更少受到黑客和 DDoS 攻击的威胁。你还可以在不触及网站内容的情况下随心所欲地修改主题。如果你在 Jekyll/HTML/CSS 中遇到无法修复的问题，你描述演讲、出版物等的 markdown 文件是安全的。你可以回滚更改，甚至删除仓库并重新开始——只要确保保存 markdown 文件！最后，你还可以编写脚本来处理网站上的结构化数据，例如[这个脚本](https://github.com/academicpages/academicpages.github.io/blob/master/talkmap.ipynb)，它分析关于演讲页面的元数据以显示[你演讲过的每个地点的地图](https://academicpages.github.io/talkmap.html)。

# 开始使用

1. 如果您还没有GitHub账户，请注册一个，并确认您的电子邮件（必须！）
2. 通过点击右上角的“Use this template”按钮，复制[这个模板](https://github.com/academicpages/academicpages.github.io)。
3. 转到仓库的设置（从“Code”开始的标签中最右边的一项，应该在“Unwatch”下面）。将仓库重命名为“[your GitHub username].github.io”，这也将是你网站的URL。
4. 设置全站配置并创建内容和元数据（见下文——也可以参考[这个差异集](http://archive.is/3TPas)，展示了为用户名为“getorg-testacct”的用户设置[示例网站](https://getorg-testacct.github.io/)时更改了哪些文件）。
5. 将任何文件（如PDF、.zip文件等）上传到files/目录。它们将出现在https://[your GitHub username].github.io/files/example.pdf。
6. 通过转到仓库设置中的“GitHub pages”部分来检查状态。

## 全站配置

网站的主配置文件位于根目录下的[_config.yml](https://github.com/academicpages/academicpages.github.io/blob/master/_config.yml)文件中，它定义了侧边栏和其他全站特性的内容。您需要将默认变量替换为关于您自己和您网站GitHub仓库的信息。顶部菜单的配置文件位于[_data/navigation.yml](https://github.com/academicpages/academicpages.github.io/blob/master/_data/navigation.yml)。例如，如果您没有作品集或博客文章，您可以从那个navigation.yml文件中移除这些项目，以从标题中移除它们。

## 创建内容和元数据

对于网站内容，每种类型的内容都有一个Markdown文件，存储在如_publications、_talks、_posts、_teaching或_pages等目录中。例如，每次演讲都是一个Markdown文件，存储在[_talks目录](https://github.com/academicpages/academicpages.github.io/tree/master/_talks)中。每个Markdown文件的顶部都有关于演讲的结构化数据YAML，主题将解析这些数据以执行许多很酷的操作。关于演讲的相同结构化数据用于生成[演讲页面](https://academicpages.github.io/talks)上的演讲列表、每个特定演讲的[个人页面](https://academicpages.github.io/talks/2012-03-01-talk-1)、[简历页面](https://academicpages.github.io/cv)上的演讲部分，以及您进行演讲的[地点地图](https://academicpages.github.io/talkmap.html)（如果您运行这个[Python文件](https://github.com/academicpages/academicpages.github.io/blob/master/talkmap.py)或[Jupyter笔记本](https://github.com/academicpages/academicpages.github.io/blob/master/talkmap.ipynb)，它将根据_talks目录的内容创建地图的HTML）。

**Markdown生成器**

该仓库包括[一组Jupyter笔记本](https://github.com/academicpages/academicpages.github.io/tree/master/markdown_generator)，它们可以将包含有关演讲或展示的结构化数据的CSV转换为个人Markdown文件，这些文件将被正确地格式化为Academic Pages模板。该目录中的样本CSV是我用来创建我自己的网站stuartgeiger.com的。我通常的工作流程是，我保持一个我的出版物和演讲的电子表格，然后运行这些笔记本中的代码来生成Markdown文件，然后提交并推送到GitHub仓库。

## 如何编辑您的网站GitHub仓库

许多人使用git客户端在本地计算机上创建文件，然后将它们推送到GitHub的服务器。如果您不熟悉git，您可以直接在github.com界面中编辑这些配置和Markdown文件。导航到一个文件（如[这个](https://github.com/academicpages/academicpages.github.io/blob/master/_talks/2012-03-01-talk-1.md)），点击内容预览右上角的铅笔图标（在“Raw | Blame | History”按钮的右侧）。您可以通过点击铅笔图标右侧的垃圾桶图标来删除文件。您也可以通过导航到一个目录并点击“Create new file”或“Upload files”按钮来创建新文件或上传文件。

示例：编辑演讲的Markdown文件 [/images/editing-talk.png](https://kimi.moonshot.cn/images/editing-talk.png)

## 更多信息

关于配置Academic Pages的更多信息可以在[指南](https://academicpages.github.io/markdown/)、[不断增长的维基](https://github.com/academicpages/academicpages.github.io/wiki)中找到，您总是可以在GitHub上[提问](https://github.com/academicpages/academicpages.github.io/discussions)。这个主题是从[Minimal Mistakes主题](https://mmistakes.github.io/minimal-mistakes/docs/configuration/)（这个主题是从那里分叉出来的）的[指南](https://mmistakes.github.io/minimal-mistakes/docs/configuration/)也可能有所帮助。

请注意，由于网络原因，我无法成功解析您提供的网页链接。这可能是由于链接本身的问题，也可能是网络问题。建议您检查网页链接的合法性，并适当重试。如果您不需要这些链接的解析内容，上述翻译应该能够回答您的问题。

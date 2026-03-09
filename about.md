---
layout: lecture
title: "我们为何开设这门课程"
---

在传统的计算机科学教育中，你很可能会修读大量讲授高深计算机主题的课程，涵盖从操作系统到编程语言再到机器学习的方方面面。然而在许多院校里，有一个至关重要的主题却鲜少被提及，往往被留给学生自行摸索：**计算生态素养**。

多年来，我们在麻省理工学院参与教授了多门课程，一次又一次地发现许多学生对可用的工具所知甚少。计算机本是为自动化手工任务而设计，然而学生们却常常手工执行重复性任务，或者未能充分利用版本控制和文本编辑器等强大工具。往轻了说，这导致效率低下、时间浪费；往重了说，则会引发数据丢失或无法完成某些任务等问题。

这些主题并未被纳入大学课程体系：学生们从未被教导如何使用这些工具，或者至少未被教导如何高效使用它们，因此在本应简单的任务上浪费了时间和精力。标准的计算机科学课程缺失了关于计算生态系统的关键主题，而这些内容本可以让学生们的学习生活轻松许多。

# 计算机科学教育的遗珠一课

为了弥补这一缺憾，我们开设了这门课程，涵盖所有我们认为对成为一名高效的计算机科学家和程序员至关重要的主题。本课程注重实践，提供工具和技术的动手入门，让你能够立即将所学应用到各种实际场景中。本课程的最新版本经过大幅修订，于 2026 年 1 月在麻省理工学院的“独立活动期(Independent Activities Period)”开设——这是一个为期一个月的学期，以学生主导的短期课程为特色。虽然课程讲座本身仅向麻省理工学院开放，但我们会向公众提供所有课程材料以及课程视频录像。

如果你觉得这门课程可能适合你，下面是课程中会学习的一些具体内容：

## 命令行 与 Shell

学习如何使用别名、脚本和构建系统来自动化常见的重复性任务，从而避免反复从文档中复制粘贴命令，也不再需要“依次运行这 15 条命令”，更不用担心“忘记执行某一步”或“忘记传入某个参数”。

例如，快速搜索历史命令可以显著节省时间。下面的示例展示了几种在 shell 历史记录中查找 `convert` 命令的技巧。

<video autoplay="autoplay" loop="loop" controls muted playsinline  oncontextmenu="return false;"  preload="auto"  class="demo">
  <source src="{{ '/static/media/demos/history.mp4' | relative_url }}" type="video/mp4">
</video>

## 版本控制

学习如何**正确**使用版本控制，并充分发挥它的作用：在问题发生时保护你的代码、与他人协作，以及快速查找并定位有问题的变更。

不再需要动不动就 `rm -rf; git clone` 重新开始；合并冲突也会大大减少（当然，可能还是会有一些）；不会再留下大段被注释掉的代码；也不必再为找不到究竟是哪一次修改弄坏了代码而烦恼，更不用担心“糟了，我们是不是把还能用的代码删掉了？”。

我们还会教你如何通过拉取请求(Pull Request)为他人的项目做贡献。

在下面的示例中，我们使用 `git bisect` 来查找是哪次提交破坏了单元测试，然后用 `git revert` 来修复它。

<video autoplay="autoplay" loop="loop" controls muted playsinline  oncontextmenu="return false;"  preload="auto"  class="demo">
  <source src="{{ '/static/media/demos/git.mp4' | relative_url }}" type="video/mp4">
</video>

## 文本编辑

学习如何在命令行中高效地编辑文件，无论是本地还是远程环境，并充分利用编辑器的高级功能。这样你就不必再在不同机器之间来回复制文件，也能避免反复进行重复性的编辑操作。

Vim 宏是 Vim 最强大的功能之一。下面的示例中，我们通过嵌套的 Vim 宏，快速将一个 HTML 表格转换为 CSV 格式。

<video autoplay="autoplay" loop="loop" controls muted playsinline  oncontextmenu="return false;"  preload="auto"  class="demo">
  <source src="{{ '/static/media/demos/vim.mp4' | relative_url }}" type="video/mp4">
</video>

## 远程机器

学习如何使用「SSH 密钥」和「终端复用工具」在远程机器上高效工作，从而让你的远程开发环境更加稳定和轻松。你不再需要为了同时运行两个命令而打开一堆终端，也不用在每次连接时反复输入密码，更不会因为网络断开或重启电脑而丢失所有工作。

在下面的示例中，我们使用 `tmux` 在远程服务器上保持会话持续运行，并使用 `mosh` 支持网络漫游以及断线重连。

<video autoplay="autoplay" loop="loop" controls muted playsinline  oncontextmenu="return false;"  preload="auto"  class="demo">
  <source src="{{ '/static/media/demos/ssh.mp4' | relative_url }}" type="video/mp4">
</video>

## Finding files

学习如何快速找到你需要的文件，而不必在项目目录中一层层点击或浏览文件，直到偶然找到包含目标代码的那个文件。

在下面的示例中，我们使用 `fd` 快速查找文件，用 `rg` 搜索代码片段，并借助 `fasd` 快速 `cd` 到最近或最常访问的文件和目录，甚至可以直接用 `vim` 打开它们。

<video autoplay="autoplay" loop="loop" controls muted playsinline  oncontextmenu="return false;"  preload="auto"  class="demo">
  <source src="{{ '/static/media/demos/find.mp4' | relative_url }}" type="video/mp4">
</video>

## 数据处理

学习如何直接在命令行中快速而灵活地对数据和文件进行修改、查看、解析、绘图以及计算。这样你就不需要再从日志文件里反复复制粘贴数据，也不用手动计算统计结果，更不必依赖电子表格来生成图表。

## 代码质量与持续集成

学习如何使用自动格式化(autoformatting)、代码检查(linting)、测试(testing)以及代码覆盖率(code coverage)等工具来提升代码质量。告别难以阅读的代码，减少回归问题，也不会再出现“在你电脑上能运行，但在别人电脑上就崩溃”的情况。

## 不止于代码

学习如何编写优秀的文档，如何与开源项目维护者清晰沟通，如何提交有价值的问题反馈（issues），以及如何提交能够顺利被合并的 Pull Request。这样就不会再有用户因为无法上手你的软件而感到困惑，也不会再遇到维护者迟迟没有回应的情况。

# 结语

以上内容以及更多主题将贯穿 9 次课程讲座，每次课程都配有练习，帮助你自己动手熟悉这些工具。

除了 2026 年版本的课程外，你也可以浏览 [2020]({{ '/2020/' | relative_url }}) 年和 [2019]({{ '/2019/' | relative_url }}) 年的课程内容。不同版本在部分细节上有所区别，其中 2026 年版本更贴近当下的技术环境和学习需求，而较早的版本则提供了另一种视角和补充内容，同样值得参考。

我们期待与你一起探索这些实用的工具和技术！

祝你编程愉快！<br>
[Anish](https://anish.io/)、[Jon](https://thesquareplanet.com/) 和 [Jose](https://josejg.com/)

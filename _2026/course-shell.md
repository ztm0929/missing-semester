---
layout: lecture
title: "课程概览 + Shell 入门"
description: 了解本课程的背景与目标，并开始学习 Shell 的基础用法。
thumbnail: /static/assets/thumbnails/2026/lec1.png
date: 2026-01-12
ready: true
video:
  aspect: 56.25
  id: MSgoeuMqUmU
---

# 我们是谁？

本课程由 [Anish](https://anish.io/)、[Jon](https://thesquareplanet.com/) 和 [Jose](http://josejg.com/) 联合讲授。我们都是 MIT 校友，在学生时代就创办了这门 MIT IAP 课程。如有任何问题，欢迎通过以下方式联系我们：<br>[missing-semester@mit.edu](mailto:missing-semester@mit.edu)

我们不以此课程获得报酬，也不以任何方式将其商业化。我们将所有的 [课程资料](https://missing.csail.mit.edu/) 和 [讲座录像](https://www.youtube.com/@MissingSemester) 免费公开。如果你想支持我们的工作，最好的方式就是向他人推荐这门课程。如果你是公司、大学或其他组织，在更大范围内使用了本课程的内容，欢迎邮件告诉我们你的使用情况或提供反馈，我们很希望听到这些信息 :)

# 课程目的

作为计算机科学家，我们都深知计算机擅长辅助完成重复性任务。然而，我们往往不经意间遗漏了一点：**这个优势不仅适用于程序执行的计算过程，对我们使用计算机本身也同样适用**。我们掌握着大量功能强大的工具，这些工具能显著提升我们的工作效率、帮助解决更复杂的问题。可惜的是，许多人仅仅利用了这些工具的冰山一角；我们往往只是死记硬背几句「魔法咒语」来应付日常工作，一旦陷入困境就盲目地从网上复制粘贴命令。

本课程致力于 [解决这个问题]({{ '/about/' | relative_url }}) 。

我们想教你如何充分利用已知的工具，为你介绍新的工具来扩充你的工具箱，并激发你对探索（乃至自己开发）更多工具的热情。这正是我们所认为的大多数计算机科学课程中所缺失的内容。

# 课程结构

本课程是一门免学分（费用）课程，包含九场 1 小时的讲座，每场讲座围绕一个 [特定主题]({{ '/2026/' | relative_url }}) 展开。这些讲座在很大程度上彼此独立，但随着学期进行，我们会假设你已经熟悉前面讲座的内容。我们提供在线讲义，但课堂上可能会涵盖讲义中没有的内容（如演示等）。与往年一样，我们会录制讲座并将录音录像 [在线发布](https://www.youtube.com/@MissingSemester) 。

考虑到仅用几场 1 小时讲座要涵盖大量内容，这些讲座的信息量相当大。为了让你有时间按自己的节奏熟悉内容，每场讲座都附带一组习题，指导你学习讲座的核心知识点。我们不设专门的答疑时间，但欢迎你在 [OSSU Discord](https://ossu.dev/#community) 的 `#missing-semester-forum` 频道或通过邮件 [missing-semester@mit.edu](mailto:missing-semester@mit.edu) 向我们提问。

由于时间有限，我们无法以全日制课程的详细程度涵盖所有工具。在可能的情况下，我们会为你指引资源来进一步探讨某个工具或话题；如果有什么特别引起你兴趣的，欢迎随时联系我们咨询！

最后，如果你对课程有任何反馈，欢迎邮件告诉我们：<br>[missing-semester@mit.edu](mailto:missing-semester@mit.edu)

# 主题一：Shell

{% comment %}
lecturer: Jon
{% endcomment %}

## Shell 是什么？

如今的计算机拥有多种多样的界面来接收命令：华丽的图形用户界面、语音输入接口、AR/VR，以及近来出现的大语言模型。这些交互接口在 80% 的使用场景中都表现出色，但它们往往在根本上受到限制——你无法点击一个不存在的按钮，也无法下达一条未被编程的语音命令。要充分利用计算机提供的所有工具，我们必须「复古」一下，使用一个古老而强大的文本界面：Shell 。

几乎所有你能接触到的平台都以某种形式提供了 Shell，其中许多还提供了多个 Shell 供你选择。尽管各 Shell 在细节上各不相同，但在本质上它们都大同小异：它们都允许你运行程序、向程序提供输入，并以半结构化的方式检查程序的输出。

要打开 Shell 的**提示符**（即你可以输入命令的地方），首先需要一个**终端**——它是与 Shell 交互的可视化界面。你的设备很可能已预装了终端，如果没有预装，你也可以安装一个：

- **Linux：**按下 <kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>T</kbd>（适用于大多数发行版），或者在应用菜单中搜索「终端（Terminal）」。
- **Windows：**按下 <kbd>Win</kbd> + <kbd>R</kbd> ，输入 `cmd` 或 `powershell` ，然后按下 <kbd>Enter</kbd> 。也可以在开始菜单中搜索「终端（Terminal）」或「命令提示符（Command Prompt）」。
- **macOS：**按下 <kbd>⌘ Cmd</kbd> + <kbd>Space</kbd> 打开 「聚焦（Spotlight）」，输入「终端（Terminal）」，然后按下 <kbd>Enter</kbd> 。还可以在「应用程序」→「实用工具」→「终端」中找到它。

在 Linux 和 macOS 上，这通常会打开 Bourne Again Shell，简称「bash」。它是应用最广泛的 Shell 之一，其语法与你在其他许多 Shell 中看到的类似。在 Windows 上，你可能会看到「批处理（batch）」或「powershell」Shell，具体取决于你运行的命令。这些都是 Windows 特有的，我们在本课程中不会重点关注，尽管它们对我们要教授的大多数内容都有对应实现。你可以考虑使用 [适用于 Linux 的 Windows 子系统（WSL）](https://learn.microsoft.com/zh-cn/windows/wsl/) 或 Linux 虚拟机。

还有其他一些 Shell ，它们在使用体验上相较于 bash 做了许多改进（例如 fish 和 zsh 是最常见的）。虽然这些 Shell 非常流行（所有授课教师都在使用其中之一），但它们的普及程度远不及 bash，而且它们依赖的许多概念也与 bash 相同，因此本讲不会重点介绍这些 Shell 。

## 为什么你要关心 Shell ？

Shell 的优点不只是比「点来点去」快得多，还具备一种在任何单一图形化程序中都难以获得的表达能力。正如我们将要看到的，Shell 让你能够**以富有创造性的方式把不同程序组合起来**，从而自动化几乎任何任务。

熟悉 Shell 还非常有助于你在开源软件世界中畅行无阻（许多安装说明都需要用到 Shell）、为你的软件项目搭建持续集成（如 [代码质量]({{ '/2026/code-quality' | relative_url }}) 一讲所述），以及在其他程序出错时进行排障。

## 在 Shell 中导航

当你打开终端时，会看到一个通常长这样子的**提示符**：

```console
missing:~$
```

这是 Shell 的主要文本交互界面。它告诉你：你当前在名为 `missing` 的机器上，你的「当前工作目录」（也就是你现在所在的位置）是 `~` ，它是「home 目录」的简写，在 Linux 上通常对应 `/home/用户名`（例如 `/home/jon` ）。<br>
`$` 表示你当前不是 root 用户（后面会详细讲）。在这个提示符后，你可以输入一条命令，Shell 会对其进行解释并执行。最基本的命令就是运行一个程序：

```console
missing:~$ date
Fri 10 Jan 2020 11:49:31 AM EST
missing:~$
```

这里我们执行了 `date` 程序，它会（不出所料地）打印当前日期和时间。随后 Shell 会等待我们输入下一条命令。<br>
我们也可以带上**参数（_argument_）**来执行命令：

```console
missing:~$ echo hello
hello
```

在这个例子中，我们让 Shell 执行 `echo` 程序，并传入参数 `hello` 。`echo` 程序的作用很简单：它会把收到的参数原样打印出来。Shell 在解析这条命令时，会先按照空白字符（whitespace，如空格、Tab 等）把整条命令拆分成若干部分，然后把第一个单词当作要执行的程序，其后的每一个单词都会作为参数传递给这个程序，程序可以在运行时读取这些参数。<br>
如果你想传递的参数本身包含空格或其他特殊字符（例如一个名为「My Photos」的目录），可以用两种方式处理：

- 用 `'` 或 `"` 把整个参数括起来，例如 `"My Photos"`
- 只对需要的字符进行转义，用反斜杠 `\`，例如 `My\ Photos`

对于初学者最重要的一条命令也许是 `man`，即 「manual（手册）」的缩写。
`man` 命令有很多用途，其中之一是帮你查询系统中任意命令的详细说明。比如运行 `man date`，它会告诉你 `date` 是什么，以及你可以传入哪些参数来改变它的行为。对大多数命令来说，你通常也可以通过加上 `--help` 参数来查看更简短的帮助信息。

> 除了 `man` 之外，我们也推荐安装 [`tldr`](https://tldr.sh/) ：它会直接在终端里给出常见的命令使用示例，非常方便。此外，大语言模型通常也很擅长解释命令的工作原理，以及应该如何调用命令来实现你想完成的任务。

学会 `man` 之后，下一个最重要的命令是 `cd`（change directory，切换目录）。这个命令实际上是 Shell 的内建命令，而不是独立程序（也就是说，输入 `which cd` 会显示 `no cd found`）。你给它传入一个路径，该路径就会成为你当前的工作目录。你也会在 Shell 提示符中看到当前工作目录随之变化。

```console
missing:~$ cd /bin
missing:/bin$ cd /
missing:/$ cd ~
missing:~$
```

> 需要注意的是，Shell 通常自带自动补全功能，所以按下 <kbd>Tab</kbd> 往往能更快地补全路径。

许多命令在没有指定路径时，默认会作用于当前工作目录。如果你不确定自己现在位于哪个目录，可以运行 `pwd`（print working directory 的意思，即「打印当前工作目录」），或者查看 `$PWD` 环境变量（例如运行 `echo $PWD`）。这两种方式都会输出当前工作目录的路径。

当前工作目录的另一个重要作用，是让我们能够使用**相对路径**。到目前为止我们看到的路径都是**绝对路径**：它们以 `/` 开头，给出了从文件系统根目录（ `/` ）到目标位置所需经过的完整目录路径。
在实际使用中，你会更常接触到相对路径。之所以称为「相对」，是因为它们是相对于当前工作目录来解释的。对于相对路径（也就是**任何不以 `/` 开头的路径**），Shell 会先在当前工作目录中查找路径的第一个部分，然后再像平常一样逐级向下查找。例如：

```console
missing:~$ cd /
missing:/$ cd bin
missing:/bin$
```

每个目录里还都有两个「特殊路径」：`.` 和 `..` 。
其中，`.` 表示「当前目录」，`..` 表示「父目录」。例如：

```console
missing:~$ cd /
missing:/$ cd bin/../bin/../bin/././../bin/..
missing:/$
```

对于大多数命令参数来说，绝对路径和相对路径通常可以互换使用；只是在使用相对路径时，一定要时刻清楚你当前所在的工作目录！

> 我们建议安装并使用 [`zoxide`](https://github.com/ajeetdsouza/zoxide) 来加速 `cd` 操作。它提供的 `z` 命令会记住你经常访问的路径，让你用更少的输入实现快速跳转。

## Shell 中有哪些可用的程序？

但 Shell 是怎么知道去哪里找 `date` 或 `echo` 这样的程序呢？当 Shell 需要执行一条命令时，它会查询一个名为 `$PATH` 的环境变量。这个变量列出了一系列目录，Shell 会在这些目录中搜索与命令名称匹配的程序：

```console
missing:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
missing:~$ which echo
/bin/echo
missing:~$ /bin/echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
```

当我们运行 `echo` 命令时，Shell 会识别出需要执行名为 `echo` 的程序，然后在 `$PATH` 中以冒号（`:`）分隔的目录列表里逐个搜索同名文件。一旦找到，就会运行它（**前提是该文件是可执行的**，关于这点稍后会详细说明）。<br>
我们可以用 `which` 程序来查看某个命令实际对应哪个文件。我们也可以完全绕过 `$PATH` ，**直接给出要执行文件的完整路径**。

这也揭示了一个办法：我们可以通过列出 `$PATH` 中所有目录的内容，来确定 Shell 中有哪些程序可供执行。我们可以把目录路径传给 `ls` 程序来实现（程序名称取自「list」，用于列出文件）：

```console
missing:~$ ls /bin
```

> 我们建议安装并使用 [`eza`](https://eza.rocks/)，它是一个更加现代友好的工具，用于替代 `ls` 。

在大多数计算机上，这会**打印出非常多的程序**，但我们这里只关注其中最重要的几个。先从一些简单的开始：

- `cat hello.txt`：打印 `hello.txt` 的全部内容
- `sort hello.txt`：将 `hello.txt` 的各行按字典序排序后输出
- `uniq hello.txt`：去除 `hello.txt` 中连续重复的行
- `head hello.txt` 和 `tail hello.txt`：分别打印 `hello.txt` 的前几行和后几行

> 我们建议安装并使用 [`bat`](https://github.com/sharkdp/bat) 来替代 `cat`，它支持语法高亮和分页滚动。

还有一个命令是 `grep pattern hello.txt`，它会在指定的文本文件(即 `hello.txt` )中查找所有匹配 `pattern` 的行。这个命令非常实用，值得多花点时间了解，它的功能比你想象的要丰富得多。

这里的 `pattern` 实际上是**正则表达式（regular expression）**，可以描述非常复杂的匹配模式——我们会在「代码质量」一讲中 [详细讲解]({{ '/2026/code-quality/#regular-expressions' | relative_url}}) 。

除了指定单个文件，你也可以指定一个目录作为搜索范围（或者直接不写，默认就是当前目录 `.` ），并加上 `-r` 参数让 `grep` 递归搜索目录里的所有文本文件，输出匹配的行。

> 如果想要更快、更好用的体验，可以考虑安装 [`ripgrep`](https://github.com/BurntSushi/ripgrep) 来替代 `grep` 。它默认就会递归搜索当前工作目录里的文本文件，使用起来更直观，但可移植性稍弱一些。

还有一些非常实用的工具，它们的使用方式可能稍微复杂一些。我们先来看看 `sed` ——一个可编程的文件编辑器。它有自己的「小语言」，可以用来自动化修改文件。最常见的用法是：

```console
missing:~$ sed -i 's/pattern/replacement/g' hello.txt
```

这条命令会把 `hello.txt` 中所有的 `pattern` 替换为 `replacement` 。具体来说：
- `-i` 参数表示直接修改文件（inline），而不是只在终端输出替换后的内容
- `s/` 是 `sed` 语法里表示「替换」的意思
- 两个 `/` 用来分隔「匹配模式」和「替换内容」
- 结尾的 `/g` 表示在每一行中**替换所有匹配项**，而不仅仅是第一个

> 译者注：<br> 
> `sed` 是 stream editor（流编辑器） 的缩写，最早设计用来对输入流中的文本进行自动化处理，而不仅仅是单个文件。<br>
> `s/` 为什么表示替换：在 `sed` 的命令语法里，`s` 就是 substitute（替换） 的首字母，表示「把匹配到的内容替换成其他内容」。<br>
> `/g` 为什么表示替换所有匹配项：结尾的 `g` 是 global（全局） 的意思，表示在每一行中替换所有匹配项，如果没有 `g` ，`sed` 只会替换每行的第一个匹配项。

和 `grep` 一样，这里的 `pattern` 也是正则表达式，可以描述非常复杂的匹配模式。此外，正则表达式替换还允许 `replacement` 引用匹配模式中的部分内容，我们稍后会通过例子演示这一点。

接下来是 `find` ，它可以（递归地）查找满足特定条件的文件。比如：

```console
missing:~$ find ~/Downloads -type f -name "*.zip" -mtime +30
```

这会在下载（Downloads）目录中查找所有超过 30 天的 ZIP 文件。

```console
missing:~$ find ~ -type f -size +100M -exec ls -lh {} \;
```

这会在你的「home 目录」中查找所有大于 100M 的文件并列出它们。需要注意的是，**`-exec` 参数接受一条命令**，命令以单独的 `;` 结尾（因此我们需要像转义空格那样对它进行转义）。`find` 会把每个匹配到的文件路径替换到 `{}` 的位置。

```console
missing:~$ find . -name "*.py" -exec grep -l "TODO" {} \;
```

这会在当前工作目录下查找所有包含 TODO （这个大写单词）的 `.py` 文件。

`find` 的语法可能有点让人望而生畏，但希望通过这些例子，你能感受到它有多么实用！

> 我们建议安装并使用 [`fd`](https://github.com/sharkdp/fd) 来替代 find，它更加人性化（但可移植性稍弱）。

接下来我们介绍 `awk`，它和 `sed` 一样，也有自己的小语言。如果说 `sed` 是专门用来编辑文件的，那么 `awk` 则是专门用来解析文件的。
`awk` 最常见的用途是处理具有规则语法的数据文件（比如 CSV 文件），从每条记录（即每一行）中提取你想要的部分：

```console
missing:~$ awk '{print $2}' hello.csv
```

这条命令会打印 `hello.csv` 中每一行的第二列（默认以空白字符分隔，空格或制表符都算）。如果你的文件是逗号分隔的（CSV 文件常见格式），可以加上 `-F,` 参数：

```console
missing:~$ awk -F, '{print $2}' hello.csv
```

这样就会把每一行按逗号分成列，然后打印第二列。

除了提取列，`awk` 还能做很多操作——比如过滤行、计算统计、求和等等。具体可以通过习题自己动手试试。

将这些工具组合起来，我们可以完成一些很酷的操作，比如：

```console
missing:~$ ssh myserver 'journalctl -u sshd -b-1 | grep "Disconnected from"' \
  | sed -E 's/.*Disconnected from .* user (.*) [^ ]+ port.*/\1/' \
  | sort | uniq -c \
  | sort -nk1,1 | tail -n10 \
  | awk '{print $2}' | paste -sd,
postgres,mysql,oracle,dell,ubuntu,inspur,test,admin,user,root
```

这条命令从远程服务器上抓取 SSH 日志（关于 `ssh` 我们会在下一讲详细介绍），搜索断开连接的消息，从每条消息中提取用户名，最后打印出现次数最多的前 10 个用户名（用逗号分隔）。这一切都在一条命令里完成！我们把逐步拆解这条命令的任务留作习题。

## The shell language (bash)

The previous example introduced a new concept: pipes (`|`). These let
you string together the output of one program with the input of another.
This works because most command-line programs will operate on their
"standard input" (where your keystrokes normally go) if no `file`
argument is given. `|` takes the "standard output" (what normally gets
printed to your terminal) of the program before the `|` and makes it be
the standard input of the program after the `|`. This allows you to
_compose_ shell programs, and it's part of what makes the shell such a
productive environment to work in!

In fact, most shells implement a full programming language (like bash),
just like Python or Ruby. It has variables, conditionals, loops, and
functions. When you run commands in your shell, you are really writing a
small bit of code that your shell interprets. We won't teach you all of
bash today, but there are some bits you'll find particularly useful:

First, redirects: `>file` lets you take the standard output of a program
and write it to `file` instead of to your terminal. This makes it easier
to analyze after the fact. `>>file` will append to `file` rather than
overwrite it. There's also `<file` which tells the shell to read from
`file` instead of from your keyboard as the standard input to a program.

> This is a good time to mention the `tee` program. `tee` will print
> standard input to standard output (just like `cat`!), but will _also_
> write it to a file. So `verbose cmd | tee verbose.log | grep CRITICAL`
> will preserve the full verbose log to a file while keeping your
> terminal clean!

Next, conditionals: `if command1; then command2; command3; fi` will
execute `command1`, and if it doesn't result in an error, will run
`command2` and `command3`. You can also have an `else` branch if you
wish. The most common command to use as `command1` is the `test`
command, often abbreviated simply as `[`, which lets you evaluate
conditions like "does a file exist" (`test -f file` / `[ -f file ]`) or
"does a string equal another" (`[ "$var" = "string" ]`). In bash,
there's also `[[ ]]`, which is a "safer" built-in version of `test` that
has fewer odd behaviours around quoting.

Bash also has two forms of loops, `while` and `for`. `while command1; do
command2; command3; done` functions just like the equivalent `if`
command, except that it will re-execute the whole thing over and over
for as long as `command1` does not error. `for varname in a b c d; do
command; done` executes `command` four times, each time with `$varname`
set to one of `a`, `b`, `c`, and `d`. Instead of listing the items
explicitly, you'll often use "command substitution", such as:

```bash
for i in $(seq 1 10); do
```

This executes the command `seq 1 10` (which prints the numbers from 1 to
10 inclusive) and then replaces the whole `$()` with that command's
output, giving you a 10-iteration for loop. In older code you'll
sometimes see literal backticks (like ``for i in `seq 1 10`; do``)
instead of `$()`, but you should strongly prefer the `$()` form as it
can be nested.

While you _can_ write long shell scripts directly in your prompt, you'll
usually want to write them into a `.sh` file instead. For example,
here's a script that will run a program in a loop until it fails,
printing the output only of the failed run, while stressing your CPU in
the background (useful to reproduce flaky tests for example):

```bash
#!/bin/bash
set -euo pipefail

# Start CPU stress in background
stress --cpu 8 &
STRESS_PID=$!

# Setup log file
LOGFILE="test_runs_$(date +%s).log"
echo "Logging to $LOGFILE"

# Run tests until one fails
RUN=1
while cargo test my_test > "$LOGFILE" 2>&1; do
    echo "Run $RUN passed"
    ((RUN++))
done

# Cleanup and report
kill $STRESS_PID
echo "Test failed on run $RUN"
echo "Last 20 lines of output:"
tail -n 20 "$LOGFILE"
echo "Full log: $LOGFILE"
```

This has a number of new things in it that I recommend you spend some
time diving into, as they're very useful in crafting useful shell
invocations like background jobs (`&`) to run programs concurrently,
trickier [shell
redirections](https://www.gnu.org/software/bash/manual/html_node/Redirections.html),
and [arithmetic
expansion](https://www.gnu.org/software/bash/manual/html_node/Arithmetic-Expansion.html).

It's worth spending a second on the first two lines of the program
though. The first is the "shebang" -- you'll see this at the top of
other files than shell scripts too. When a file that starts with the
magic incantation `#!/path` is executed, the shell will start the
program at `/path`, and pass it the contents of the file as input. In
the case of a shell script, this means passing the contents of the shell
script to `/bin/bash`, but you can also write Python scripts with a
shebang line of `/usr/bin/python`!

The second line is a way to make bash "stricter", and mitigate a number
of footguns when writing shell scripts. `set` can take a whole lot of
arguments, but briefly: `-e` makes it so that if any command fails, the
script exits early; `-u` makes it so that use of undefined variables
crashes the script rather than just using an empty string; and `-o
pipefail` makes it so that if programs in a `|` sequence fail, the
shell script as a whole also exits early.

> Shell programming is a deep topic, just as any programming language
> is, but be warned: bash has an unusual number of gotchas, to the point
> that there are [multiple](https://tldp.org/LDP/abs/html/gotchas.html)
> websites dedicated to [listing them](https://mywiki.wooledge.org/BashPitfalls).
> I highly recommend making heavy use of
> [shellcheck](https://www.shellcheck.net/) when writing them. LLMs are
> also great at writing and debugging shell scripts, as well as
> translating them to a "real" programming language (like Python) when
> they've grown too unwieldy for bash (100+ lines).

# Next steps

At this point you know your way around a shell enough to accomplish
basic tasks. You should be able to navigate around to find files of
interest and use the basic functionality of most programs. In the next
lecture, we will talk about how to perform and automate more complex
tasks using the shell and the many handy command-line programs out
there.

# Exercises

All classes in this course are accompanied by a series of exercises.
Some give you a specific task to do, while others are open-ended, like
"try using X and Y programs". We highly encourage you to try them out.

We have not written solutions for the exercises. If you are stuck on
anything in particular, feel free to post in `#missing-semester-forum`
on [Discord](https://ossu.dev/#community) or send us an email describing
what you've tried so far, and we will try to help you out. These
exercises will also likely work well as initial prompts in a
conversation with an LLM where you can interactively dive into the
topic. The real value in these exercises is the journey of discovering
the answers, not the answer itself. We encourage you to follow tangents
and ask "why" as you work through them, rather than just looking for the
shortest path to the solution.

1. For this course, you need to be using a Unix shell like Bash or ZSH. If
   you are on Linux or macOS, you don't have to do anything special. If you
   are on Windows, you need to make sure you are not running cmd.exe or
   PowerShell; you can use [Windows Subsystem for
   Linux](https://docs.microsoft.com/en-us/windows/wsl/) or a Linux virtual
   machine to use Unix-style command-line tools. To make sure you're running
   an appropriate shell, you can try the command `echo $SHELL`. If it says
   something like `/bin/bash` or `/usr/bin/zsh`, that means you're running
   the right program.

1. What does the `-l` flag to `ls` do? Run `ls -l /` and examine the output.
   What do the first 10 characters of each line mean? (Hint: `man ls`)

1. In the command `find ~/Downloads -type f -name "*.zip" -mtime +30`, the
   `*.zip` is a "glob". What is a glob? Create a test directory with some
   files and experiment with patterns like `ls *.txt`, `ls file?.txt`, and
   `ls {a,b,c}.txt`. See [Pattern
   Matching](https://www.gnu.org/software/bash/manual/html_node/Pattern-Matching.html)
   in the Bash manual.

1. What's the difference between `'single quotes'`, `"double quotes"`, and
   `$'ANSI quotes'`? Write a command that echoes a string containing a
   literal `$`, a `!`, and a newline character. See
   [Quoting](https://www.gnu.org/software/bash/manual/html_node/Quoting.html).

1. The shell has three standard streams: stdin (0), stdout (1), and stderr
   (2). Run `ls /nonexistent /tmp` and redirect stdout to one file and
   stderr to another. How would you redirect both to the same file? See
   [Redirections](https://www.gnu.org/software/bash/manual/html_node/Redirections.html).

1. `$?` holds the exit status of the last command (0 = success). `&&` runs
   the next command only if the previous succeeded; `||` runs it only if
   the previous failed. Write a one-liner that creates `/tmp/mydir` only if
   it doesn't already exist. See [Exit
   Status](https://www.gnu.org/software/bash/manual/html_node/Exit-Status.html).

1. Why does `cd` have to be built into the shell itself rather than a
   standalone program? (Hint: think about what a child process can and
   cannot affect in its parent.)

1. Write a script that takes a filename as an argument (`$1`) and checks
   whether the file exists using `test -f` or `[ -f ... ]`. It should print
   different messages depending on whether the file exists. See [Bash
   Conditional
   Expressions](https://www.gnu.org/software/bash/manual/html_node/Bash-Conditional-Expressions.html).

1. Save the script from the previous exercise to a file (e.g., `check.sh`).
   Try running it with `./check.sh somefile`. What happens? Now run
   `chmod +x check.sh` and try again. Why is this step necessary? (Hint:
   look at `ls -l check.sh` before and after the `chmod`.)

1. What happens if you add `-x` to the `set` flags in a script? Try it with
    a simple script and observe the output. See [The Set
    Builtin](https://www.gnu.org/software/bash/manual/html_node/The-Set-Builtin.html).

1. Write a command that copies a file to a backup with today's date in the
    filename (e.g., `notes.txt` → `notes_2026-01-12.txt`). (Hint: `$(date
    +%Y-%m-%d)`). See [Command
    Substitution](https://www.gnu.org/software/bash/manual/html_node/Command-Substitution.html).

1. Modify the flaky test script from the lecture to accept the test command
    as an argument instead of hardcoding `cargo test my_test`. (Hint: `$1`
    or `$@`). See [Special
    Parameters](https://www.gnu.org/software/bash/manual/html_node/Special-Parameters.html).

1. Use pipes to find the 5 most common file extensions in your home
    directory. (Hint: combine `find`, `grep` or `sed` or `awk`, `sort`,
    `uniq -c`, and `head`.)

1. `xargs` converts lines from stdin into command arguments. Use `find` and
    `xargs` together (not `find -exec`) to find all `.sh` files in a
    directory and count the lines in each with `wc -l`. Bonus: make it
    handle filenames with spaces. (Hint: `-print0` and `-0`). See `man
    xargs`.

1. Use `curl` to fetch the HTML of the course website
    (`https://missing.csail.mit.edu/`) and pipe it to `grep` to count how
    many lectures are listed. (Hint: look for a pattern that appears once
    per lecture; use `curl -s` to silence the progress output.)

1. [`jq`](https://jqlang.github.io/jq/) is a powerful tool for processing
    JSON data. Fetch the sample data at
    `https://microsoftedge.github.io/Demos/json-dummy-data/64KB.json` with
    `curl` and use `jq` to extract just the names of people whose version
    is greater than 6. (Hint: pipe to `jq .` first to see the structure;
    then try `jq '.[] | select(...) | .name'`)

1. `awk` can filter lines based on column values and manipulate output.
    For example, `awk '$3 ~ /pattern/ {$4=""; print}'` prints only lines
    where the third column matches `pattern`, while omitting the fourth
    column. Write an `awk` command that prints only lines where the second
    column is greater than 100, and swaps the first and third columns. Test
    with: `printf 'a 50 x\nb 150 y\nc 200 z\n'`

1. Dissect the SSH log pipeline from the lecture: what does each step do?
    Then build something similar to find your most-used shell commands from
    `~/.bash_history` (or `~/.zsh_history`).

---
layout: page
title: 计算机科学教育的遗珠一课
description: 掌握高效利器，让你在计算机科学与编程实践中事半功倍。
# subtitle: IAP 2026
subtitle: "2026"
nositetitle: true
---

大学计算机科学课程教授操作系统、机器学习等众多高深领域，但有一门至关重要的学科却鲜被讲授，通常被留给学生自己摸索：工具的精通之道。我们将教你如何掌握命令行、运用强大的文本编辑器、利用版本控制系统的高级特性，以及更多实用技能！

在整个学生生涯中，学生会花费数百小时使用这些工具，职业生涯中更是数千小时。因此，让这一体验尽可能顺畅无阻是明智之举。掌握这些工具不仅能减少为工具所累的时间，更重要的是让你解决曾经看似不可能的复杂问题。

当今软件工程领域正在经历剧变，AI 赋能和增强工具与工作流程的涌现推动了这一变革。当恰当运用并充分认识其局限时，这些工具往往能为计算机科学从业者带来显著收益，因此值得深入学习。由于 AI 是跨领域的关键赋能技术，本课程并未设立独立的 AI 讲座，而是在每场讲座中融入了最新的 AI 工具与技术。

详细了解 [本课程的设计理念]({{ '/about/' | relative_url }}) 。

{% comment %}
# Registration

Sign up for the IAP 2026 class by filling out this [registration form](https://forms.gle/j2wMzi7qeiZmzEWy9).
{% endcomment %}

# 课程安排

{% comment %}
**Lecture**: [35-225](https://whereis.mit.edu/?go=35), 1:30--2:30pm (_exception_: 3--4pm on Friday 1/16)<br>
**Discussion**: [OSSU Discord](https://ossu.dev/#community) (use `#missing-semester-forum` like you would use Piazza, and `#missing-semester` to chat with the class/instructors)
{% endcomment %}

<ul>
{% assign lectures = site['2026'] | sort: 'date' %}
{% for lecture in lectures %}
    {% if lecture.phony != true %}
        <li>
        <strong>{{ lecture.date | date: '%-m/%-d/%y' }}</strong>:
        {% if lecture.ready %}
            <a href="{{ lecture.url }}">{{ lecture.title }}</a>
        {% else %}
            {{ lecture.title }} {% if lecture.noclass %}[no class]{% endif %}
        {% endif %}
        </li>
    {% endif %}
{% endfor %}
</ul>

## 往年特别专题

本课程的讲授内容每年都会有所调整。对于希望了解我们历年来所涉及完整主题的同学，我们在此列出 2026 年未包含、但在往年讲授过的一些专题。

{% comment %} pop to remove default "posts" collection {% endcomment %}
{% assign sorted_collections = site.collections | sort: 'label' | pop | reverse %}
<ul>
{% for collection in sorted_collections %}
    {% assign grouped_lectures = site[collection.label] | group_by: 'date' | sort: 'name' %}
    {% for group in grouped_lectures %}
        {% assign sorted_lectures = group.items | sort: 'order' %}
        {% for lecture in sorted_lectures %}
            {% if lecture.special == true %}
                <li>
                    <strong>{{ lecture.date | date: '%-m/%-d/%y' }}</strong>:
                    <a href="{{ lecture.url }}">{{ lecture.title }}</a>
                </li>
            {% endif %}
        {% endfor %}
    {% endfor %}
{% endfor %}
</ul>

{% comment %}
Lecture videos will be made available to MIT students immediately after lecture (via Panopto). The system has a limitation that only those with an MIT Kerberos can access the raw lecture videos. We are working on editing lecture videos and uploading them to YouTube. A couple have been uploaded already; we expect the rest to be uploaded by mid-February.

If you can't wait until January 2026, you can also take a look at the lectures
from the [previous offering of the course](/2020/), which covers many of the
same topics.
{% endcomment %}

# 基础信息

**讲师阵容**：本课程由 [Anish](https://anish.io/)、[Jon](https://thesquareplanet.com/) 和 [Jose](https://josejg.com/) 联合讲授。<br>
**有任何疑问**：欢迎通过 [missing-semester@mit.edu](mailto:missing-semester@mit.edu) 邮件咨询我们。
**讨论区**：可以在 [OSSU Discord](https://ossu.dev/#community) 社区讨论课程（使用 `#missing-semester-forum` 频道进行课程讨论，就如同使用 [Piazza](https://piazza.com/) 一样；使用 `#missing-semester` 频道与老师和同学交流）。

# 走向世界

我们也将本课程资源分享到 MIT 之外，期待更多人从中受益。你可以在以下平台找到相关讨论和分享：

 - Hacker News ([2026](https://news.ycombinator.com/item?id=47124171), [2020](https://news.ycombinator.com/item?id=22226380), [2019](https://news.ycombinator.com/item?id=19078281))
 - Lobsters ([2026](https://lobste.rs/s/q4ykw7/missing_semester_your_cs_education_2026), [2020](https://lobste.rs/s/ti1k98/missing_semester_your_cs_education_mit), [2019](https://lobste.rs/s/h6157x/mit_hacker_tools_lecture_series_on))
 - r/learnprogramming ([2026](https://www.reddit.com/r/learnprogramming/comments/1r93yk6/the_missing_semester_of_your_cs_education_2026/), [2020](https://www.reddit.com/r/learnprogramming/comments/eyagda/the_missing_semester_of_your_cs_education_mit/), [2019](https://www.reddit.com/r/learnprogramming/comments/an42uu/mit_hacker_tools_a_lecture_series_on_programmer/))
 - r/programming ([2020](https://www.reddit.com/r/programming/comments/eyagcd/the_missing_semester_of_your_cs_education_mit/), [2019](https://www.reddit.com/r/programming/comments/an3xki/mit_hacker_tools_a_lecture_series_on_programmer/))
 - X ([2026](https://x.com/anishathalye/status/2024521145777848588), [2020](https://twitter.com/jonhoo/status/1224383452591509507), [2019](https://x.com/jonhoo/status/1090323977766137858))
 - Bluesky ([2026](https://bsky.app/profile/jonhoo.eu/post/3mfa2bhyuj22i))
 - Mastodon ([2026](https://fosstodon.org/@jonhoo/116098318361854057))
 - LinkedIn ([2026](https://www.linkedin.com/posts/anishathalye_i-returned-to-mit-during-iap-january-term-activity-7430285026933522433-Ehr9))
 - YouTube ([2026](https://www.youtube.com/playlist?list=PLyzOVJj3bHQunmnnTXrNbZnBaCA-ieK4L), [2020](https://www.youtube.com/playlist?list=PLyzOVJj3bHQuloKGG59rS43e29ro7I57J), [2019](https://www.youtube.com/playlist?list=PLyzOVJj3bHQuiujH1lpn8cA9dsyulbYRv))

# 译文

{% comment %} keep these in alphabetical order {% endcomment %}

- [Arabic（阿拉伯语）](https://missing-semester-ar.github.io/)
- [Bengali（孟加拉语）](https://missing-semester-bn.github.io/)
- 简体中文
- [繁体中文](https://missing-semester-tw.github.io/)
- [German（德语）](https://missing-semester-de.github.io/)
- [Italian（意大利语）](https://missing-semester-it.github.io/)
- [Japanese（日语）](https://missing-semester-jp.github.io/)
- [Kannada（卡纳达语/印度卡纳塔克邦官方语言）](https://missing-semester-kn.github.io/)
- [Korean（韩语）](https://missing-semester-kr.github.io/)
- [Persian（波斯语）](https://missing-semester-fa.github.io/)
- [Portuguese（葡萄牙语）](https://missing-semester-pt.github.io/)
- [Russian（俄语）](https://missing-semester-rus.github.io/)
- [Serbian（塞尔维亚语）](https://netboxify.com/missing-semester/)
- [Spanish（西班牙语）](https://missing-semester-esp.github.io/)
- [Swedish（瑞典语）](https://itiquette.github.io/den-saknade-terminen/)
- [Thai（泰语）](https://missing-semester-th.github.io/)
- [Turkish（土耳其语）](https://missing-semester-tr.github.io/)
- [Vietnamese（越南语）](https://missing-semester-vn.github.io/)

> MIT 官方注：<br>
> 以上为社区译本的外部链接，我们未对其进行审核。<br>
> 如果你增添了本课程的翻译，欢迎提交[拉取请求(Pull Request)](https://github.com/missing-semester/missing-semester/pulls)，我们会将其收录到上述列表中！

> 简体中文译者注：<br>
> 如有任何错漏、补充或修订建议，欢迎 [发起议题(Issue)](https://github.com/ztm0929/missing-semester/issues) 或 [提交拉取请求](https://github.com/ztm0929/missing-semester/pulls)。

## 致谢

{% comment %}
2026 acks; previous years' acks are on their respective pages
{% endcomment %}

感谢 Elaine Mello 和 [MIT Open Learning](https://openlearning.mit.edu/) 为我们提供讲座视频的录制条件。<br>
感谢 Luis Turino / [SIPB](https://sipb.mit.edu/) 将本课程纳入 [SIPB IAP 2026](https://sipb.mit.edu/iap/) 项目并给予支持。

---

<div class="small center">
<p><a href="https://github.com/missing-semester/missing-semester">英文源码</a> | <a href="https://github.com/ztm0929/missing-semester">中文源码</a></p>
<p>本站采用 CC BY-NC-SA 协议授权</p>
<p>查看 <a href="{{ '/license/' | relative_url }}">贡献与翻译指南</a></p>
</div>

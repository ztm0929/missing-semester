---
layout: page
title: 过往讲座
description: >
  查看 Missing Semester 往届课程。
---

{% comment %} pop to remove default "posts" collection {% endcomment %}
{% assign sorted_collections = site.collections | sort: 'label' | pop | reverse %}
<ul>
{% for collection in sorted_collections %}
    {% if forloop.index == 1 %}
        <li><a href="/">{{ collection.label }}</a>（最新版）</li>
    {% else %}
        <li><a href="/{{ collection.label }}/">{{ collection.label }}</a></li>
    {% endif %}
{% endfor %}
</ul>

每一年的课程内容都是完整且相对独立的。我们建议从最新版本的课程资料开始学习。由于不同年份涵盖的主题会有所变化，我们也继续保留并提供往年课程的讲义和视频。

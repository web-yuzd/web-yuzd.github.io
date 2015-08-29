---
layout: page
title: 博客主页
tagline: 每天问自己一遍：努力和遗憾，哪一个更痛苦！
---
{% include JB/setup %}


    
## 目录



<ul class="posts">
  {% for post in site.posts %}
    <li>
      <span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a>
      <p>{{ post.excerpt }}</p>
    </li>
  {% endfor %}
</ul>




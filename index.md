---
layout: page
title: 志冬的博客主页
tagline: 大家好，这是我的前端开发博客！
---
{% include JB/setup %}


    
## 博文目录



<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>




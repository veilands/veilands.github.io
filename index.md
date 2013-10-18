---
layout: page
title: My Public Notebook
permalink: /index.html
---

###University related posts

<ul class="posts">    
    {% for post in site.posts %}
      <li><span class="datums">{{ post.date | date_to_string }} - </span><a class="ieraksts" href="{{ post.url }}">{{ post.title }}</a></li>
    {% endfor %}
</ul>

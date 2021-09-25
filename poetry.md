---
layout: page
permalink: /writing/
title: 
description: 
---

<div class="header-bar">
  <h1>Writing</h1>
  <h2 class="title-description">글쓰기와 기록</h2>
  <br/>
</div>

<ul class="post-list">
{% for poem in site.poetry reversed %}
    <li>
        <h2><a class="poem-title" href="{{ poem.url | prepend: site.baseurl }}">{{ poem.title }}</a></h2>
        <p class="post-meta">{{ poem.date | date: '%B %-d, %Y — %H:%M' }}</p>
      </li>
{% endfor %}
</ul>
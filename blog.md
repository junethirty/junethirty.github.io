---
layout: default
title: 
permalink: /blog/
description: 
---



<div class="header-bar">
  <h1>Blog</h1>
  <h2 class="title-description">배운 것들을 하나씩 씁니다</h2>
  <br/>
</div>


<ul class="post-list">
    {% for post in site.posts %}
      <li>
        <div class="post-item">
             <h2><a href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a></h2>
            <p class="post-description"><a href="{{ post.url | prepend: site.baseurl }}">{{ post.description }}</a></p>
           <p class="post-meta">{{ post.date | date: '%B %-d, %Y' }}</p>
        </div>
        <hr/>
      </li>
    {% endfor %}
</ul>
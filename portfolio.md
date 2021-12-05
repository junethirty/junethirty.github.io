---
layout: page
title: 
permalink: /portfolio/
---


<div class="header-bar">
  <h1>Portfolio</h1>
  <h2 class="title-description"></h2>
</div>






<ul class="post-list">
    {% for post in site.portfolio %}
      <li>
        <a class="post-section" href="{{ post.url | prepend: site.baseurl }}">
        <div class="portfolio-item">
                        {% if post.img %}
                        <img class="post-thumnail" src="{{ post.img }}"/> 
                        {% else %}
                            <div class="page-margin-top"></div>
                        {% endif %}   
            <div class="post-tag">{{ post.tag }}</div>
            <div class="post-container">
                <h2>{{ post.title }}</h2>
                <p class="post-subtitle">{{ post.subtitle }}</p>
                {% if post.previewtext %}
                <div class="post-previewtext">{{ post.previewtext }}</div>
                {% else %}
                {% endif %}  
           </div>
           <!--
           <p class="post-meta">{{ post.date | date: '%B %-d, %Y' }}</p> 
           -->
        </div>
        </a>
        <hr/>
      </li>
    {% endfor %}
</ul>




<!--  타일 형식 포트폴리오
<br/><br/><br/><br/>







{% for project in site.portfolio %}

{% if project.redirect %}
<div class="project">
    <div class="thumbnail">
        <a href="{{ project.redirect }}" target="_blank">
        {% if project.img %}
        <img class="thumbnail" src="{{ project.img }}"/>
        {% else %}
        <div class="thumbnail blankbox"></div>
        {% endif %}    
        <span>
            <p>{{ project.description }}</p>
            <h1>{{ project.title }}</h1>
        </span>
        </a>
    </div>
</div>
{% else %}

<div class="project">
    <div class="thumbnail">
        <a href="{{ site.baseurl }}{{ project.url }}">
        {% if project.img %}
        <div class="thumbnail" style="background-image : url({{ project.img }});"></div>
        {% else %}
        <div class="thumbnail blankbox"></div>
        {% endif %}    
        <span>
            <span class="portfoilo text">
            <p>{{ project.description }}</p>
            <h1>{{ project.title }}</h1>
            </span>
        </span>
        </a>
    </div>
</div>

{% endif %}

{% endfor %}
-->
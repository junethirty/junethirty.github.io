---
layout: page
title: 
permalink: /portfolio/
---

<div class="header-bar">
  <h1>Portfolio</h1>
  <h2 class="title-description"></h2>
</div>

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
            <h1>{{ project.title }}</h1>
            <br/>
            <p>{{ project.description }}</p>
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
            <h1>{{ project.title }}</h1>
            <p>{{ project.description }}</p>
        </span>
        </a>
    </div>
</div>

{% endif %}

{% endfor %}

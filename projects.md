---
title: Projects
layout: page
permalink: /projects/
---
<link rel="stylesheet" href="/assets/page.css">

{% assign projects = site.projects | sort: 'date' | reverse %}
{% for project in projects %}
<div class="item">
  <h3><a href="{{ project.url }}">{{ project.title }}</a></h3>
  <p>{{ project.date | date: "%B %e, %Y" }}</p>
</div>
{% endfor %}

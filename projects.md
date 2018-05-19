---
title: Projects
layout: page
permalink: /projects/
---

{% for project in site.projects %}	
  <h3><a href="{{ project.url }}">{{ project.title }}</a></h3>
  <p><small><strong>{{ project.date | date: "%B %e, %Y" }}</strong>
{% endfor %} 
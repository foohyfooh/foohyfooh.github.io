---
title: Projects
layout: page
permalink: /projects/
---

{% assign projects = site.projects | sort: 'date' | reverse %}
{% for project in projects %}
  <h3><a href="{{ project.url }}">{{ project.title }}</a></h3>
  <p><small><strong>{{ project.date | date: "%B %e, %Y" }}</strong></small></p>
{% endfor %}

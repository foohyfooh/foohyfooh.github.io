---
title: Posts
layout: page
permalink: /posts/
---

{% assign posts = site.posts | sort: 'date' | reverse %}
{% for post in posts %}
  <h3><a href="{{ post.url }}">{{ post.title }}</a></h3>
  <p><small><strong>{{ post.date | date: "%B %e, %Y" }}</strong></small></p>
{% endfor %}

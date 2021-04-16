---
title: Posts
layout: page
permalink: /posts/
---

{% assign posts = site.posts | sort: 'date' | reverse %}
{% for post in posts %}
<div class="item">
  <h3><a href="{{ post.url }}">{{ post.title }}</a></h3>
  <p>{{ post.date | date: "%B %e, %Y" }}</p>
</div>
{% endfor %}

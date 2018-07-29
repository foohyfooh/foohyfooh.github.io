---
title: Home
layout: page
---
<link rel="stylesheet" href="/assets/page.css">

I have a BSc. Computer Science from the University of the West Indies, St. Augustine. I am a member of the UWI Computing Society (UWICS) and was the Web Master for two academic years, and I am a member of UWI Jammers. Currently I am working as a Software Engineering Intern at [Virtana](https://virtanatech.com/) through the DCIT Internship Programme.<br>

My interests include Computer Science and Engineering, Electronics, Programming Languages, Competitive Programming, Machine Learning, and Computer Accessibility.


## Recent Posts
{% assign posts = site.posts | sort: 'date' | reverse %}
{% for post in posts limit:4 %}
<div class="item">
  <h3><a href="{{ post.url }}">{{ post.title }}</a></h3>
  <p>{{ post.date | date: "%B %e, %Y" }}</p>
</div>
{% endfor %}

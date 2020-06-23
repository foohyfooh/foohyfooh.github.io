---
title: Home
layout: page
---
<link rel="stylesheet" href="/assets/page.css">

I have a BSc. Computer Science from the University of the West Indies (UWI), St. Augustine, and I am currently pursuing a MSc. Data Science from UWI. I am a member of the UWI Computing Society (UWICS) and was the Web Master for two academic years, and I am a member of UWI Jammers.  Currently I am working as an Associate Software Engineer at [Virtana](https://virtanatech.com/).

My computer interests include Computer Science and Engineering, Electronics, Programming Languages, Competitive Programming, Machine Learning, and Computer Accessibility. <br>
My gaming interests include Pokémon, Naruto Ultimate Ninja series, Super Smash Bros. Ultimate, and Nintendo games in general.


## Recent Posts
{% assign posts = site.posts | sort: 'date' | reverse %}
{% for post in posts limit:4 %}
<div class="item">
  <h3><a href="{{ post.url }}">{{ post.title }}</a></h3>
  <p>{{ post.date | date: "%B %e, %Y" }}</p>
</div>
{% endfor %}

---
title:  Pokémon
layout: post
permalink: /pokemon/
categories: Pokémon
---

## Hightlighted Content

<div class="item">
  <h3 markdown="1">[Nekkra's Pokémon Spotlights](/pokemon/Nekkra-Pokemon-Spotlights)</h3>
  <p>Last Updated: April 25, 2021 for Players Cup 3</p>
</div>

## Posts

{% assign posts = site.categories["Pokémon"] | sort: 'date' | reverse %}
{% for post in posts %}
<div class="item">
  <h3  markdown="1">[{{ post.title }}]({{ post.url }})</h3>
  <p>{{ post.date | date: "%B %e, %Y" }}</p>
</div>
{% endfor %}

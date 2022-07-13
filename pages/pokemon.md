---
title:  Pokémon
layout: post
permalink: /pokemon/
categories: Pokémon
---

## Hightlighted Content

<div class="item">
  <h3 markdown="1">[Pokémon Spotlights](/pokemon/Pokemon-Spotlights)</h3>
  <p>Last Updated: July 12, 2022 for 2022 North America International Championships</p>
</div>
<div class="item">
  <h3 markdown="1">[HP Calculator](/pokemon/HP-Activation-Calculator)</h3>
  <p>Last Updated: May 20, 2021 with Gen 8 mechanics</p>
</div>

## Posts

{% assign posts = site.categories["Pokémon"] | sort: 'date' | reverse %}
{% for post in posts %}
<div class="item">
  <h3  markdown="1">[{{ post.title }}]({{ post.url }})</h3>
  <p>{{ post.date | date: "%B %e, %Y" }}</p>
</div>
{% endfor %}

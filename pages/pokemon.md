---
title:  Pokémon
layout: post
permalink: /pokemon/
categories: Pokémon
---

## Hightlighted Content

<div class="item">
  <h3 markdown="1">[Pokémon Spotlights](/pokemon/Pokemon-Spotlights)</h3>
  <p>Last Updated: September 10, 2022 for 2022 World Championships</p>
</div>
<div class="item">
  <h3 markdown="1">[HP Calculator](/pokemon/HP-Activation-Calculator)</h3>
  <p>Last Updated: May 20, 2021 with Gen 8 mechanics</p>
</div>
<div class="item">
  <h3 markdown="1">[PKHeX Sorting Plugin](https://github.com/foohyfooh/PKHeXSortingPlugin)</h3>
</div>

## Posts

{% assign posts = site.categories["Pokémon"] | sort: 'date' | reverse %}
{% for post in posts %}
<div class="item">
  <h3  markdown="1">[{{ post.title }}]({{ post.url }})</h3>
  <p>{{ post.date | date: "%B %e, %Y" }}</p>
</div>
{% endfor %}

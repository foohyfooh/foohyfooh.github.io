---
title:  Pokémon
layout: post
permalink: /pokemon/
categories: Pokémon
---

## Hightlighted Content

<div class="item">
  <h3 markdown="1">[Pokémon Spotlights](/pokemon/Pokemon-Spotlights)</h3>
  <p>Last Updated: August 14, 2023 for 2023 World Championships</p>
</div>
<div class="item">
  <h3 markdown="1">[HP Calculator](/pokemon/HP-Activation-Calculator)</h3>
  <p>Last Updated: May 20, 2021 with Gen 8 mechanics</p>
</div>
<div class="item">
<h3 markdown="1">[PKHeX Plugin Pile](https://github.com/foohyfooh/PKHeXPluginPile)</h3>
  <p>My pile of PKHeX Plugins</p>
</div>

## Posts

{% assign posts = site.categories["Pokémon"] | sort: 'date' | reverse %}
{% for post in posts %}
<div class="item">
  <a href="{{ post.url }}">{{ post.title }}</a>
  <p>{{ post.date | date: "%B %e, %Y" }}</p>
</div>
{% endfor %}

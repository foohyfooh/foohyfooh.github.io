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
  <h3>PKHeX Plugins</h3>
  <p markdown="1" class="subitem">[Sorting Plugin](https://github.com/foohyfooh/PKHeXSortingPlugin) - Sort boxes in PKHeX</p>
  <p markdown="1" class="subitem">[Raid Import Plugin](https://github.com/foohyfooh/PkmRaidImportPlugin) - Import raid files from Project Pokemon Event Gallery</p>
  <p markdown="1" class="subitem">[SV Vivillon Plugin](https://github.com/foohyfooh/SVivillonPlugin) - Change overworld Vivillon in Scarlet/Violet</p>
</div>

## Posts

{% assign posts = site.categories["Pokémon"] | sort: 'date' | reverse %}
{% for post in posts %}
<div class="item">
  <a href="{{ post.url }}">{{ post.title }}</a>
  <p>{{ post.date | date: "%B %e, %Y" }}</p>
</div>
{% endfor %}

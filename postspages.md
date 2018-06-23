---
title: Posts
layout: page
permalink: /posts/
pagination:
  enabled: true
  trail:
    before: 2
    after: 2
---
<link rel="stylesheet" href="/assets/page.css">

{% if paginator.page_trail %}
<nav id="trail">
  <a id="newer" {% unless paginator.previous_page %}class="disabled"{% endunless %} href="{{ paginator.previous_page_path | prepend: site.baseurl }}" aria-label="Newer">
    <svg width="1792" height="1792" viewBox="0 0 1792 1792" xmlns="http://www.w3.org/2000/svg"><path d="M1011 1376q0 13-10 23l-50 50q-10 10-23 10t-23-10l-466-466q-10-10-10-23t10-23l466-466q10-10 23-10t23 10l50 50q10 10 10 23t-10 23l-393 393 393 393q10 10 10 23zm384 0q0 13-10 23l-50 50q-10 10-23 10t-23-10l-466-466q-10-10-10-23t10-23l466-466q10-10 23-10t23 10l50 50q10 10 10 23t-10 23l-393 393 393 393q10 10 10 23z"/></svg>
  </a>
  
  {% for trail in paginator.page_trail %}
    <a {% if page.url == trail.path %}class="selected disabled"{% endif %} href="{{ trail.path | prepend: site.baseurl }}" aria-label="{{trail.title}}">{{ trail.num }}</a>
  {% endfor %}
  
  <a id="older" {% unless paginator.next_page %}class="disabled"{% endunless %}href="{{ paginator.next_page_path | prepend: site.baseurl }}" aria-label="Older">
    <svg width="1792" height="1792" viewBox="0 0 1792 1792" xmlns="http://www.w3.org/2000/svg"><path d="M979 960q0 13-10 23l-466 466q-10 10-23 10t-23-10l-50-50q-10-10-10-23t10-23l393-393-393-393q-10-10-10-23t10-23l50-50q10-10 23-10t23 10l466 466q10 10 10 23zm384 0q0 13-10 23l-466 466q-10 10-23 10t-23-10l-50-50q-10-10-10-23t10-23l393-393-393-393q-10-10-10-23t10-23l50-50q10-10 23-10t23 10l466 466q10 10 10 23z"/></svg>
  </a>
</nav>
{% endif %}


{% for post in paginator.posts %}
<div class="item">
  <h3><a href="{{ post.url }}">{{ post.title }}</a></h3>
  <p>{{ post.date | date: "%B %e, %Y" }}</p>
</div>
{% endfor %}


{% if paginator.page_trail %}
<nav id="trail">
  <a id="newer" {% unless paginator.previous_page %}class="disabled"{% endunless %} href="{{ paginator.previous_page_path | prepend: site.baseurl }}" aria-label="Newer">
    <svg width="1792" height="1792" viewBox="0 0 1792 1792" xmlns="http://www.w3.org/2000/svg"><path d="M1011 1376q0 13-10 23l-50 50q-10 10-23 10t-23-10l-466-466q-10-10-10-23t10-23l466-466q10-10 23-10t23 10l50 50q10 10 10 23t-10 23l-393 393 393 393q10 10 10 23zm384 0q0 13-10 23l-50 50q-10 10-23 10t-23-10l-466-466q-10-10-10-23t10-23l466-466q10-10 23-10t23 10l50 50q10 10 10 23t-10 23l-393 393 393 393q10 10 10 23z"/></svg>
  </a>
  
  {% for trail in paginator.page_trail %}
    <a {% if page.url == trail.path %}class="selected disabled"{% endif %} href="{{ trail.path | prepend: site.baseurl }}" title="{{trail.title}}">{{ trail.num }}</a>
  {% endfor %}
  
  <a id="older" {% unless paginator.next_page %}class="disabled"{% endunless %}href="{{ paginator.next_page_path | prepend: site.baseurl }}" aria-label="Older">
    <svg width="1792" height="1792" viewBox="0 0 1792 1792" xmlns="http://www.w3.org/2000/svg"><path d="M979 960q0 13-10 23l-466 466q-10 10-23 10t-23-10l-50-50q-10-10-10-23t10-23l393-393-393-393q-10-10-10-23t10-23l50-50q10-10 23-10t23 10l466 466q10 10 10 23zm384 0q0 13-10 23l-466 466q-10 10-23 10t-23-10l-50-50q-10-10-10-23t10-23l393-393-393-393q-10-10-10-23t10-23l50-50q10-10 23-10t23 10l466 466q10 10 10 23z"/></svg>
  </a>
</nav>
{% endif %}

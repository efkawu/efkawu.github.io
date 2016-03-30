---
layout: default
title: "Playlists"
date: 2014-06-02T12:26:34-04:00
modified: 2014-08-18T14:21:32-04:00
excerpt: "A collection of thoughts, inspiration, mistakes, and other minutia I’ve written."
feature:
  visible: true
  headline: "Featured Articles"
  category: playlists
image:
  feature: 
---

{% if page.image.feature %}
  <div class="image-wrap">
  <img src=
    {% if page.image.feature contains 'http' %}
      "{{ page.image.feature }}"
    {% else %}
      "{{ site.url }}/images/{{ page.image.feature }}"
    {% endif %}
  alt="{{ page.title }} feature image">
  {% if page.image.credit %}
    <span class="image-credit">Photo Credit: <a href="{{ page.image.creditlink }}">{{ page.image.credit }}</a></span>
  {% endif %}
  </div><!-- /.image-wrap -->
{% endif %}

<div id="main" role="main">
  <div class="article-author-side">
    {% include _author-bio.html %}
  </div>
  <div id="index">
    <h1>{{ page.title }}</h1>
    <p></p>
    {% for post in site.posts %}
    {% unless post.next %}
      <h3>{{ post.date | date: '%Y' }}</h3>
      {% else %}
        {% capture year %}{{ post.date | date: '%Y' }}{% endcapture %}
        {% capture nyear %}{{ post.next.date | date: '%Y' }}{% endcapture %}
        {% if year != nyear %}
          <h3>{{ post.date | date: '%Y' }}</h3>
        {% endif %}
      {% endunless %}
      <article>
        {% if post.link %}
          <h2 class="link-post"><a href="{{ site.url }}{{ post.url }}" title="{{ post.title }}">{{ post.title }}</a> <a href="{{ post.link }}" target="_blank" title="{{ post.title }}"><i class="fa fa-link"></i></a></h2>
        {% else %}
          <h2><a href="{{ site.url }}{{ post.url }}" title="{{ post.title }}">{{ post.title }}</a></h2>
          <p>{{ post.excerpt | strip_html | truncate: 160 }}</p>
        {% endif %}
      </article>
    {% endfor %}
  </div><!-- /#index -->
</div><!-- /#main -->

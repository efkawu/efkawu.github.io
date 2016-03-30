---
layout: page
title: "Sitemap"
date: 2014-12-26
modified: 2015-05-22T12:22:34-04:00
excerpt: "Sitemap"
fullwidth: true
share: false
ads: false
---

A hierarchical breakdown of all the sections and pages found on the site. 
For you robots out there an [XML version]({{ site.url }}/sitemap.xml) is available for digesting.

<div class="sitemap">
  <ul id="primaryNav" class="col6">
    <li id="home"><a href="{{ site.url }}/">Home</a></li>
    <li><a href="{{ site.url }}/about/">About</a></li>
    <li><a href="#archives">Archives</a>
      <ul>
        <li><a href="#archives-year">Archives by Year</a>
          <ul>
            <!--<li><a href="{{ site.url }}/2014/">2015</a></li>-->
            <!--<li><a href="{{ site.url }}/2014/">2014</a></li>-->
            <!--<li><a href="{{ site.url }}/2013/">2013</a></li>-->
        {% for post in site.posts %}
          {% assign currentdate = post.date | date: "%Y" %}
          {% if currentdate != date %}
            <li id="y{{currentdate}}">{{ currentdate }}</li>
            {% assign date = currentdate %} 
          {% endif %}
            <ul><li><a href="{{ post.url }}">{{ post.title }}</a></li></ul>
        {% endfor %}
          </ul>
        </li>

        <!--<li><a href="{{ site.url }}/tag/">Archives by Tag</a>-->
          <!--<ul>-->
            <!--{% assign tags_list = site.tags | sort %}  -->
            <!--{% for tag in tags_list %} -->
              <!--<li><a href="{{ site.url }}/tag/{{ tag[0] | replace:' ','-' | downcase }}/">{{ tag[0] }}</a></li>-->
            <!--{% endfor %}-->
          <!--</ul>-->
        <!--</li>-->
      </ul>
    </li>
    <!--<li><a href="{{ site.url }}/articles/">Blog Articles</a>-->
      <!--<ul>-->
        <!--{% for post in site.categories.articles %}-->
          <!--{% include post-list.html %}-->
        <!--{% endfor %}-->
      <!--</ul>-->
    <!--</li>-->
  </ul><!-- /.col5 -->
</div><!-- /.sitemap -->

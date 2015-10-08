---
layout: default
title: Tags
---

<h1>{{ page.title }}</h1>
<p>&nbsp;</p>

{% comment %} Get our tags and sort them. {% endcomment %}
{% capture tags %}
  {% for tag in site.tags %}
    {{ tag[0] }}
  {% endfor %}
{% endcapture %}
{% assign sortedtags = tags | split:' ' | sort %}


{% for tag in sortedtags %}
{% assign tag_stripped = tag | replace: ",", "" %}

  <h3 id="{{ tag_stripped }}">{{ tag_stripped }}</h3>
  <ul>
  {% for post in site.tags[tag] %}
    <li>
		{{ post.date | date: "%B %d, %Y" }}: <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
  </ul>
{% endfor %}


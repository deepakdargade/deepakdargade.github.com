---
layout: default
title: Blog | Deepak Dargade
header: Blog
subheading: I'm a Mumbai-based Entrepreneur, Ruby on Rails monomaniac and Food enthusiast.
permalink: /blog/
---

{% for post in site.posts %}
  <p>
    <a href="{{ post.url }}">{{ post.headline }}</a>
    <br>
    <small>{{ post.date | date_to_string }}</small>
  </p>
{% endfor %}
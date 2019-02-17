---
layout: page
title: Blog
permalink: /blog/
---

{% for post in site.posts %}

### <a href="{{ post.url }}">{{ post.title }}</a>

Posted **{{ post.date | date: "%A, %d %B %Y" }}** {% if post.categories > 0 %} in *{{ post.categories | join: ", " }}* {% endif %}  
Tagged *{{ post.tags | join ", " }}*. 
[Permalink]({{ post.url }})

{{ post.content }}

{% endfor %}
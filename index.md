---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
title: Latest Posts
---

# Latest Posts

{% for post in site.posts %}

### <a href="{{ post.url }}">{{ post.title }}</a>

Posted **{{ post.date | date: "%A, %d %B %Y" }}** {% if post.categories > 0 %} in *{{ post.categories | join: ", " }}* {% endif %}  
Tagged *{{ post.tags | join ", " }}*

{{ post.excerpt }}

[(Continued...)]({{ post.url }})

{% endfor %}
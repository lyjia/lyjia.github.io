---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
title: 
bigtitle: 
---

# Latest Posts

{% for post in site.posts %}
## <a href="{{ post.url }}">{{ post.title }}</a>
{% include post-content-header.html %}

<div class="post-content">
{{ post.excerpt }}
</div>
[(Continued...)]({{ post.url }})

{% endfor %}
---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
---

# Latest Posts

{% for post in site.posts %}
## <a href="{{ post.url }}">{{ post.title }}</a>
{% include post-content-header.html %}

{{ post.excerpt }}

[(Continued...)]({{ post.url }})

{% endfor %}
---
layout: page
title: Blog
permalink: /blog/
---

{% for post in site.posts %}

<h1 class="post-title-list"><a href="{{ post.url }}">{{ post.title }}</a></h1>
{% include post-content-header.html %}

{{ post.content }}

{% endfor %}
---
layout: default
title: Home
---

{% for post in site.posts %}
# [{{ post.title }}]({{ post.url }})

{{ post.excerpt }}

{% if forloop.last == false %}
* * *
{% endif %}
{% endfor %}

{% comment %}
  <!-- debug -->
  <pre>
    {{ site | inspect }}
  </pre>
{% endcomment %}

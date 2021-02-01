---
layout: default
title: Home
---

{% for post in site.posts %}

# [{{ post.title }}]({{ post.url }})

{% if post.image %}[![{{ post.title }}]({{ post.image }})]({{ post.url }}){% endif %}

{{ post.excerpt }}

{% if forloop.last == false %}

---

{% endif %}

{% endfor %}

{% comment %}

  <!-- debug -->
  <pre>
    {{ site | inspect }}
  </pre>

{% endcomment %}

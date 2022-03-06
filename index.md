---
title: "Ramaraj's blogs"
---

<ul>
  {% for post in site.posts %}
    <li>
      <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
      <h3>{{ post.url }}<h3>
    </li>
  {% endfor %}
</ul>

---
title: "Ramaraj's blogs"
---

I'm glad you are here. I plan to talk about ...

<ul>
  {% for post in site.posts %}
    <li>
      <h2><a href="blogs/{{ post.url }}">{{ post.title }}</a></h2>
      {{ post.excerpt }}
    </li>
  {% endfor %}
</ul>

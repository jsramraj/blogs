---
title: "Ramaraj's blogs"
---

<ul>
  {% for post in site.posts %}
    <li>
      <h2><a href="{{ site.baseurl }}/{{ post.url }}">{{ post.title }}</a></h2>
      <p><time datetime="{{ post.date | date: "%Y-%m-%d" }}">{{ post.date | date_to_long_string }}</time></p>
    </li>
  {% endfor %}
</ul>

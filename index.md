---
layout: default
title: Home
---

<h1 class="post-title">Posts</h1>

<ul>
  {% for post in site.posts %}
    <li class="post-title">
      <a href="{{ post.url }}"> {{ post.title }} </a> &mdash; <em>{{ post.date | date_to_string }}</em>
    </li>
  {% endfor %}
</ul>

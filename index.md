---
layout: page
title: my development
tagline: playground and blog
---
## Hello there

Somehow you've come across this dumping ground of project ideas, thoughts, and
(perhaps helpful) advice. Feel free to look around.

## Recent Posts

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

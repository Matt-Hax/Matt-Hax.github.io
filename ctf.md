---
layout: default
title: Page Title
---

# CTF Writeups

<ul>
  {% for writeup in site.ctf %}
    <li><a href="{{ writeup.url }}">{{ writeup.title }}</a></li>
  {% endfor %}
</ul>

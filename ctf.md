---
layout: default
title: CTF Writeups
permalink: /ctf/
---

<link rel="stylesheet" href="/assets/css/custom.css">

# CTF Writeups

<ul>
  {% for writeup in site.ctf %}
    <li><a href="{{ writeup.url }}">{{ writeup.title }}</a></li>
  {% endfor %}
</ul>

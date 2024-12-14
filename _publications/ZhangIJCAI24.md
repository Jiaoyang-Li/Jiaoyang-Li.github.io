---
layout: archive
permalink: /publications/ZhangIJCAI24/
title: Guidance Graph Optimization for Lifelong Multi-Agent Path Finding
author_profile: true
---
{% assign pub_key = "ZhangIJCAI24" %}

{% include base_path %}
{% assign pub = null %}
{% for p in site.data.pubs %}
  {% if p.key == pub_key %}
    {% assign pub = p %}
    {% break %}
  {% endif %}
{% endfor %}
{% include pub-page.html %}
     
         

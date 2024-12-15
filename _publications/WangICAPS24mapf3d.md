---
layout: publication
permalink: /publications/WangICAPS24mapf3d/
author_profile: true
---
{% assign pub_key = "WangICAPS24mapf3d" %}

{% include base_path %}
{% assign pub = null %}
{% for p in site.data.pubs %}
  {% if p.key == pub_key %}
    {% assign pub = p %}
    {% break %}
  {% endif %}
{% endfor %}
{% include pub-page.html %}

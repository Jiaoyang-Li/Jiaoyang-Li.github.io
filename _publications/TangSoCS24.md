---
layout: publication
permalink: /publications/TangSoCS24/
author_profile: true
---
{% assign pub_key = "TangSoCS24" %}

{% include base_path %}
{% assign pub = null %}
{% for p in site.data.pubs %}
  {% if p.key == pub_key %}
    {% assign pub = p %}
    {% break %}
  {% endif %}
{% endfor %}
{% include pub-page.html %}
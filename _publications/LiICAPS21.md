---
layout: publication
permalink: /publications/LiICAPS21/
author_profile: true
---
{% assign pub_key = "LiICAPS21" %}

{% include base_path %}
{% assign pub = null %}
{% for p in site.data.pubs %}
  {% if p.key == pub_key %}
    {% assign pub = p %}
    {% break %}
  {% endif %}
{% endfor %}
{% include pub-page.html %}
 
<div style="text-align:center; width:100%; display: flex; align-items: center; justify-content: center;">
    <iframe style="max-width: 500px; aspect-ratio: 16/9;"
        src="https://www.youtube.com/embed/Pw4GBL1UhPA"
        title="YouTube video player" frameborder="0"
        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen>
    </iframe>
</div>
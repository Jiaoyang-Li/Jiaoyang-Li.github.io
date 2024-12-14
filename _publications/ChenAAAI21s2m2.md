---
layout: publication
permalink: /publications/ChenAAAI21s2m2/
author_profile: true
---
{% assign pub_key = "ChenAAAI21s2m2" %}

{% include base_path %}
{% assign pub = null %}
{% for p in site.data.pubs %}
  {% if p.key == pub_key %}
    {% assign pub = p %}
    {% break %}
  {% endif %}
{% endfor %}
{% include pub-page.html %}

<div style="text-align: center"> 
    <video style="max-width:500px" controls> 
        <source type="video/mp4" src="/images/S2M2-demo.mp4" /> 
    </video>
</div>

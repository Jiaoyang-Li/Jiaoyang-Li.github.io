---
layout: publication
permalink: /publications/LiAAMAS20/
author_profile: true
---
{% assign pub_key = "LiAAMAS20" %}

{% include base_path %}
{% assign pub = null %}
{% for p in site.data.pubs %}
  {% if p.key == pub_key %}
    {% assign pub = p %}
    {% break %}
  {% endif %}
{% endfor %}
{% include pub-page.html %} 
     
<p style="text-align:center;">
    <img src="/images/formation-random-4x.gif" style="max-height:150pt" alt="formation-random"/>
    <img src="/images/formation-tight-4x.gif" style="max-height:150pt" alt="formation-tight"/>
    <img src="/images/formation-wide-4x.gif" style="max-height:150pt" alt="formation-wide"/>
</p>
         

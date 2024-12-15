---
layout: publication
permalink: /publications/ZhongICRA22/
author_profile: true
---
{% assign pub_key = "ZhongICRA22" %}

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
        <source type="video/mp4" src="/images/icra22-demo.mp4" /> 
    </video>
</div>
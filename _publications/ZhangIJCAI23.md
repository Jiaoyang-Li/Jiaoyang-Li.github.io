---
layout: publication
permalink: /publications/ZhangIJCAI23/
author_profile: true
---
{% assign pub_key = "ZhangIJCAI23" %}

{% include base_path %}
{% assign pub = null %}
{% for p in site.data.pubs %}
  {% if p.key == pub_key %}
    {% assign pub = p %}
    {% break %}
  {% endif %}
{% endfor %}
{% include pub-page.html %}


<div style="display: flex; flex-wrap: wrap; text-align: center">
    <div style="min-width:300px;flex: 1;margin: 5px;">
        <video width="300px" autoplay loop controls> 
            <source type="video/mp4" src="https://jiaoyangli.me/images/human-designed-map.mp4" /> 
        </video>
        <figcaption>Traditional human-designed map</figcaption>
    </div>
    <div style="min-width:300px;flex: 1;margin: 5px;">
        <video width="300px" autoplay loop controls> 
            <source type="video/mp4" src="https://jiaoyangli.me/images/dsage-map.mp4" /> 
        </video>
        <figcaption>Our designed map</figcaption>
    </div>
</div>
<div style="clear:both;"></div>
---
layout: publication
permalink: /publications/LiAAAI23/
author_profile: true
---
{% assign pub_key = "LiAAAI23" %}

{% include base_path %}
{% assign pub = null %}
{% for p in site.data.pubs %}
  {% if p.key == pub_key %}
    {% assign pub = p %}
    {% break %}
  {% endif %}
{% endfor %}
{% include pub-page.html %}

Coordinating vehicles with optimal solver MILP (left), our solver PSL (middle), and greedy solver FCFS (right):
<p style="text-align:center;">
    <img src="/images/MILP-crosswalk.gif" style="max-height:150pt" alt="Mixed Integer Linear Programming"/>
    <img src="/images/PSL-crosswalk.gif" style="max-height:150pt" alt="Our MAPF-Based Algorithm"/>
    <img src="/images/FCFS-crosswalk.gif" style="max-height:150pt" alt="First Come First Served"/>
</p>
---
layout: archive
title: "ARCS Lab Members"
permalink: /people/
author_profile: true
---

{% include base_path %}


<img src="https://jiaoyangli.me/images/logo-white-background.png" title="logo" width="800pt" alt="ARCS Lab"/>

A summary of each member's ongoing research can be found 
[here](https://jiaoyang-li.github.io/files/ARCS-2024-Orientation-Poster.pdf "Download poster") 
(updated date: August 2024).


<!-- ## Current Members -->

<h2>Ph.D. Students</h2>
<ul style="margin-bottom: 1px">
    {% for person in site.data.people %}
        {% if person.role=="PhD student" %}
            {% include person.html %}
        {% endif %}
    {% endfor %}
</ul>

<h2>Masters Students</h2>
<ul style="margin-bottom: 1px">
    {% for person in site.data.people %}
        {% if person.role=="masters student" %}
            {% include person.html %}
        {% endif %}
    {% endfor %}
</ul>

<h2>Undergraduate Students</h2>
<ul style="margin-bottom: 1px">
    {% for person in site.data.people %}
        {% if person.role=="undergraduate student" %}
            {% include person.html %}
        {% endif %}
    {% endfor %}
</ul>

<h2>Visitors</h2>
<ul style="margin-bottom: 1px">
    {% for person in site.data.people %}
        {% if person.role=="visitor" %}
            {% include person.html %}
        {% endif %}
    {% endfor %}
</ul>

<h2>Alumni</h2>
<ul style="margin-bottom: 1px">
    {% for person in site.data.people %}
        {% if person.role=="alumnus" %}
            {% include person.html %}
        {% endif %}
    {% endfor %}
</ul>

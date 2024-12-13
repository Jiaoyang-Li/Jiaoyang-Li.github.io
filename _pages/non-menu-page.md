---
permalink: /non-menu-page/
layout: archive
author_profile: true
redirect_from: 
  - "/nmp/"
  - "/nmp.html"
---
<!--title: "Page not in menu"
excerpt: "This is a page not in the main menu"-->
{% include base_path %}
<!--{% include toc %}-->


<tr>
    <td>
        Guidance Graph Optimization for Lifelong Multi-Agent Path Finding
    </td>
</tr>

{% for pub in site.data.pubs %}
        {% include pub.html %}
    {% endfor %}
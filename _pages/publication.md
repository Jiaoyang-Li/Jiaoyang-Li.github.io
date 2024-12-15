---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---

{% include base_path %}

You can also find my articles on
<a href="https://scholar.google.com/citations?user=F5qzvmkAAAAJ&hl=en">my Google Scholar profile</a>.
<br>

<a href="#year2025">2025</a> |
<a href="#year2024">2024</a> |
<a href="#year2023">2023</a> |
<a href="#year2022">2022</a> |
<a href="#year2021">2021</a> |
<a href="#year2020">2020</a> |
<a href="#year2019">2019</a> |
<a href="#year2018">2018</a> |
<a href="#year2017">2017</a> |
<a href="#preprints">Preprints</a> |
<a href="#thesis">Thesis</a>

<!--{% assign sorted_pubs = site.data.pubs | sort: "year" | reverse %}-->
{% assign current_year = "" %}
{% assign highlighted_names = "Jiaoyang Li" | split: "," %}
{% assign display_links = "true" %}

<div style="clear: both;"></div>

{% for pub in site.data.pubs %}
    {% if pub.year != current_year %}
        {% unless current_year == "" %}
            </ul>
        {% endunless %}
        <h2>{{ pub.year }}</h2><a name="year{{ pub.year }}"></a>
        <ul>
        {% assign current_year = pub.year %}
    {% endif %}
    {% include pub.html %}
{% endfor %}
{% if site.data.pubs.size > 0 %}
    </ul>
{% endif %}

<h2>Preprints</h2><a name="preprints"></a>
<ul>
    {% for pub in site.data.preprints %}
        {% include pub.html %}
    {% endfor %}
</ul>

<h2>PhD Thesis</h2><a name="thesis"></a>
<ul>
    <li>
        <a href="/publications/LiPhD22">Efficient and Effective Techniques for Large-Scale Multi-Agent Path Finding</a>.
        (<b>Best Dissertation Awards by ICAPS, AAMAS, and USC Viterbi School of Engineering</b>)<br/>
        <b>Jiaoyang Li</b>.<br/>
        <i>{PhD thesis, Department of Computer Science, University of Southern California, Los Angeles (California)</i>, 2022.<br/>
        [<a href="javascript:void(0)" onclick="(function(target, id) { if ($('#' + id).css('display') == 'block') { $('#' + id).hide('fast'); $(target).text('bibtex') } else { $('#' + id).show('fast'); $(target).text('bibtex▲') } })(this, 'bibtex-LiPhD22');">bibtex</a>]
        [<a href="/files/phd-thesis-final.pdf">pdf</a>]
        <div id="bibtex-LiPhD22" style="display:none; font-size:small">
            <pre>@phdthesis{LiPhD22,
  title     = {Efficient and Effective Techniques for Large-Scale Multi-Agent Path Finding},
  author    = {Jiaoyang Li},
  school    = {University of Southern California},
  year      = {2022}
}</pre></div>
    </li>
</ul>
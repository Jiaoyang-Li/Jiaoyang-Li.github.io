---
index: MaAAMAS17
permalink: /publications/2017-AAMAS
title: "Lifelong Multi-Agent Path Finding for Online Pickup and Delivery Tasks"
authors: ['Hang Ma', 'Jiaoyang Li', 'T. K. Satish Kumar', 'Sven Koenig'] 
venue: 'International Conference on Autonomous Agents and Multi-Agent Systems'
venue-abbr: 'AAMAS'
venue-type: 'proceedings'
pages: 837--845
year: 2017
pdfurl: http://jiaoyang-li.github.io/files/2017-AAMAS.pdf
publisherurl: https://dl.acm.org/citation.cfm?id=3091243
codeurl:
talkurl:
excerpt: 'This paper is about the number 3. The number 4 is left for future work.'
collection: publications
layout: archive
author_profile: true
---

{% include base_path %}

{%- if page.excerpt -%}
  ({{page.excerpt}})<br>
{%- endif -%}

{%- if page.pages -%}
  {%- for author in page.authors -%}
    {%- unless forloop.last -%}
      {{author}},&nbsp;
    {%- else -%}
      and {{author}}.
    {%- endunless -%}
  {%- endfor -%} <br>
  <i>{{ page.venue }} (<strong>{{ page.venue-abbr }}</strong>)</i>, pages {{ page.pages }}, {{ page.year }}.<br>
{%- else -%}
  {{ page.title }} <br>
  {%- for author in page.authors -%}
    {%- unless forloop.last -%}
      {{author}},&nbsp;
    {%- else -%}
      and {{author}}.
    {%- endunless -%}
  {%- endfor -%} <br>
  <i>{{ page.venue }} (<strong>{{ page.venue-abbr }}</strong>)</i>, (in print), {{ page.year }}.<br>
{%- endif -%}

{%- assign bibtex-id = {{ 'bibtex-' + page.index }} -%}

{%- if page.publisherurl -%}
  [[publisher]({{ page.publisherurl }})]&nbsp;
{%- endif -%}
{%- if page.pdfurl -%}
  [[pdf]({{ page.pdfurl }})]&nbsp;
{%- endif -%}
{%- if page.codeurl -%}
  [[code]({{ page.codeurl }})]&nbsp;
{%- endif -%}
[<a href="javascript:void(0)" onclick="(function(target, id) { if ($('#' + id).css('display') == 'block') { $('#' + id).hide('fast'); $(target).text('bibtex') } else { $('#' + id).show('fast'); $(target).text('bibtex▲') } })(this, '{{ bibtex-id }}');">bibtex</a>]
<div id='{{ bibtex-id }}' style="display:none">
  <pre>@inproceedings{ {{ page.index }},
    author    = {&nbsp;{%- for author in page.authors -%}
    {%- unless forloop.last -%}
      {{author}} and&nbsp;
    {%- else -%}
      {{author}}
    {%- endunless -%}
  {%- endfor -%}&nbsp;},
    title     = {Lifelong Multi-Agent Path Finding for Online Pickup and Delivery Tasks},
    booktitle = {Proceedings of the International Conference on Autonomous Agents and Multi-Agent Systems (AAMAS)},
    pages     = {837--845},
    year      = {2017}
  }
  </pre>
</div>

{% if page.venue-type == 'proceedings' %}
<pre>
@inproceedings{ {{ page.index }},
  author    = {&nbsp;{%- for author in page.authors -%}
    {%- unless forloop.last -%}
      {{author}} and&nbsp;
    {%- else -%}
      {{author}}
    {%- endunless -%}
  {%- endfor -%}&nbsp;},
  title     = { {{ page.title }} },
  booktitle = { Proceedings of the {{page.venue}} ({{page.venue-abbr}}) },
  pages     = { {{ page.pages }} },
  year      = { {{ page.year }} }
}
</pre>
{% elsif page.venue-type == 'article' %}
<pre>
@article{ {{ page.index }},
  author    = {&nbsp;{%- for author in page.authors -%}
    {%- unless forloop.last -%}
      {{author}} and&nbsp;
    {%- else -%}
      {{author}}
    {%- endunless -%}
  {%- endfor -%}&nbsp;},
  title     = { {{ page.title }} },
  journal   = { {{ page.venue }} },
  pages     = { {{ page.pages }} },
  year      = { {{ page.year }} },
  doi       = { {{ page.publisher }} },
}
</pre>
{% endif %}

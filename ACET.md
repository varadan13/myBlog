---
title: ACET
layout: page
permalink: /ACET/
---

### Free formula sheets and theory to crack Actuarial Common Entrance Test   

{%- assign date_format = site.minima.date_format | default: "%b %-d, %Y" -%} 
{% for item in site.ACET %}

    {%- if item.title -%}
    <h1 class="page-heading"><a href = "{{ item.url }}">{{ item.title }}</a></h1>
    {%- endif -%}
    {%- if item.Description -%}
    <p>{{ item.Description }}</p>
    {%- endif -%}

{% endfor %}

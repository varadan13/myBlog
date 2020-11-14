---
title: 	InnumerateMe
layout: page
permalink: /InnumerateMe/
---

{%- assign date_format = site.minima.date_format | default: "%b %-d, %Y" -%} 
{% for item in site.InnumerateMe %}

	{%- if item.title -%}
    <h1 class="page-heading"><a href = "{{ item.url }}">{{ item.title }}</a></h1>
	{%- endif -%}
	{%- if item.Description -%}
	<p>{{ item.Description }}</p>
	{%- endif -%}

{% endfor %}
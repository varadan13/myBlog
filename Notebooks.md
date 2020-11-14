---
title: Notebooks
layout: page
permalink: /Notebooks/
---

{% for item in site.Notebooks %}
	{%- if item.title -%}
    <h1 class="page-heading"><a href = "{{ item.url }}">{{ item.title }}</a></h1>
	{%- endif -%}
	{%- if item.Description -%}
	<p>{{ item.Description }}</p>
	{%- endif -%}
	
{% endfor %}

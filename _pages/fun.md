---
layout: page
title: fun
permalink: /fun/
description: Some of the things that I do outside of data science!
nav: true
nav_order: 4
display_categories: [fun]
horizontal: false
---

<!-- pages/fun.md -->
<div class="fun">
{% if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized projects -->
  {% for category in page.display_categories %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>
  {% assign categorized_fun = site.fun | where: "category", category %}
  {% assign sorted_fun = categorized_fun | sort: "importance" %}
  <!-- Generate cards for each project -->
  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_fun %}
      {% include fun_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_fun %}
      {% include fun.liquid %}
    {% endfor %}
  </div>
  {% endif %}
  {% endfor %}

{% else %}

<!-- Display fun without categories -->

{% assign sorted_fun = site.fun | sort: "importance" %}

  <!-- Generate cards for each project -->

{% if page.horizontal %}

  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for item in sorted_fun %}
      {% include fun_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for item in sorted_fun %}
      {% include fun.liquid %}
    {% endfor %}
  </div>
  {% endif %}
{% endif %}
</div>

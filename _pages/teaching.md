---
layout: page
permalink: /teaching/
title: teaching
description: All about what I've taught and materials
nav: true
nav_order: 6
display_categories: [teaching assistant, tutoring]
horizontal: false
---

<!-- pages/teaching.md -->
<div class="teaching">
{% if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized teaching materials -->
  {% for category in page.display_categories %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>
  {% assign categorized_teaching = site.teaching | where: "category", category %}
  {% assign sorted_teaching = categorized_teaching | sort: "importance" %}
  <!-- Generate cards for each teaching entry -->
  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for item in sorted_teaching %}
      {% include teaching_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for item in sorted_teaching %}
      {% include teaching.liquid %}
    {% endfor %}
  </div>
  {% endif %}
  {% endfor %}

{% else %}

<!-- Display teaching materials without categories -->

{% assign sorted_teaching = site.teaching | sort: "importance" %}

  <!-- Generate cards for each teaching entry -->

{% if page.horizontal %}

  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for item in sorted_teaching %}
      {% include teaching_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for item in sorted_teaching %}
      {% include teaching.liquid %}
    {% endfor %}
  </div>
  {% endif %}
{% endif %}
</div>

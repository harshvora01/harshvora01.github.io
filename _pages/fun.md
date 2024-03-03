---
layout: page
title: Fun
permalink: /fun/
description:
nav: true
nav_order: 3
display_categories:
horizontal: false
---

<!-- pages/fun.md -->
<div class="fun">
{% if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized fun -->
  {% for category in page.display_categories %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>
  {% assign categorized_fun = site.fun | where: "category", category %}
  {% assign sorted_fun = categorized_fun | sort: "importance" %}
  <!-- Generate cards for each project -->
  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-2">
    {% for project in sorted_fun %}
      {% include fun_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="grid">
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
    <div class="row row-cols-2">
    {% for project in sorted_fun %}
      {% include fun_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="grid">
    {% for project in sorted_fun %}
      {% include fun.liquid %}
    {% endfor %}
  </div>
  {% endif %}
{% endif %}
</div>

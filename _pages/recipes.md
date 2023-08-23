---
layout: page
title: recipes
permalink: /recipes/
description: A list in no particular order or the things we tend to cook more often.
nav: true
nav_order: 2
display_categories: [fun]
horizontal: false
---

<!-- pages/recipes.md -->
<div class="recipes">
{%- if site.enable_recipes_categories and page.display_categories %}
  <!-- Display categorized projects -->
  {%- for category in page.display_categories %}
  <h2 class="category">{{ category }}</h2>
  {%- assign categorized_recipes = site.recipes | where: "category", category -%}
  {%- assign sorted_recipes = categorized_recipes | sort: "importance" %}
  <!-- Generate cards for each project -->
  {% if page.horizontal -%}
  <div class="container">
    <div class="row row-cols-2">
    {%- for recipe in sorted_recipes -%}
      {% include recipes_horizontal.html %}
    {%- endfor %}
    </div>
  </div>
  {%- else -%}
  <div class="grid">
    {%- for recipe in sorted_recipes -%}
      {% include recipes.html %}
    {%- endfor %}
  </div>
  {%- endif -%}
  {% endfor %}

{%- else -%}
<!-- Display projects without categories -->
  {%- assign sorted_recipes = site.recipes | sort: "importance" -%}
  <!-- Generate cards for each project -->
  {% if page.horizontal -%}
  <div class="container">
    <div class="row row-cols-2">
    {%- for recipe in sorted_recipes -%}
      {% include recipes_horizontal.html %}
    {%- endfor %}
    </div>
  </div>
  {%- else -%}
  <div class="grid">
    {%- for recipe in sorted_recipes -%}
      {% include recipes.html %}
    {%- endfor %}
  </div>
  {%- endif -%}
{%- endif -%}
</div>

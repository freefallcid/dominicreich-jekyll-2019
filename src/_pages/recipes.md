---
layout: page
permalink: /rezepte/
title: "Rezepte"
excerpt: "A collection of recipes that I find awesome"
last_modified_at: 
---

{% assign recipes = site.recipes |  sort: "date" | reverse %}

{{ page.excerpt | markdownify }}

<div class="gallery">
  {% for post in recipes %}
    {% include entry.html class="gallery-item" %}
  {% endfor %}
</div>

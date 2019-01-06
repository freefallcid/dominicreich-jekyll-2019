---
layout: page
permalink: /recipes/
title: "Recipes"
excerpt: "A collection of recipes that I find awesome"
# image:
#   path: &image /assets/images/
#   width: 1920
#   height: 793
#   feature: *image
last_modified_at: 2019-01-05T23:02:40+01:00
---

{% assign recipes = site.recipes |  sort: "order" %}

<div class="gallery">
  {% for post in recipes %}
    {% include entry.html class="gallery-item" %}
  {% endfor %}
</div>

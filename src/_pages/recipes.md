---
layout: page
permalink: /rezepte/
title: &title Rezepte
alt_title: *title
excerpt: &excerpt A collection of recipes that I find awesome
introduction: *excerpt
date: 2016-08-26
# last_modified_at: 
---

{% assign recipes = site.recipes |  sort: "date" | reverse %}

{{ page.excerpt | markdownify }}

<div class="gallery">
  {% for post in recipes %}
    {% include entry.html class="gallery-item" %}
  {% endfor %}
</div>

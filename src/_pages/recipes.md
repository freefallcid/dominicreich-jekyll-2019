---
layout: page
permalink: /rezepte/
title: &title Rezepte
excerpt: >
  Eine nette Ansammlung toller Rezepte (die ich nicht vergessen möchte).
# date: 
# last_modified_at: 
---

{% assign recipes = site.rezepte |  sort: "date" | reverse %}

{{ page.excerpt | markdownify }}

<div class="gallery">
  {% for post in recipes %}
    {% include entry.html class="gallery-item" %}
  {% endfor %}
</div>

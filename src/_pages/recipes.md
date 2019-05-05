---
layout: page
permalink: /rezepte/
title: &title Rezepte
excerpt: >
  Eine kleine Sammlung toller Rezepte. Die Rezepte sind in der Regel (auch wenn
  die Quellenangabe eventuell fehlt) nicht von mir -- du findest hier lediglich
  tolle Rezepte, die ich selbst verwende und toll finde.

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

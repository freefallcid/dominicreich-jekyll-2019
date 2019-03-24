---
layout: page
permalink: /rezepte/
title: &title Rezepte
excerpt: >
  Eine nette Ansammlung toller Rezepte (die ich besser nicht vergessen sollte).
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

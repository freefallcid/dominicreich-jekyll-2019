---
layout: page
permalink: /klamm/
title: "Hausbau Klamm"
excerpt: "Wichtiges und Nicht-Wichtiges zum Sammeln"
last_modified_at: 
sitemap: false
---

{% assign items = site.klamm |  sort: "date" | reverse %}

{{ page.excerpt | markdownify }}

<div class="gallery">
  {% for post in items %}
    {% include entry.html class="gallery-item" %}
  {% endfor %}
</div>

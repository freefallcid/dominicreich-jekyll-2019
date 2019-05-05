---
layout: page
permalink: /sitemap/
title: Sitemap
excerpt: Eine Auflistung aller verfügbaren Seiten auf dominicreich.com
date: 2016-08-26
last_modified_at: 2019-05-05T19:41:47+02:00
toc: true
---

Eine Auflistung aller Artikel und Seiten auf dieser Webseite. Für Such-Roboter
gibt es eine [XML-Version](/sitemap.xml).

## Seiten

- [Über mich](/about/)
- [Kontakt](/kontakt/)
- [Häufig gestellte Fragen](/faqs/)
- [Unterstütze mich](/support/)
- [Terms and policies](/terms/)
- [Wake Island Warriors](/wiw/)
- [Tag-Index](/tag/)

## [Blog-Artikel](/artikel/)

<ul>
  {% for post in site.categories.artikel %}
    {% include post-list.html %}
  {% endfor %}
</ul>

## [Rezepte](/rezepte/)

<ul>
  {% for post in site.rezepte %}
    {% include post-list.html %}
  {% endfor %}
</ul>

## [Notizen](/notizen/)

<ul>
  {% for post in site.categories.notizen %}
    {% include post-list.html %}
  {% endfor %}
</ul>

## [Portfolio](/portfolio/)

{% comment %}
### [Footografie]({% link _portfolio/photography.md %})

<ul>
  {% for post in site.categories.fotografie %}
    {% include post-list.html %}
  {% endfor %}
</ul>

### [Zeitraffer-Videos]({% link _portfolio/timelapse.md %})

<ul>
  {% for post in site.categories.zeitraffer %}
    {% include post-list.html %}
  {% endfor %}
</ul>

### [Software]({% link _portfolio/software.md %})

<ul>
  {% for post in site.categories.software %}
    {% include post-list.html %}
  {% endfor %}
</ul>
{% endcomment %}

<ul>
  {% comment %}{% assign posts = site.portfolio | sort: "order" | reverse %}{% endcomment %}
  {% assign posts = site.portfolio | sort %}
  {% for post in posts %}
    {% include post-list.html %}
  {% endfor %}
</ul>

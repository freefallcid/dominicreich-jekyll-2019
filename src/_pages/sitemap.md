---
layout: page
permalink: /sitemap/
title: Sitemap
excerpt: Eine Auflistung aller verfügbaren Seiten auf dominicreich.com
date: 2016-08-26
last_modified_at: 2019-03-17T22:15:31+01:00
toc: true
---

Eine Auflistung aller Artikel und Seiten auf dieser Webseite. Für robots gibt es
eine [XML-Version](/sitemap.xml).

## Seiten

- [Über mich](/ueber-mich/)
- [Kontakt](/kontakt/)
- [Frequently asked questions](/faqs/)
- [Show your support](/support/)
- [Terms and policies](/terms/)
- [Wake Island Warriors](/wiw/)
- [Tag-Index](/tag/)

## [Blog-Artikel](/artikel/)

<ul>
  {% for post in site.categories.articles %}
    {% include post-list.html %}
  {% endfor %}
</ul>

## [Rezepte](/rezepte/)

<ul>
  {% for post in site.recipes %}
    {% include post-list.html %}
  {% endfor %}
</ul>

## [Notizen](/notizen/)

<ul>
  {% for post in site.categories.notes %}
    {% include post-list.html %}
  {% endfor %}
</ul>

## [Portfolio](/portfolio/)

{% comment %}
### [Footografie]({% link _portfolio/photography.md %})

<ul>
  {% for post in site.categories.photography %}
    {% include post-list.html %}
  {% endfor %}
</ul>

### [Zeitraffer-Videos]({% link _portfolio/timelapse.md %})

<ul>
  {% for post in site.categories.timelapse %}
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
  {% assign posts = site.portfolio | sort: "order" | reverse %}
  {% for post in posts %}
    {% include post-list.html %}
  {% endfor %}
</ul>

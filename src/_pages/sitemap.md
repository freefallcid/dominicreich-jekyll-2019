---
layout: page
permalink: /sitemap/
title: "Sitemap"
excerpt: "An index of all the pages found on dominicreich.com"
last_modified_at: 2019-01-05T23:00:11+01:00
toc: true
---

A hierarchical breakdown of all the sections and pages found on the site. For you robots out there, here is an [XML version](/sitemap.xml) available for your crawling pleasure.

## Pages

- [About](/about/)
- [Contact](/contact/)
- [Frequently asked questions](/faqs/)
- [Show your support](/support/)
- [Terms and policies](/terms/)
- [Wake Island Warriors](/wiw/)
- [Tag index](/tag/)

## [Blog articles](/articles/)

<ul>
  {% for post in site.categories.articles %}
    {% include post-list.html %}
  {% endfor %}
</ul>

## [Recipes](/recipes/)

<ul>
  {% for post in site.recipes %}
    {% include post-list.html %}
  {% endfor %}
</ul>

## [Today I learned](/til/)

<ul>
  {% for post in site.categories.til %}
    {% include post-list.html %}
  {% endfor %}
</ul>

## [Portfolio work](/work/)

{% comment %}
### [Photography]({% link _work/photography.md %})

<ul>
  {% for post in site.categories.photography %}
    {% include post-list.html %}
  {% endfor %}
</ul>

### [Timelapse videos]({% link _work/timelapse.md %})

<ul>
  {% for post in site.categories.timelapse %}
    {% include post-list.html %}
  {% endfor %}
</ul>

### [Software]({% link _work/software.md %})

<ul>
  {% for post in site.categories.software %}
    {% include post-list.html %}
  {% endfor %}
</ul>
{% endcomment %}

<ul>
  {% assign posts = site.work | sort: "order" | reverse %}
  {% for post in posts %}
    {% include post-list.html %}
  {% endfor %}
</ul>

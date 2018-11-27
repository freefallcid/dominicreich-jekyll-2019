---
layout: page
permalink: /sitemap/
title: "Sitemap"
excerpt: "An index of all the pages found on mademistakes.com"
last_modified_at: 2018-12-08 23:33:27
---

A hierarchical breakdown of all the sections and pages found on the site. For you robots out there, here is an [XML version](/sitemap.xml) available for your crawling pleasure.

## Pages

- [About](/about/)
- [Contact](/contact/)
{% comment %}- [Frequently asked questions](/faqs/){% endcomment %}
- [Show your support](/support/)
- [Terms and policies](/terms/)
- [Style guide](/style-guide/)
- [Tag index](/tag/)

## [Blog articles](/articles/)

<ul>
  {% for post in site.categories.articles %}
    {% include post-list.html %}
  {% endfor %}
</ul>

## [Today I learned](/til/)

<ul>
  {% for post in site.categories.til %}
    {% include post-list.html %}
  {% endfor %}
</ul>

<h2><a href="/howto/">Howto Collection</a></h2>
<ul>
  {% for post in site.categories.howto %}
    {% include post-list.html %}
  {% endfor %}
</ul>

## [Portfolio work](/work/)

<ul>
  {% for post in site.work %}
    {% include post-list.html %}
  {% endfor %}
</ul>

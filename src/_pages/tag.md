---
layout: archive
permalink: /tag/
title: Tag-Archiv
date: 2016-08-26
last_modified_at: 2019-03-17T22:10:12+01:00
excerpt: Ein nach Tags sortiertes Archiv meiner Beiträge
---

Ein Archiv von {{ site.posts | size }} Beiträgen, aufgelistet nach den folgenden
{{ site.tags | size }} Tags.

<div class="entries__columns">
  <h2 class="title">Nach Tags anzeigen</h2>
  <ul>
    {% assign sorted_tags = site.tags | sort_tags_by_name %}
    {% for tag in sorted_tags %}
      <li>
        <a href="/tag/{{ tag[0] | replace:' ','-' | downcase }}/">
          <strong>{{ tag[0] }}</strong> <span class="count">{{ tag[1] }}</span>
        </a>
      </li>
    {% endfor %}
  </ul>
</div>

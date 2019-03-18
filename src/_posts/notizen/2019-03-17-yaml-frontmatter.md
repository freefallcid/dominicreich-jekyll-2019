---
title: YAML-Frontmatter
excerpt: Eine Seite mit aktuell gehaltenen Frontmatter-Informationen.
# image:
#   path: &image /assets/images/.jpg
#   feature: *image
#   width: 1920
#   height: 800
#   caption: "[Foto von **Unbekannt** via Unsplash](https://)"
categories: [notizen]
tags: [yaml]
toc: true
# support: true
# comments: true
# comments_locked: true
# published: false
# last_modified_at: 
---

Ich möchte hier Informationen zu den verschiedenen Möglichkeiten in Jekyll zum
Thema YAML-Frontmatter speichern.

{% notice info %}
Diese Notiz wird von Zeit zu Zeit aktualisiert.
{% endnotice %}

## Die rechte Spitzklammer `>`

Die rechte Spitzklammer sorgt dafür, dass der Inhalt der nachfolgenden,
eingerückten Zeilen ohne Zeilenumbruch verwendet werden kann. Es wird nur ein
Paragraf erzeugt und alle Zeilenumbrüche entfernt. [Quelle][1]

```yaml
---
excerpt: >
  Zeile 1 des excerpts
  Zeile 2 des excerpts
---
```

## Die Pipe `|`

: Die Pipe funktioniert wie die rechte Spitzklammer, jedoch werden die
Zeilenumbrüche erhalten. Dies macht es einfach Code-Beispiele zu speichern.
[Quelle][1]

```yaml
---
excerpt: |
  <?php
    phpinfo();
  ?>
---
```

[1]: https://idratherbewriting.com/documentation-theme-jekyll/mydoc_yaml_tutorial#example-2-line-breaks

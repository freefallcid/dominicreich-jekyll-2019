---
title: YAML-Frontmatter
excerpt: Eine Seite mit aktuell gehaltenen Frontmatter-Informationen.
categories: [notizen]
tags: [yaml]
toc: true
last_modified_at: 2019-07-29T16:51:13+02:00
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

Die Pipe funktioniert wie die rechte Spitzklammer, jedoch werden die
Zeilenumbrüche erhalten. Dies macht es einfach Code-Beispiele zu speichern.
[Quelle][1]

``` yaml
introduction: |
  Oder etwa um Listen einzubinden:

  - Punkt 1
  - Punkt 2
  - Punkt 3
    - Unterpunkt 1
    - Unterpunkt 2
```

[1]: https://idratherbewriting.com/documentation-theme-jekyll/mydoc_yaml_tutorial#example-2-line-breaks

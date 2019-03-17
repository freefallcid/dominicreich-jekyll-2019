---
title: Partitiontabelle sichern
excerpt: >
 Erstelle eine exakte Kopie der Partitiontabelle und kopiere diese auf eine
 weitere (gleich große) Festplatte.
tags: [terminal, linux, til]
# last_modified_at: 2018-01-30T20:49:34+01:00
categories: [notes]
---

Erstelle eine exakte Kopie der Partitiontabelle mit dem Tool
[sfdisk](https://github.com/karelzak/util-linux).

{% notice danger %}
Verwende diese Methode nur mit **MBR**-Partitionstabellen.
{% endnotice %}

Speichern der Tabelle in einer Textdatei.

``` bash
sfdisk -d /dev/sda > /root/sda.backup.txt
```

Zum schreiben auf eine neue Festplatte sollte diese dieselbe Geometrie aufweisen.

``` bash
sfdisk /dev/sda < /root/sda.backup.txt
```

Das war's auch schon.

**Nicht vergessen:** Nach dem Schreiben der Tabelle müssen die erstellten
Partitionen jedoch noch mit dem jeweiligen Dateisystem formatiert werden.

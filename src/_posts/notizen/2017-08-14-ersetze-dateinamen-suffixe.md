---
title: Ersetze mehrere Dateinamen-Suffixe auf einmal
excerpt: Ändere alle Dateinamen-Suffixe in einem Verzeichnis in der Konsole.
tags: [linux, macos, terminal, til]
# last_modified_at: 2018-01-30T20:30:24+01:00
categories: [notizen]
---

Hier notiert weil ich mir die Syntax von `basename` noch nie merken konnte...

``` bash
for i in *.eml; do mv "$i" $(basename -s .eml "$i").txt; done
```

Obiger Einzeiler nennt alle `eml`-Dateien in `txt`-Dateien um.

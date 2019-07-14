---
title: Windows certutil
excerpt: >
  Fügt ein Zertifikat dem Windows Zertifikatsspeicher hinzu.
  In der Eingabeaufforderung.
tags: [windows, terminal, til]
categories: [notizen]
---

Ein schneller Weg um ein Zertifikat in der Eingabeaufforderung zu importieren.

Eine [Admin-Shell](https://google.com/search?q=how+to+open+an+admin+shell+windows)
wird dazu benötigt.

``` terminal
certutil -f -addstore CA "\\domain\sysvol\domain\scripts\path\certificate.crt"
```

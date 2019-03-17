---
title: Windows certutil
excerpt: >
  Fügt ein Zertifikat dem Windows Zertifikatsspeicher hinzu.
  In der Eingabeaufforderung.
tags: [windows, terminal, til]
# last_modified_at: 2018-01-29T23:59:49+01:00
categories: [notes]
---

Ein schneller Weg um ein Zertifikat in der Eingabeaufforderung zu importieren.

Eine [Admin-Shell](https://google.com/search?q=how+to+open+an+admin+shell+windows)
wird dazu benötigt.

``` terminal
certutil -f -addstore CA "\\domain\sysvol\domain\scripts\path\certificate.crt"
```

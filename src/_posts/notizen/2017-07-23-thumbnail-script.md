---
title: Thumbnails in der Konsole erzeugen
excerpt: >
  Erzeuge schnell einen 100%-igen 300&times;300-Crop aus der Mitte eines Bildes.
  Verwendet ImageMagick.
tags: [linux, macos, terminal, photography, til]
# last_modified_at: 2018-01-30T00:16:55+01:00
categories: [notizen]
---

Das Script generiert ein 300&times;300-Pixel Vorschaubild.

Verwende das Script mit zwei Argumenten. Das erste Argument `$1` sollte das
Original-Bild sein. Das zweite Argument `$2` sollte das Ausgabe-Bild sein.

``` bash
#!/bin/bash
convert $1 -gravity Center -crop 50x50%+0+0 -resize 300x -fuzz 15% +repage $2
```

Das Script kann später in etwa so ausgeführt werden:

``` terminal
$ ./script Image1.jpg Cropped-1.jpg
```

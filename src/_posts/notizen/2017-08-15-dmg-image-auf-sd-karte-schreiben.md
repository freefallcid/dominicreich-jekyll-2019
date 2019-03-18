---
title: Schreibe ein `dmg`-Image auf eine SD-Karte
excerpt: Ein `dmg`-Image soll auf eine SD-Karte geschrieben werden.
tags: [macos, terminal, til]
# last_modified_at: 2018-01-30T21:15:35+01:00
categories: [notizen]
---

Auch das kann ich mir nicht merken und muss es ständig nachlesen, wenn ich es
wieder brauche.

``` terminal
$ hdiutil convert backup.dmg -format UDTO -o raw-image.img
$ mv raw-image.img.cdr raw-image.img
$ sudo dd if=raw-image.img bs=1m of=/dev/rdisk3
```

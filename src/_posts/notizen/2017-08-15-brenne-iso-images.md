---
title: Schreibe ISO-Images auf einen Rohling
excerpt: >
  Schreibe ein Disk-Image auf einen CD- oder DVD-Rohling. Im Terminal
  unter MacOS.
tags: [macos, terminal, til]
categories: [notizen]
---

Weil ich mir diesen total einfachen Befehl nicht merken kann.

Es ist egal ob das zu beschreibende Medium ein CD-ROM-Rohling oder ein DVD-Rohling
ist -- allerdings sollte es selbsterklärend sein, dass das Disk-Image auf den
Rohling passen sollte.

``` terminal
$ hdiutil burn ~/Downloads/image.iso
```

Einfach, oder?

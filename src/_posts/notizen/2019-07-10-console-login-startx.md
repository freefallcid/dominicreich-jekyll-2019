---
title: X direkt nach Konsolenlogin starten
excerpt: >
  Starte X gleich nach dem Login auf einer virtuellen Konsole (vtty, tty).
categories: [notizen]
tags: [X11, zsh, linux, freebsd]
---

Nach dem Login auf einer vorher definierten (siehe unten) virtuellen Konsole
kannst du X automatisch starten. Die dafür zu verwendende Konsole kannst du
selbst bestimmen.

Inhalt der Datei `.zlogin` im Heimverzeichnis:

``` bash
if [[ -z ${DISPLAY} && ${TTY} == "/dev/tty1" ]]; then
  exec startx -- vt1
fi
```

{% notice info %}
**Info:** Die Namen der Terminals können dabei variieren. Unter Gentoo Linux
heißen diese zum Beispiel `tty1`, `tty2` und so weiter. Unter FreeBSD heißen
diese (glaub' ich) `ttyv0`, `ttyv1` etc.
{% endnotice %}

### Weitere Informationen

- <https://www.howtoforge.de/anleitung/linux-tty-befehl/>
- <https://askubuntu.com/questions/66195/what-is-a-tty-and-how-do-i-access-a-tty#answers>
- <https://www.freebsd.org/doc/de_DE.ISO8859-1/books/handbook/consoles.html>

---
title: X direkt nach Konsolenlogin starten
excerpt: >
  Starte X gleich nach dem Login auf einer virtuellen Konsole (vtty, tty).
# image:
#   path: &image /assets/images/$3.jpg
#   feature: *image
#   width: ${4:1920}
#   height: ${5:800}
#   caption: "[Foto von **${6:Unbekannt}** via ${7:Unsplash}](${8:https://})"
categories: [notizen]
tags: [X11, linux, freebsd]
# toc: true
# support: true
# comments: true
# comments_locked: true
# published: false
# last_modified_at: 
---

Nach dem Login auf einer vorher definierten (siehe unten) virtuellen Konsole
kannst du X automatisch starten. Die dafür zu verwendende Konsole kannst du
selbst bestimmen.

Inhalt der Datei `.zlogin` im Heimverzeichnis:

```
if [[ -z ${DISPLAY} && ${TTY} == "/dev/ttyv0" ]]; then
  exec startx -- vt1
fi
```

`/dev/ttyv0` ist dabei das Terminal, auf dem die Anmeldung erfolgen soll. Nach
erfolgreichem Login wird auf `vt1` ein X-Server gestartet.

{% notice info %}
**Info:** Der Name der virtuellen Konsolen kann dabei variieren. Unter Kali Linux
heißen diese zum Beispiel `tty1`, `tty2` und so weiter...
{% endnotice %}

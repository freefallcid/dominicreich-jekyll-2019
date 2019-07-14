---
title: Ports unter FreeBSD verwalten
excerpt: |
  Verwalte installierte Ports unter FreeBSD.
categories: [notizen]
tags: [freebsd, ports]
toc: true
support: true
---

## Neue Ports installieren

In der Regel installiere ich neue Ports im klassischen Stil: ich öffne ein
Terminal und wechsle zum Verzeichnis `/usr/ports`. Von dort aus lassen sich alle
Ports ganz schnell durchsuchen, etwa mit `make search` oder über
`echo */$portname`. Wenn der benötigte Port gefunden wurde wechsle ich in dessen
Verzeichnis und starte meistens ein `make config-recursive`. Danach kann der
Port auch schon mit `make install clean` installiert werden.

## Ports aktualisieren

Es gibt viele Tools, die einem das Management mit den Ports vereinfachen. Ich
habe bislang nur wenige davon getestet. Vorweg genommen sei, dass portmaster als
Bash-Skript kommt und portupgrade ruby-Abhängigkeiten hat.

Egal welches Tool man sich für die Paketverwaltung aussucht, den Ports-Tree sollte
man in jedem Fall aktuell halten. Das geht mit Bordmitteln:

``` terminal
# portsnap fetch update
```

Nach einer (Neu-)Installation von FreeBSD wird der Ports-Tree mittels
`portsnap fetch extract` aktualisiert.

Dann sehen wir uns kurz an, für welche Ports es neue Pakete gibt:

``` terminal
# pkg version -vl\<
de-libreoffice-6.0.7    <   needs updating (index has 6.2.2)
gqrx-2.11.5_6,1         <   needs updating (index has 2.11.5_7,1)
vlc-3.0.6_8,4           <   needs updating (index has 3.0.6_12,4)
yarn-1.13.0             <   needs updating (index has 1.15.2)
```
Wenn man der Spitzklammer keinen Backslasch voranstellen will, kann man den
Befehl auch anders schreiben[^backslash]: `pkg version -vl"<"`. Jetzt kann das Update starten:

[^backslash]: Da die Spitzklammer normalerweise dazu verwendet wird, Dateien umzuleiten, sollte die Spitzklammer hier entweder in Gänsefüßchen stehen oder ein Backslasch vorangestellt sein, damit die Spitzklammer dem Programm (`pkg`) als Argument übergeben wird. [Lese mehr](https://scriptingosx.com/2017/08/special-characters/).

### Mit portupgrade

``` terminal
# portupgrade -acDrv
```

{% notice %}
| :-: | :----------- |
| `a`   | Führt die Aktion für alle installierten Ports aus. |
| `c`   | Führt zuerst `make config-conditional` für jeden Task aus. |
| `D`   | Löscht fehlgeschlagene Distributionsdateien und versucht es erneut, falls die Dateiprüfung fehlschlägt. |
| `r`   | Inkludiere auch die Abhängigkeiten der Pakete. |
| `v`   | Verbose. Mehr Ausgabe, mehr Information. |
{% endnotice %}

### Mit portmaster

``` terminal
# portmaster -na
```

{% notice %}
| :-: | :----------- |
| `a`   | prüft alle Ports, aktualisiert diese, falls nötig |
| `n`   | durchläuft alle Aktionen, aber kompiliert oder installiert keine Ports |
{% endnotice %}

{% comment %}
  portupgrade -rR *

  portversion |grep \<

  portupgrade -a -m BATCH=yes
  wie etwa
  portsnap fetch update && portupgrade -a -m BATCH=yes
{% endcomment %}

---
title: Ports unter FreeBSD verwalten
excerpt: |
  Verwalte installierte Ports unter FreeBSD.
# image:
#   path: &image /assets/images/freebsd.jpg
#   feature: *image
#   width: 1920
#   height: 800
#   caption: "[Foto von **Unbekannt** via Unsplash](https://)"
categories: [notizen]
tags: [freebsd, ports]
# toc: true
support: true
# comments: true
# comments_locked: true
# published: false
# last_modified_at: 
---

## Ports aktualisieren

Als erstes wird der Ports-Tree aktualisiert.

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

[^backslash]: Da die Spitzklammer normalerweise dazu verwendet wird, Dateien umzuleiten, sollte die Spitzklammer hier entweder in Gänsefüßchen stehen oder ein Backslasch vorangestellt sein, damit die Spitzklammer dem Programm (`pkg`) als Argument übergeben wird.

``` terminal
# portupgrade -acDrv
```

{% notice %}
#### Was bedeuten die Argumente?

| :-: | :----------- |
| a   | Führt die Aktion für alle installierten Ports aus. |
| c   | Führt zuerst `make config-conditional` für jeden Task aus. |
| D   | Löscht fehlgeschlagene _Distfiles_ und versucht es erneut, falls die Dateiprüfung fehlschlägt. |
| r   | Inkludiere auch die Abhängigkeiten der Pakete. |
| v   | Mehr Ausgabe, mehr Information. |
{% endnotice %}


{% comment %}
  portupgrade -rR *

  portversion |grep \<

  portupgrade -a -m BATCH=yes
  wie etwa
  portsnap fetch update && portupgrade -a -m BATCH=yes
{% endcomment %}

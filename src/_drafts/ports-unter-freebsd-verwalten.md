---
title: Ports unter FreeBSD verwalten
excerpt: |
  Verwalte installierte Ports unter FreeBSD.
image:
  path: &image /assets/images/freebsd.jpg
  feature: *image
  width: 1920
  height: 800
  caption: "[Foto von **Unbekannt** via Unsplash](https://)"
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
chromium-72.0.3626.121_1           <   needs updating (index has 73.0.3683.103_1)
de-libreoffice-6.0.7               <   needs updating (index has 6.2.2)
gnuradio-3.7.13.4_3                <   needs updating (index has 3.8.g20190309_2)
gqrx-2.11.5_6,1                    <   needs updating (index has 2.11.5_7,1)
gr-osmosdr-0.1.4.99_4,1            <   needs updating (index has 0.1.4.99_6,1)
vlc-3.0.6_8,4                      <   needs updating (index has 3.0.6_12,4)
wsjtx-2.0.0_1                      <   needs updating (index has 2.0.1_1)
yarn-1.13.0                        <   needs updating (index has 1.15.2)
```

Jetzt kann das Update starten:

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

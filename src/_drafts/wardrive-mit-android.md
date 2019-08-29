---
title: Wardrive mit Android
excerpt: >
  Erstens vergesse ich die Befehle an sich und zweitens kommt mir `giskismet`
  spanisch vor
categories: [notizen]
tags: [linux, android]
# toc: true
# support: true
# comments: true
# comments_locked: true
# published: false
# last_modified_at: 
---

1. Starte die BlueNMEA-App auf dem Smartphone
2. Portweiterleitung einrichten
   
   ``` bash
   adb forward tcp:4352 tcp:4352
   ```

   Eventuell benötigt man 32bit-Bibliotheken
   
   ``` bash
   dpkg --add-architecture i386 && apt-get update && apt-get install ia32-libs lib32ncurses5
   ```
3. GPS Daemon starten

   ``` bash
   gpsd -N -n -D5 tcp://localhost:4352
   ```
4. Daten via Giskismet holen und exportieren
   
   ``` bash
   giskismet -x Kismet-DATE***.netxml
   ```

   ``` bash
   giskismet -q "SELECT * FROM WIRELESS" -o output.kml
   ```
5. Die exportierte kml-Datei kann mit mit Google Earth ansehen

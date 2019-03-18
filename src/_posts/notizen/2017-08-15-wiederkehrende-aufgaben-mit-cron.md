---
title: Wiederkehrende Aufgaben mit cron ausführen
excerpt: Führe ein Skript am ersten Samstag in jedem zweiten Monat aus.
tags: [linux, macos, cron, til]
# last_modified_at: 2018-02-01T23:12:06+01:00
categories: [notizen]
repo: staubsauger-erinnerung
---

Vorweg die Hintergrundgeschichte: wir hatten ein Staubsauger-System im Haus, das
im Schnitt alle zwei Monate gereinigt werden musste. Da wir uns den Termin nur
schlecht merken konnten habe ich an dieser Lösung gebastelt.

## Erste Konfiguration

Diese Konfiguration ist nicht mehr aktuell und nicht mehr in Verwendung.

``` bash
30  3 1-7 1,3,5,7,9,11 Sat /Users/dominic/bin/notify.sh
```

Das Skript `/Users/dominic/bin/notify.sh` wird ausgeführt:

- im Monat `1,3,4,7,9,11`
- an den Tagen `1–7`
- falls der Tag ein `Sat` ist (ein Samstag)
- um 03:30 Uhr

Das lief ganz gut, jedoch verwende ich derzeit eine andere Konfiguration -- die
mir die Möglichkeit bietet, einen Report zu versenden, auch wenn das Skript
eigentlich keine Aktion ausführen würde.

Würde ich das so laufen lassen, würde das Skript nur am ersten Samstag in jedem
zweiten Monat ausgeführt werden. Ich möchte jedoch, dass das Skript tatsächlich
an jedem Samstag ausgeführt wird, aber nur am ersten in jedem zweiten Monat einen
Bericht sendet.

Deshalb verwende ich nun folgende (ähnliche) Konfiguration.

## Zweite Konfiguration

Diese Konfiguration war zueletzt auf meinem FreeBSD-Server[^server] aktiv.

[^server]: `poison-ivy.dominicreich.com`

``` bash
30  3 * 1,3,5,7,9,11 6  /Users/dominic/bin/notify.sh
```

Diese Version lässt das Skript an jedem Samstag (`6`) in den Monaten `1,3,5,7,9,11`
ausführen; das Skript checkt selbst ob es der erste Samstag im jeweiligen Monat ist.

Damit erhalte ich an jedem Samstag in den oben genannten Monaten einen Bericht
über die Ausführung des Skriptes. Es lässt sich dadurch einfach feststellen, ob
das Skript noch korrekt ausgeführt wird oder nicht.

Nachstehend ein Beispiel für die Routine im Skript, die feststellt, ob es die
Aktion ausführen soll oder nicht.

``` bash
# get the actual day in numbers form
TODAY="`date +%_d`"

# check if its the first saturday (the first saturday must be one of day 1-7)
if [ $TODAY -gt "7" ]; then
  # that means, $TODAY is greater than 7. Send a negative report and quit the script.
  ACTION='NO'
  # set a variable or silently quit the program
  #return 0
else
  # execute the final action/function
  # set special variables etc.
  ACTION='YES'
fi
# you can now decide what to do. read content of $ACTION and execute the
# correct functions here depending on the valued of $ACTION that we have set in
# our if-clause above. Or just quite the script silently in the proper branch
# of that if-clause.
```

Wie gesagt, das Skript läuft derzeit auf meinem NAS zuhause und wurde daher
an diese Umgebung angepasst. Eine aktuelle Fassung des
[Skriptes]({{ site.author.github }}/{{ page.repo }}) kann auf Github
nachgelesen werden.

---
title: WiW trial handout text generator
# excerpt: 
# image:
#   path: &image "/assets/images/.jpg"
#   feature *image
#   width: 1600
#   height: 640
repo: wiw-trial-handout
categories: [software]
tags: [visual basic, wiw]
toc: true
# last_modified_at: 
---

Als wir noch [im Clan Battlefield 2 spielten]({% link _pages/wiw.md %}) rekrutierten
wir neue Mitglieder. Als wir die Aufnahme ins Trial-Programm[^trial] angekündigt
haben schrieben wir ständig ähnlich klingende Beiträge. Eigentlich kopierten wir
nur die alten Beiträge von bereits aufgenommenen Mitgliedern und änderten die
Namen bzw. Zeiten.

[^trial]: Im Trial-Programm musste der Rekrut im Forum und am Gameserver aktiv sein. Wir haben uns sein Verhalten im Forum und seine Spielweise am Server angesehen und nach angemessener Zeit ein Urteil über seine Aufnahme in den Clan gefällt.

Dieses Tool generiert nun ständig denselben Text und füllt Namen und Zeiten für
den Benutzer aus.

{% figure caption:"Ein Beispiel: Tippe den Namen ein und markiere die Zeitspanne." %}
  ![Einstellungen Beispiel-Bildschirmfoto](/assets/images/wiw-trial-handout.jpg)
{% endfigure %}

{% figure caption:"Die Ausgabe des Textes erfolgt umgehend. Kopiere ihn ins Forum." %}
  ![Ausgabe Beispiel-Bildschirmfoto](/assets/images/wiw-trial-handout-2.jpg)
{% endfigure %}

## Verwendung

Fülle den Namen des neuen Mitglieds aus, wähle, ob der Rekrut ein "Cut-Off"[^cutoff]
bekommen soll und markiere die Zeitspanne am Kalender mit der Maus. Klicke auf
<kbd>Generate Text</kbd> und im Handumdrehen kannst du den ausgegebenen Text
kopieren.

[^cutoff]: Ein Cut-Off ist die Möglichkeit, die Trial-Zeitspanne zu verkürzen. In der Regel wird dies nur Rekruten gewährt, die vorher schon am Gameserver bekannt sind und regelmäßig spielen.

## Installation und Quellcode

Du kannst den Code gerne [forken](https://help.github.com/en/articles/fork-a-repo)
und an deine eigenen Bedürfnisse anpassen.

<p markdown="0">
  <a href="https://tools.dore.pw/WiW-Trial-Handout-Generator/setup.exe" class="btn"
  title="Führe das Setup-Programm aus und installiere das Tool in Windows">Installieren</a>
  <a href="{{ site.author.github }}/{{ page.repo }}"
  class="btn" title="Öffne das Repository auf Github">Quellcode</a>
  <a href="{{ site.author.github }}/{{ page.repo }}/issues"
  class="btn">Github Issues</a>
</p>

## Lizenz

Das Tool wird unter der
[MIT License](https://github.com/{{ page.github_username }}/{{ page.repo }}/blob/master/LICENSE)
vertrieben.

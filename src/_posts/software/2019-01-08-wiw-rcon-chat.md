---
title: WiW RCON Chat
excerpt: 
# image:
#   path: &image "/assets/images/.jpg"
#   feature *image
#   width: 1600
#   height: 640
repo: wiw-rcon-chat
categories: [software]
tags: [visual basic, wiw]
toc: true
last_modified_at: 2019-01-08T14:14:12+01:00
---

Das Tool sortiert die Chatlogs vom RCON-Service [rconnet.de](http://rconnet.de/).
Die dortigen Logfiles mussten immer von unten nach oben gelesen werden. Mein Tool
dreht diese Reihenfolge um und filtert nach angegebenen Filtern aus. Ebenso lassen
sich zusätzlich alle Servermeldungen ausblenden.

{% figure caption:"Ausschneiden & Einfügen -- es ist wirklich so einfach." %}
  ![Beispiel-Bildschirmfoto](/assets/images/wiw-rcon-chat.jpg)
{% endfigure %}

## Verwendung

Kopiere den ganzen Chatlog von rconnet.de und füge ihn ins obere Textfeld ein.
Setze die gewünschten Filter und klicke auf <kbd>Sort and Filter</kbd>.

## Installation und Quellcode

Du kannst den Code gerne [forken](https://help.github.com/en/articles/fork-a-repo)
und an deine eigenen Bedürfnisse anpassen.

<p markdown="0">
  <a href="https://tools.dore.pw/WiW-RCON-Chat/setup.exe" class="btn"
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

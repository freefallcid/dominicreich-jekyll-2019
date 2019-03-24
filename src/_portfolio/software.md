---
layout: archive
title: Software
excerpt: Einige Tools, die ich in Visual Basic geschrieben habe.
#introduction: ""
image: 
  path: &image /assets/images/coding-924920_1920.jpg
  width: 1920
  height: 793
  feature: *image
  # caption: [Foto von **StockSnap** via Pixabay](https://pixabay.com/photo-924920/)
#tags: [visual basic, .net, wiw]
work: Software development
date: 2016-08-26
last_modified_at: 2019-03-17T19:59:44+01:00
order: 3
---

Einige meiner Tools, die eventuell hilfreich sein könnten :wink:.

{% notice %}
#### Ein paar Infos gleich vorweg

- Die Oberfläche einiger Tools ist in englisch gehalten, anderer wiederum in 
  deutsch.
- Die Tools werden unter der [MIT-Lizenz](#lizenz) veröffentlicht (außer FEWO
  Preiskalkulation).
- Die meisten Tools verwenden das
  [.NET Framework 4.5](https://www.microsoft.com/de-at/download/details.aspx?id=30653).
  FEWO Preiskalkulation verwendet
  [4.5.2](https://www.microsoft.com/de-at/download/details.aspx?id=42643).
- Die Tools verwenden das "neuartige" Design von Windows -- die Bildschirmfotos
  wurden allerdings ohne diesem gemacht. Retro und so...
- Ich bin kein besonders guter Programmieren, weshalb durchaus Fehler im Code
  vorhanden sein werden. Solltest du Fehler finden und/oder beheben, so lass es
  mich bitte wissen -- ich würde meine Tools auch gerne erweitern bzw. sicherer
  machen.
{% endnotice %}

## [MD5 Converter]({% post_url software/2019-01-05-md5converter %})

Mit diesem Tool lässt sich ein im Textfeld eingegebener Text in Echtzeit in einen
MD5-Hash umwandeln.

{% figure caption:"Der Hash wird generiert während du den Text eingibst." %}
  ![Beispiel-Bildschirmfoto](/assets/images/md5convert.jpg)
{% endfigure %}
{:.gallery-2-col}

## [Leitungslängenberechnung]({% post_url software/2019-01-07-leitungslaengenberechnung %})

Dieser kleine Helfer kalkuliert den Mindestquerschnitt einer Ader eines Kabels
in der Gebäudeinstallation. Es berücksichtigt **österreichisches Vorschriften**.

{% figure caption:"Werte eingeben und Ergebnisse ablesen. Easy, oder?" %}
  ![Beispiel-Bildschirmfoto](/assets/images/leitungslaengenberechnung.jpg)
{% endfigure %}
{:.gallery-2-col}

## FEWO Preiskalkulation

At version 2. This app lets you quickly calculate a usual overnight stay. Or a holiday. With or without pets. You can set your own values for different situations (summer/winter; how many people; with kids) and so on.

{% figure caption:"The tool in action. Select the time on the calendar and fill out the fields on the left side. It calculates different things on the fly." %}
  ![Example screenshot](/assets/images/fewo-preis.jpg)
{% endfigure %}
{:.gallery-2-col}

The tool was built for my parents---because of that it is made to fit their needs. You might fork the repository and change whatever is needed to fit your needs.

{% comment %}
<p markdown="0">
  <a href="https://tools.dore.pw/Fewo-Preis/setup.exe" class="btn">Setup</a>
  <a href="https://github.com/freefallcid/Preiskalkulation-2" class="btn">Source code</a>
  <a href="https://github.com/freefallcid/Preiskalkulation-2/issues" class="btn">Issues</a>
</p>
{% endcomment %}

## [WiW RCON Chat]({% post_url software/2019-01-08-wiw-rcon-chat %})

Das Tool sortiert die Chatlogs vom RCON-Service [rconnet.de](http://rconnet.de/).
Die dortigen Logfiles mussten immer von unten nach oben gelesen werden. Mein Tool
dreht diese Reihenfolge um und filtert nach angegebenen Filtern aus. Ebenso lassen
sich zusätzlich alle Servermeldungen ausblenden.

{% figure caption:"Ausschneiden & Einfügen -- es ist wirklich so einfach." %}
  ![Beispiel-Bildschirmfoto](/assets/images/wiw-rcon-chat.jpg)
{% endfigure %}
{:.gallery-2-col}

{% comment %}
<p markdown="0">
  <a href="https://tools.dore.pw/WiW-RCON-Chat/setup.exe" class="btn">Setup</a>
  <a href="https://github.com/freefallcid/wiw-rcon-chat" class="btn">Source code</a>
  <a href="https://github.com/freefallcid/wiw-rcon-chat/issues" class="btn">Issues</a>
</p>
{% endcomment %}

## [WiW Trial Handout Generator]({% post_url software/2019-01-08-wiw-trial-handout %})

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
{:.gallery-2-col}

{% figure caption:"Die Ausgabe des Textes erfolgt umgehend. Kopiere ihn ins Forum." %}
  ![Ausgabe Beispiel-Bildschirmfoto](/assets/images/wiw-trial-handout-2.jpg)
{% endfigure %}
{:.gallery-2-col}

{% comment %}
<p markdown="0">
  <a href="https://tools.dore.pw/WiW-Trial-Handout-Generator/setup.exe" class="btn">Setup</a>
  <a href="https://github.com/freefallcid/wiw-trial-handout" class="btn">Source code</a>
  <a href="https://github.com/freefallcid/wiw-trial-handout/issues" class="btn">Issues</a>
</p>
{% endcomment %}

## Lizenz

In der Regel werden meine Tools unter der
[MIT-Lizenz](https://opensource.org/licenses/MIT) veröffentlicht. Sieh dir
die jeweilige Github-Seite für mehr Informationen an.

Falls du Fragen haben solltest, kannst du dich gerne über das
[Kontaktformular]({% link _pages/contact.md %}) bei mir melden. 

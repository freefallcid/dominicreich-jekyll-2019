---
title: Leitungslängenberechnung
excerpt: 
# image:
#   path: &image "/assets/images/.jpg"
#   feature *image
#   width: 1600
#   height: 640
repo: leitungslaengenberechnung
categories: [software]
tags: [visual basic, electrical engineering]
toc: true
last_modified_at: 2019-01-08T14:14:07+01:00
---

Dieser kleine Helfer kalkuliert den Mindestquerschnitt einer Ader eines Kabels
in der Gebäudeinstallation. Es berücksichtigt **österreichisches Vorschriften**.

{% notice danger %}
#### :exclamation: Schalte dein Gehirn ein!

Du solltest bereits Erfahrung auf dem Gebiet der Elektrotechnik besitzen und
vorallem aber solltest du die hier dargestellten Werte verstehen. Die App dient
als Hilfsmittel und nimmt dir nicht die **Arbeit des Denkens** ab! Sieh dir den
[Code](#installation-und-quellcode) an um meine Kalkulationen zu verifizieren.
{% endnotice %}

{% figure caption:"Werte eingeben und Ergebnisse ablesen. Easy, oder?" %}
  ![Beispiel-Bildschirmfoto](/assets/images/leitungslaengenberechnung.jpg)
{% endfigure %}

## Verwendung

Das Programm setzt *Grundlagen der Elektrotechnik* voraus.

{% figure caption:"Beispiel anhand der Formel für den Leiterquerschnitt. Generiert mit [HostMath](http://www.hostmath.com/) und [Roger's Online Equation Editor](http://rogercortesi.com/eqn/)" %}
  ![example of single-phase alternating current formula](/assets/images/leitungslaengenberechnung_equation.png)
{% endfigure %}
{:.gallery-2-col}

{% comment %}
http://rogercortesi.com/eqn/index.php?filename=tempimagedir%2Feqn1684.png&latextext=A+%3D+%5Cfrac%7B2+%5Ctimes+l+%5Ctimes+I+%5Ctimes+%5Ccos%7D%7B%5Cgamma+%5Ctimes+U_%7Ba%7D%7D&outtype=png&bgcolor=white&txcolor=black&res=225&antialias=1
{% endcomment %}

| Symbol        | Einheit         | Beschreibung |
| :---:         | :---:           | :--- |
| A             | mm<sup>2</sup>  | Leiterquerschnitt |
| l             | m               | Länge des Kabels |
| I             | A               | Stromstärke in Ampere |
| cos           |                 | Wirkungsgrad (0,8) |
| &gamma;       | Sm<sup>-1</sup> | Elektrische Leitfähigkeit in Siemens/meter (bei Kupfer: 58 &times; 10<sup>6</sup>) |
| U<sub>a</sub> | V               | Spannungsabfall (in Österreich max. 3%) |

In der Regel rechne ich mit einem Spannungsabfall von 1,5%, so habe ich noch ein
wenig Reserve um die vorgegebenen 3% nicht zu überschreiten.

[Lese mehr zu diesem Thema](https://www.schalter-steckdosen-shop24.de/ratgeber/faq/themen/berechnung-leitungslaenge-und-leitungsquerschnitte.php).

## Installation und Quellcode

Du kannst den Code gerne [forken](https://help.github.com/en/articles/fork-a-repo)
und an deine eigenen Bedürfnisse anpassen.

<p markdown="0">
  <a href="https://tools.dore.pw/Leitungslaengenberechnung/setup.exe" class="btn"
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

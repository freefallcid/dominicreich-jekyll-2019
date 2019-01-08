---
title: "Leitungslängenberechnung"
excerpt: ""
# image:
#   path: &image "/assets/images/.jpg"
#   feature *image
#   width: 1600
#   height: 640
categories: [software]
tags: []
last_modified_at: 
toc: true
---

This is a tool to calculate the minimal needed cross-section of an electrical wire in a building. It refers to **austrian law**.

{% notice danger %}
#### :exclamation: Don't forget to use your brain!

It might sound harsh---but you shouldn't rely on this app as there could be still some bugs in the app.  
Have a look at [the code](#files-and-codes) yourself to **verify my calculations**.
{% endnotice %}

{% figure caption:"It looks a bit distracting but you really need those inputs to calculate the cross-section of a wire." %}
  ![Example screenshot](/assets/images/leitungslaengenberechnung.jpg)
{% endfigure %}

## Usage

The app is in german only. If you need this in english please fork the repository on github and modify it to your needs. Feel free to ask if you need help---but I can't promise anything. :wink:

For example we calculate a cable in a single-phase alternating current system.

{% figure caption:"Example formula for single-phase alternating current. Generated with [HostMath](http://www.hostmath.com/) and [Roger's Online Equation Editor](http://rogercortesi.com/eqn/)" %}
  ![example of single-phase alternating current formula](/assets/images/leitungslaengenberechnung_equation.png)
{% endfigure %}
{:.gallery-2-col}

{% comment %}
http://rogercortesi.com/eqn/index.php?filename=tempimagedir%2Feqn1684.png&latextext=A+%3D+%5Cfrac%7B2+%5Ctimes+l+%5Ctimes+I+%5Ctimes+%5Ccos%7D%7B%5Cgamma+%5Ctimes+U_%7Ba%7D%7D&outtype=png&bgcolor=white&txcolor=black&res=225&antialias=1
{% endcomment %}

| Symbol        | Unit            | Description |
| :---:         | :---:           | :--- |
| A             | mm<sup>2</sup>  | cross-section that we want to calculate in square-millimeters|
| l             | m               | lenght of the desired wire in meters|
| I             | A               | current in ampere |
| cos           |                 | [level of efficiency][1] (this is usually something around 0.8) |
| &gamma;       | Sm<sup>-1</sup> | [electric conductivity][2] in Siemens/meter (on copper this is 58 &times; 10<sup>6</sup>) |
| U<sub>a</sub> | V               | voltage drop in volts (in Austria this should not be more than 3%) |

[1]: https://en.wikipedia.org/wiki/Efficiency#In_physics
[2]: https://en.wikipedia.org/wiki/Electrical_resistivity_and_conductivity#Resistivity_and_conductivity_of_various_materials

Usually I calculate with a voltage drop of 1.5%---so there should be enough space to not exceed the 3% given by the power supply company.

[Read more](https://www.schalter-steckdosen-shop24.de/ratgeber/faq/themen/berechnung-leitungslaenge-und-leitungsquerschnitte.php) about this topic on this **german**[^german] website.

[^german]: I'd have put an english website here but my english is not that perfect to verify the website that I link to. For german speaking visitors this might come in handy but the rest needs to do its own translation, sorry.

## Files and Codes

Choose if you want to install with the setup-tool, view the source code on Github and compile the application yourself. Please report any issues preferably on Github or via the [contact form]({% link _pages/contact.md %}).

<p markdown="0">
  <a href="https://tools.dore.pw/Leitungslaengenberechnung/setup.exe" class="btn">Setup</a>
  <a href="https://github.com/freefallcid/leitungslaengenberechnung" class="btn">Source code</a>
  <a href="https://github.com/freefallcid/leitungslaengenberechnung/issues" class="btn">Issues</a>
</p>

## License

As most of the stuff hosted on Github this tool is free and open source software, distributed under the [MIT License](https://github.com/freefallcid/leitungslaengenberechnung/blob/master/LICENSE).

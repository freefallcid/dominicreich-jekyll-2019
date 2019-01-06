---
layout: archive
title: "Software"
excerpt: "Some applications that I developed in Visual Basic."
introduction: "Tiny pieces of little helpers---hopefully"
# image: 
#   path: &image /assets/images/visual-basic.png
#   width: 690
#   height: 359
#   feature: *image
tags: [software, visual basic, .net, wiw]
work: "Software development"
last_modified_at: 2018-12-10T21:09:35+01:00
order: 1
---

There are a few tools that I created in Visual Basic on my old windows machine.

{% notice %}
#### Some things just right away

- Some tools might be written in english, some in german. The WiW tools are in english. Normally.
- Those tools are open source (except FEWO Preiskalkulation---because I have to remove some hardcoded things before I publish the code) and free to use (MIT License)
- Most tools use the [.NET Framework 4.5](https://www.microsoft.com/de-at/download/details.aspx?id=30653)---FEWO Preiskalkulation uses [4.5.2](https://www.microsoft.com/de-at/download/details.aspx?id=42643) (note the links point to a german website)
- The tools use the newer design of Windows---the screenshots have been made without them. For old-school reasons... ;-)
- I am not an advanced programmer, so the code and the project files might miss something or are badly coded---please keep that in mind before using the tools. If you have something to add to the code please let me know, I'd like to upgrade my tools aswell when I find some time for it.
{% endnotice %}

## [MD5 Converter]({% post_url software/2019-01-05-md5converter %})

A simple md5-Hash generator that creates hashes while you type. Easy to copy the hash.

{% figure caption:"Easy to use---type your phrase and it converts the string while you type." %}
  ![Example screenshot](/assets/images/md5convert.jpg)
{% endfigure %}
{:.gallery-2-col}

<p markdown="0">
  <a href="https://tools.dore.pw/MD5-Convert/setup.exe" onclick="ga('send', 'event', 'Setup', 'md5Convert', '{{ page.url }}');" class="btn">Setup</a>
  <a href="https://github.com/freefallcid/md5Convert" onclick="ga('send', 'event', 'Source code', 'md5Convert', '{{ page.url }}');" class="btn">Source code</a>
</p>

## Leitungslängenberechnung

This is a tool to calculate the maximum of lenght of a electrical circuit in a building. It refers to **austrian law**.

{% notice danger %}
#### :exclamation: Don't forget to use your brain!

It might sound harsh---but you shouldn't rely on this app as there could be still some bugs in the app.  
Have a look at the code yourself to verify my calculations.
{% endnotice %}

{% figure caption:"Fill out the textfields and hit **BERECHNEN** to calculate the lenght. On other tabs you find other functions as well." %}
  ![Example screenshot](/assets/images/leitungslaengenberechnung.jpg)
{% endfigure %}
{:.gallery-2-col}

<p markdown="0">
  <a href="https://tools.dore.pw/Leitungslaengenberechnung/setup.exe" onclick="ga('send', 'event', 'Setup', 'Leitungslängenberechnung', '{{ page.url }}');" class="btn">Setup</a>
  <a href="https://github.com/freefallcid/leitungslaengenberechnung" onclick="ga('send', 'event', 'Source code', 'Leitungslängenberechnung', '{{ page.url }}');" class="btn">Source code</a>
</p>

## FEWO Preiskalkulation

At version 2. This app lets you quickly calculate a usual overnight stay. Or a holiday. With or without pets. You can set your own values for different situations (summer/winter; how many people; with kids) and so on.

{% figure caption:"The tool in action. Select the time on the calender and fill out the fields on the left side. It calculates different things on the fly." %}
  ![Example screenshot](/assets/images/fewo-preis.jpg)
{% endfigure %}
{:.gallery-2-col}

The tool was built for my parents---because of that it is made to fit their needs. You might fork the repository and change whatever is needed to fit your needs.

<p markdown="0">
  <a href="https://tools.dore.pw/Fewo-Preis/setup.exe" onclick="ga('send', 'event', 'Setup', 'FEWO Preiskalkulation', '{{ page.url }}');" class="btn">Setup</a>
  <a href="https://github.com/freefallcid/Preiskalkulation-2" onclick="ga('send', 'event', 'Source code', 'FEWO Preiskalkulation', '{{ page.url }}');" class="btn">Source code</a>
</p>

## WiW RCON Chat

A simple chat viewer to use with [rconnet.de](http://rconnet.de). The chatlogs were produced from bottom to top---that means you had to read those logs from bottom to the top which is not a normal or usual way of how you read things. It was not naturally.

This tool's purpose was re-sorting of the reading direction as well as the possibility to filter for specific words. And quickly remove those server messages at the cost of an additional click.

{% figure caption:"Paste the chatlog on the top textfield. Setup the filter words by entering the word in the top right textfield and hit enter. It gets added to the list below." %}
  ![Example screenshot](/assets/images/wiw-rcon-chat.jpg)
{% endfigure %}
{:.gallery-2-col}

<p markdown="0">
  <a href="https://tools.dore.pw/WiW-RCON-Chat/setup.exe" onclick="ga('send', 'event', 'Setup', 'WiW RCON Chat', '{{ page.url }}');" class="btn">Setup</a>
  <a href="https://github.com/freefallcid/wiw-rcon-chat" onclick="ga('send', 'event', 'Source code', 'WiW RCON Chat', '{{ page.url }}');" class="btn">Source code</a>
</p>

## WiW Trial Handout Generator

This app creates a standardised text that we used in our clan to respond to a given trial period membership, called recruitment period.

{% figure caption:"Enter the recruits name, select if the recruits gets a cutoff and select the time span on the calendar. Then hit **Generate Text**." %}
  ![Example screenshot](/assets/images/wiw-trial-handout.jpg)
  ![Example screenshot result](/assets/images/wiw-trial-handout-2.jpg)
{% endfigure %}
{:.gallery-2-col}

<p markdown="0">
  <a href="https://tools.dore.pw/WiW-Trial-Handout-Generator/setup.exe" onclick="ga('send', 'event', 'Setup', 'WiW Handout Generator', '{{ page.url }}');" class="btn">Setup</a>
  <a href="https://github.com/freefallcid/wiw-trial-handout" onclick="ga('send', 'event', 'Source code', 'WiW Handout Generator', '{{ page.url }}');" class="btn">Source code</a>
</p>

## License

My tools are mostly licensed under the MIT License. Have an eye on the respective github page for detailed information.

If you got a question, [let me know]({% link _pages/contact.md %}).

{% include_cached support.html %}

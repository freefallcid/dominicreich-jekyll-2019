---
permalink: /wiw/
title: "=WiW= Memorial"
excerpt: "Years ago we all played a game called Battlefield 2. The game bound us together as a team, or, as a family..."
image:
  path: &image /assets/images/wiw.jpg
  width: 160
  height: 64
  feature: *image
  teaser: /assets/images/wiw-320.jpg
tags: [videogames]
# toc: true
last_modified_at: 2017-11-01T21:36:30+01:00
---

{% notice warning %}
#### Migration status
This page looks good but I might have forgotten something. Please [report](/contact/) errors or bugs to me. Thank you!
{% endnotice %}

Years ago we all played a game called Battlefield 2. The game bound us together as a team, or more, as a family...

{% figure caption:"We had a lot of fun. Thank you all for beeing there!" %}
![wiw site logo sepia](/assets/images/wiw-logo-sepia.jpg)
{% endfigure %}

I myself started to be a member of [**=WiW=**][wiwforum] back in 2010, specifically on May 20<sup>th</sup> 2010, when I was [granted the membership](https://web.archive.org/web/20100524010630/http://www.wakeislandwarriors.com/community/viewforum.php?f=5) (uhm, sorry the post itself is not available on the wayback archive :disappointed_relieved:)  of the best community that I can still remember. My old computer served me well for a while --- it was one of the first 64bit beasts that came out at that time.

When time went by, I started paying the admin fee for the clan and became one of the admins. It made things a bit easier as I was able to remove rule-breakers by myself but it also made things a bit more complicated than before --- I had to know the regular players better to know if someone is reporting a rule-breaker because he broke a rule or just for his own advantage. This went on for a few weeks or months and settled down with the time. I got more and more relaxed at playing and administration of the game felt more easier and made fun again. Also watching other players for a while wasn't that bad --- it felt good to do a good thing beside playing the game. I think everyone benefits from good admins.

{% youtube 2fd2vgkM8nY %}

=WiW= did some re-structuring in its hierarchy and I got the role of the head-admin. This happened around the last epoche of BF2, if not the beginning of BF3. I can remember a shitload of talk about good and bad admining on the BF3 Karkand map. Hell, was it a pain every and every time again :disappointed:. Anyway, also on BF3 we got some good servers up and running for quite a while --- you've seen when people were present and when our lifes at home needed us more than the game :wink:.

At the time of BF3 we had a third server for a short time --- I enjoyed the SQDM rounds with you guys a lot. Shit, I started getting good at that game --- which wasn't the case back in BF2 times :satisfied:.

{% youtube njJ6uYQdveA %}

The next video shows a few guys with no luck. But neither had I luck --- my team did not help me much :disappointed:.

{% youtube h26dA_pB_sM %}

*If you like, watch my [Battlefield 2](https://www.youtube.com/playlist?list=PLAVuOpof7vDrLj6gNgPIAde6CLZC5CoCy) or [Battlefield 3](https://www.youtube.com/playlist?list=PLAVuOpof7vDoNS_1ECqkx5XusLjI7CjMM) playlists on YouTube --- I'm going forward in history and tell you the rest of the story so you can read on.*

With beeing head-admin for a while, I got asked to join the recruitment team --- which consisted of Niels and Bange at that moment (I think Spocki already left, but I'm not really sure about that right now). Time went by with playing and recruiting new members mostly on BF3 but also sometimes on BF2, still. 

Anyway, Bange was pushed towards the Mods group and Sanna joined the recruitment team. I created two tools at that time: a) [WiW Trial Handout Generator](https://github.com/freefallcid/wiw-trial-handout), which created a pre-defined text that recruiters post when a new members is granted a trial period and b) [WiW RCON Chat](https://github.com/freefallcid/wiw-rcon-chat), a tool made to properly read and filter logfiles of [rconnet.de](http://rconnet.de)[^rconnet].

To follow time I felt the need to leave the clan. I had not enough free time to bring into the community. I stepped back from recruiting and Morphoes took place. From then I was normal clan member without the need of any hassle to bring or not to bring into --- not that anyone would have told me to bring, but this was my own decision to take away some stress that I would probably just make myself :tired_face:.

I never left the clan officially[^clan] --- but in fact I wasn't that present in the clan around the 23<sup>rd</sup> of November 2014.

On December 6<sup>th</sup>, 2014 I went totally insane and copied nearly the whole wake island warriors website to my webserver --- to host a personal copy of the forum of that time. To produce a copy of the website, I used httrack and this piece of command line input:

``` console
$ httrack 'http://www.wakeislandwarriors.com/forum/ucp.php?mode=login?>postfile:websites/hts-post0' \
  -O '/home/dominic/websites/wiw' -'*' -'mime:*/*' +'mime:text/html' \
  +'mime:image/*' +'www.wakeislandwarriors.com/forum/viewforum.php?f=*' \
  +'www.wakeislandwarriors.com/forum/viewtopic.php?f=*' \
  +'www.wakeislandwarriors.com/forum/memberlist.php?mode=viewprofile&u=*' \
  +'www.wakeislandwarriors.com/forum/index.php' \
  +'www.wakeislandwarriors.com/forum/*.gif*[<100]' \
  +'www.wakeislandwarriors.com/forum/*.png*[<100]' \
  +'www.wakeislandwarriors.com/forum/*.jpg*[<100]' +'tmsn.at/*.png*[<100]' \
  +'*/*.css*[<100]' -T60 -R2 -%v -%c1 -c4 -o \
  -F 'Mozilla/5.0 (X11; Operatoah Systemz; Linux x86_64; rv:34.0) like Gecko' -r999999
```

{% comment %}
Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)

Use this user agent string but modified to personal use:

Mozilla/5.0 (compatible; FreefallCid MirrorBot/0.1; +https://dominicreich.com/wiw)
{% endcomment %}

I advise you to not use that code any more, it does not filter out enough URLs and results in you [bumping][bumping] a shitload of topics. It also fetches CSS files online which do not get loaded if you serve your mirror via HTTPS (this might also depends on your server configuration though). You may use [my copy](/dominic/wiw-archive/)[^mirror] for your readings if you like.

[wiwforum]: http://www.wakeislandwarriors.eu/forum/
[bumping]: https://www.webopedia.com/TERM/T/thread_bump.html

[^rconnet]: rconnet.de log files were printed upwards down, so you had to read them from the bottom to the top. My tool re-ordered all the lines you gave it and it had the possibility to filter out server messages or text that you could specify.
[^mirror]: Like I said already, the stylesheets and javascripts do not get loaded due to the Content-Security-Policy of my webserver.
[^clan]: But I tried xD --- I announced to not have enough time to participate in clan management and clan life as a whole. Nowadays (a few years later) I realized that many (if not all) people in the clan went AWOL. Some people pop by from time to time. And some I haven't seen for ages.

{% notice info %}
**Update:** A new version gets mirrored right now, although to let the webserver breath a bit I do not leech down the website but I try to fetch it site-by-site, so this might take a while as I expect a few gigabytes to be downloaded.

*I will update this site when that process has been finished (and tested).*

**Update Feb 2018:** There are still bugs and errors on the new mirror. I will repeat the fetch some day. Sorry, for the inconvinience. Meanwhile, have fun on the net.
{% endnotice %}

*[SQDM]: Squad Death Match
*[AWOL]: absent without official leave

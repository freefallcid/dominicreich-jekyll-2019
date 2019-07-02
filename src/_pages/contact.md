---
permalink: /kontakt/
title: Kontakt
image:
  path: &image /assets/images/letters-2794672_1920.jpg
  feature: *image
  width: 1600
  height: 640
  caption: "[Foto von **geralt** via Pixabay](https://pixabay.com/photo-2794672/)"
date: 2016-08-26
last_modified_at: 2019-03-24T20:10:16+01:00
excerpt: Bevorzugte Methoden um mit mir Kontakt aufzunehmen.
---

Hast du Fragen über mich, diese Webseite oder die Artikel bzw. Beiträge, die ich
hier veröffentliche?

Benutze das Formular hier um mir eine Email zu senden. Dies ist der einfachste
Weg mich zu kontaktieren -- ich antworte in der Regel am Abend oder am nächsten
Tag. Ich bin nicht sehr aktiv in sozialen Netzwerken unterwegs, weshalb dort
eine Antwort von mir meist länger dauert.

<form id="contact" name="contact" accept-charset="UTF-8" autocomplete="off" enctype="multipart/form-data" method="POST" data-netlify-recaptcha="true" data-netlify="true" netlify-honeypot="comment">
  <div>
    <label id="lblName" for="name">Name
      <input id="name" name="name" type="text" spellcheck="false" maxlength="255" required placeholder="Dein Name">
    </label>
  </div>
  <div>
    <label id="lblEmail" for="email">Email-Adresse <small>(wird nicht veröffentlicht)</small>
      <input id="email" name="email" type="email" spellcheck="false" maxlength="255" required placeholder="email@example.com">
    </label>
  </div>
  <div>
    <label id="lblHeardOf" for="heard-of">Wie hast du von meiner Seite erfahren?
      <input id="heard-of" name="heard-of" type="text" spellcheck="true" maxlength="255" placeholder="z.Bsp.: Web-Forum oder Suche (bitte gib einen Namen oder eine Adresse an)">
    </label>
  </div>
  <div>
    <label>Nachricht: <textarea name="message" spellcheck="true" rows="10" cols="50" required placeholder="Hallo, ..."></textarea></label>
  </div>
  <div>
    <label id="lblFile" for="file">Dateien (Bilder, Fotos, Screenshots) <small>(falls nötig)</small>
      <input id="file" name="file" type="file" accept="image/*,.pdf" multiple>
    </label>
  </div>
  <div data-netlify-recaptcha="true"></div>
  <div>
    <button id="submit" name="submit" type="submit" class="btn">Nachricht abschicken</button>
  </div>
  <div class="hidden">
    <label id="lblComment" for="comment">Nicht ausfüllen
      <input name="comment">
    </label>
  </div>
</form>

{% comment %}

<!-- this is an old form for reference only ! -->

<form id="form1" name="form1" accept-charset="UTF-8" autocomplete="off" enctype="multipart/form-data" method="post" novalidate action="https://dominicreich.com/cgi-bin/fm18.pl">
  <div class="form-group">
    <label class="sr-only" id="title7" for="Field7"><strong>Name</strong></label>
    <input id="Field7" name="realname" type="text" maxlength="255" placeholder="Name">
  </div>
  <div class="form-group">
    <label class="sr-only" id="title2" for="Field2"><strong>Email address</strong><span id="req_2" class="req">*</span> <small>(will remain private)</small></label>
    <input id="Field2" name="your_email" type="email" spellcheck="false" maxlength="255" required placeholder="Email address (will remain private)">
  </div>
  <div class="form-group">
    <label class="sr-only" id="title10" for="Field10"><strong>How&rsquo;d you hear about my website?</strong></label>
    <input id="Field10" name="heard_of" type="text" maxlength="255" placeholder="How&rsquo;d you hear about my website?">
  </div>
    <div class="form-group">
    <label class="sr-only" id="title11" for="Field11"><strong>Subject</strong></label>
    <input id="Field10" name="subject" type="text" maxlength="255" placeholder="Subject">
  </div>
  <div class="form-group">
    <label class="sr-only" id="title1" for="Field1"><strong>Message</strong><span id="req_1" class="req">*</span></label>
    <textarea id="Field1" name="message" spellcheck="true" rows="10" cols="50" required placeholder="Message"></textarea>
  </div>
  <div class="form-group">
    <button id="saveForm" name="saveForm" class="btn" type="submit">Send Message</button>
  </div>
  <div class="form-group hidden">
    <label for="comment">Do Not Fill This Out</label>
    <textarea name="comment" id="comment" rows="1" cols="1"></textarea>
    <input type="hidden" name="env_report" value="REMOTE_HOST,REMOTE_ADDR,REMOTE_USER,HTTP_USER_AGENT">
    <input type="hidden" name="recipient" value="webmail@dominicreich.com">
    <input type="hidden" name="email" value="webformmailer@dominicreich.com">
    <input type="hidden" name="required" value="realname,message">
    <input type="hidden" name="print_config" value="your_email,subject">
    <input type="hidden" name="print_blank_fields" value="1">
  </div>
</form>
{% endcomment %}

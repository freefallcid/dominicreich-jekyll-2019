---
permalink: /contact/
title: "Contact"
last_modified_at: 2018-12-08 22:46:00
excerpt: "Preferred methods of sending your questions, inquires, messages, and love letters to me."
---

Have questions about me, this website, or the things that I publish here?

Use the contact form below to get in contact with me---this is the easiest way for a first contact.
I will close down the social memberships that I currently maintain---I do not have the time needed for those to manage.

<form id="contact" name="contact" accept-charset="UTF-8" autocomplete="off" enctype="multipart/form-data" method="POST" novalidate data-netlify="true">
  <div>
    <label id="lblName" for="name">Name
      <input id="name" name="name" type="text" spellcheck="false" maxlength="255" required placeholder="Your name">
    </label>
  </div>
  <div>
    <label id="lblEmail" for="email">Email address <small>(will remain private)</small>
      <input id="email" name="email" type="email" spellcheck="false" maxlength="255" required placeholder="email@address.com">
    </label>
  </div>
  <div>
    <label id="lblHeardOf" for="heard-of">How you'd hear about my site?
      <input id="heard-of" name="heard-of" type="text" spellcheck="true" maxlength="255" placeholder="e.g. web search or another forum (please name it or address it)">
    </label>
  </div>
  <div>
    <label>Message: <textarea name="message" spellcheck="true" rows="10" cols="50" required placeholder="Hi there, I'd like to..."></textarea></label>
  </div>
  <div>
    <label id="lblFile" for="file">Files or photos <small>(if you need to attach)</small>
      <input id="file" name="file" type="file" accept="image/*,.pdf" multiple>
    </label>
  </div>
  <div data-netlify-recaptcha="true"></div>
  <div>
    <button id="submit" name="submit" type="submit" class="btn">Send message</button>
    <button id="reset" name="reset" type="reset" class="btn">Reset all input</button>
  </div>
  <div class="hidden">
    <label id="lblComment" for="comment">Do not fill this out
      <textarea name="comment" id="comment" rows="1" cols="1"></textarea>
      <input type="hidden" id="idstamp" name="idstamp" value="WW91J3JlIHdlbGNvbWUhCg==">
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

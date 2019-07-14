---
title: So kompiliere ich den Newsreader tin
excerpt: Meine Konfiguration des Newsreaders [tin](http://www.tin.org/).
tags: [macos, terminal, til]
categories: [notizen]
---

Für den Fall, dass ich [tin](http://www.tin.org/) nochmal kompilieren möchte.

``` terminal
$ ./configure --prefix=/opt/local \
  --mandir=/opt/local/share/man \
  --infodir=/opt/local/share/info \
  --datadir=/opt/local/share \
  --sysconfdir=/opt/local/etc \
  --with-defaults-dir=/opt/local/etc/tin \
  --enable-break-long-lines --enable-nntp \
  --enable-mh-mail-handling \
  --enable-included-msgs --enable-ipv6 \
  --with-coffee --disable-pgp-gpg \
  --with-editor=vim --with-mailer=mutt \
  --enable-cancel-locks
```

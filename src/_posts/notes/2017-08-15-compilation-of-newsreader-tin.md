---
title: "The way I compile the newsreader tin"
excerpt: "This is the build configuration that I used the last time."
tags: [macos, terminal]
# last_modified_at: 2018-02-01T20:07:25+01:00
categories: [til]
---

Maybe I need this some day.

``` terminal
$ ./configure --prefix=/opt/local --mandir=/opt/local/share/man \
--infodir=/opt/local/share/info --datadir=/opt/local/share \
--sysconfdir=/opt/local/etc --with-defaults-dir=/opt/local/etc/tin \
--enable-break-long-lines --enable-nntp --enable-mh-mail-handling \
--enable-included-msgs --enable-ipv6 --with-coffee --disable-pgp-gpg \
--with-editor=vim --with-mailer=mutt --enable-cancel-locks
```

---
title: Kurze Key-IDs in GnuPG anzeigen lassen
excerpt: >
  Selbst entscheiden, welches `keyid-format` für die Anzeige verwendet werden soll.
date: 2019-08-11
categories: [notizen]
tags: []
# toc: true
# support: true
# comments: true
# comments_locked: true
# published: false
# last_modified_at: 
---

``` terminal
$ gpg --keyid-format short --list-key max
gpg: "Trust-DB" wird überprüft
gpg: marginals needed: 3  completes needed: 1  trust model: pgp
gpg: Tiefe: 0  gültig:   2  signiert:   0  Vertrauen: 0-, 0q, 0n, 0m, 0f, 2u
gpg: nächste "Trust-DB"-Pflichtüberprüfung am 2021-08-10
pub   rsa2048/0F313069 2019-08-11 [SC] [verfällt: 2021-08-10]
      CA1D78E33971E94B4631B99F1FAA896E0F313069
uid      [ ultimativ ] Max Mustermann <test@localdomain.local>
sub   rsa2048/C366F253 2019-08-11 [E] [verfällt: 2021-08-10]
```

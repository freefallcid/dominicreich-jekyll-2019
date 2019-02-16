---
title: "Writing a dmg-file to a SD-card"
excerpt: "Another quick reference to write a SD-card out of a `dmg`-file."
tags: [macos, terminal, til]
# last_modified_at: 2018-01-30T21:15:35+01:00
categories: [notes]
---

Another set of commands that I cannot remind me of when I need it.

``` terminal
$ hdiutil convert backup.dmg -format UDTO -o raw-image.img
$ mv raw-image.img.cdr raw-image.img
$ sudo dd if=raw-image.img bs=1m of=/dev/rdisk3
```

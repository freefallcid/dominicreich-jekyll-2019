---
title: Klone ein Git-Repository
excerpt: Wie man ein Git-Repository richtig klont.
categories: [notizen]
tags: [git, linux, macos, freebsd]
# toc: true
# support: true
# comments: true
# comments_locked: true
# published: false
# last_modified_at: 
---

Ein Verzeichnis (zum Beispiel von einem USB-Stick) ins Heimverzeichnis klonen:

```
$ cd ~/new-path
$ git clone /Volumes/USB-Stick/old-path .
```

Das Repository kann mit `git pull` aktualisiert werden.

Eigentlich wird das lokale Repository gleich wie eine URL behandelt.

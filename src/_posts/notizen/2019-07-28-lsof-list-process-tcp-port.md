---
title: Welcher Prozess lauscht auf einem bestimmten Port?
excerpt: >
  Du willst herausfinden welcher Prozess auf einem bestimmten Port lauscht?
categories: [notizen]
tags: [linux, terminal]
# toc: true
# support: true
# comments: true
# comments_locked: true
# published: false
# last_modified_at: 
---

Kurz und bündig:

``` terminal
# lsof -i :25
COMMAND   PID USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
master  17688 root   13u  IPv4 445271      0t0  TCP localhost:smtp (LISTEN)
```

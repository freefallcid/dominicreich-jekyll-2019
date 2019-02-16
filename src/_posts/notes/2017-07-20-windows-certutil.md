---
title: "Windows certutil"
excerpt: "Adds a certificate to the windows certification manager."
tags: [windows, terminal]
# last_modified_at: 2018-01-29T23:59:49+01:00
categories: [til]
---

A quick way for adding a certificate to the systems root certification path.

Although, you need an [admin-shell](https://www.google.com/search?rls=en&q=how+to+open+an+admin+shell+windows&ie=UTF-8&oe=UTF-8) for this to work.

``` terminal
certutil -f -addstore CA "\\domain\sysvol\domain\scripts\path\certificate.crt"
```

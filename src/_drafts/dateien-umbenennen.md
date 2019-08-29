---
title: Massenhaft Dateien umbenennen
excerpt: Umbenennen von vielen ähnlich klingenden Dateinamen
categories: [notizen]
tags: []
# toc: true
# support: true
# comments: true
# comments_locked: true
# published: false
# last_modified_at: 
---

Muss man viele Dateien umbenennen helfen Schleifen ungemein.

``` bash
for file in F0000*
do
    echo mv "$file" "${file/#F0000/F000}"
    # ${file/#F0000/F000} means replace the pattern that starts at beginning of string
done
```

_Quellen: [debian-administration.org](https://debian-administration.org/article/150/Easily_renaming_multiple_files), [stackoverflow.com](http://stackoverflow.com/questions/2372719/using-sed-to-mass-rename-files)_

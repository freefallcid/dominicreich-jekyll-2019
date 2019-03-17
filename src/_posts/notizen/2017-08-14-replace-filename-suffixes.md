---
title: "Replace multiple filename suffixes"
excerpt: "Change plenty of file suffixes with this little one-liner."
tags: [linux, macos, terminal, til]
# last_modified_at: 2018-01-30T20:30:24+01:00
categories: [notes]
---

Because I cannot remember that syntax of `basename`...

``` terminal
$ for i in *.eml; do mv "$i" $(basename -s .eml "$i").txt; done
```

That will rename all `eml`-files into `txt`-files.

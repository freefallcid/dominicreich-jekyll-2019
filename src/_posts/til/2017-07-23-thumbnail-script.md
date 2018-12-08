---
title: "Quickly create thumbnails"
excerpt: "Create a 100% crop of an image on the fly. Uses ImageMagick."
tags: [linux, macos, terminal, photography]
# last_modified_at: 2018-01-30T00:16:55+01:00
categories: [til]
---

That script creates a 300px thumbnail of a picture.

Run this script with two arguments. The first argument `$1` is the input file (your original content).
Use the second argument `$2` as an output file (your thumbnail).

``` bash
#!/bin/bash
convert $1 -gravity Center -crop 50x50%+0+0 -resize 300x -fuzz 15% +repage $2
```

Make sure you put the file in your `$PATH`.

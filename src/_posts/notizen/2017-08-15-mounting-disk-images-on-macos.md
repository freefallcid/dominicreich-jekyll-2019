---
title: "Mounting disk-images on macOS"
excerpt: "Help me remember how to mount iso or raw disk-images on macOS with hdiutil."
tags: [macos, terminal, til]
# last_modified_at: 2018-01-30T21:41:35+01:00
categories: [notes]
---

You can mount `iso` and `img` files with `hdiutil` on macOS. I'll write down both versions here.

{% notice warning %}
#### :warning: Information
`img`-files are consideres as so called [raw images](https://en.wikipedia.org/wiki/IMG_(file_format))
while `iso`-files are plain [ISO images](https://en.wikipedia.org/wiki/ISO_image). When I talk about
`img`-files, I mainly talk about image files that I create with [dd](https://en.wikipedia.org/wiki/Dd_(Unix)).
Also note that I may use partitions as a word for slices here.
{% endnotice %}

# `iso`-files

The mounted image will be available in `/Volumes`.

``` terminal
$ hdiutil mount backupdisk.iso
```

# `img`-files

raw images can be mounted with a more complex command. First we list the partitions
available in that image container---we then mount only the needed partition.

``` terminal
$ hdiutil attach -imagekey diskimage-class=CRawDiskImage -nomount image.img
/dev/disk5            FDisk_partition_scheme
/dev/disk5s1          Windows_FAT_32
/dev/disk5s2          Linux
$ mount_msdos /dev/disk5s1 ~/test
```

We unmount that device when we finished our work with it.

``` terminal
$ hdiutil detach disk5
"disk5" unmounted.
"disk5" ejected.
```

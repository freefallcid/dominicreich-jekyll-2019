---
title: Mounten von Disk-Images unter MacOS
excerpt: >
  Das Mounten von ISO-Images ist nicht schwer. Allerdings vergesse ich ständig
  wie das mit RAW-Images geht. Hier steht wie's geht.
tags: [macos, terminal, til]
categories: [notizen]
---

Du kannst unter macOS `iso`- und `img`-Dateien mit `hdiutil` mounten.

{% notice info %}
`img`-Dateien sind sogenannte [RAW-Images](https://en.wikipedia.org/wiki/IMG_(file_format)),
während `iso`-Dateien einfache [ISO-Images](https://en.wikipedia.org/wiki/ISO_image)
sind.
{% endnotice %}

# `iso`-Dateien

Das Image wird unter `/Volumes` eingehängt.

``` terminal
$ hdiutil mount backupdisk.iso
```

# `img`-Dateien

Etwas komplexer wird es mit RAW-Images. Zuerst listen wir die darin enthaltenen
Partitionen (Slices) auf. Wir werden dann nur die benötigte Partition mounten.

``` terminal
$ hdiutil attach -imagekey diskimage-class=CRawDiskImage -nomount image.img
/dev/disk5            FDisk_partition_scheme
/dev/disk5s1          Windows_FAT_32
/dev/disk5s2          Linux
$ mount_msdos /dev/disk5s1 ~/test
```

Nach Abschluss der Arbeiten am Image hängen wir das Image wieder aus.

``` terminal
$ hdiutil detach disk5
"disk5" unmounted.
"disk5" ejected.
```

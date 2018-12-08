---
title: "Partition table backup"
# excerpt: "Create a duplicate of a hard disk without copying over all the data."
tags: [terminal, linux]
# last_modified_at: 2018-01-30T20:49:34+01:00
categories: [til]
---

Create a partition tables backup with the tool [sfdisk](https://github.com/karelzak/util-linux).

Easily create a partition table backup to copy to a new hard drive or just for a backup.

{% notice danger %}
:exclamation: Use this only with **MBR** type of hard disks.
{% endnotice %}

Save the partition table to a file.

``` terminal
# sfdisk -d /dev/sda > /root/sda.backup.txt
```

For recovery you can save this partition to a new hard drive with the exact same geometry.

``` terminal
# sfdisk /dev/sda < /root/sda.backup.txt
```

That's it. After recovery you still need to format the partitions with the correct filesystems.

---
title: Kali Linux Persistence
excerpt: >
  Kurzer "Walktrough" fürs Einrichten von Kali Linux auf einem USB-Stick mit
  verschlüsselter "Persistence"-Partition.
categories: [notizen]
tags: [kali, LUKS, linux]
toc: true
support: true
# comments: true
# comments_locked: true
# last_modified_at: 
---

Schreibe ein [Kali Linux Image](https://www.kali.org/downloads/) auf einen
USB-Stick.

## Stick identifizieren

Zuerst finden wir heraus, unter welchem Namen wir den USB-Stick finden:

``` terminal
# dmesg | tail
usb 2-1.2: SerialNumber: 4C530001010625114363
usb-storage 2-1.2:1.0: USB Mass Storage device detected
scsi host6: usb-storage 2-1.2:1.0
scsi 6:0:0:0: Direct-Access   SanDisk  Ultra USB 3.0  1.00 PQ: 0 ANSI: 6
sd 6:0:0:0: Attached scsi generic sg3 type 0
sd 6:0:0:0: [sdc] 30031250 512-byte logical blocks: (15.4 GB/14.3 GiB)
sd 6:0:0:0: [sdc] Write Protect is off
sd 6:0:0:0: [sdc] Mode Sense: 43 00 00 00
sd 6:0:0:0: [sdc] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
sd 6:0:0:0: [sdc] Attached SCSI removable disk
```

Wir verwenden also `/dev/sdc` und schreiben das Image direkt auf den Stick. **Der
Stick sollte nicht gemountet sein!**

Mein Stick ist leer bzw. wurde er vorher mittels `dd if=/dev/zero of=/dev/sdc bs=512 count=1`
gelöscht.

``` terminal
# fdisk -l /dev/sdc                             
Disk /dev/sdc: 14,3 GiB, 15376000000 bytes, 30031250 sectors
Disk model: Ultra USB 3.0   
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
```

## Kali Image auf den Stick schreiben

``` terminal
# dd if=kali-linux-2019.2-amd64.iso of=/dev/sdc bs=512k                
6395+1 Datensätze ein
6395+1 Datensätze aus
3353227264 bytes (3,4 GB, 3,1 GiB) copied, 365,951 s, 9,2 MB/s
```

{% notice warning %}
Der "blocksize"-Parameter (`bs=512k` ) kann erhöht werden. Dadurch würde der Vorgang
etwas schneller, jedoch kann es in Abhängigkeit der Hardware und anderer Faktoren
zu **unbrauchbaren** USB-Sticks kommen.

Weitere Informationen findest du im Artikel
[Making a Kali Bootable USB Drive](https://docs.kali.org/downloading/kali-linux-live-usb-install).
{% endnotice %}

Kurzer Check mit `fdisk`:

``` terminal
# fdisk -l /dev/sdc
Disk /dev/sdc: 14,3 GiB, 15376000000 bytes, 30031250 sectors
Disk model: Ultra USB 3.0   
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x825c29ed

Device     Boot   Start     End Sectors  Size Id Type
/dev/sdc1  *         64 6547199 6547136  3,1G 17 Hidden HPFS/NTFS
/dev/sdc2       6547200 6548671    1472  736K  1 FAT12
```

## Persistence Partition einrichten

Im Anschluss wird die Partition erstellt. Ich verwende hier einen 16GB-Stick.
Unter `fdisk` wird mir der Stick mit 14,3 GiB angezeigt.

``` terminal
# end=14gb
# read start _ < <(du -bcm kali-linux-2019.2-amd64.iso | tail -1)
# parted /dev/sdc mkpart primary $start $end
Warning: You requested a partition from 3198MB to 14,0GB (sectors 6246093..27343750).
The closest location we can manage is 3353MB to 14,0GB (sectors 6548672..27343750).
Is this still acceptable to you?
Yes/No? y                                                                 
Warning: The resulting partition is not properly aligned for best performance.
Ignore/Cancel? i                                                          
Information: You may need to update /etc/fstab.
```

Man sieht die neu hinzugefügte Partition:

``` terminal
# fdisk -l /dev/sdc
Disk /dev/sdc: 14,3 GiB, 15376000000 bytes, 30031250 sectors
Disk model: Ultra USB 3.0   
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x825c29ed

Device     Boot   Start      End  Sectors  Size Id Type
/dev/sdc1  *         64  6547199  6547136  3,1G 17 Hidden HPFS/NTFS
/dev/sdc2       6547200  6548671     1472  736K  1 FAT12
/dev/sdc3       6548672 27343750 20795079  9,9G 83 Linux
```

### LUKS einrichten

Wir erstellen nun unseren LUKS-Container:

``` terminal
# cryptsetup --verbose --verify-passphrase luksFormat /dev/sdc3

WARNING!
========
Hiermit werden die Daten auf »/dev/sdc3« unwiderruflich überschrieben.

Are you sure? (Type uppercase yes): YES
Geben Sie die Passphrase für »/dev/sdc3« ein: 
Passphrase bestätigen: 
Schlüsselfach 0 erstellt.
Befehl erfolgreich.
# cryptsetup luksOpen /dev/sdc3 my_usb
Geben Sie die Passphrase für »/dev/sdc3« ein:
```

### Dateisystem erstellen

Erstellen des Dateisystems:

``` terminal
# mkfs.ext3 -L persistence /dev/mapper/my_usb
mke2fs 1.44.5 (15-Dec-2018)
Creating filesystem with 2598872 4k blocks and 650240 inodes
Filesystem UUID: 42483522-f350-4747-9651-ed5518b1db6c
Superblock backups stored on blocks: 
  32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632

Allocating group tables: done                            
Writing inode tables: done                            
Creating journal (16384 blocks): done
Writing superblocks and filesystem accounting information: done 

# e2label /dev/mapper/my_usb persistence
```

Nun erstellen wir die Datei `persistence.conf` auf unserer verschlüsselten
Partition.

``` terminal
# mkdir -p /mnt/my_usb
# mount /dev/mapper/my_usb /mnt/my_usb
# echo "/ union" > /mnt/my_usb/persistence.conf
# umount /dev/mapper/my_usb
```

Zum Schluss schließen wir den LUKS-Container wieder:

``` terminal
# cryptsetup luksClose /dev/mapper/my_usb
```

Die Konfiguration ist nun abgeschlossen und kann beim Start von Kali Linux
ausgewählt werden.

{% notice %}
Der Original-Artikel ist unter
[Kali Linux Live USB Persistence](https://docs.kali.org/downloading/kali-linux-live-usb-persistence)
zu finden. Die wichtigsten Befehle und Überlegungen wurden hier niedergeschrieben,
damit die Information nicht verloren geht, falls der Kali Webserver offline sein
sollte.
{% endnotice %}

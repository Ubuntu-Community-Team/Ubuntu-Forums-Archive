---
title: "usb disk partially visible"
date: 2009-09-07
forum: x86 64-bit Users
---

### Post by Aegedus on 2009-09-07
Hello,

I' really disappointed with an usb disk and my X86-64bit Jaunty distrib.

First, I have an usb 350Go disk with some trouble under windows.
I plugged it on my linux station and then I've been able to see it and to read it with fdisk. I retrieve most of my data using tesdisk.

One day after, I re-plug the disk ... then, I have some strange behaviors from the linux OS (see below) and I can't mount or read anything (fdisk, testdisk, mount, blkid, gparted ...) but I can see partially the device (/proc/partitions, /var/log/messages). How can I retrieve any data now ?

Thanks in advance for your help.
Aegedus.


Here are some informations, the disk device is sdb :

1/ The /var/log/messages shows me some troubles reading partition, exactly like 2 days ago :
```
Sep  8 01:00:02 home264 kernel: [ 3187.728651] Info fld=0x0
Sep  8 01:00:02 home264 kernel: [ 3187.728654] sd 9:0:0:0: [sdb] Add. Sense: Noadditional sense information
Sep  8 01:00:22 home264 kernel: [ 3207.537637] sd 9:0:0:0: [sdb] Sense Key : NoSense [current]
Sep  8 01:00:22 home264 kernel: [ 3207.537650] Info fld=0x0
Sep  8 01:00:22 home264 kernel: [ 3207.537653] sd 9:0:0:0: [sdb] Add. Sense: Noadditional sense information
```2/ But now, the fdisk don't see anymore the sdb disk and its partitions :
```
Disque /dev/sda: 80.0 Go, 80026361856 octets
255 têtes, 63 secteurs/piste, 9729 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets
Identifiant de disque : 0x17d9b8c2

Périphérique Amorce  Début        Fin      Blocs     Id  Système
/dev/sda1   *           1        9408    75569728+  83  Linux
/dev/sda2            9409        9729     2578432+   5  Etendue
/dev/sda5            9409        9729     2578401   82  Linux swap / Solaris
```3/ All partitions are visible in /proc/partitions :
```
cat /proc/partitions
major minor  #blocks  name

   8        0   78150744 sda
   8        1   75569728 sda1
   8        2          1 sda2
   8        5    2578401 sda5
   8       16  117220824 sdb
   8       17   55191276 sdb1
   8       18          1 sdb2
   8       21   62026933 sdb5
```4/ THe lsusb command detected the usb disk box, the "Initio" in this list :
 ```
sudo lsusb
Bus 001 Device 007: ID 13fd:1840 Initio Corporation
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 002: ID 1267:0103 Logic3 / SpectraVideo plc G-720 Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```My config is a standard Ubuntu 9.04 jaunty with Kubuntu.
```
 uname -a
Linux home264 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 x86_64 GNU/Linux
```

---

### Post by mgranet on 2009-09-08
It sounds like your disk has died. I would stop further attempts at data retrieval, unplug the drive, and take it to a specialist data recovery shop.

---

### Post by Aegedus on 2009-09-08
> **mgranet said:**
> It sounds like your disk has died.

I'm afraid of this end ...I wait few times for any news posts and I will decide.
AG

---


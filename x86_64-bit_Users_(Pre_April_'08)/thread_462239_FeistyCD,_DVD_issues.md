---
title: "Feisty/CD, DVD issues"
date: 2007-06-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by Malibyte on 2007-06-02
I have installed Feisty (actually, did the dist-upgrade from Dapper LTS -> Edgy -> Feisty).

I can't mount the CD/DVD drive (or access it with Xine):

The drive is a Plextor SATA unit, on /dev/scd0; there are symlinks /dev/sr0 and /dev/cdrom pointing to it.

```

[rcs@yoda: ~]$ mount /cdrom
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@yoda:/home/rcs# dmesg | tail
[  753.942300] cdrom: This disc doesn't have any tracks I recognize!
[  753.962654] cdrom: This disc doesn't have any tracks I recognize!
[  758.526914] attempt to access beyond end of device
[  758.526919] sr0: rw=0, want=68, limit=4
[  758.526922] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
[ 1069.195321] attempt to access beyond end of device
[ 1069.195325] sr0: rw=0, want=68, limit=4
[ 1069.195329] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
[ 1069.215596] cdrom: This disc doesn't have any tracks I recognize!
[ 1069.245155] cdrom: This disc doesn't have any tracks I recognize!


```

This happens with multiple, known-good discs.

Trying to play a DVD with Xine:

```

[rcs@yoda: ~]$ xine
This is xine (X11 gui) - a free video player v0.99.5cvs.
(c) 2000-2006 The xine Team.
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdread: Can't seek to block 256
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdread: Can't seek to block 256
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.

```

This drive works; I have another distro on the same machine which can use it without problems.  

The above happen whether I try to access the drive as my regular user or as root; the regular user is in the "cdrom" group anyway.

What do I have misconfigured?

Thanks for any help!
Bob

---

### Post by kuja on 2007-06-04
I doubt you have anything misconfigured. It's failing to make the driver read the disk. Probably a kernel issue, try downloading an older kernel (perhaps the one from 6.10?) and installing it, boot into it, and see if the problem goes away.

---

### Post by ©TriMoon® on 2007-06-04
Try mounting it in /dev/media/ instead....

My cdrom is connected as slave on my IDE controller, so you should change to your needs.
This is what my ubuntu has created for me in my /etc/fstab:
```
/dev/hdb /media/cdrom0 udf,iso9660 user,noauto 0 0
```
And i got a SymLink:
/dev/media/cdrom -> /dev/media/cdrom0

---

### Post by tszanon on 2007-06-05
> **©TriMoon® said:**
> Try mounting it in /dev/media/ instead....

My cdrom is connected as slave on my IDE controller, so you should change to your needs.
This is what my ubuntu has created for me in my /etc/fstab:
```
/dev/hdb /media/cdrom0 udf,iso9660 user,noauto 0 0
```
And i got a SymLink:
/dev/media/cdrom -> /dev/media/cdrom0
I think you meant **/media/cdrom** and **/media/cdrom0** instead of **/dev/media**.

---

### Post by ©TriMoon® on 2007-06-06
> **tszanon said:**
> I think you meant **/media/cdrom** and **/media/cdrom0** instead of **/dev/media**.

Technical term for cases like that is [img]http://img400.imageshack.us/img400/8008/oops7yt.gif[/img][img]http://www.pcinpact.com/forum/style_emoticons/default/transpi.gif[/img]

---

### Post by accmariano on 2008-02-10
Hi All 

After several days of looking for, i've solved the issue

First I enter in bios Setup and set UDMA to UDMA4, and type of drive CDROM

Then, I do:

hdparm -p4 /dev/hdb  (To set PIO in 4)
hdparm -c2 /dev/hdb  ( to set IO to 32 bits and sync)


This fix my problem to play dvds in xine, mplayer and VLC


I don't know which of this actions solve the problem, but now its work!!!

Regards

---


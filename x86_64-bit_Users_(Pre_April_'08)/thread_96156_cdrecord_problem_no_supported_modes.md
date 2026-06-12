---
title: "cdrecord problem: no supported modes"
date: 2005-11-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by fidlet on 2005-11-28
I use Breezy on my g3 iBook.  When I try to use cdrecord to burn an iso
with the command cdrecord -dev=/dev/cdrom -data name.iso, I get the
following message:

[INDENT]cdrecord: Warning: using inofficial version of libscg
(ubuntu-0.8ubuntu1 '@(#)scsitransp.c      1.91 04/06/17 Copyright
1988,1995,2000-2004 J. Schilling').
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   :
Vendor_info    : 'TOSHIBA '
Identifikation : 'DVD-ROM SD-R2412'
Revision       : '1R19'
Device seems to be: Generic mmc2 DVD-ROM.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE
Supported modes:
cdrecord: Drive does not support TAO recording.
cdrecord: Illegal write mode for this drive.[/INDENT]

There are NO supported modes for this drive!  Any ideas as to what is
going on?

---

### Post by ssam on 2005-11-28
is it a cd write? it might just be a dvd drive.

can you burn a cd using nautilus, right click (f12) on an iso file and choose 'write to disk'

---

### Post by Entity on 2005-11-28
[QUOTE=ssam]is it a cd write? it might just be a dvd drive.

can you burn a cd using nautilus, right click (f12) on an iso file and choose 'write to disk'[/QUOTE]Or maybe a combe drive. I don't know if this will help but make sure DMA is enabled :

```
sudo hdparm -d1 /dev/cdrom
```

Add this at the end of your /etc/hdparm.conf file to enable DMA on system startup :

```
/dev/cdrom {
       dma = on
}
```

And try using sudo to burn.

---

### Post by fidlet on 2005-11-28
Enabling DMA did the trick!  Thanks so much.

---

### Post by Entity on 2005-11-28
[QUOTE=fidlet]Enabling DMA did the trick!  Thanks so much.[/QUOTE]You're lucky it was just not working before... On my powerbook it was begining to burn but failing right after... I screwed a couple of CDs because of this :)

---


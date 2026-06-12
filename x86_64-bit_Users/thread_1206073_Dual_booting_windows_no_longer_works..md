---
title: "Dual booting windows no longer works."
date: 2009-07-06
forum: x86 64-bit Users
---

### Post by acidblue on 2009-07-06
I had a system failure(cmos battery + other stuff) and had to do 
a complete re-install of Ubuntu 9 and WinXP.
Both installs went fine,(Win first then Unbuntu).
But when i try to boot into XP i get an error: System Exec file not found.
Or something similar, can't remember exactly.

Here is what fdisk -l returns:
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       18662   149902483+  83  Linux
/dev/sda2           18663       19457     6385837+   5  Extended
/dev/sda5           18663       19457     6385806   82  Linux swap / Solaris

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4e5d0e61

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24792   199141708+   7  HPFS/NTFS

And here is my current menu.lst file:
I've shortened it just so you can just see the WinXP part.

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
map		(hd1) (hd0)
map		(hd1) (hd0)
chainloader	+1

One HD is IDE the other SATA.
WinXP is the first HD Unbuntu the 2nd.
this worked fine before, the only difference is grub is on MBR of the 
WinXP HD instead of the Unbuntu HD.
Both HD are Master-no slaves.

---

### Post by Sef on 2009-07-07
> WinXP is the first HD Unbuntu the 2nd.

The fdisk says the opposite.  > /dev/sda1               1       18662   149902483+  83  Linux> /dev/sdb1   *           1       24792   199141708+   7  HPFS/NTFS

>  Both HD are Master-no slaves. 	

Try setting one to slave and see if that helps.

---

### Post by acidblue on 2009-07-07
I can't Winxp is on ide and Ubuntu is on sata.

---

### Post by merlinus on 2009-07-08
Try changing this:

title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
map        (hd1) (hd0)
map        (hd1) (hd0)
chainloader    +1

to this:

title        Microsoft Windows XP Professional
rootnoverify    (hd1,0)
savedefault
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

---

### Post by acidblue on 2009-07-08
When i change it to hd1,0 .
I get: Error 13 unsupported executable file.
When it's hd0,0 i get' Starting.....  with a blinking cursor, but win 
never loads.
I suppose i could get my win install cd and do FIXMBR, but that will
over write grub. then i would have to reinstall grub, which i don't know
how to do, have it installed to /root of Unbuntu disk like it was before
so i don't end up having the same problem.

---

### Post by merlinus on 2009-07-08
So maybe despite the results from fdisk win is on on hd0.  In that case, you do not need map statements.

Try this:

title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1

---

### Post by j0eb0b on 2009-07-08
You might try downloading SuperGrub to a CD, setting the bios in the PC to boot from the CD and see if you can fix your MBR.  I have been using SuperGrub to switch between XP, 9.04 and Windows 7 in a disk environment similar to yours.

---

### Post by sdlynx on 2009-07-08
If you just did a clean install why not just do it again..?  Unless of course you've already started using Windows and Ubuntu

---

### Post by acidblue on 2009-07-08
> **merlinus said:**
> So maybe despite the results from fdisk win is on on hd0.  In that case, you do not need map statements.

Try this:

title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1

Thanks Merlinus, that did it.
Whew ! for a minute i thought i was goning to have to
re-install both OS's.
You the man!

---

### Post by merlinus on 2009-07-08
Excellent news!  Life in Darkside just got a whole lot better!  :biggrin:

---


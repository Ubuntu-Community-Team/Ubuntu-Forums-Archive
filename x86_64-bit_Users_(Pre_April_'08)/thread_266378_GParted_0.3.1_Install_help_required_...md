---
title: "GParted 0.3.1 Install help required .."
date: 2006-09-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by perimere on 2006-09-27
G'Day,

I'm running 64-bit 6.06 Dapper Drake. 

I have a 1.0TB ext3 partition that I'm trying to resize (up to 1.5TB). Gparted 0.1 which is installed from the 6.06 repository is unable to do this. 

It reports the new size as being -666566MB and the resize dialogue just exits after about a minute leaving the partition unchanged - but thankfully still useable ;)

I have downloaded the tarball for 0.3.1 from the GParted site, but am running into issues trying to .configure.

I have installed the libgtkmm-2.4-dev package, but I believe gparted requires 2.8 as a dependency.

Has anyone installed the newer version of GParted and have some tips to share?

Cheers

perimere

---

### Post by bigken on 2006-09-27
I would use the [gparted]("http://gparted.sourceforge.net/livecd.php") liveCD much easier ;)

---

### Post by perimere on 2006-09-27
I had tried that. I need to invest some time in identifying the correct RAID card module to use.

I do prefer having the software available in Ubuntu though and not having to boot off CD to perform partition activities .....


Cheers

perimere

---

### Post by perimere on 2006-09-27
Hit a dead end on the LiveCD. It appears that my RAID card is not support.

The Gparted FAQ ([http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)) indicates a dependency of Gtkmm >= 2.8.x. It looks like 6.06 installs the 2.4 lib (libgtkmm-2.4-dev)?

Anyone had any luck finding/installing a 2.8 package? Does Eft ship with a later version of gparted (i.e. 0.3.x) or the Gtkmm lib??

Just looking for some insight on the best way to progress this.

TIA

perimere

---

### Post by bigken on 2006-09-27
eft knot3 has gparted 0.2.5

---

### Post by perimere on 2006-09-29
Thanks BigKen,

Well I hate to admit it, but in the end I used my second partition with XP on it, and used Partition Magic.

A bit let down that I had so many issues under Linux, as Im' working hard on migrating away from MS.

As a side note, qtparted didn't work either, so it wasn't just that gparted hasn't matured enough yet :(

---


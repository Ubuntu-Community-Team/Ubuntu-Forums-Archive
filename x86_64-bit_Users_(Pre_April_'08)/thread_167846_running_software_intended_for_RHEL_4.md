---
title: "running software intended for RHEL 4?"
date: 2006-04-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by 5horizons on 2006-04-29
Hello,

I've got a bit of a problem here.  I've been trying to use CentOS 3.6 and 4.3 for x86_64 on a nice new dual opteron machine because the seismic processing software we use requires RHEL 3/4 (this software is essential for this machine).  3.6 was giving me the occasional lockup when someone logs out.  4.3 has serious problems with the 3ware 9500S sata raid controller.  I've spent several days trying to get CentOS 4 on this machine.  I detest using and looking after Redhat boxes, and would love to use Ubuntu on this machine (apt is amazing, upgrades are almost painless, and the stability and overall quality control appear to be much better).  Other reports indicate that Dapper works nicely with the 3ware raid cards "out of the box" which is always nice.

The processing software is installed from a CD or tar.gz file, and contains some pre-compiled software (a bit of C and Fortran) but nothing necessarily redhat specific.  I've installed the 32 bit version of a couple of Ubuntu boxes, and it works fantastically (apart from some minor X issues).  

The link above indicated that the 64 bit version is only compiled for RHEL 3 (and now 4), which has an older glibc version (2.3.2 and 2.3.4 respectively) than Ubuntu breezy or dapper (I forget what version these use).  My question is: Is there a way to get this software to work on Ubuntu?  Can I run an older version of glibc for this software?  Does it really matter - should I just try it with breezy/dapper?

This machine has 16 gigs of ram (I know, pretty wild!) so its not reasonable to use the 32 bit version of CentOS or Ubuntu.  I had Breezy for x86_64 installed on this machine before I was forced to change to CentOS - so I know it works very well.  I just need to know how to support binaries for a different version of glibc (the company that makes the software doesn't want to support any more distros).

Thanks in advance for any info

---

### Post by tseliot on 2006-04-29
[QUOTE=5horizons]This machine has 16 gigs of ram (I know, pretty wild!) so its not reasonable to use the 32 bit version of CentOS or Ubuntu.[/QUOTE]
You can recompile the kernel and enable the support for more than 4GB.

---

### Post by 5horizons on 2006-04-29
the 32 bit version is limited to 4 gigs (if I remember correctly) but the 64 bit version uses all 16 gigs.  I'm pretty sure that the 32 bit version can't use any more than that, unless I'm mistaken.  I'll look into it.

Thanks

---

### Post by tseliot on 2006-04-29
[QUOTE=5horizons]the 32 bit version is limited to 4 gigs (if I remember correctly) but the 64 bit version uses all 16 gigs.  I'm pretty sure that the 32 bit version can't use any more than that, unless I'm mistaken.  I'll look into it.

Thanks[/QUOTE]
It can support up to 64GB if you enable the support in the kernel. Below is a screenshot of menuconfig on my computer:
[[IMG]http://img216.imageshack.us/img216/3473/memorysupport0gy.th.png[/IMG]]("[URL=http://img216.imageshack.us/my.php?image=memorysupport0gy.png)"][[IMG]http://img216.imageshack.us/img216/3473/memorysupport0gy.th.png[/IMG]](http://img216.imageshack.us/my.php?image=memorysupport0gy.png)[/URL]

---


---
title: "Installing a new graphics card"
date: 2008-03-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by johnwillyums on 2008-03-10
Hi all. I'm running Ubuntu 7.10 64x in a dual boot with Vista HP 64x.
At the moment I'm using an nVidia 8600GT but would like to upgrade to an 8800GT bit it seems the dual boot complicates things (especially as I'm pretty non techy).
Vista forums advise me to boot Vista into safe mode, uninstall the old drivers, run a driver cleaner, swap cards and then install the appropriate driver from nVidia's website.
However since installing Ubuntu my boot menu has changed and Ubuntu+recovery mode+memtest +Vista/ Longhorn are my only choices.
I've looked in setup (del) and BIOS (tab) and I can't see a way to boot Vista into safe mode. Mind you the whole grub and bash thing is incomprehensible to me I'm afraid so I might be missing the obvious.

Can anybody help me with some simple instructions please?
Also, if I do manage to install a new card will it work in Ubuntu?

Thanks in advance, John:confused:

---

### Post by Kilz on 2008-03-10
> **johnwillyums said:**
> Hi all. I'm running Ubuntu 7.10 64x in a dual boot with Vista HP 64x.
At the moment I'm using an nVidia 8600GT but would like to upgrade to an 8800GT bit it seems the dual boot complicates things (especially as I'm pretty non techy).
Vista forums advise me to boot Vista into safe mode, uninstall the old drivers, run a driver cleaner, swap cards and then install the appropriate driver from nVidia's website.
However since installing Ubuntu my boot menu has changed and Ubuntu+recovery mode+memtest +Vista/ Longhorn are my only choices.
I've looked in setup (del) and BIOS (tab) and I can't see a way to boot Vista into safe mode. Mind you the whole grub and bash thing is incomprehensible to me I'm afraid so I might be missing the obvious.

Can anybody help me with some simple instructions please?
Also, if I do manage to install a new card will it work in Ubuntu?

Thanks in advance, John:confused:

As long as its from Nvidia to Nvidia you may not have any issues.

---

### Post by warp99 on 2008-03-10
You should have no problems because the same driver is used for both cards under Linux:

[http://www.nvidia.com/object/IO_18897.html](http://www.nvidia.com/object/IO_18897.html)

Just insert the new card and boot, there should be no issues whatsoever. :)

---

### Post by johnwillyums on 2008-03-11
Thanks very much to you both. That's very reassuring and I'm going to order the card today.
Cheers, John

---

### Post by marstein on 2008-03-14
In Vista AFAIK you should uninstall the drivers, shutdown, install card, boot, install the drivers (check for the latest) and then reboot again. 
You can boot into safe mode by pressing F8 after selecting Vista in the boot screen.

---


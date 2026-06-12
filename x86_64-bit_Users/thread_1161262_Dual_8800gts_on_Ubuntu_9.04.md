---
title: "Dual 8800gts on Ubuntu 9.04"
date: 2009-05-16
forum: x86 64-bit Users
---

### Post by The_Giver on 2009-05-16
So I have been trying to install the nvidia drivers for the longest time... I can't even get one video card to work correctly. The saddest thing is this worked out of the box inside a VM.. all monitors worked nicely.... sigh.


Anyway, I'm using the x64 bit version of 9.04.

I tried doing a lot of things, including installing from the command line using the nvidia drivers found:

[http://www.nvidia.com/object/linux_display_amd64_180.51.html](http://www.nvidia.com/object/linux_display_amd64_180.51.html)




I followed this tutorial:

[http://ubuntuforums.org/showthread.php?t=747210](http://ubuntuforums.org/showthread.php?t=747210)


I also tried this:


[http://www.thinkingserious.com/2008/04/19/fix-nvidia-drivers-after-hardy-heron-rc1-upgrade/](http://www.thinkingserious.com/2008/04/19/fix-nvidia-drivers-after-hardy-heron-rc1-upgrade/)




I also tried this:

[http://ubuntuforums.org/showthread.php?t=1054842](http://ubuntuforums.org/showthread.php?t=1054842)




So with all of them, doing startx or nvidia-settings or gdm start.. gives me crap about either "fatal error, no screen found" or... some variation of that.


My xorg.conf file is really mostly empty.. I don't even see resolutions for the display. I would post the xorg.conf file of each step.. but that means no xserver .



Thanks

---

### Post by pixel :-) on 2009-05-17
Have you tried to install the driver from the apt-get ? The tutorial you are giving are quite old(8.04-8.10), normally the drivers must be available from the official repos by now.

---


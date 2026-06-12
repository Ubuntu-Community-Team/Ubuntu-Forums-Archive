---
title: "[SOLVED] Using the Grub to start ubuntu"
date: 2007-11-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by Fat.Baztard on 2007-11-09
Hi 

I did an upgrade to Ubuntu 7.10 and upgraded my ATI cards.

Now nothing happens after the Ubuntu loading page appears.  My monitor just shuts down. Ive already posted a thread for this but in the meantime could someone post a link or tut showing me how to use the GRUB to open Ubuntu. Even if i load Ubuntu in recovery mode and type in EXIT in the GRUB the same thing happens.I read on a post that doing that should fix the issue.

Its driving me nuts. 
Thanks  
G

FYI:My previous post is [http://ubuntuforums.org/showthread.php?t=605922](http://ubuntuforums.org/showthread.php?t=605922)

---

### Post by dabl on 2007-11-09
A lot of information about Grub is here:

[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)


And more is here, if you want to make a super Grub boot CD:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

However, Grub is only going to boot what you have, and apparently what you have is a borked X server.  You might want to try booting a Ubuntu Live CD, and then mounting your root partition and editing your /etc/X11/xorg.conf file to remove that last tweak that took your monitor down.  You can always set it up as a VESA display while awaiting a better solution to the ATI driver issues.  :)

---


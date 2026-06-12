---
title: "dual boot install issue - cannot boot Ubuntu"
date: 2005-12-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by etien on 2005-12-28
Hi there, great forum, and from what I read, great OS too. First question here, hopefully the last... Here's the situation :

G5 1.6Ghz
2 HDs SATA (80 & 160 Go)

MacOS 10.4.3 on first HD
Installing Ubuntu 5.10 on a 15 Go partition on second HD.

Everything went fine, I had the dedicated partition reformatted automatically by the Ubuntu installer, who created 3 new partitions within the allocated 15 gigs, a boot, a ext3, a swap.

All hardware, network, etc discovered and automatically setup, installation ok, I'm asked to take out the CD and reboot to finish installation. Done.

The mac reboots to 10.4.3.

D'oh I think, this is a dual boot machine now, should've hold Alt at startup. I try this, get to the boot panel where you can choose a system, (all detected ok, 2x10.4.3 as I have a CCC clone of my main system on the second HD, and 1 Ubuntu), I select Ubuntu, click OK.

Black screen, few lines, I'm asked to press:

l for GNU/Linux
x for MacOSX
c for CDrom

I press l (as in lower case L), but it brings me back to the boot panel.

And there you go, my problem. I can't seem to be able to boot into Ubuntu. I have searched the net, read all threads tagged "dual boot" on the Mac section of this forum, no answers or mentions of this particular issue. I have read here and there that you could edit yaboot.conf for dual booting issues (not this particular one though), but the Linux volumes are invisible to 10.4, so no easy way to do this apparently. I'm downloading the Ubuntu LiveCD as we speak to try to mount the volumes and get to the conf file, but in the meantime I thought I'd drop you guys a line or two...

Any help very much appreciated !

---

### Post by Rxke on 2005-12-28
Are you familiar with the open firmware boot? (altctrl O F or something like that, i keep forgetting...)
There you can boot directly, if the bootloader works, problem is, knowing the exact name of the partition... It would be a way to know it's bootable at all...

---

### Post by etien on 2005-12-28
I know and sometimes use the open firmware (to reset nvram for instance). I'll give this a try (if I manage to find the right command and partition name that is...)
Thanks a lot, that's at least something I haven't tried yet !

---

### Post by Rxke on 2005-12-28
```
boot hd:<partition number>,yaboot
``` should do it... I think (the # is the bootpartition (ext2) so boot hd:12,yaboot or something similar.

errrr... But not sure how to do that with two disks....

---

### Post by etien on 2005-12-28
I've just reformatted my first disk into three partitions, one for 10.4, one for Linux and for data. And will be starting reinstall of Ubuntu on this first HD in a coupla minutes. If still no luck, I'll try in open firmware.
thanks again for your help.

---

### Post by etien on 2005-12-28
reinstall on first HD solved it. No problem whatsoever. Seems so that installing on secondary HD is not possible !

thanks a lot for your help.

---

### Post by MonolithTMA on 2005-12-28
As we discussed in another recent thread, OS X's Startup Disk will interfere with Yaboot, so look out for that as well.

---

### Post by Mukke on 2006-05-09
hmmmm
i run in sort of the same problem tho i guess i did something wrong to install Ubuntu itself cause at the end of my installation it sais it cannot make my yaboot.conf file or sumething and that i gotta do it by hand.

If i startup with alt i see my secaond HD but with an os x icon (well they both have it). But my 1st HD (250G) is running macosx and my 2nd HD (80G) is format UFS an during the install i selected that one to format it to be able to install Ubuntu. The 2nd drive is an external FireWire drive.

Edit:
So How do i install that yaboot.conf file manual?
What has to be in thet file ?
And where does the file has to be ?

---


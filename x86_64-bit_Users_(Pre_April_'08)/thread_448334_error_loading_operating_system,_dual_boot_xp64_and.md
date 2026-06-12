---
title: "error loading operating system, dual boot xp64 and ubuntu 7.04"
date: 2007-05-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by vecryn on 2007-05-19
Ok, first question I guess is can you have Windows xp64bit and ubuntu having a dual boot system?  I'm just wondering if xp64 is what is causing this issue.

I have it setup so far like this.
C drive is 62gig Master drive
D drive is 100+gig about 170gig or so (I partitioned a 250gig drive having one partition 62gig, the rest went to the other partition.)
E drive is a slave HD 40gig

I installed windows xp64bit onto the 62gig partition, booted just fine, installed all the updates etc, then installed ubuntu 7.04 onto the 40gig slave HD.  When the install was complete it asked me to reboot, and to remove the install cd from the cd tray.  I did this and as soon as it loaded up it got to the point where it would boot saying Boot from cd, then since no disks are in the cd try it tried booting from the hard drive and gave me "error loading operating system"

If I put in the windows xp64 install disk it will get to this part again, and says to boot from cd press any key.  if I touch nothing at all it will jump over to booting up ubuntu.  Windows xp64 is in this list of options of what to boot but if I select it nothing happens.  it will load ubuntu though, but only if the install disk is in the tray, either windows or ubuntu's if not it gives the error loading operating system message.  So i'm not fully sure what the problem is here.  it seems like a boot issue, but at the same time it wont load windows xp64 at all even with the cd there.  I tried repairing it and I still have the same problem.

---

### Post by eddieb on 2007-05-19
The answer to question one is yes.
I am assuming both drives are ata as you have said the 40 gig is a slave,( if the 250 was a sata the 40 should be a master). It sounds to me as if the grub is confused.
I would suggest reinstalling Windows on the 250 and then install Ubuntu on the same drive.
The 250 would have to be faster than the 40 and therefore you would gain when using 64 bit.

---

### Post by vecryn on 2007-05-19
Ok, i'll try that out.  thank you very much for your responce.  And yeah both drives are ata

---

### Post by Sayonara on 2007-06-30
I had this error but under slightly different circumstances.

I have two SATAII drives in a striped RAID array, which is my main disc, split into two partitions - one for Windows, one is for Ubuntu.

Thoe two drives use the native SATA ports on my Gigabyte GA-K8N Ultra-9 motherboard. I have been using WinXP 64 very successfully from the array for several months.

On my primary IDE channel, I have a Maxtor ATA drive (documents, thank goodness I backed them up) and my DVD rewriter.

The problem is that when I tried to install Ubuntu today, it correctly identified the free partition on the RAID array as being the proper location to install itself (using "guided install, largest free space"), however on restart after the installation finished, POST and BIOS all went as normal until the bit where the OS or choice of OSes should have appeared. Then I got the same error message as vecryn - "error loading operating system".

I've had to cobble together a working XP64 installation with a partial reinstallation :(

I think what may have happened is that the bootloader got stuck on hd0, which presumably is the ATA drive, since its partitions are labelled hd1, hd2 etc, whereas the partitions on the RAID array are labelled s-something.

Has anyone got any ideas or experience with this problem?

---


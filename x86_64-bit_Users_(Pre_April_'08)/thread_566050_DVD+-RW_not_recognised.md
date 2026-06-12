---
title: "DVD+/-RW not recognised"
date: 2007-10-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by giddylad on 2007-10-03
Before I begin, I know this subject has been brought up a hell of a lot around here but i've done A LOT of searching around on the web for this and tried many different ways of attacking it but i'm still at a loss so I need a bit of help from you guys/gals if at all possible...?

My setup:

ASUS P5K-SE
C2D E6550
2Gb PC2-6400 RAM
1x 250Gb SATA HD (main)
1x 160Gb IDE HD (extra)
1x DVD+/-RW IDE (Optiarc (NEC) AD-7170A)

There is only one IDE port on my motherboard so both the IDE hard drive and DVDRW are connected to it. The DVDRW is set to master, and the hard drive to slave. BIOS recognises both drives.

Windows is installed on the SATA drive.

I'm using the 6.06 alternate install CD burned at 4x and verified (md5). I have already made a 10Gb partition (ext3) and 2Gb partition (linux swap) on my SATA hard drive, right after my XP partition of 50gb.

Upon launching the boot CD, i'm asked what to do - I chose to install (text). I verify language and country and then i'm greeted with a prompt stating that no CD-ROM has been found. However, there obviously HAS been or I wouldn't have been able to get this far.

I have tried booting without the IDE HD attached (just the DVDRW and SATA HD), and I have tried changing the jumpers on both drives to cable-select.

I have tried a different DVD-ROM drive (old one I had spare).

I read somewhere that the install likes a floppy drive (for some reason), so I installed my old one and (as advised) placed a blank formatted floppy in the drive whilst the installation was running. But this hasn't done anything at all.

Nothing has worked. I did try to install the distro from a seperate partition as advised elsewhere, but couldn't get GRUB to boot properly. I could select GRUB from the startup menu, but the machine either immediatley rebooted, or I was just taken to a GRUB > prompt and didn't have a clue what to do.

Finally, I tried a different version - 7.04. This, unfortunatley, had the same problem.

I'm completley lost. If I could get 'CD-ROM drivers', perhaps that would help. However, I can't find anything on this subject.

Can anyone help?! Has this been fixed yet? Is there a release somewhere that works around this problem?

I would REALLY like to start using Ubuntu on this new machine. I did have a chance to play with it on my old P4, but sadly, it's gone to a better home now.

Many thanks in advance.

---

### Post by giddylad on 2007-10-03
I've come across [this]("https://help.ubuntu.com/community/SmartBootManagerHowto") article. Tried it and not even the boot manager on the floppy recognises my DVDRW.

I did come across another article (about 2/3rds the way down [this ]("http://www.24b6.net/?cat=3")page that suggests the following:

After choosing language from the boot installer, press ALT+F2, then enter and type:
insmod /lib/modules/2.6.xxxxx/kernel/drivers/cdrom/cdrom.ko
insmod /lib/modules/2.6.xxxxx/kernel/drivers/ide/ide-core.ko
insmod /lib/modules/2.6.xxxxx/kernel/drivers/ide/ide-generic.ko
insmod /lib/modules/2.6.xxxxx/kernel/drivers/ide/ide-cd.ko
insmod /lib/modules/2.6.xxxxx/kernel/drivers/ideide-core.ko

Now, obviously this article is for an older version of Linux, but it does state that it corrects the problem when booting from an IDE drive with a SATA motherboard. The 2.6.xxxxx directory doesn't exist but i've no clue as to how to find out where these files may be on the CD so that I might try this method.

Is it possible that newer boards are cutting out IDE controllers?
Would a SATA CD drive be better to install from?

All suggestions welcome

---

### Post by water8 on 2007-10-19
I am using GA-G33M-S2H, and have similar problem of not detecting IDE CDROM. My quick fix is use a USB cdrom. or you may try a SATA cdrom. Or i believe someone is using Flashdrive.

---


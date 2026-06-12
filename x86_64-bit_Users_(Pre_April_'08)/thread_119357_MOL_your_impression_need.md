---
title: "MOL: your impression need"
date: 2006-01-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by Lanrond on 2006-01-19
Hi all, this is my first post in the technical section, so I'm a little excited. ;) 

I've been tried Ubuntu on my iMac DV (G3) for a couple of week (live distro) and now I'm going to install it.

Anyway, I still have a lot of sw that runs on MacOS (9) and I would like to keep on using it at least for the time needed to find out what are the best alternative applications.

I know I must make a complete back-up of my system, but then I could:

a) reformat my HD making 2 partitions
b) restore my MacOS9 on one of the two partitions
c) install Ubuntu on the other
d) dual boot

or

a) install Ubuntu from scratch
b) install MacOnLunux
c) use my Mac apps *inside* Ubuntu.

Can you point out the pro/cons of the two choises, please?
Has anyone had any experience with MOL to share?

Consider that my G3 is 400MHz, my HD is 40 GB and the memory installed is 768 MB.

Thank you very much in advance.

Greetings

---

### Post by Peter76 on 2006-01-19
Another solution ( maybe ); post what apps you want to keep using in macos 9 and we tell you about the similar ubuntu ones, so you only need ubuntu

---

### Post by Lanrond on 2006-01-19
[QUOTE=Peter76]Another solution ( maybe ); post what apps you want to keep using in macos 9 and we tell you about the similar ubuntu ones, so you only need ubuntu[/QUOTE]

Apart from some games (**Caesar3**, **Ferazel**, **MidnightMansion**, **Boxikon**,...) I can do without... maybe ;) , the apps I intensively use are mainly **Graphic Converter**, great shareware for image manipulation, converting and printing, **Toast** for burning CDs, **AppleWorks** (OpenOffice can be a substitute maybe?), **Retrospect Xpress** for backing-up. I already know of the obvious substitutions for browsing and mailing, but I think it could be difficult to get rid of **MacSoup** as newsreader.

There are also many other apps I use, but they are not so essential, nonetheless I would try to keep them.

---

### Post by tmeier on 2006-01-19
MOL is a good way to still use your Mac apps and run linux.  However, I think that to run MOL you still need to have os9 installed on a partition, which also allows for dual boot.  I would suggest making 2 partitions and installing os 9 on one of the partitions (I think 2nd but check in this forum to know for sure) FIRST and then leave the other as free space and let ubuntu install format it for you.  

Then follow the instructions on the wiki for maconlinux.  I even have it working with tiger on a powerbook g4.  Hope this helps.

---

### Post by Ptero-4 on 2006-01-19
Maconlinux doesn't need a partition with OS 9. You can use a disk image to install OS 9 into. You install OS 9 by booting off the OS 9 CD (Yes, mol can boot off a CD).

---

### Post by Lanrond on 2006-01-20
[QUOTE=Ptero-4]Maconlinux doesn't need a partition with OS 9. You can use a disk image to install OS 9 into.[/QUOTE]

Are you saying that I could use a disk image of my mac disk located (for example) on an external HFS+ drive and use it to run MacOnLinux?

Can anyone share his/her impression about the performance?
Do you think it's passably responsive?

---

### Post by ssam on 2006-01-20
there are a few advantages to using mol with an image file (its easier to move/resize files than partitions). you might still be better with a real bootable mac os 9 partition.

that way if for some reason you need to boot to mac os 9 you can. while you are migrating between operating systems its useful to have a fully work version of the old one. MOL is good for running mac os and mac os software, but it does not have full access to the real hardware. you may have a hard time getting things like cd writing or printing to work in MOL.

then i would aim to use all linux native software. once you can go without mac os, then do a full transition

---

### Post by Lanrond on 2006-01-20
Thank you all for the info.
I think dual boot is what I need, at least for now.

---

### Post by jdp on 2006-01-23
[QUOTE=Lanrond]Thank you all for the info.
I think dual boot is what I need, at least for now.[/QUOTE]

You should also know that you can resize your OS 9 partition without wiping it.  There is a [forum post](http://ubuntuforums.org/showthread.php?t=89960) on just this subject.  I've successfully done it myself on an 8500/120 running 9.1.

---

### Post by Lanrond on 2006-01-24
Thank you jdp.
I had already read the article, but I assumed that the described procedure was valid **only** for an OSX partition.
So I prepared a back-up of my OS9 partition to reformat the drive, but now I think I will try this hack (just to be prepared for some future need).

---


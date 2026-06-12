---
title: "Installing Breezy PPC on Pismo w/ bad DVD drive (i.e.: Install from HD)"
date: 2006-01-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by fiestaforever on 2006-01-23
Hi, 
I have a Pismo (G3/400) I want to put 5.10 on. Unfortunately the DVD drive is broken (like most of those LG drives). 
So I'll have to repartition *somehow* (probably via USB stick/HD) and have no idea how to proceed beyond that. There will only be OS 9 on it, there's no way to get OS X on it.
There is a guide for install from HD [http://www.ubuntuforums.org/showthread.php?t=28948]("http://www.ubuntuforums.org/showthread.php?t=28948"), but I think it only applies to x86. 
Any ideas how I can install PPC from a hard drive? I think I'll have to copy some files to the OS 9 (HFS+) partition, or onto the external hard drive (probably on a FAT32 partition, as the Pismo is my only Mac around at the moment). I will only have max 3-4 GB of space for the root/home partition left, btw (6 GB hard drive, OS 9+Mac apps have to stay for now).
TIA

---

### Post by deteringb on 2006-01-25
I have a Pismo as well and Ubuntu works GREAT!! (384mb RAM, 12GBHD).  Much better than ydl or OSX.  The tricky part for you is going to be keeping 9 while partitioning the drive.  I don't see how it can be done....

---

### Post by Muchmore on 2006-01-27
I am trying to install Breezy onto a Beige G3 and I was wondering if you know of any guides that might help?  Do you have any advice on this install?

Thanks,
Andrew
Muchmore

---

### Post by fiestaforever on 2006-01-27
While searching for a solution for my Pismo, 
I've found several sites referring to beige G3s. 
Because they weren't of much help for me (the beige G3 is an "Old World" Mac, the Pismo is a "New World" Mac, both are very different in respect to booting/installation; the difference is in the firmware), I didn't take too much notice, but here are two (Google searching will certainly give you many more and better sites; search the forum as well): 
[http://www.gifford.co.uk/~coredump/beigeg3.htm](http://www.gifford.co.uk/~coredump/beigeg3.htm) (English)
[http://www.linux-france.org/macintosh/ubuntu504_G3.html](http://www.linux-france.org/macintosh/ubuntu504_G3.html) (French) 
Not necessarily suitable for Breezy, but a start.

---

### Post by bongshoe on 2006-01-29
If your drive is failing in the same way as mine you might want to try a DVD install, as my pismo's dying optical drive still seems to read DVD(r) fine, though CDs are almost a lost cause at this point unless I eject and reload them again and again.. 

I'm thinking about attempting the install on my pismo/400, though I don't like the idea of losing my OS 9 partition and I'm not sure performance would be much better than X.4.4 with only 256mb under the hood, so I'll see how it goes on the 12" 867 first I guess.. is there any documentation relating to triple booting OS 9, X and Ubuntu?  Anyone know if it is possible?  :???:

---

### Post by mjlee105 on 2006-01-31
I am also trying to load Ubuntu to a Imac G3 DV (pink) with a busted DVD player,  not willing to spend the 300 dollars to have it fixed.  I have tried attaching a USB CD drive to it, but it will not boot from the drive. I do not care if os9 is blown away.  just as soon have a pure linux g3.  Any suggestions.  please keep any answers to english.  i speak MCP but not linux or unix.  I got the intel version running on an old Emachine pc the other day, and it runs rings around the win-me that was on their before.

---

### Post by ssam on 2006-02-03
if the machine will do target disk mode (hold 'T' at boot, and it will pretend to be a firewire disk) then you may be able to repartition and install from another mac.

you could take the hard drive out, put it in another mac, install ubuntu, and then swap the disk back.

buy a new cd drive. i think 300 dollars to fix the cd drive in an imac is a bit steep. you should be able to find a drive much cheaper and install it your self. i have upgraded the hard drive in an imac dv, i dont think its much harder to get to the cd drive.

---


---
title: "error 21"
date: 2006-12-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by mitpat on 2006-12-30
After installing ubuntu 6.10 (64 bit edition)  on my sony vaio AR21s i get error 21 on boot and then it freezes there

any idea how to fix it, thanks

---

### Post by pseudonym on 2006-12-30
Did you change anything in the BIOS boot order? That error means that grub can't find the disk it's set to boot from...

---

### Post by mitpat on 2006-12-30
no i haven't changed anything in the bios boot order except when i moved cd boot to first before i installed ubuntu

i'm completely new to this and this is my first time installing any form of ubuntu or linux for that matter

---

### Post by pseudonym on 2006-12-30
Your model vaio has 2 hard drives, right? Is windows installed on one, and ubuntu now installed on the other (or so you thought)? A little info is needed on the layout of your hard disk(s)...

---

### Post by mitpat on 2006-12-30
windows is installed on the first drive and ubuntu is installed on the second, i hope

---

### Post by ucsdrake on 2007-01-02
hey, im having the exact same problem at the moment and just like you, this is my first encounter with linux at all (and ubuntu). 

I have Windows on my first HDD (its an interior HDD with only windows due to work)
and for my second HDD its an external (Kaser 250gb) and I set it up with the following partitions

Windows (NTFS)
Lin/Win Shared (Fat32)
Linux Swap (Linux Swap)
General Linux (EXT3)

when i was completing the intsallation, I noticed it as asking where i would like the GRUB to be installed.  I picked the default (hd0) [i didnt know any better]

since searching the forums I've found that I should have (or at least i believe) i should have placed (hd1) in the field since then i think ive found a decent thread on how to fix this 

[http://ubuntuforums.org/showthread.php?t=24113&page=3&highlight=reinstall+grub](http://ubuntuforums.org/showthread.php?t=24113&page=3&highlight=reinstall+grub)

can any experianced user of ubuntu please tell me if im on the right track with this? and if this is the right way to go about fixing the problem (i think you have the same one as me mitpat)

---


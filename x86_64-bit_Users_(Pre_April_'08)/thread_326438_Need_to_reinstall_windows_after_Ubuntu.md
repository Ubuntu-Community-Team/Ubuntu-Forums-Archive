---
title: "Need to reinstall windows after Ubuntu"
date: 2006-12-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by eric.stone on 2006-12-27
After running Ubuntu, Knoppix, Mepis triple boot on my AMD 64 for a year I have to renstall windows for professional purposes.   I understand that I must first install Windows and then install Ubuntu.  My problem is that I can't figure out how to install Windows.  My BIOS is set to boot to my CD but it neverthless loads GRUB and doesn't see the Windows install disk in my CD.
Thanks in advance,
Eric

---

### Post by pseudonym on 2006-12-27
Are you sure your windows install disk is in good condition? Can it be read by another computer?...

---

### Post by eric.stone on 2006-12-27
The disk is good.  I can see it on Ubuntu.   
E

---

### Post by shutterbc on 2006-12-27
Hmm... the CD-ROM boot should be controlled by your BIOS and never hit your hard drive if you have a good CD.  Unless I am missing something here, you might want to try disconnecting your hard drive and just try to boot off the CD straight away.  Are you able to boot off of any other CDs?

---

### Post by hinzel on 2006-12-28
i know that this sounds stupid, but double check that you saved your bios settings when you exited it.

do you have 2 cd roms installed by any chance? double check that you have the right one in top priority for your boot sequence..

---

### Post by kesman on 2006-12-30
And after you get to install windows, remember that it overruns your grub from mbr and you've got to restore it somehow, perhaps with a live cd or alternate install disks recovery option.

---


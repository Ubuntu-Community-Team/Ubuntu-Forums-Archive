---
title: "Question relating to dual booting"
date: 2008-03-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by Maxwell85 on 2008-03-22
Ok, so Ive dual booted windows XP professional 64, and Ubuntu 64 together, works great.  Recently, I upgraded my motherboard, processor, and ram to meet todays standards.  Ubuntu boots fine with the new hardware, finds everything, and everything works, including internet etc, Windows however does not have the drivers for the mouse or keyboard present, I suspected there might be problems with Windows after an upgrade of this magnitude.  So, I formatted my windows partition (leaving ubuntus intact) and reinstalled XP 64.  Works fine now, everything runs great, except now I dont get the boot option to get into Ubuntu anymore.  What can I do to restore this boot screen?

---

### Post by kaivalagi on 2008-03-22
Sounds like you lost your grub mbr entry, these instructions should do the trick: [http://ubuntuforums.org/showthread.php?t=224351&highlight=lost+grub+reinstall]("http://ubuntuforums.org/showthread.php?t=224351&highlight=lost+grub+reinstall")

Hope that helps

---

### Post by sandysandy on 2008-03-22
other option is to boot into Super Grub Disk ( [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/) ) and let it fix MBR for you.

have a look at this link also


[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)


regards

---

### Post by Maxwell85 on 2008-03-24
Thank you both very much :)  Ill work on this as soon as I get home from class tonight.

---

### Post by Maxwell85 on 2008-03-26
Huzzah!  Instructions for restoring MBR through Live CD worked without a hitch, thanks again!

---


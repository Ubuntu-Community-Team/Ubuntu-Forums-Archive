---
title: "Grub boot loader"
date: 2006-12-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by Chris Jones on 2006-12-30
Is there a way to stop a kernel upgrade (Kubuntu 6.06) from over writing a hand edited grub menu.lst.  Grub keeps being overwritten with kernel options I don't need.

best wishes

Chris Jones.

---

### Post by ESPOiG on 2006-12-30
just back it up and wen u do an update just copy it back

---

### Post by pseudonym on 2006-12-30
> **Chris Jones said:**
> Is there a way to stop a kernel upgrade (Kubuntu 6.06) from over writing a hand edited grub menu.lst.  Grub keeps being overwritten with kernel options I don't need.
Another way is to open up /boot/grub/menu.lst in your favourite editor, find the line 'defoptions=...', uncomment it, and change these 'default options' to the ones you use, then reboot.

Bear in mind that this maintains the same boot options for all installed kernels, so if you have more than one, and need to use separate options for each, the 'back up and copy' method might suit you better. :)

---

### Post by Chris Jones on 2006-12-30
Many thanks for the replies.

GNU/Linux has been my only production OS since Slackware 4 and my Mac SE went into retirement but I have only in the last few months used Kubuntu and Debian for less then a year and so have yet to fully learn and understand how these distros work. 

I rebuilt my desktop machine as a very low cost (AMD Sempron 2800+ with 754 pin mainboard which are at rock bottom prices) 64 bit multimedia sketch pad on which I hope to work on some ideas for multimedia verse performance. So far 64 bit Kubuntu, which started out as a Ubuntu DVD, has been easy enough to install and has proven very willing to be modified and tweaked and for my needs this is important. So far, nothing I have done has broken anything beyond an easy repair, which says something positive.

Anyways, many thanks, again.

---


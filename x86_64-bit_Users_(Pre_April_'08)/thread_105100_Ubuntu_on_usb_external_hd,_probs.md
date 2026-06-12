---
title: "Ubuntu on usb external hd, probs?"
date: 2005-12-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by trjtrj on 2005-12-17
I have an 3200+AMD 64 system and want to put Ubuntu on my 4th hd, a usb external.  HD1 has my winXPos, HD2 my winXP64 os and HD3 is a storage drive ntfs format.

My usb external has 2 primary partitions and I want to put Ubuntu on the 1st.  The second primary partition would stay ntfs.

I have done 5.10 64 instal cd and it seems to work, but when I get to the remove cd, reboot, the reboot starts Ubuntu and then crashes while loading the kernal.  What can i do to make this setup work and boot?

please reply to this post if U are an Ubuntu hi IQ type and have an answer.

---

### Post by trjtrj on 2005-12-18
Me again,

Well, I gave up trying to put Ubuntu on an external USB harddrive.  I just could not make it work.  I did learn about Ubuntu/Linux in trying to find an answer.

I put Ubuntu 5.10 on my ide slave drive, hd 1, and it works.  I put the grub on a floppy (fd0)so I only use the floppy when I want to boot Ubuntu.  I have WinXP 32 os on my C;\ hd0 and WinXP 64 on my E:\ sata hd2.  I can dual boot those os via the boot.ini on C:\ just fine.

My system is 3200+ amd64 on an msi mb, chipset nvidia 2.  Ubuntu has no problems finding my hardware.  My hb deskjet 882 works.  Don't print a test page as it uses way too much ink.  Just test with some text.

---


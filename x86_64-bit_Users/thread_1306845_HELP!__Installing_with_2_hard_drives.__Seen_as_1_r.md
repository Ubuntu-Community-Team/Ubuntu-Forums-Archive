---
title: "HELP!  Installing with 2 hard drives.  Seen as 1 raided harddrive"
date: 2009-10-30
forum: x86 64-bit Users
---

### Post by BPSPaw4 on 2009-10-30
Ok, so I've been having problems installing.  I have 2 SATA hard drives in my computer:
SATA1 - Blank harddrive (want fresh ubuntu install on this one)
SATA2 - Windows xp, works fine.

I previously have 9.04 32-bit installed on SATA-2 using it as the primary boot drive and grub to choose between linux and xp.

If both hard drives are plugged in while I try to install 9.10 I get to the Partition manager in the setup.  It shows my drives and being one 320gb hard drive (I have two identical 160gb).  So I go into the bios and make sure raid is disabled, it is.  Both the SATA hard drive settings are auto so I go back in and it still does the same thing.  

I decide to try with the SATA2 (xp) hard drive unplugged. I'm using the live cd on bootup to get into the installation.  I once again get to the partition manager and this time no hard drives are detected.  I've also tried the text install and selecting NO when it asks to load raid drivers.  

If i try booting into this hard drive (thats formatted already through windows with Ext2Fsd and works fine) it boots up the grub menu and i get Grub Error 2.

I tried clearing grub using windows recovery cd and fixmbr, thinking that getting rid of grub before installing might help but its still there.  I've been searching all around the internet for someone with this same problem but to no avial.

Anyone have any recommendations?

It does the same with the 32-bit installation of 9.10 and 9.04

---


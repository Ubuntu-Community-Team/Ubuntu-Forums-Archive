---
title: "Getting error in VirtualBox"
date: 2009-02-20
forum: x86 64-bit Users
---

### Post by steve70 on 2009-02-20
I have Virtual Box running on top of 8.10 64-bit edition. I was able to successfully create 4 Virtual machines (3 with Server 03 and 1 XP client. 

However, I get a VBox error message ('DISK_FULL'error) while I was doing updates on the machines, stating that I need to increase my HD space.

I found some solutions, but it involves gparted. Here comes the crazy questions...

1. Is there a way to mount the desktop version of gparted as an .iso image for my V'Box machines

2. If not, what's the best site to download a current .iso image for gparted for the 64-bit version (d'loaded a couple, but crapped out after mounting on machines.).....

---

### Post by Thelasko on 2009-02-23
Answer 1: NO

Answer 2: I think you are very confused.  If you use the [GParted Live CD]("http://gparted.sourceforge.net/livecd.php"), you should be able to boot from it in your virtual machine and make changes.  It doesn't matter if it's 64-bit or 32-bit.

You may have to change the boot order on your virtual machine. (under settings>general, or press F12 on bootup)

---


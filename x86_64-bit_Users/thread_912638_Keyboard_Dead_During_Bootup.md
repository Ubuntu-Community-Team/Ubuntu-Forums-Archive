---
title: "Keyboard Dead During Bootup"
date: 2008-09-06
forum: x86 64-bit Users
---

### Post by ozarkhollar on 2008-09-06
Trying to upgrade 7.10 to 8.04 with Canonical DVD (tried downloads first).  Hangs on "Language Selection" and reverts to the initramfs prompt well documented elsewhere.
 
I now notice the USB keyboard is not responding during bootup.  Cannot access BIOS nor edit bootloader.  Keyboard does not power up until after bootup begins, therefore cannot install or run the Live CD, etc.

Kubuntu only machine:

Asus A8N-E
AMD Athlon 64 X2 3800+
2 gb mem
Sony DVD RW AW-G170A
2 80G WD IDE
GeForce 7300
CK804 USB controller

This box is a year old build started with 7.04 and upgraded to 7.10 through Alt CD upgrade.
 
Any ideas on getting the Keyboard to work?  No PS/2 available to try.

---

### Post by ozarkhollar on 2008-09-07
> **ozarkhollar said:**
> Trying to upgrade 7.10 to 8.04 with Canonical DVD (tried downloads first).  Hangs on "Language Selection" and reverts to the initramfs prompt well documented elsewhere.
.

Solved.  Well sorta.  Found a PS/2 in the ditch down the road...

---

### Post by Thelasko on 2008-09-08
I've had similar problems with bootup in the Live CD.  Once I install Ubuntu, it works fine.  Thank goodness I don't need anything other than the default option in the CD's menu.

[This appears to be the bug report.]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/212928")

---


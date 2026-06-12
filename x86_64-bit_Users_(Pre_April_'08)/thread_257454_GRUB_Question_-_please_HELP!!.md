---
title: "GRUB Question - please HELP!!"
date: 2006-09-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by mrw on 2006-09-14
I have a dual boot windows/Ubuntu system with Ubuntu on a second hard drive. For some unknown reason I lost this drive and reset the MBR. As a result my system now boots to Windows. Since then I've fixed the second hard drive and everything is intact. How do I restore bootup so that GRUB is used instead of Windows MBR??

---

### Post by mrw on 2006-09-14
I've solved the problem. This was wierd. When I booted this morning the 2nd hard drive with Ubunutu was gone - nowhere to be seen. I restored windows MBR. In windows the drive didn't show up at all. I then swapped SATA ports on the the motherboard and behold the drive returned -can't explain that (this is a new computer).
I then loaded a live-cd Ubuntu and ran GRUB and installed it into the mbr and things are back to normal.

---

### Post by mitch.c on 2006-09-14
> **mrw said:**
> How do I restore bootup so that GRUB is used instead of Windows MBR??
Take a look at the article here: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

It's pretty straight forward really, just follow the instructions carefully.

---


---
title: "format a second hard drive"
date: 2008-05-02
forum: x86 64-bit Users
---

### Post by bethnesbitt on 2008-05-02
The other day I updated my ubuntu to 8.04.  I knew from playing around so much that my system was slower then it should have been, and the update was the straw that broke the camels back.

I decided to redo everything, and install the amd64 instead of the i386.  I forgot though that the amd64 would not let me in after installing because my board does not support my larger ide drive.  I then reinstalled again on my sata drive, but now I have a dual boot.

How can I get rid of the dual boot so that the IDE can be used for storage only.  I already know how to mount a second drive, I just do not know how to delete the dual boot so that I can format it.

:KS

---

### Post by Grishka on 2008-05-02
if you just want to get rid of unnecessary boot options, you can edit /boot/grub/menu.lst file and manually remove the entries you don't need. make a backup copy of this file, though, because you can make your system unbootable if something goes wrong. you can also play around with startupmanager from the repos. I think it can also provide the functionality you need, but it's not safe, either, as it has been reported to make people's systems unbootable as well.

---

### Post by bethnesbitt on 2008-05-02
> **Grishka said:**
> if you just want to get rid of unnecessary boot options, you can edit /boot/grub/menu.lst file and manually remove the entries you don't need. make a backup copy of this file, though, because you can make your system unbootable if something goes wrong. you can also play around with startupmanager from the repos. I think it can also provide the functionality you need, but it's not safe, either, as it has been reported to make people's systems unbootable as well.

Thanks, I really wanted to know what I needed to edit to get rid of the boot list when I reboot.  I figured out how to format and repartition the drive for use of just storage using qtparted.  :)

---


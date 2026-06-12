---
title: "Problem with installation - 'hdc: ide_intr: huh?'"
date: 2007-03-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by Floren on 2007-03-22
Hi,

I have a problem while trying to install Ubuntu on a AMD64 (dual core, double processor) machine.

I was trying the 6.10 version of Ubuntu and when I click on install (also happens when checking the CD for errors) I got messages of this sort:

[ 209.754682] hdc: ide_intr: huh? expected NULL handler on exit
[ 229.488865] hdc: ide_intr: huh? expected NULL handler on exit
[ 229.538083] Buffer I/O error on device hdc, logical block 176813
... (more lines similar to the ones above)


I tried an older CD with Ubuntu 6.06 and it did not work either. And 6 months ago, with that same CD and the same machine I did not have any trouble.

Any idea what's going on?

   Floren

---

### Post by mixium on 2007-03-22
Hi,

You could be having a failure with the CD player itself. Can you swap it out with another or perhaps clean it?

Also, try unplugging all of your usb devices.

This maybe a useful post [http://ubuntuforums.org/showthread.php?t=186115](http://ubuntuforums.org/showthread.php?t=186115)

Michael

---

### Post by ilmorris on 2007-03-24
> **Floren said:**
> Hi,

I have a problem while trying to install Ubuntu on a AMD64 (dual core, double processor) machine.

I was trying the 6.10 version of Ubuntu and when I click on install (also happens when checking the CD for errors) I got messages of this sort:

[ 209.754682] hdc: ide_intr: huh? expected NULL handler on exit
[ 229.488865] hdc: ide_intr: huh? expected NULL handler on exit
[ 229.538083] Buffer I/O error on device hdc, logical block 176813
... (more lines similar to the ones above)


I tried an older CD with Ubuntu 6.06 and it did not work either. And 6 months ago, with that same CD and the same machine I did not have any trouble.

Any idea what's going on?

   Floren

I've had this exact same error recently on multiple linux distro's across several different desktops.  What has worked for me, assuming you're using an IDE cd-rom to install, is to change the IDE cable from the newer 80-pin to an older 40-pin cable.  This has corrected the problem for me every time I have seen this error.

---


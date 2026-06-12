---
title: "newbie to linux -- booting off cd"
date: 2005-12-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by runxctry on 2005-12-23
apologize in advance for the newbie question.

apple powerbook 15", hi-res version.

Can't boot off the cd -- tried holding down alt key, C and command-alt-shift-delete.  none of the options work.

maybe it's this -- upon downloading the image file and before burning, OSX auto-mounted the iso's as a disk image.  could this have caused a problem?

Thanks!

---

### Post by DevilsAdvocate on 2005-12-23
I'm guessing you simply burned a data disk and not a bootable CD.  Reburn the image but unmount it first.  I use Nero in Windows but not sure what you use w/ a Mac.  You need to find out how to "burn an iso" though.

---

### Post by 3rdalbum on 2005-12-24
According to many users, mounting an ISO image will destroy it. So unfortunately, it looks like you'll need to turn off the automounting and download the whole thing again.

---

### Post by macheadPDX on 2005-12-25
I'd agree with unmounting the ISO image before burning. I use free xcdroast to burn ISO images. It works...

---

### Post by lorne_kun on 2005-12-25
In order to have the image burned properly, you must "get info" on the image and lock it. Then you have to use Disk Utility to burn the image, otherwise it will NOT be bootable (disk utility can be found inside the "Utilities" folder inside the "Applications" folder).

---

### Post by Macbuntu on 2005-12-27
Burning Bootable Disc in OS X using Apple Disc Utility

1. After downloading the ISO image, it will mount automatically (white icon with several folders inside). Eject it.
2. A .dmg file will be left in the desktop. ( gray hardisk icon)
3. Go to Disk Utility> Burn
4. Finder will prompt you locate the ISO image
5. Select the .dmg file
6. Insert a blank disc
7. Burn baby Burn
;)

---

### Post by runxctry on 2006-01-08
thank you all for your input, using your suggestions work great!!!

---


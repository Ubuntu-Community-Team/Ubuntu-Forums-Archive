---
title: "Getting files to USB or CD"
date: 2008-09-29
forum: x86 64-bit Users
---

### Post by mrhirsh on 2008-09-29
I've got a Toshiba laptop, dual boot with Win. Vista.  I've got some pictures that I installed on the Linux side (*.jpg).  I am trying to copy them to either a CD or (preferably) a flash drive.  Linux does not seem to be recognizing any of the above.  Any suggestions?

In the alternative to doing this "save to" in Linux, is there any way to access the files either through Vista or the DOS prompt?

Thanks for any help.

Michael

---

### Post by aoanla on 2008-09-29
I'm a bit confused - are you saying that flash storage media aren't automatically mounted when you attach them?

They should appear in /media/  (and should also get an icon on the Desktop)...

---

### Post by mrhirsh on 2008-09-29
Correct.  The Flash drive is not "showing up"

---

### Post by aoanla on 2008-09-30
Interesting. 

If you plug in a flash drive to one of your usb ports, and type:

lsusb

what do you get? One of the entries should be the flash drive...

---


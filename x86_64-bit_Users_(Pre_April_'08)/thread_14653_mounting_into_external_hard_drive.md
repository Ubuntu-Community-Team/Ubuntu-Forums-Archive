---
title: "mounting into external hard drive"
date: 2005-02-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by kraptor on 2005-02-08
i keep getting the error message "wrong fts type" while trying to mount into my external usb hard drive... ... any suggestions
thanks
kraptor

---

### Post by AndersAA on 2005-02-09
tried finding out which filesystem is on it?  Not all external drives are formated per default, so if it's brand new you might need to format it.  (Note that I've used them without any problems whatsoever, plug into usb2/firewire and they auto mount and work flawlessly, no problems at all.  Which has impressed me a lot! :) ).

---

### Post by ulefr01 on 2005-02-09
there is a problem if you connect your external hard drive to the firewire after that you are logged on to your system. 
If you switch on your external harddrive and your harddrive is connected to your Pc to the Firewire port before you switch on your Pc then it works.
Afterwards you get an sbp2 error or something like that.

When you connect your harddisk to a Usb port then there will be no problem even you connect your harddisk after that you are logged on to your system.

---

### Post by kraptor on 2005-02-10
i managed to finally mount to the usb drive... i wasnt too sure of the mount point but anyways...
mount /dev/sda1 /mnt/usbhd
this lets me access the files through the root terminal, but i have mp3s and other stuff that i need to open... so when i try browsing the usbhd directory using music player... the folder is empty... which is wierd...
kraptor

---

### Post by AndersAA on 2005-02-10
[QUOTE=kraptor]i managed to finally mount to the usb drive... i wasnt too sure of the mount point but anyways...
mount /dev/sda1 /mnt/usbhd
this lets me access the files through the root terminal, but i have mp3s and other stuff that i need to open... so when i try browsing the usbhd directory using music player... the folder is empty... which is wierd...
kraptor[/QUOTE]

that's probably a permission issue.  Try:
mount /dev/sda1 /mnt/usbhd -o uid=1000

---


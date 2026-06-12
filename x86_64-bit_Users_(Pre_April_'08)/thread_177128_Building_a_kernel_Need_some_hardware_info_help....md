---
title: "Building a kernel: Need some hardware info help..."
date: 2006-05-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by shorty0927 on 2006-05-15
I'm trying to build a kernel.  It seems that in order to choose the right kernel elements to include in the build, I need to know more intimate details about my Powerbook hardware, such as what company made a particular part and its model number (for example, the Airport Extreme is made by Broadcom, model #4306).

Apple's documentation doesn't seem to offer a lot of help in this department--does anyone know of a good website that'll help me dig up this information? 

Thanks!

---

### Post by BoneKracker on 2006-05-16
Apple's specs database:
[http://support.apple.com/specs/](http://support.apple.com/specs/)

Some useful links on these pages:
[http://www.everythingmac.com/](http://www.everythingmac.com/)
[http://www.macspeedzone.com/html/hubs/central/powerbooks.html](http://www.macspeedzone.com/html/hubs/central/powerbooks.html)

Also, you can get a lot of the info by booting a live CD that has good hardware detection (like the Ubuntu live CD) and use the following commands:

dmesg
lspci
cat /var/log/xorg.0.log (or whatever the xserver log file is)
other log files (like kernel log)

---


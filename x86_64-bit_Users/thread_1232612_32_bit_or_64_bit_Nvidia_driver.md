---
title: "32 bit or 64 bit Nvidia driver"
date: 2009-08-05
forum: x86 64-bit Users
---

### Post by tajreed on 2009-08-05
Are the Nvidia drivers in the repositories 32 bit? Should I use a 64 bit on a 64 bit machine or does it make a difference. I'm having some trouble getting the Nividia driver from the repositories to I.D. my monitor. I'm using 64 bit 9.04.

---

### Post by wojox on 2009-08-05
You could go to the site and download exactly what you need:
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

Then use this document to install it:
[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

---

### Post by 3Miro on 2009-08-05
If you have 32-bit machine you should use the 32-bit driver, if you have a 64-bit machine, you should use the 64-bit driver (note the change is on the interface between the kernel and the device, all video cards are 32-bit anyway).

The one in the repositories is the correct version for you. They may have something newer at the Nvidia site, however, the Ubuntu community always tests what is in the repository (i.e. the Nvidia version may still have some glitches, especially if it is an beta).

---

### Post by tajreed on 2009-08-06
Thanks for the replies fellow Ubuntu'ers. I'll continue using the one in the repos. And check my vga cable for errors.

---


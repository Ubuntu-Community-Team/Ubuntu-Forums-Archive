---
title: "CUPS and/or Apple LaserWriter Select 310 Not Working"
date: 2005-05-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by chessforce on 2005-05-13
Hello,

I have an Apple LaserWriter Select 310, which did work on a computer with a 32-bit CPU and Ubuntu 5.04 "Hoary Hedgehog".  However, now I cannot get it to work on a AMD Athlon 64 with Ubuntu Hoary x86-64 Edition (tried both with native 64-bit CUPS and the 32-bit chroot'ed CUPS).  The printer simply blinks and stops.  Upon checking the CUPS logs, I did not find any errors or warnings.  So, I was wondering if anyone had an idea(s) on what to do.  Thanks!

---

### Post by nmsa on 2005-05-14
I can't print from ubuntu hoary on a amd64.
I have a Samsung SCX-4216F and on my laptops (Ubuntu Hoary and Mandrake 10.1) printing is ok.

During installation of the driver I have the following errors:
```
cp: cannot stat `/usr/bin/lpr.cups': No such file or directory
ERROR: Module mfpportprobe does not exist in /proc/modules
ERROR: Module mfpport does not exist in /proc/modules
Unable to update /etc/rc.d/rc.sysinit
```I have this error while running the printer configurator:
```
/usr/local/bin/samsung/Configurator
/usr/local/bin/samsung/Configurator: error while loading shared libraries: 
libcups.so.2: cannot open shared object file: No such file or directory
```  
/usr/lib/libcups.so.2 file exists.
CUPS is installed (checked with Synaptic).

Any idea?

---

### Post by aronchi on 2005-11-10
I have the same problem with an SCX-4216F samsung printer.

It prints blank pages, what's the problem? Did you managed to get it work?

---

### Post by hulleye on 2006-04-18
any help on this would be sincerely appreciated. Have a Samsung SCX-4216f installed with Ubuntu 5.10... but get the same error msgs during installation of the driver as stated in the msg from nmsa.

The printer seems to communicate with the computer. Upon sending a print job, the printer warms up and "Printing..." appears on the display status on the printer, but no pages are printed!!

Any help would be appreciated.

---


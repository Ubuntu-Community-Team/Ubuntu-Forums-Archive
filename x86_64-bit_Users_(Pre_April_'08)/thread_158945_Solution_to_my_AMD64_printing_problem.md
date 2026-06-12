---
title: "Solution to my AMD64 printing problem"
date: 2006-04-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by adarkar9 on 2006-04-12
After searching the forums, then the web, I finally stumbled onto this solution to my printing problem:

[http://www.linuxprinting.org/show_printer.cgi?recnum=Samsung-QL-5100A](http://www.linuxprinting.org/show_printer.cgi?recnum=Samsung-QL-5100A)

This solution worked great for getting printing to work on my Asus A8N-E motherboard.  Hopefully this helps some others that are having the same issue.

Here is the solution, in case the above link dies:

Ubuntu (5.10) includes all the correct drivers you will need for this printer
however I had some issues with this printer on AMD64 (motherboard is Asus A8N-E for Athlon 64).

Printing (with any suggested driver) was garbage completely unrecognizable until
I went into the BIOS and set the parallel port to use address 3BC, IRQ 7 in SPP
mode.  I haven't verified if the change from default address is necessary but the
default mode of EPP (or it might have been EPP+ECP) was definitely causing a
problem.

---


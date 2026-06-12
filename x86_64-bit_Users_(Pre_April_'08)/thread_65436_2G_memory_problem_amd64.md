---
title: "2G memory problem amd64"
date: 2005-09-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by jmaf on 2005-09-14
I have  Hoary with an amd64 kernel and 2G of memory but ubuntu only see 1024m.

MemTotal:      1023756 kB





Do I have to build my own kernel??

Is there any work around?

thank you

---

### Post by negatory on 2005-09-14
Strange...have you checked that in the bios?Does that display the correct amount?
Your kernel should detect the other 1GB....
Pedro Carrico

---

### Post by Kuolio on 2005-09-14
I also suspect hardware problem. Check for bios-settings and that memory is showing up OK.. if  bios is ok, try running memtest86 to see if your memory is ok.

If those both turn out OK, then it realy is problem with your kernel.

---


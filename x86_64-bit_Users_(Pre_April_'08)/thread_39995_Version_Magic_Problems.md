---
title: "Version Magic Problems"
date: 2005-06-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by sgtstadanko on 2005-06-07
Ok....i've managed to screw something up with my headers.  I am running kernel 2.6.10-5-amd64-generic and whenever I try to compile any module and insert, it fails with invalid format and dmesg says " version magic '2.6.10-5-amd64-generic gcc-3.4' should be '2.6.10-5-amd64-generic gcc-3.3'".  I have tried uninstalling an reinstalling the linux-headers packages but keep getting the same error.  I have the following linux-header packages installed: 

linux-headers-2.6.10-5
linux-headers-2.6.10-5-amd64-generic
linux-headers-2.6.10-5-amd64-k8

What am i missing here?

thanks,
bill

---

### Post by FluffyElmo on 2005-06-07
Just a guess, but it seems to be looking for a different version of gcc. Both 3.3 and 3.4 are available in Synaptic. If you just installed the 'gcc' package it installed 3.4, try 3.3 and see if it fixes the problem.

---


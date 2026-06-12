---
title: "Edgy install problem on AMD athlon64 (keyboard/ mouse not working)"
date: 2007-01-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by tbwolfe on 2007-01-24
I am having problems installing Edgy on my AMD 64.  I have tried the standard (32 bit ) install as well as the  64 bit in Edgy  and the 64 bit Dapper.  All of these are giving me the same problem.  My keyboard and mouse (both USB) seem to be recognized on boot.  I am able to use the keyboard to choose the install option from the boot screen.  when the live desktop launches, the keyboard and mouse are no longer recognized and do not seem to be getting power, therefore, I can't make any selections, or progress beyond this point.  I have used these specific install cd's several times, and with no problems.  

Any suggestions on how I may go about resolving this issue would be greatly appreciated.

(I would prefer to use the 32bit version, but at this point, either is fine.)  

Thanks!

---

### Post by livelives on 2007-01-24
Hi

This problem is occurred because, " Your System Is over locked " 

Go to BIOS and Load the SETUP DEFAULT Values. Then restart the system. Try to Install Ubuntu(any version 32 or 64 bit). 

SUCCESSFUL INSTALL

-----------------------------------
livelives

---

### Post by tbwolfe on 2007-01-24
Thanks for the suggestion, livelives.  I finally figured out what the problem was.  Apparently, i needed to diable Legacy Support for USB.  I hope that this helps anyone else faced with this problem.

Thanks Again!

---

### Post by danteman on 2007-01-29
Hi,

Did you disable USB legacy support?? I thought that would disable the USB ports?

/D

---

### Post by tbwolfe on 2007-01-29
That's what I would have thought as well.  One of my coworkers suggested that as a possible solution and it ended up working.  I was pretty surprised. :)

---


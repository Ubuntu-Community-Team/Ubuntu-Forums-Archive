---
title: "X Server crash after fresh iMac install"
date: 2006-01-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by aarenj on 2006-01-14
I have an iMac DV Edition 400Mhz G3 with the following onboard videocard

# VRAM: 8 MB SGRAM
# Video: supports resolutions of 640 x 480, 800 x 600, and 1024 x 768 using ATI RAGE 128 VR chip set and 2X AGP
# monitor: 15" (13.8" viewable) multiscan to 1024 x 768

after fresh first-time installation of ubuntu everything appeared to work fine until the first boot after installation was completed.

the ubuntu boot screen came up and loaded witx h no visable errors, after that the screen goes black for a few sconds then an X Server appears and says the it has crashed and will not be loaded. after that I'm at a command line for linux.

I'm such a newbie at this unless I get a fix with fairly detailed instructions I'm fairly confident I won't get past this point.

I have seen some web articles that seem to indicate I'm not the only one with this problem, except none of them had fixes.

help, thanks

AJ

---

### Post by fourchannel on 2006-01-14
if you don't have a graphical desktop to work out of, this will be harder to fix..
 
but whatever is causing problems, is most likely somewhere in your Xorg.0.log
 
run this command and see if you can see any problems.
 
```
cat /var/log/Xorg.0.log | less
```
 
thats a zero, not a letter o. and the | is a pipe. shift+\
 
the log is going to be looooonnnnggggg.... so you will have a lot to wade through. but if you could cut and paste it here, it would be best. but it sounds like that's not gonna happen... =D
 
*note: errors in the log file start with EE. Might help you find what's wrong faster.

---

### Post by aarenj on 2006-01-15
I hope this is what you were looking for, the results were as follows...


(WW) ****INVALID IO ALLOCATION**** b: 0x400 e: 0x4ff correcting^G
(EE) R128(0): Cannot read V_BIOS (5)
Skipping "/usr/X11R6/lib/modules/libfb,a:fbmmx.o": No symbols found

Fatal server error:
Caught signal 7. Server aborting

Thanks!

---

### Post by Avicus on 2006-01-16
Change the DefaultDepth to 15 in your xorg.conf, thats the only thing that sucks about this model of mac and ubuntu. Or use debian. :P
Let me know if this works for you. It did for me.

---


---
title: "Missing libGL"
date: 2006-05-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by crazy_fox on 2006-05-03
Here is the story, my 3D (open GL ) graphics where not functioning well. So i decided it was time to visit ATI (i got a laptop with ATI RADEON mobility) and downlowd the proper ones.

So i downloaded the "ATI driver installer" (from [https://support.ati.com/ics/support/KBAnswer.asp?questionID=1177](https://support.ati.com/ics/support/KBAnswer.asp?questionID=1177) ) , did the installation, and everything seemed to be working. Restarted the box, everything is cool.

But when i tried to see what would happen with a game with 3D graphics, i got the following error.

> fox@zion:~$ armagetron
/usr/games/armagetron.real: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory


Now i check for the lib in Synaptic, and it says its installed.
Any ideas?

---

### Post by jpkotta on 2006-05-03
Do this:```
ls -l /usr/lib/libGL*
``` and ```
dpkg -S libGL.so
``` and post the results.

You might want to try the Ubuntu package, that will might work better than the ATI installer.  There are instructions in the wiki for installing the package.

---

### Post by crazy_fox on 2006-05-03
I did follow the instuctions..

Fixed the problem, by the notes on the end of the wiki instructions, havent tried yours. The Xserver wont start with fglxr set as the driver. So i had to restore it to ATI..

Now my problem is that 3D rendering is very very slow.. Any suggestions?

---

### Post by jpkotta on 2006-05-03
Your rendering is slow because you're doing the rendering in software instead of hardware.  You're not using ATI's driver, which is called fglrx, but the open driver instead.

Please start your X server with the fglrx driver.  We already know it doesn't work, but it will produce a log in /var/log/X.0.log.  Post this file so we can see exactly what's happening.

---

### Post by crazy_fox on 2006-05-04
OK, will do tonight... Hope i can post stuff here with lynx ;)

---


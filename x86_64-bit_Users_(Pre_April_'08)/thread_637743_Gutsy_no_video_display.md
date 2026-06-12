---
title: "Gutsy no video display?"
date: 2007-12-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by Gleeman on 2007-12-11
Hi, I couldn't find a thread with this problem on the forums, hope somebody can help.

I have a fresh install of 7.10 dual booting with XP on a partitioned HDD.  Install went fine, installed the ATI driver for my X1650 Pro, used Ubuntu several times with no problems, really enjoyed it.  I had no problem in windows either.

I went to boot into Ubuntu the other day, and it boots fine, I can even hear the startup sound and can login if I type my name and P/W, then it boots into the desktop with sound, but the whole time the screen is black.  All I see is the startup splash, no lost connection message on the LCD, etc.

XP is just fine as well.

Thanks for any help!

---

### Post by ken_vh on 2007-12-11
Did you update your drivers recently? Or changed the screen resolution?
(or did you do a recent upgrade that might have contained a graphics driver update?)

If so:
Open a console(ctrl+alt+f1) and log in.
Go to /etc/X11
Find old xorg.conf files:
ls xorg.conf.*

If you find old files, please continue the following steps:

First make a copy of your current xorg.conf to something like xorg.conf.yourbackup, so you can always revert it back again:
cp xorg.conf xorg.conf.backup

If there's any old xorg.conf files(called something xorg.conf.1, xorg.conf.2), try to revert one of these by copying it into xorg.conf.

Reboot and see if your system boots correctly.
If it still doesn't work, reboot, open a terminal and try copying the other xorg.conf.[something] into xorg.conf.

If these attempts fail: copy your backup of xorg.conf back:
cd /etc/X11
cp xorg.conf.backup xorg.conf

If your system doesn't give you a console(because your monitor doesnt get a signal or gets a bad signal) you can always follow these steps by first booting a LiveCD and doing it from there.

---

### Post by Gleeman on 2007-12-11
Thanks for the help, I'll give it a shot, but I haven't changed anything, and Ubuntu was working fine the previous times I've used it.  I can even boot into safe mode and see everything at the command line, but as soon as I start GNOME, the screen blacks out.

---

### Post by Gleeman on 2007-12-26
Thanks for the help, changing the xorg.conf worked like a charm!

\\:D/

---


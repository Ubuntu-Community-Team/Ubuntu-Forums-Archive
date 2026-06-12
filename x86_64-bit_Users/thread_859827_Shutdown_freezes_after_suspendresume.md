---
title: "Shutdown freezes after suspend/resume"
date: 2008-07-14
forum: x86 64-bit Users
---

### Post by VvWolverinevV on 2008-07-14
After suspend/resume, restart hangs at the shutdown Ubuntu logo after the progress bar reaches completely empty.  If it helps, I found a [similar post]("http://ubuntuforums.org/showthread.php?t=734602") in the Development Forum.  I seem to remember having this problem in 7.10 and solving it by removing some KDE packages, but I can't remember which ones :(

---

### Post by tuxxy on 2008-07-14
I personally would remove all KDE apps, they ruined my GNOME without even being loaded.

Also you could try removing any power saving features which fixed any hanging I ever experienced

---

### Post by VvWolverinevV on 2008-07-15
Thanks for the suggestions.  After some more testing, I realized that the problem is only in restarting.  When I resume from suspend I receive a couple of errors to the effect of "device not ready" in Bash before proceeding to GNOME.  It seems that after receiving these errors, the system will on restart hang as described in the OP with all USB devices powered off.  Does anyone know what's going on or how to record those errors that only flash on the screen for a fraction of a second :confused:

---

### Post by VvWolverinevV on 2008-07-19
*Bump*

Is it possible that an unresponsive USB port is causing it to hang?

---

### Post by maheshasolkar on 2008-07-21
I've had this problem too. I tried to look through dmesg output immediately after force-restarting upon this error situation. I couldn't find any error message in there. Is there a place to look if there was an unresponsive hardware?

---

### Post by VvWolverinevV on 2008-07-26
I caught a bit more of the error message that flashes on screen before gnome starts.  There are 3 lines:
```
...
...ata 4: soft reset failed (device not ready)
...ata 3: soft reset failed (device not ready)
```, where "..." is something I didn't catch.  I think USB devices are listed on lines 2 and 3, but I'm not sure.  A way to log that message would be great.

---

### Post by fudoki on 2008-07-26
> **VvWolverinevV said:**
> *Bump*

Is it possible that an unresponsive USB port is causing it to hang?

On my dual-boot XP-UbuntuStudio machine this was the exact problem.  My MagicJack phone gizmo on the USB port was the prob.  Don't know why.  All device commands (hdinfo, usbview, kinfocenter, etc.) showed the MJ adapter as a drive, which is normal, and reported it was operating normally.

Disconnecting the MagicJack adapter from the USB port made the problem go away.  Now I simply unplug it before I boot into Linux, since it don't work in Linux anyway, and problem solved.

This is likely true of other USB devices that are actual or pseudo drives (like the MJ adapter).

Hope this helps.

---


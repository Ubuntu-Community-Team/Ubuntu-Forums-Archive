---
title: "cdrom busy error during multi-disk program install with Wine"
date: 2007-06-10
forum: Wine
---

### Post by Shazaam on 2007-06-10
:(
I am unable to install any multi-disk games/programs using Wine. I have tried the umount -f command, changed the drive in winecfg, no-cd hacks and searched but I haven't had any luck. The second disk NEVER gets recognised or the install fails. I haven't tried to copy the disks to the hard drive yet. Has anyone had any success doing this?

---

### Post by cogadh on 2007-06-10
When the game asks for the next disk, open a second terminal and enter this:
```
wine eject
```
That should eject the disk and allow you to put in a new disk without killing the install process.

---

### Post by Shazaam on 2007-06-10
Tried that before, no joy but thanks anyway.

---

### Post by cogadh on 2007-06-10
When you run the install from the terminal, are you navigating to the install CD and running "wine install.exe" or are you opening the terminal and entering "wine /path/to/install.exe"? If you are navigating to the CD, don't do that, the fact that the terminal is "in" the CD can prevent it from being ejected.

---

### Post by tagra123 on 2007-06-10
If all else fails open a second terminal and type sudo eject.

Insert the next cd wait for it to get mounted and proceed with the installation.

---

### Post by Shazaam on 2007-06-10
> **cogadh said:**
> When you run the install from the terminal, are you navigating to the install CD and running "wine install.exe" or are you opening the terminal and entering "wine /path/to/install.exe"? If you are navigating to the CD, don't do that, the fact that the terminal is "in" the CD can prevent it from being ejected.

What I have had the most sucess with is to pop the first cd in, wait for it to mount and open in nautilus, then I right click the "setup.exe" icon and choose "Open With Wine Windows Emulator". Could this be the problem?

---

### Post by cogadh on 2007-06-10
Possibly. If Nautilus is still accessing the CD, then it might not let it unmount. Also, it is better to run Wine from the terminal, that way you can get any error messages that may come from Wine, which you won't get when you use the right-click method.

---

### Post by Khufucius on 2010-02-18
The "wine eject" thing really helped me; thanks.

-Khuf

---


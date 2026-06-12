---
title: "revertin to xserver.conf backup"
date: 2009-01-20
forum: x86 64-bit Users
---

### Post by Thoralex on 2009-01-20
Hi, i tried to upgrade the driver for my nvidia 8800gt last night and seem to have messd up somewere. When i installed the driver it made a new xserver.conf an a backup of the old one. Now when i try to boot xserver don't work and i get a blanc screen with no possibility to do anything. Since i think the driver installed properly (it said so) i guess going back to the old xserver.conf should solve the problem.
So the qyestion is: how do i change to the old file without knowing its name?

Thanks
Thor

---

### Post by Yellow Pasque on 2009-01-20
I assume you can get to a console by booting in recovery mode (or pressing Ctrl+Alt+F1 after booting normally)
```
cd /etc/X11
ls
```
I'm not sure what nvidia renames your old xorg.conf to.

---

### Post by Thoralex on 2009-01-20
Hmm... When i ty to cd to that folder it seas
```
bash: cd: /etc/x11: No such file or directory
``` 
Any ideas?

---

### Post by mckeja on 2009-01-20
> **Thoralex said:**
> Hmm... When i ty to cd to that folder it seas
```
bash: cd: /etc/x11: No such file or directory
``` 
Any ideas?


Linux, unlike Windows, is case sensitive. The correct path name is: /etc/X11
Make sure the X is capitalized.

Also, your issue may be the one I posted about earlier. There seems to be an issue with machines that have more than 1 video card. EnvyNG fails for the same reason that the GUI fails after installing the driver: X doesn't know which video card is the default.  Take a look at my reply on here for ideas:

[http://ubuntuforums.org/showthread.php?t=1042426](http://ubuntuforums.org/showthread.php?t=1042426)

---

### Post by Thoralex on 2009-01-20
the big x worked, what do i do next? ls gives a list of files

I only have 1 graphics card

---

### Post by cariboo on 2009-01-20
The easiest way to solve your problem, is to restart in recovery mode and choose xfix at the menu, once it is done choose resume, which should get you back to the default desktop, where you can install the restricted drivers.

Jim

---

### Post by Thoralex on 2009-01-20
tryed it but that does'nt work either, no change at all

---

### Post by Thoralex on 2009-01-21
Can i reinstall or reset x from the command line? I know how to make it work after installing the sistem so maybe that would sove it? the backup made by nvidia is not there.

---


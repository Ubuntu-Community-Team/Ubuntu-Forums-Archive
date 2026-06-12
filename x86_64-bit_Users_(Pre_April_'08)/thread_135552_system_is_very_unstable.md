---
title: "system is very unstable"
date: 2006-02-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by Sherlock Holmboy on 2006-02-24
i tried installing the 64bit version, but the installer and the post installation package setup kept freezing. i tried a 32bit install. the first install phase went smoothely, but the package install still would freeze. 

Then i tried a server install, installing ubuntu-desktop afterwords. It kept freezing during the installation, so i had to keep restarting and "dpkg --configure -a" untill all packages where installed. i got gnome and x to start, but the system will still freeze at the drop of a hat.

then i tried a server reinstall with KDE, just to see if it changed anything, but just like gnome it doesn't take long to freeze. 

some times it freezes bringing up on the graphical login or while in an X environment, but it also freezes in prompt mode. the freezes make send my bios into safe mode as if im overclocking. my bios in total default

im running:
AMD +2700
nvidia 6600 pci-e
foxconn mobo
pci scsi HD
768 mb ram

ps. i installed off a pressed cd that installed fine on another system

---

### Post by bjweeks on 2006-02-24
Does Windows work, cause it sounds like a hardware issue?

---

### Post by Sherlock Holmboy on 2006-02-24
windows worked fine

---

### Post by Meuro on 2006-02-24
dude, read the previous thread that i wrote.  the problem sounds familiar

---

### Post by ctaborda on 2006-02-24
if u would specify where your thread is.. heh a link

---

### Post by mpk on 2006-02-24
My installation experiences were exactly the same. I posted my solutions here:
[http://www.ubuntuforums.org/showthread.php?t=135270](http://www.ubuntuforums.org/showthread.php?t=135270)

---

### Post by Sherlock Holmboy on 2006-02-25
turned out to be a buggy stick of memory. crashing stopped after i removed it:)

---


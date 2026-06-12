---
title: "display issues while trying to install dapper drake"
date: 2006-12-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by niallcd on 2006-12-16
I have been trying to boot up with the ubuntu 6.06 live cd and I'm having some display issues.

here are some quick specs on my machine:

Athlone 64bit deluxe kv8 
ATI 9800 pro

I have tried to boot up into ubuntu several times. the first time I tried, I am using the amd64 version of 6.06. When I tried to boot from the CD, I got the menu screen, and I selected the first option to "boot or install" ubuntu. I got the splash screen with the progress bar, and then after that finished, the screen went completely blank. the signal going from the pc to the display was gone and the display said "no signal". so I restarted and when I got to the menu, I tried boot with safe graphics mode. I had the exact same problem, the screen went blank.

I did manage to get it to work when I changed the driver section in the kernel from "ati" to "vesa" how ever it makes everything sluggish and slow. 
I recently chaged the driver in etc/X11/xorg.conf back to ati and upon rebooting got the black /blank screen again. 


I have tried to go into the kernel recovery mode to fix this with sudo vi /etc/X11/xorg.conf
but once I chage the driver from "ati" to "radeon" I dont know how to exit the recovery mode and save the changes.


If anyone has any ideas I would love to hear them.

NiallD.

---

### Post by K.Mandla on 2006-12-16
> **niallcd said:**
> I have tried to go into the kernel recovery mode to fix this with sudo vi /etc/X11/xorg.conf
but once I chage the driver from "ati" to "radeon" I dont know how to exit the recovery mode and save the changes.
If you're having difficulty saving the file, try using nano instead of vi. 

```
sudo nano /etc/X11/xorg.conf
```
Nano is a little easier to decipher. I tried vi twice in my linux career, about a year ago ... and I haven't touched it since. 

In nano, once you've made the changes, press CTRL+O to write out the file, and CTRL+X to exit. From there, you should be able to reboot and see if your changes to the xorg file worked.

---


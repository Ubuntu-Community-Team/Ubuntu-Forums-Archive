---
title: "help with video card"
date: 2007-09-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by mikawber on 2007-09-05
I just decided to do a clean install the 64 bit version of Feisty. I downloaded and installed the drivers for my NVIDIA 8600 GT. After installing everything was working fine but now when I reboot the screen goes black after selecting Ubuntu in grub. If I disable the nvidia drives and just use "nv" the screen still goes black for about 10 seconds and then displays the login screen. Any ideas why or how to fix this? Thanks

---

### Post by mikawber on 2007-09-05
oh and when I installed the nvidia drivers I got the following error

> WARNING: Unable to perform the runtime configuration check for library 'libGL.so.1' ('/usr/lib32/libGL.so.100.14.11'); assuming successfuk installation

---

### Post by mikawber on 2007-09-06
come on somebody has to know whats going on, anybody?

---

### Post by mikawber on 2007-09-06
Ok I've managed to get the video drivers to work successfully, however I still have no load screen during boot and during shutdown. Any ideas?

---

### Post by pnotequalsnp on 2007-09-09
you could try to edit /boot/grub/menu.lst, replacing "splash" with "nosplash".  I have had the same symptons in the past.

---

### Post by glee on 2007-09-09
Sounds similar to my problem. See [http://ubuntuforums.org/showthread.php?t=546607]("http://ubuntuforums.org/showthread.php?t=546607")

---

### Post by mikawber on 2007-10-06
I was wondering if anyone knows how to fix this issue. Its extremely annoying. Please help

---


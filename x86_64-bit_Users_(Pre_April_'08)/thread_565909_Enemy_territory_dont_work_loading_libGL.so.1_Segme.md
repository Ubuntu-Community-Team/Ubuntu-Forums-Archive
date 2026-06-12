---
title: "Enemy territory dont work loading libGL.so.1: Segmentation fault"
date: 2007-10-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by blobo on 2007-10-02
so today i installed kubuntu its too many years whitout linux :P
so i install latest nvidia driver all works fine but when i try start playing Enemy territory its give me error here some logs

[http://pastebin.com/m3e6c2a1b](http://pastebin.com/m3e6c2a1b)

and i am using kubuntu 64bit amd

---

### Post by roachk71 on 2007-10-02
I have the same graphics and driver configuration. It would appear that your original OpenGL libraries were replaced by nVidia's during the driver installation procedure, since they conflict.

Apparently, Enemy Territory relies on the original GL libraries.

Unfortunately, many nVidia cards don't work well without the proprietary drivers and OpenGL libraries. You could try uninstalling the driver and libraries, and reinstalling the originals through apt-get or synaptic (after restoring your original xorg.conf file), but I seriously doubt that would be of any great help.

I guess the developers really have their work cut out for them... :(

---

### Post by Mathieu 7-7 on 2007-10-03
Hi,
French people (like me :lolflag:) are upgeading to Gutsy (unstable but go well) because compatibillity problemes betwen 32 bits 3D softwares in resolved.

I know, my English is really bad ... Hope i help

---------------------------------------------
2.6.20-16-generic,  x86_64, 2.2 Mhz, Geforce 6600 GT AGP, 1go RAM.
Cherchez et vous trouverez

---


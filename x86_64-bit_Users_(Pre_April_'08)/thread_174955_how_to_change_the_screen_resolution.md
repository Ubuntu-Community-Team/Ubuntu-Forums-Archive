---
title: "how to change the screen resolution"
date: 2006-05-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by ragnar_123 on 2006-05-12
how do I change the screen resolution after I installed ubuntu, the screen resolution is 1024 x 768, and I want it to be 1280 x 1024. Is there a way to do that without reinstalling ?

---

### Post by khightower on 2006-05-12
what type of graphics card are you using?

---

### Post by ragnar_123 on 2006-05-12
nvidia 7800 gtx

msi i think....

---

### Post by khightower on 2006-05-12
You can use System>Administration>Synaptic Package Manager to install the Nvidia Drivers for your video card.

When you open the package manager search for nvidia-glx. These are the drivers that are provided by Nividia. This should help you out.

You might want to look in to Easy Ubuntu, its a small app that install video drivers and other usefull things like MP3 support. Try it out [http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

---

### Post by sjasty on 2006-05-13
An Easy way to change the display resolution is:

System -> Preferences -> Screen Resolution.

---

### Post by ragnar_123 on 2006-05-13
[QUOTE=sjasty]An Easy way to change the display resolution is:

System -> Preferences -> Screen Resolution.[/QUOTE]

well... i didn't choose 1024 x 1024 in the setup...

---

### Post by turbojugend_gr on 2006-05-13
[QUOTE=ragnar_123]how do I change the screen resolution after I installed ubuntu, the screen resolution is 1024 x 768, and I want it to be 1280 x 1024. Is there a way to do that without reinstalling ?[/QUOTE]

Hi, had the same problem, have the same card lol.
I believe you should be ok by changing your /etc/X11/xorg.conf file by :#sudo gedit etc/X11/xorg.conf#. then add the "1280x1024" for all the color deapths, add this in the "Device SCREEN" section near the bottom of this file. then restart your machine.

If nothing changes when you are back, then get ready for some Heavy work. type in a terminal:```
sudo dpkg-reconfigure xserver-xorg
```

follow the questions and you come to the resolutions be carefull to press the SPACEBAR for the 1280x1024 resoltuion also...If it is a graphical mode menu, else jsut add it to the others.

Inform me with  your progress.

---

### Post by ragnar_123 on 2006-05-14
thank a lot :) the first method didn't work :(

but [q] sudo dpkg-reconfigure xserver-xorg [/q]

did work :)

thank you

---


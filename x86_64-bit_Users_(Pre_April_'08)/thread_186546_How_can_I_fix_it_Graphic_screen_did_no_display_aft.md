---
title: "How can I fix it? Graphic screen did no display after instalation of ubuntu!"
date: 2006-06-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by sidy on 2006-06-02
Hi there,

My PC:
AMD 64 processor.
1G Ram.
Motherboar: Asus K8V-X.
Graphic Card: nVidia Corporation NV34 [GeForce FX5200LP].
Ubuntu installed: 5.10 64bit.

I had this problem before (graphic screen no displaying), and I fixed dooing this:

Ctrl+alt+F1
sudo dpkg-reconfigure xserver-xorg
nv
nv nVidia FX5200LP
#enter in all the rest, then#
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm restart

Then graphic screen displayed, but at this time it didn't.](*,) 
So, WHAT CAN I DO TO HAVE GRAPHIC SCREEN DISPLAING?
Or, WHAT HAVE I DONE WRONG AT THIS TIME?
Or, WHAT SOULD I DO DIFFENT TO FIX IT?

I'm not an expert, can you please give me same directions, step by step, please!

Rgds.

---

### Post by miggl on 2006-06-02
You should try installing Ubuntu 6.06, you probably will have less problems.
But for your current dylemna you might want to try this:```
sudo pico /etc/X11/xorg.conf
```Look for the section that identifies your graphic card, there should be a line "Driver" "nv" or "Driver" "nvidia". Change the nv/nvidia to "vesa". Comment out any options in that section by adding "#" to the front of the line. Now reboot, and it should come up. Once it comes up, reinstall the nvidia drivers, edit xorg.conf again, and restore it to the previous values. 
This helped me getting around GDM problems when I was messing around with the XServer.

Good luck!

---

### Post by davidlm on 2006-06-02
Yes, it's work, when i do the distupgrade... and reboot no init the graphic display... 

I change to vesa and reboot

The graphic display work and then install the driver for xorg... (i don't knowed the package)

for me the via,

---


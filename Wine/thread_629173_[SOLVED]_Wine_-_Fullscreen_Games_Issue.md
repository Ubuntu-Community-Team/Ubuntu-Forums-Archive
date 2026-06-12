---
title: "[SOLVED] Wine - Fullscreen Games Issue"
date: 2007-12-02
forum: Wine
---

### Post by b0rka7a on 2007-12-02
When I start a fullscreen game in Wine my monitor changes it's frequency from 87Hz to 50Hz. After I exit the game I have to manually set the frequency to 87Hz :(
Is there a way to fix this ?

My OS is Ubuntu 7.10 Gutsy;
My monitor is NEC MultiSync FE750;
My graphics card is Inno3D 7300GT 256MB (I installed the drivers from Envy, because the nvidia-glx-new driver from Ubuntu didn't work);
My Wine version is 0.9.50;
I attached my xorg.conf file if you need it.

P.S. Sorry for my bad English :)

---

### Post by cogadh on 2007-12-02
It must be a game setting that is making the change. What games are you trying run?

---

### Post by b0rka7a on 2007-12-02
Counter Strike 1.6, World of Warcraft, Flatout, GTA San Andreas
In all these games this happens.

P.S. Actually, in Ubuntu (System - Preferences - Screen Resolution) changes from 87Hz to 50Hz, but my monitor tells me that it's working at 85Hz?!

P.S.2. 85Hz is the maximum frequency that my monitor can run according to my old OS (Windows XP). I've just found that out! :D

So I'll leave it that way... :)

---

### Post by cogadh on 2007-12-02
Ah, I just noticed you are using an Nvidia card (I should read more closely apparently). The Nvidia driver does a funny thing in order to support Nvidia's Dynamic Twin View functions. It basically creates custom timings that make the system report false refresh rates. Your system is actually using the correct refresh rate, as your monitor indicates, but it will show up the Screen Resolution preferences as something weird like 67 Hz or 50 Hz, in your case. You can stop that from happening by adding an option to your xorg.conf to disable Dynamic Twin View. Here's how it is on my system:
```
Section "Device"
	Identifier	"Generic Video Card"
	Boardname	"NVIDIA GeForce 7 Series"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Option		"DynamicTwinView"	"false" <---this is the important entry
	Screen	0
	Vendorname	"NVIDIA"
EndSection
```
With that option set to "false", the system will always report your actual refresh rate. I have found that some games run through Wine can't tolerate the odd refresh rates that Dynamic Twin View creates. However, adding the option will disable some of the monitor configuration functions in the Nvidia control panel. I never really needed them myself, but you might.

---

### Post by b0rka7a on 2007-12-02
Thanks ! :D All works normally now. I added the line
```
	Option		"DynamicTwinView"	"false"
```
in xorg.conf (at Section "Device"), restarted the PC and at the login screen Ubuntu said something like it's not working properly and gnome is going to repair it at the next start of the X server. After that I restarted the X server (Ctrl + Alt + Backspace), checked that Ubuntu is telling me the right frequency at Screen Resolution and everything was perfect ! :D

---


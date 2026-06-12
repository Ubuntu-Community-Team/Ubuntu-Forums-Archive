---
title: "ati card Hd 3600 series does not work in ubuntu"
date: 2008-07-23
forum: x86 64-bit Users
---

### Post by fedora on 2008-07-23
help I've display card ati Hd 3600 series but it does not work well with ubuntu the monitor is continuously flicking especially when playing games or even during movie playing.
thank you

---

### Post by kingtaurus on 2008-07-23
Okay. Do you know which graphics drivers you are using? (Fixing these type of problems takes a little more information ... if possible could you please include a copy of /var/log/Xorg.0.log and /etc/X11/xorg.conf, as well as information about the monitor, whether the card is AGP or PCI-E).

---

### Post by fedora on 2008-07-26
thank your mr kingtaurus for reply my monitor is lcd g901dw, i think that my graphic card is pci E and the output information you asked is attached
thank you for interest and help

---

### Post by lavinog on 2008-07-26
Do you have desktop effects turned on? if so that is the problem.
It is somewhat a bug/design flaw with compositing windows, DRI, and ATI drivers.
I think intel drivers have the same issue...only Nvidia seems to have a work around for this at the moment...the ATI drivers will work fine when DRI2 is available.
One work around for videos is to use the non accelerated mode (X11) instead of xv
people are claiming that opengl apps seem to be ok with the latest (8-7) fglrx ATI driver, but only if ran in full screen.

The ultimate fix would be to turn off desktop effects.

---

### Post by fedora on 2008-07-26
thank you lavinog for interest i turned the desktop visual effect off and it is fix the flicking during playing videos but what about the games which asking for enabling the accelerating ati cards. 
thank you again

---

### Post by lavinog on 2008-07-26
I'm not sure what you mean with the games.

You can check if opengl is working by typing **glxgears** in the terminal
you should get over 1500fps if not then 3d acceleration is not enabled.
Right now only the restricted driver provides 3d support. go to system>administration>hardware drivers and make sure that the ATI accelerated driver is checked.
If you manually installed the ATI proprietary driver you don't need to do this, but you should still see "in use" in the hardware drivers window

Also a new ATI driver (8.7) came out this week.  The driver in the repositories is 8.3.

---

### Post by markbuntu on 2008-07-27
If you want the latest ATI driver, version 8.7. You can follow these directions. Use Method 2 for the latest driver and folow the directions very carefully:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

The directions for tweaking it are here:

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)


I have a HD36501GB and it works fine except for the flickering in windows when desktop effects are on. Otherwise it works fantastic for full screen games, HD video, etc.

I would recommend the 8.7 driver, it is far better than the 8.3 in the repository and has numerous fixes and the Catalyst AI.

---

### Post by miecz on 2008-08-03
i want to buy a new laptop and the video card in it is a mobility radeon 3650hd and i am wondering if this would work i mean i want full 3d acceleration and im not sure on how i can achieve this thing...this said can someone tell me if this what was posted here would work (theoretically) or wouldnt...?

---

### Post by Kilz on 2008-08-03
> **miecz said:**
> i want to buy a new laptop and the video card in it is a mobility radeon 3650hd and i am wondering if this would work i mean i want full 3d acceleration and im not sure on how i can achieve this thing...this said can someone tell me if this what was posted here would work (theoretically) or wouldnt...?

Read post 7.

---


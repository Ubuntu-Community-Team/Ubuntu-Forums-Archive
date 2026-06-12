---
title: "Nvidia Quadro NVS 140M Issue"
date: 2008-09-11
forum: x86 64-bit Users
---

### Post by Postaled on 2008-09-11
I have a Dell Latitude with an Nvidia Quadro NVS 140M video card, I go and downlaod the latest drivers from Nvidia.  Then I followed a few tutorials on how to install them.  (tried each way)  Whenever I go and install them my laptop boots and instead of a login screen my screen starts flashing white and then eventually goes into low graphics mode.  The X11 log file says that tehre is no compatible X driver available... Any ideas?  Also tried lower versions of the driver.. still nothing

---

### Post by John Jason Jordan on 2008-09-11
> **Postaled said:**
> I have a Dell Latitude with an Nvidia Quadro NVS 140M video card, I go and downlaod the latest drivers from Nvidia.  Then I followed a few tutorials on how to install them.  (tried each way)  Whenever I go and install them my laptop boots and instead of a login screen my screen starts flashing white and then eventually goes into low graphics mode.  The X11 log file says that tehre is no compatible X driver available... Any ideas?  Also tried lower versions of the driver.. still nothing
Try using the driver that is in the Ubuntu repositories. Since you currently cannot get X to start, boot in Recovery Mode. You may need to hit Esc just after your BIOS splash screen in order to see the boot menu. 

Recovery mode will boot you to a command line. At the command line type:

sudo apt-get install nvidia-glx-new

That ought to install the correct driver. If you still have problems there are lots of other command line things to try, but start with that.

I have a Lenovo Thinkpad which has the same video card. I use the nvidia-glx-new driver and have no problems. So I know it can be made to work; it's just a case of fixing what went wrong.

---

### Post by Postaled on 2008-09-11
Well its giving me an option to use "low graphics" mode now
but still not using the nvidia driver

my Xorg.0.log at the bottom has an 
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

I have rebooted many times, just to clarify

---

### Post by John Jason Jordan on 2008-09-11
> **Postaled said:**
> my Xorg.0.log at the bottom has an 
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
That's because it does not recognize the driver you installed. Sometimes the latest driver from nVidia has glitches. Furthermore, there are several nVidia drivers for Linux and different cards require different drivers. It's possible that you installed the wrong one. That's why I suggest you uninstall the driver you downloaded and then install the nVidia driver that is in the Ubuntu repositories. To install the one in the Ubuntu repositories use the apt-get command I mentioned previously. Then you will be using the same driver I am using. The driver I am using works perfectly.

---

### Post by Postaled on 2008-09-12
I just did a clean install and did it the way you wrote.  I am no longer getting THAT error, but 

(WW) NVIDIA(GPU-0):  The EDID read for the display device DFP-0 is invalid:  the checksum for EDID version 1 is invalid.  And its staying on white screen with crazy lines thing

---

### Post by tuxxy on 2008-09-12
Disable that driver and then I recommend you try and install the correct driver using envyng, this should select the correct one for your card.

To install open a terminal and type;

```
sudo apt-get install envyng-gtk
```

---

### Post by Postaled on 2008-09-12
woot, it worked usign envy

<3 to both of you for helping

---


---
title: "Hardware drivers"
date: 2008-08-12
forum: x86 64-bit Users
---

### Post by jpaulb on 2008-08-12
There was a question asked 
[COLOR=DarkOrange]*Did you not try system > admin > hardware drivers first?*[/COLOR]

I do not have that showing. What apps must I install?
I have tried to install the nVidia drivers for a GForce 6200 card only to get the 800x640 mode also

---

### Post by PCessna on 2008-08-12
> **jpaulb said:**
> There was a question asked 
[COLOR=DarkOrange]*Did you not try system > admin > hardware drivers first?*[/COLOR]

I do not have that showing. What apps must I install?
I have tried to install the nVidia drivers for a GForce 6200 card only to get the 800x640 mode also


For Ubuntu:
```
 sudo apt-get install envyng-gtk
```



then install NVIDIA drivers to automatic, and that ATI or whatever make sure it is checked to uninstalled!

---

### Post by kaizer05 on 2008-08-12
sorry, i've installed ubuntu in my laptop (Acer 4520), and i can't use the wireless device (atheros), i can't turn it on either...why is that? thanks for d help

---

### Post by jpaulb on 2008-08-12
> **PCessna said:**
> For Ubuntu:
```
 sudo apt-get install envyng-gtk
```



then install NVIDIA drivers to automatic, and that ATI or whatever make sure it is checked to uninstalled!

Looks like it already is:confused:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
envyng-gtk is already the newest version.
The following packages were automatically installed and are no longer required:
  python-jppy libpthread-stubs0 libgl1-mesa-dev python-pisock
  python-gnome2-extras python-egenix-mxtools libgdl-gnome-1-0 x11proto-kb-dev
  mesa-common-dev txt2pdbdoc xtrans-dev libgdl-1-common x11proto-input-dev
  libxcb-xlib0-dev libglu1-mesa-dev python-vobject dkms libgda3-common
  libxau-dev libc6-dev libgda3-3 libx11-dev linux-libc-dev libxcb1-dev
  python-egenix-mxdatetime python-dateutil x11proto-core-dev make libgdl-1-0
  libxdmcp-dev libpthread-stubs0-dev jppy python-pyparsing
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by cariboo on 2008-08-12
We may have a bit of miscommunication here, hardware drivers is located at System-->Administration-->Hardware Drivers.

Jim

---

### Post by jpaulb on 2008-08-13
> **cariboo907 said:**
> We may have a bit of miscommunication here, hardware drivers is located at System-->Administration-->Hardware Drivers.

Jim
I do no have that option available, therefore some software must be missing on my box.

---

### Post by jpaulb on 2008-08-17
After rebooting I found the system -> administration -> hardware drivers.

It claims that the the Nvidia graphic drivers are not installed. nvidia-glx 1.96.43.05+ is installed and goggle earth is not complaining of of the lack of a 3d accelerator


I am using the GeForce 6200 TurboCache(TM)
If I try to enable the hardware driver, nvidia-glx-new is installed this throws the display into a low resolution mode.

---


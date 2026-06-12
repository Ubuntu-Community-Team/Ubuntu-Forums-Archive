---
title: "Ubuntu 7.10 Enyx Compiz and XGL"
date: 2007-10-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by devzero on 2007-10-27
Hi,

I set the new Kernel up, as I got told in the XFI Thread.
I reinstalled the NVIDIA Driver with envy, so i got the Xserver
running.

As I wanted to enable compiz over the Display settings it tells me
that it needs to install the 3d acceleration drivers to run.

As I did that an rebootet my machine the XServer goes up and tells me that its now in
a low res mode. I can setup my settings again, but there is no matter what I finaly do it
ends in a lockup and blank screen. I cant switch to the console anymore if the xserver stated.

if I enforce compiz with start /usr/bin/compiz it tells me:

Checking for Xgl: not present. 
Detected PCI ID for VGA: 03:00.0 0300: 10de:0191 (rev a2) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator

and the titlebar is gone.

how can I install XGL over envy or otherwise without ending in a crash?

---

### Post by praxis22 on 2007-10-27
Using Envy is often a bad idea, you're better off using the restricted drivers manager. under:

System -> Administration.

I'd yank the drivers and try again as above. This is highly dependent on using the stock kernel, not a hand rolled one, unless you really know what you're doing.

---

### Post by devzero on 2007-10-28
Hi,

I want use that restricted drivermanager, but that damn thing wont work easily
with a custom kernel, I found a manual that u might get that thing to work
but I doubt it.

---

### Post by blakeg on 2007-10-28
I have always removed the restricted-everything (manager, kernels, packages, etc) and installed the nvidia drivers manually.

It requires some command line magic and a few extra packages, but for the most part, its simple and doesnt require a lot of time to do.

However, I don't run the 64bit version of ubuntu, so I am unsure if you would see any differences or not.

BlakeG

---


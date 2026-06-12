---
title: "nvidia-glx on 9.10 help!"
date: 2009-10-13
forum: x86 64-bit Users
---

### Post by jackschmidt on 2009-10-13
Hi,

I have an Intel i5 with an Inno3D Geforce 9500 GT 1 GB RAM and I'm trying to get the nvidia-glx 185 to work on this.  I installed the amd64 beta release and the display is a little crazy so I thought to install the nvidia drivers.

When I activate it through System -> Admin -> hardware drivers, it downloads and installs the driver package.  But when I do sudo modprobe nvidia, I get a FATAL: module not found.  I'm in the process of downloading the official driver off of nvidia's website but I would rather have this working under Ubuntu's packages.  Please help me!

EDIT:
I've compiled the official nvidia drivers and it's working.  The next problem is that the desktop screen is too large for the desktop!

---

### Post by duanedesign on 2009-10-24
Make sure you have the package: nvidia-settings

```
sudo apt-get install nvidia-settings
```

You can launch it with

```
gksudo nvidia-settings
```

Or you can access it at
System > Administration > NVIDIA X Server Settings

[LIST]
[*] Xserver Display Configuration
[*] Click Detect Displays at the bottom.
[*] Select Resoloution and select 60Hz or whatever is closest to 60Hz.
[*] Click the "Advanced..." button and see what it says under "Panning: " it should say the same as the resoloution.
[*]-click the Save to X config file button to keep the settings
[/LIST]

Restart to see if this makes a difference.
If this does not help please post your xorg.conf file.

---


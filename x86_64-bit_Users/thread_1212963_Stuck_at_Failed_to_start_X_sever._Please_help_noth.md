---
title: "Stuck at Failed to start X sever. Please help nothing works."
date: 2009-07-14
forum: x86 64-bit Users
---

### Post by cchester on 2009-07-14
Hello,

I am having a serious problem that I can't get past. I am trying to follow this guide [http://ubuntuforums.org/showthread.php?t=1125400]("http://ubuntuforums.org/showthread.php?t=1125400") to try and help me out in fixing my problem with no luck.

I am running Ubuntu 9.04 64bit and just did the upgrades it suggested one of which was my NVIDIA Drivers. Now all I get is a screen that says "Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server out put to diagnose the problem?" I tried to download the drivers via this command wget [ftp://download.nvidia.com/XFree86/Linux-x86_64/185.18.14/NVIDIA-Linux-x86_64-185.18.14-pkg2.run](ftp://download.nvidia.com/XFree86/Linux-x86_64/185.18.14/NVIDIA-Linux-x86_64-185.18.14-pkg2.run) -O NVIDIA-Linux-185.18.pkg.run but I am told it can't find the file. I have tried everything with no luck what so ever.

Is there a way I can edit my grub file to load the vesa drivers so I can at least get into my gui to try and fix this, because all I can do right now is use the command line and I am having no luck, or can I load uo my live cd to fix this.

Please help.

Thanks.

---

### Post by wojox on 2009-07-14
go into /etc/X11/ and copy your xorg.backup or xorg.conf.failsafe to xorg.conf

---

### Post by cchester on 2009-07-14
How do I do this? Sorry I don't know what the command to do that is. Is it copy xorg.backup?

Thanks still need more help.

> **wojox said:**
> go into /etc/X11/ and copy your xorg.backup or xorg.conf.failsafe to xorg.conf

---

### Post by cchester on 2009-07-14
Ok I did this:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.original
sudo dpkg-reconfigure -phigh xserver-xorg

And I got xserver-xorg is broken or not fully installed

Please help.

Thanks.

---

### Post by wojox on 2009-07-14
You copied them backwards.

Name of file to be copied = first argument.
Name of destination file = second argument.

```
sudo cp /etc/X11/xorg.conf.failsafe /etc/X11/xorg.conf
```

---

### Post by cchester on 2009-07-14
Ok I did this:

sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

Then

sudo dpkg-reconfigure -phigh xserver-xorg

And I got xserver-xorg is broken or not fully installed

I didn't have a xorg.con.failsafe by the way.

Please help.

Thanks. 
> **wojox said:**
> You copied them backwards.

Name of file to be copied = first argument.
Name of destination file = second argument.

```
sudo cp /etc/X11/xorg.conf.failsafe /etc/X11/xorg.conf
```

---

### Post by cchester on 2009-07-14
Bump*****

---

### Post by grege on 2009-07-18
try

sudo apt-get install xserver-xorg

then

sudo dpkg-reconfigure -phigh xserver-xorg

given this post is three days old I would guess you have just reinstalled by now.

I would recommend you install Midnight Commander file manager, it make life easy when copying files, editing files, making symlinks etc using a text interface.

sudo apt-get install mc

then sudo mc to find and edit system files as required. In /etc/X11/xorg.conf find this section and change driver "nvidia" to "vesa"

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

---

### Post by cchester on 2009-07-19
Thanks I did finally get it working without reinstalling but I will definately do what you suggested in the event that this happens again.

Thanks again for the reply.

---


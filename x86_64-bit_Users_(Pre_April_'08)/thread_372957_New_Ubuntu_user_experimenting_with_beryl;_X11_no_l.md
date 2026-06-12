---
title: "New Ubuntu user experimenting with beryl; X11 no longer boots"
date: 2007-02-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by yaazz on 2007-02-28
Hello everyone, I have been taking an intro to *nix programming course at my university and have aquired a newfound respect for linux. I have used Ubuntu at school for a while now, but I decided to install it at home and start playing around with it a little more. 

I read up a little bit on beryl, and I think it sounds really awesome. Before I go any farther you will probably want to know my system specs 

Amd 64 3000+ 
1 gb ram 
(evga)Nvidia 7800GT 256MB video card 
(evga)Nforce 4 motherboard 
120gb sata HD (Windows Vista RC1) 
100gb sata HD (ubuntu amd64 6.10) 

I followed [these]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia#Automatic_installation") instructions on installing beryl, and the script seems to have worked correctly, but after a reboot, gnome boots up, then crashes back to the terminal immediately. 

Any ideas on what I did wrong? 

thanks for the help in advance, once I get this fixed I will no doubt be a new regular on your forum!

---

### Post by ffxr on 2007-02-28
try and retrieve your xorg.conf backup.. 

i notice in the script this:
**"/etc/X11/xorg.conf /etc/X11/xorg.conf.backup.beryl-script"**

so at that terminal...

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup2
sudo cp /etc/X11/xorg.conf.backup.beryl-script /etc/X11/xorg.conf 
```

reset the pc, if it comes back.. your in luck and u can try below, if not you may have to setup ubuntu again.. & then u could follow below... 

###########

that script looks a little complicated & may haveinstalled the wrong graphics drivers.., possibly the nvidia 32bit ones..

 your probably better lookin for your howto on these forums..


this is something you *could* have done:

get your propietary linux nvidia 64bit drivers here, download to your home dir.
[http://www.nvidia.com/object/linux_display_amd64_1.0-9746.html](http://www.nvidia.com/object/linux_display_amd64_1.0-9746.html)

then @ Terminal:

```
sudo gedit /etc/default/linux-restricted-modules-common
```

and make the bottom line look like:

```
DISABLED_MODULES="nv"
```


then Terminal @ home directory

```
sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
sudo rm /etc/init.d/nvidia-* sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86_64-1.0-9746-pkg2.run 
sudo nvidia-xconfig --add-argb-glx-visuals 
sudo /etc/init.d/gdm start
```


And restart your computer., you should start seeing nvidia logos being flashed about the place..

then install beryl..

add ```
 deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main 
``` to your /etc/apt/sources.list

get key:
```

sudo echo && wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- 
```

and run:

```
sudo apt-get update
sudo aptitude install beryl emerald-themes

beryl-manager
```


that worked for me a few days ago anyway.. .. it may even be possible to recover completely from the terminal if the xorg.conf recover from backup doesnt work, using the commands above using wget to retrieve the nvidia drivers...

---

### Post by yaazz on 2007-03-01
Awesome that worked perfectly! Beryl is up and running, but for some reason, when opening windows inside of windows (such as "save page as" in firefox), you have to click in the main program window before the sub window will show up, how do I fix this?

Also, is Java in AMD64 Linux possible?

---

### Post by ffxr on 2007-03-01
> ... when opening windows inside of windows (such as "save page as" in firefox), you have to click in the main program window before the sub window will show up, how do I fix this?

im not sure about this, try tweaking settings in beryl manager, also try various things in advanced beryl options.. these are accessed by right clicking on the beryl diamond in your system tray, (in case you havent found them)

> Also, is Java in AMD64 Linux possible?

yeah i think so, havent had the need to install it myself yet, there is a few other threads in this forum on getting java working..

good luck.

---


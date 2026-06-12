---
title: "nVidia graphics driver problems in 64-bit 8.04"
date: 2008-10-27
forum: x86 64-bit Users
---

### Post by indiapavan on 2008-10-27
Hello to the open-source community. My name is Pavan and I am new to Ubuntu. I have currently installed Ubuntu 8.04 64-bit version. Everything seems to work fine except that my graphics driver has a problem. I enable the restricted driver for my AGP. However, when I enable visual effects to even the "normal" level, the display is not proper.:confused: I tried lowering my monitor's refresh rate to 54Hz. That seemed to help a bit. But many applications like Firefox just hang for a few seconds every now and then. I don't think this is the problem with my graphics adapter as it works exceptionally well on Windows XP. Please help me with this problem. Please explain the solutions as you would to a noob.:)

---

### Post by darthshak on 2008-10-27
> However, when I enable visual effects to even the "normal" level, the display is not proper.

Could you be more specific on that?
Which video card do you use? nVidia or ATI?

You can try using the envy installer script for installing your drivers.
```
sudo apt-get install envy
```
Then run envy and install the ATI or nvidia drivers, whichever of those is applicable to you.
Also, I dont think firefox hanging has anything to do with your graphics adapter.

---

### Post by indiapavan on 2008-10-27
> **darthshak said:**
> Could you be more specific on that?
Which video card do you use? nVidia or ATI?

You can try using the envy installer script for installing your drivers.
```
sudo apt-get install envy
```
Then run envy and install the ATI or nvidia drivers, whichever of those is applicable to you.
Also, I dont think firefox hanging has anything to do with your graphics adapter.

It actually works perfectly fine when I disable the driver. At the moment I have disabled it. I shall try the method which you suggested. My video card is nVIDIA GeForce 6100 Chipset.

---

### Post by BGFG on 2008-10-27
Hey i have the GeForce 6100 nForce 430 chipset also. 
I assume that when you go to system>>administration>>hardware Drivers
your nvidia driver says, 'in use'
There is a package to configure your nvidia settings, i don't know if you alrady have it:
System>>Administration>>Synaptic Package Manager and aside from having

nvidia-glx-new
nvidia-kernel-common and
xserver-xorg-video-nv installed,

You should also have: 

nvidia-settings 

installed. You can then configure it through System>>Administration>>Nvidia X Server settings

Hope this helps as i've never had problems with my display other than when i messed around and broke it.
BTW. I have a 17" Dell display riunning 1400x900 (max) at 60hz.

---

### Post by indiapavan on 2008-10-28
> **BGFG said:**
> Hey i have the GeForce 6100 nForce 430 chipset also. 
I assume that when you go to system>>administration>>hardware Drivers
your nvidia driver says, 'in use'
There is a package to configure your nvidia settings, i don't know if you alrady have it:
System>>Administration>>Synaptic Package Manager and aside from having

nvidia-glx-new
nvidia-kernel-common and
xserver-xorg-video-nv installed,

You should also have: 

nvidia-settings 

installed. You can then configure it through System>>Administration>>Nvidia X Server settings

Hope this helps as i've never had problems with my display other than when i messed around and broke it.
BTW. I have a 17" Dell display riunning 1400x900 (max) at 60hz.

I am now getting an error while re-installing the nvidia-glx-new package. It was there before too. But now I observed the error properly. I am now seriously considering switching back to windows. The reason being that one of my friends who has the 32 bit version and an even lower PC configuration than mine is doing graphical wonders with it. Is there a solution to my problem? I can even send you my xorg.conf file if necessary.

---

### Post by Sef on 2008-10-28
What NVidia graphics card do you have?

---

### Post by indiapavan on 2008-10-28
> **Sef said:**
> What NVidia graphics card do you have?

My video card is nVIDIA GeForce 6100 Chipset.

---

### Post by loomsen on 2008-10-30
> **indiapavan said:**
> I can even send you my xorg.conf file if necessary.

Posting it might increase chances of actually getting help by loads.

---

### Post by feenana on 2008-10-30
[img]http://www.top1gaming.com/cosplay/Goddess-16.jpg[/img]See more pics [[color=#800080]click here[/color]](http://www.top1gaming.com/coscontent-45-16.html).  Want to see more [[color=#800080]cosplayer[/color]](http://www.top1gaming.com/cosplayer.php) ? Show yourself on our forum [[color=#800080]click here [/color]](http://www.top1gaming.com/forum/forumdisplay.php?fid=29).**Recommend : **[[color=#0000ff]Chrono Trigger's Ayla [/color]](http://www.top1gaming.com/coscontent-130.html)   [[color=#0000ff]Legend of Zelda cosplay[/color]](http://www.top1gaming.com/coscontent-51.html)

---

### Post by indiapavan on 2008-10-30
This is my xorg.conf file in txt format. Its because it wouldn't let me post the original .conf file.

---

### Post by phlembob on 2008-10-30
Hi Pavan,
I have NVIDIA 6100 with no problems.  System > Hardware Drivers --- go here and pick on it.  Now, it should say something about NVIDIA proprietary drivers that aren't supported.  Highlight the box or should I say place a check in the box with your curser.  You need to leave and restart.
OK, sometimes you don't get this option, but once you have gone into Hardware Drivers within a short period of days you will get a notice of upgrade for NVIDIA drivers that aren't supported by Ubuntu.  Then you can check on it like the 1st paragraph.
:guitar:

---

### Post by dabl on 2008-10-30
I would advise doing the following -- first get out of the X server with Ctrl-Alt-F1, then log in at the CLI and shut down the X server with ```
sudo /etc/init.d/gdm stop
``` then do these:

1. Back up your existing xorg.conf file

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

2. Install and run EnvyNG

```
sudo apt-get update
```

```
sudo apt-get install envyng-core
```

```
sudo envyng -t
```

Choose #1 "Install Nvidia driver"

3. When you are returned to the CLI prompt, run the Nvidia xorg configuration utility:

```
sudo nvidia-xconfig
```

4. When it is done writing a new xorg.conf file, restart the X server with

```
startx
```

Hope this helps!  :)

---


---
title: "video problem: corrupted screen"
date: 2005-11-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by spoop on 2005-11-26
I just installed ubuntu, everything went smoothly, and I can get to the loading screen when booting that has the ubuntu logo, progress bar and list of things loading, but after that finishes, the screen gets all corrupted.  It is just a bunch of random colors.  I had this problem with the live cd also, so I do *not* believe that it is something that was messed up during the burning of the cd or installation.  Does anyone know what the problem is and how to fix it?  I am a newb to ubuntu and linux.

---

### Post by Magadass on 2005-11-26
[QUOTE=spoop]I just installed ubuntu, everything went smoothly, and I can get to the loading screen when booting that has the ubuntu logo, progress bar and list of things loading, but after that finishes, the screen gets all corrupted.  It is just a bunch of random colors.  I had this problem with the live cd also, so I do *not* believe that it is something that was messed up during the burning of the cd or installation.  Does anyone know what the problem is and how to fix it?  I am a newb to ubuntu and linux.[/QUOTE]

Same problem, I think it is due to the fact that the incorrect video drivers are being used for the 64 bit platform or something...  Or maybe its just a problem in general, I have a nforce 3 ultra chipset, how about you?

I dunno about this whole linux thing, I switched over to linux for 3 months about 8 months ago to see what all the hype was about and spent about 90% of my time trying to get my audio to work, which on my new computer and my old computer it still doesnt work, will they ever add NForce audio support other than the shitty NVidia drivers that run in legacy mode?

On another note Ubuntu is one of the few distros that recognizes my monitor correctly and actually sets the resolution accordingly!!  Freakin amazing...

---

### Post by teaker1s on 2005-11-26
sudo dpkg-reconfigure xserver-xorg
you may need to change horizontal sync and vertical refresh to match your display/lcd and possibly a different driver

---

### Post by Magadass on 2005-11-26
[QUOTE=teaker1s]sudo dpkg-reconfigure xserver-xorg
you may need to change horizontal sync and vertical refresh to match your display/lcd and possibly a different driver[/QUOTE]

So can I run this from safe mode?  Cause if I boot in normally it hangs before I can even run something and the graphics get all f'd up and torn.

The sync and refresh are fine for me I have an LCD for one so refresh doesnt do diddly...

---

### Post by RAOF on 2005-11-26
Yes, you can run that from safe mode (or recovery mode).  First of all, it's probably worth selecting the "vesa" driver when you are presented with the list of possible drivers (it will probably default to nv, ati, or something like that).  The vesa driver is pretty much failsafe.  That should get you into the GUI (and then if you want 3D acceleration or anything, it's easier to set up the correct driver).

---

### Post by spoop on 2005-11-26
Thing is, I'm a newb and I have no clue how to change refresh rate, vsync and hsync, how do I do that?:confused:

---

### Post by RAOF on 2005-11-26
By running
```
sudo dpkg-reconfigure xserver-xorg
```

But you shouldn't need to worry about that - it is unlikely to be the solution to your problem.  First try changing the driver used to "vesa" (dpkg-reconfigure will give you a big long list as one of the first questions it asks).  That should work.  If it doesn't, **then** you should start looking at more complicated problems, with more complicated solutions.

It would incidentally be useful to know what type of graphics card you have, if you know.  Nvidia?  Ati?  Integrated on the motherboard?

---

### Post by spoop on 2005-11-26
I have a nVidia XFX 6600GT pci-e.

---

### Post by RAOF on 2005-11-26
[QUOTE=spoop]I have a nVidia XFX 6600GT pci-e.[/QUOTE]
In that case, I suggest installing the nvidia drivers.  A quick howto:

In a terminal (I think that recovery mode will work fine for this), run the following commands:
```
sudo apt-get install nvidia-glx nvidia-settings
sudo nvidia-glx-config enable

```

And you should be now able to boot into a GUI.

---

### Post by Magadass on 2005-11-27
[QUOTE=RAOF]In that case, I suggest installing the nvidia drivers.  A quick howto:

In a terminal (I think that recovery mode will work fine for this), run the following commands:
```
sudo apt-get install nvidia-glx nvidia-settings
sudo nvidia-glx-config enable

```

And you should be now able to boot into a GUI.[/QUOTE]

Something even stranger to note on this issue which I will fix shortly is that this happens with Windows XP 64 bit edition also, I guess the default drivers that come with Windows XP 64 bit suck ass for NVidia cards also....

---

### Post by orandic on 2005-11-27
I had the same problem with my MSI Geforce NX6600 TD256E PCI-E and I was not selecting my resolution properly.  Make sure to select a resolution your card and monitor can handle with the space bar.  The resolution you select should then have a * next to it.

---

### Post by spoop on 2005-11-28
[QUOTE=RAOF]In that case, I suggest installing the nvidia drivers.  A quick howto:

In a terminal (I think that recovery mode will work fine for this), run the following commands:
```
sudo apt-get install nvidia-glx nvidia-settings
sudo nvidia-glx-config enable

```

And you should be now able to boot into a GUI.[/QUOTE]

Thank you, that worked.:p

---

### Post by pinkpanther01010 on 2005-11-30
I've tried everything on this post and i still have this problem..it's just an inch bar across the screen that's just a mashed GUI.  And when starting linux I get the error "Failure loading temporary name resolution"..btw i'm a noob. ;)   I have linux running on my server just fine but when I attempt to run the beast on my normal computer it gets all messed up.  for graphics = Nvidia 7800GT

---

### Post by pinkpanther01010 on 2005-11-30
alright i take that back i put on the 32bit OS and it works :) thanks for the scripts..or whatever i'm not sure what their called in linux :)

---

### Post by meles² on 2005-12-17
Hi spoop,

i had the same problem and worked around with some BIOS settings:
AGP Mode: from 8x to 4x
AGP Fast Write: from enabled to disabled.
Don't think it's professional :-k  but since that day, the graphics works fine!

Good luck
meles²

using ubuntu 5.10 64 Bit on ASUS K8V-X SE Mainbd., Athlon64+, ATI Radeon 9250 graphics adapter

---


---
title: "XServer fails to load"
date: 2006-05-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by tonyweb on 2006-05-07
Hi there,
I've used several distro in the past and now I was going to use ubuntu as my only distro and OS on my pc. My pc is an Athlon 64 3500+, with 1GB DDR2, 250GB 16M cache SATA2, and mobo ASUS A8N-VM CSM-UAYGZ.

I installed several times UBUNTU 64 Bit and it failed to load the Xserver all the times. My screen and integrated video card, both support the widescreen 1440x900 so I tried that and X failed.

So I tried all the resolutions, till the point that I selected only up to 1024x768. Nothing to do though.

As you can imagine this really disappointed me, I was expecting at least a VGA 16 colors Windows like, but nothing startx fails miserabily.

I tried sudo dpkg-reconfigure xserver-xorg  but no joy. :confused: 

Could you please help me? I don't want to use a different distro just because of this. 


Many thanks,
Tony

PS: my monitor is a KDS 19" Widescreen.

---

### Post by DarkNemesis618 on 2006-05-08
I had the same thing happen to me.  Open up your xorg.conf file and see what driver it's using.  When I first installed Ubuntu, it set the driver to "nv".  I changed it to "vesa" and it booted up fine.  Not sure if that helps, but it'd be worth a try.

---

### Post by usernamed on 2006-05-08
Hi Tony,

Have you had any luck?  Do you know the make and model of your graphics card?  Do you get any error messages?

---

### Post by kaffeine on 2006-05-08
Higher resolution is better avoided on first start (i usually set 800x600 on installation) - once you have a working X config, tweak the Vert Sync and Horz Sync frequencies in your xorg.conf (according to the capabilities of your monitor) to increase resolution.

if changing those numbers doesn't solve the issue,  it's probably a driver problem. (/var/log/xorg.0.log has useful info)

as DarkNemesis suggested - check your /etc/X11/xorg.conf file. look in the Section "Device" for what it says about the "Driver". if it is "nv" then install nvidia-glx (your mobo has an integrated nvidia GeForce video card IIRC) by doing 

```
sudo apt-get install nvidia-kernel-common nvidia-glx
```

this should change your driver name to nvidia in your xorg.conf after installation and you should be able to start X server with any resolution supported by your video card/monitor.

---

### Post by tonyweb on 2006-05-10
Thanks Kaffeine. that worked.

---


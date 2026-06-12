---
title: "Kubuntu Boots to a blank display after install"
date: 2008-01-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by jmsmms on 2008-01-08
I'm newish to most of this and could really use some help.

I've built a new box and am having problems post install. I have an asus PN32-e sli motherboard with 4GB of DDR2 800 RAM, and an Intel core2quad q6600. I have 2 GeForce 8600 GT's that I'd like to get running in SLI mode. I downloaded the 64-bit Version of Kubuntu. The Live CD boots with no problems, however post install I only get a blank screen. I've Tried installing the latest drivers from Nvidia and that doesn't fix the problem. I've banged around in My Xorg.conf file with no Luck. I don't know what else to do and could really use some help. Should I run the 32-bit version instead? ( I'd hate to do that.)

---

### Post by soslug on 2008-01-12
I have experienced something similar to that which you describe, check the usplash.conf file matches the resolution of your monitor edit usplash.conf file and run the update-initramfs

#> sudo vim usplash.conf

Configuration file /etc/usplash.conf

# Usplash configuration file
xres=1280
yres=1024

As you can see yres is set to 1024 which is larger than the 800 the screen is capable of, substitute 1024 with 800 and save this file then run sudo update-initramfs -u -k `uname -r`

#> sudo update-initramfs -u -k `uname -r`

hope this helps

---


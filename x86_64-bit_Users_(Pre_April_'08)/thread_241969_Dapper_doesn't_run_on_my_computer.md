---
title: "Dapper doesn't run on my computer"
date: 2006-08-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by Burmi on 2006-08-23
Hi!

I wanted to install Dapper, booting from CD is OK, it starts the first menu, where I can choose eg. "Start or install Kubuntu" or "Start in safe graphics mode". If I choose the first one, it loads the kernel, and than stops - background stays black, Kubuntu logo is also there as well as the status bar - which looks like if it didn't do anything since I chose to start (it's still in darker color). Neither CD ROM, nor HDD shows any signs of working. If I'm starting shut down (by pushing the power button on my comp.), it shuts down correctly (unloads everything and waits for ANY key :p )

If I choose safe graphics mode, the graphics dies at the same spot, but the system loads completely, I can here the welcome sound, but the display does not receive signal

My config is:

MSI K8N Neo 4 (nforce4 chipset)
AMD Athlon 64, 3000+
Abit ATI Radeon x700 Pro

I've tried it out on a different computer (also AMD 64 bit), it was working fine (but really slow - windows opened in about five minutes after the click, install was about 1 and a half hours), installed it, put the HDD back to the original one - just to try it out, and it died at the same spot

Does anyone has a solution for this? (Except buying a new video card...)

---

### Post by tseliot on 2006-08-23
Please follow these instructions:

1) Install Ubuntu using the alternate installation CD.

2) After the installation the xserver will crash

3) You will be able to boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

4) Type:
```
reboot
```

The Xserver should work fine

If it doesn't, repeat the process above and use "vga" instead of "vesa"

---

### Post by Burmi on 2006-08-23
Wow, Thanks!

---

### Post by Burmi on 2006-08-25
Hello again,

I finally had the oportunity to try out the method you have suggested, but it seems it does not work. Vesa seems to be a little bit better, but vga dies at the same spot (vesa also dies, but with a second later...)

An other idea to solve this problem would be greatly appriciated!
Thanks in advance!

---

### Post by SilverApple on 2006-08-26
Hi,
  This is a very common problem for us ati user, but the solution is pretty simple. all you need to do is install the ati proprietary drivers. This was taken from [http://www.ubuntuguide.org](http://www.ubuntuguide.org) and worked very well for me with full 3d hardware acceleration

Method 1: Installing Dapper's Included Driver (8.25.18) 

The included fglrx driver supports Radeon 8500+ and the X-series cards up to X1900. 

Unfortunately OpenGL seems to be broken for R200 cards (everything below Radeon 9500) in this driver version. The Troubleshooting section describes how to fix this after xorg-driver-fglrx is installed. 
[edit]
Installing the driver 

Make sure the restricted repository is enabled in /etc/apt/sources.list or this guide will not work! 

Help on enabling repositories can be found at [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu). 
sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

Now Reboot your system: 
sudo shutdown -r now

An alternative to the aticonfig --initial command is to edit /etc/X11/xorg.conf and replace the string "ati" with "fglrx" in the "Device" section. This way you won't lose your old "Screen" and "Monitor" settings. Afterwards you can use aticonfig for setting overlay etc. 
[edit]
Confirm that it works 
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.5814 (8.25.18)

---

### Post by Burmi on 2006-08-26
Thanks for the suggestion, but it did not work...

I run through the steps I found at [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide) which was very useful, but unfortunately did not work either. Finally We've figured out from xorg log, that X server crashes becuse it could not load R200 driver. My video card is using RV410 - that was really suspicious. Finally I've changed "ati" in xorg.config Device section to radeon, did the same at xorg.config-fglrx-0, and it works now perfectly!

Thanks for the suggestions and help!

---


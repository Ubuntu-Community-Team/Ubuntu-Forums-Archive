---
title: "NVIDIA 180.22 Driver + SLi configuration problem"
date: 2009-01-22
forum: x86 64-bit Users
---

### Post by Deceptia on 2009-01-22
I have two Nvidia 9600GT graphics cards in SLi mode on an Abit FP-IN9SLi motherboard. This board has a card that's like laptop memory which switches it between SLi and Normal modes. 

I just tried installing the Nvidia 180.22 driver because neither 173 nor 177 will work on my system (surprise, surprise, neither does 180.22 at the moment!). I can install the driver and it re-compiles the kernel like it should. Then when I reboot X doesn't load correctly, ctrl-alt-f7 just takes me to a black screen with a blinking cursor. All other tty terminals work fine (as just command-line terminals) but nothing I do to the X server can get it going properly. 

I did get it to work by removing one video card and switching the card on my motherboard to Normal mode. But that's not an option because I bought two video cards to USE two video cards and I'm not going to uninstall one every time I feel like farting around with 3D effects in Ubuntu. While I was messing with the X server I did try enabling sli through ```
sudo nvidia-xconfig --sli=On
``` (I also tried Auto) but it didn't do me any good. Has anyone had a similar problem?

I'd love to have 3D support so I can play with all the fun 3D effects and work on getting some games running since this is my most powerful machine. Any help is greatly appreciated!

---

### Post by dagrump on 2009-01-22
OK, both cards in & card switched over to SLI mode install the drivers & reboot. That should leave you at TTY1, login, then sudo nvidia-xconfig. That will write a xorg.conf file, now you need to find out the busid of your primary card lspci command will list your cards. Mine is 01:00:00. At this point you need to edit the xorg.conf file created earlier. sudo nano /etc/X11/xorg.conf you add in the device section BusID   "xx:yy:zz" Using the address found with lspci. Also add,  Option   "SLI"   "SFR" then ctrl o to save & ctrl X to quit.
Now sudo shutdown -r now to reboot & you should have X.
Also there is a thread "GUI doesn't load after nvidia install" or something along those lines my Xorg file is posted in it so you can take a look at it.

---


---
title: "ubuntu 7.04 64bit problem, black screen although nvidia drivers inhaled correctly"
date: 2007-08-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by frankzappatistas on 2007-08-31
I have installed ubuntu 7.04 64bit in a new PC with xfx Nvidia 8800GTS in an Asus P5N SLI Plus  motherboard with a sumsung syncmaster 206bw TFT 20'' monitor , although the nvidia drivers installed correctly, following the instructions as described in [http://ubuntuforums.org/showthread.php?t=496103&highlight=nvidia+8800+drivers](http://ubuntuforums.org/showthread.php?t=496103&highlight=nvidia+8800+drivers) when i boot my PC, in the start up, if i choose “2.6.20-16-generic” witch is the default option  on the boot loader, a black screen follows and the system restarts after a few minuets repiting this situation for ever, but if i choose "2.6.20-16-generic- recovery mode" and type “sudo dpkg-reconfigure xsever-xorg” following this procedure ubuntu starts correctly with Nvidia log on start up and everything runs smoothly, but if, for any reason I restart my PC I and up with the same problem. I am using 1680x1050 resolution but i thing the problem is that something is blocking me to save the configuration in the X configuration file. Please help, i don't want to go back to Microsoft, i want to live in UbuntuLand.

---

### Post by John.Michael.Kane on 2007-08-31
> **frankzappatistas said:**
> I have installed ubuntu 7.04 64bit in a new PC with xfx Nvidia 8800GTS in an Asus P5N SLI Plus  motherboard with a sumsung syncmaster 206bw TFT 20'' monitor , although the nvidia drivers installed correctly, following the instructions as described in [http://ubuntuforums.org/showthread.php?t=496103&highlight=nvidia+8800+drivers](http://ubuntuforums.org/showthread.php?t=496103&highlight=nvidia+8800+drivers) when i boot my PC, in the start up, if i choose “2.6.20-16-generic” witch is the default option  on the boot loader, a black screen follows and the system restarts after a few minuets repiting this situation for ever, but if i choose "2.6.20-16-generic- recovery mode" and type “sudo dpkg-reconfigure xsever-xorg” following this procedure ubuntu starts correctly with Nvidia log on start up and everything runs smoothly, but if, for any reason I restart my PC I and up with the same problem. I am using 1680x1050 resolution but i thing the problem is that something is blocking me to save the configuration in the X configuration file. Please help, i don't want to go back to Microsoft, i want to live in UbuntuLand.

Resolution methods.adjust for which gpu your using.

[screen refresh rates....]("http://ubuntuforums.org/showthread.php?p=2605716#post2605716") 

[HOWTO: change resolution/refresh rate in Xorg]("http://ubuntuforums.org/showthread.php?t=83973&highlight=resolution")

Note: Make sure to have your lcd manual, As you will need to refer to it for certain settings.

---


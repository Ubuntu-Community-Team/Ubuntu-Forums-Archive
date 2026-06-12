---
title: "missing kernel headers - ATI driver install gone sour"
date: 2009-06-02
forum: x86 64-bit Users
---

### Post by Bloemetjesgordijn on 2009-06-02
Hi Guys,

I think I just messed up my system real good. :(

I have tried to install a new ATI dirver without succes.

Now I want to reinstall my system with the 'normal' ATI version shipped with Jaunty with help of the application EnvyNG. However Envy gives an error message: "EnvyNG has detected that the headers for your kernel are missing and cannot be installed" 

According to uname -r I am on: 2.6.27-11-generic with Jaunty ???? 
It reinstalls 2.6.7.11 (I think) but still I get the ENvy error.

Please help...how can I get my system running with the normal ATI version??

PS The only way I can connect to my system is via remote (as display driver is not working).


Cheerz

Bloemetjesgordijn

---

### Post by utnubuuser on 2009-06-02
As far as I know, you don't need envy to install ATI.
At the recovery console:> sudo apt-get remove fglrx --purge
or> sudo apt-get remove envy --purge

and> sudo apt-get isntall xserver-xorg-video-ati
or> sudo apt-get install xserver-xorg-video-radeon
or > sudo apt-get install xserver-xorg-video-radeonhd
and if neccessary, > sudo dpkg-reconfigure xserver-xorg
and restart between removing the old driver/envy, and installing the new driver, then restart after new driver is installed. (not absolutely necessary, though advisable).
PS. In recovery mode you probably don't need to use "sudo".

And in your xorg.conf file, make sure you end up with "ati", "radeon" or "radeonhd"  listed as the driver in the "Device" section.

---

### Post by ajgreeny on 2009-06-02
and if neccessary,  	Quote:
 	 	 		 			 				```
sudo dpkg-reconfigure xserver-xorg 			 		
```
I think all was well until this bit which is now deprecated in ubuntu (does not work any more with the new xorg version).

Having made sure you have the kernel headers you need and the driver packages, as shown in the last post, just boot to recovery mode and choose **xfix** at the menu that appears,  Then boot to ubuntu normally and you should be back to a standard ati/radeon driver again.

---

### Post by Bloemetjesgordijn on 2009-06-02
Thx utnubuuser & ajgreeny

It worked.


@ ajgreeny

> **ajgreeny said:**
>  choose **xfix** at the menu that appears

Which menu do you mean, if I remember correctly I only got a few questions about my keyboard layout....?

Kind regards,

Bloemetjesgordijn

---

### Post by ajgreeny on 2009-06-03
I presume  from your edited post that you have now found the menu which I talked about for xfix, but if not it quickly appears after you have booted to Recovery Mode from grub.

---

### Post by Bloemetjesgordijn on 2009-06-03
all you guys ...thx for your help

---


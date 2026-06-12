---
title: "Problem starting xserv (graphical interface)"
date: 2006-05-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by Strangerdave on 2006-05-15
Greetings,

Kind of a newbie here, but I just built a system:

ASUS SLI-Premium
AMD S939 +3800 64 Manchester dual core
1 GB RAM
80 GB WD Hard Drive (it's a dual boot with Windoze on the other)
BFG GeForce 7600GT OC

I tried to install AMD64 version of Ubuntu and it failed to start xserv

I think I have to check what drivers are listed but I do not know what commands to use.  If this is not what I should be doing could someone point my in the right direction?

Thanks for any and all help

-SD-

---

### Post by Sutekh on 2006-05-15
The problem probably lies with the open source **nv** drivers that come with Ubuntu by default.


You can use this command to change them temporarily to the **vesa** drivers, which seem to be a general fix-all driver.
```
sudo dpkg-reconfigure xserver-xorg
``` - when prompted for a password, use your users password. 

 - this command will reconfigure the X server (the GUI), you will be asked a long string of questions regarding the input devices of your PC; your keyboard, mouse and monitor. If you don't know what you should answer to these questions go with the default/suggested ones.

 - the important step is when you are asked to choose the video card driver for the X server choose **vesa**

 - once you are done use this command
```
sudo /etc/init.d/gdm restart
```  - this will restart the GNOME Display Manager, and start the GUI.


 - If this all works out then you can consider installing the proprietry NVIDIA drivers to take advantage of you card. You can read all about it here

[Ubuntu Forums - HOWTO Latest NVIDIA Drivers]("http://www.ubuntuforums.org/showthread.php?t=75074")

 - Method 1 is by far the easiest method, and will install the Ubuntu repository NVIDIA drivers (v7667)

 - Method 2 is a little harder and can be used to install any version of the proprietry NVIDIA drivers.

---

### Post by Porky on 2006-05-15
hei thanks. this workt.
but it is restart not resart.  But I shudent talk:P

---

### Post by Strangerdave on 2006-05-15
Sutekh,

Thanks for the tip, I will try that out!

-SD-

EDIT**Works like a charm, now on to the second aspect of your answer, installing the correct video drivers.

---

### Post by Sutekh on 2006-05-15
[quote=Porky]hei thanks. this workt.
but it is restart not resart.  But I shudent talk:P[/quote] 
Oh thanks for pointing that out!  My sticky KVM switch strikes again!

[quote=Strangerdave]Sutekh,

Thanks for the tip, I will try that out!

-SD-

EDIT**Works like a charm, now on to the second aspect of your answer, installing the correct video drivers.[/quote]
Great to hear it's working for you!

---

### Post by lucky_duck on 2006-05-17
Hi 

I have a AMD 3800+ X2 
ASUS A8R-MVP ATI radeon xpress 200 
X800 GT PC Express Graphics card.
1.5gb or Ram

I have the same problem with the 64 Bit version and the Graphical interface. 
Is my ATI board compatable at all. Even the beta version of  Draper has a problem with my ATI chipset

Please help

---

### Post by Sutekh on 2006-05-17
[quote=lucky_duck]Hi 

I have a AMD 3800+ X2 
ASUS A8R-MVP ATI radeon xpress 200 
X800 GT PC Express Graphics card.
1.5gb or Ram

I have the same problem with the 64 Bit version and the Graphical interface. 
Is my ATI board compatable at all. Even the beta version of  Draper has a problem with my ATI chipset

Please help[/quote] Have you tried reonfiguring the xserver with the **vesa** driver?  Did this fix your problem?  The **vesa** driver should help out with both NVIDIA and ATI cards, when they are trouble.

If you get the graphical interface working with the **vesa** drivers, you could look into installing the Official ATI drivers, through one of these means.  

You can try either this HOWTO
 
 [Ubuntu Document Storage Facility - Install ATI Driver]("http://doc.gwos.org/index.php/Install_ATI_driver")
 
or look into installing EasyUbuntu (for GUI install of ATI drivers and loads of other stuff).  Im not sure if this will work for 64bit Ubuntu, I'll have to check.
 
 [Ubuntu Forums - Easy Ubuntu v2.2]("http://ubuntuforums.org/showthread.php?t=64629")

---


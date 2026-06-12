---
title: "64 bit crashes on install"
date: 2007-08-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by inverse on 2007-08-15
I am trying to install the 64 bit  version on my machine and it crashes each time I try to boot from the cd. The first splash screen comes up, then when i click on start/install it says loading linux kernel, goes to 100% then monitor turns off and nothing else happensfor several minutes untill i reset it. I have ubuntu 7.04 and i just downloaded tribe 4 of kubuntu same result.  I  installed and have been using the 32 bit version (feisty) for several weeks now on same machine.
athlon 64 3500
ati x850 
asus a8v deluxe
audigy 2

I am still a noobeee to linux but would like to try the 64 bit version to see how well it will work.

---

### Post by dabl on 2007-08-15
Your video system is not identified well enough for the installer to run in GUI mode.

I recommend you download and burn the Alternate Install CD, which will allow you to install in VGA/Text mode -- usually works on any video display system.  ;-)

---

### Post by John.Michael.Kane on 2007-08-15
Another option to try.

Reboot the machine. At the boot/install prompt (make sure to hit F6 first), and add the command below to the boot parameter.
```
nosplash noapic nolapic
```  
note: do not remove any of the commands already shown in the boot line. just add the above commands to it.

---

### Post by inverse on 2007-08-17
i found an old pny tnt2 pci card from a few years ago and put it in to try,
and it boots perfectly. already had resolution set correctly. (1680x1050) when i put the ati card back in it wont boot again. i havent tried anything else yet just getting back to working on it. can i load another driver or do something to help while i have the old card in to get it to recognize the ati card correctly?

---

### Post by John.Michael.Kane on 2007-08-17
> **inverse said:**
> i found an old pny tnt2 pci card from a few years ago and put it in to try,
and it boots perfectly. already had resolution set correctly. (1680x1050) when i put the ati card back in it wont boot again. i havent tried anything else yet just getting back to working on it. can i load another driver or do something to help while i have the old card in to get it to recognize the ati card correctly?

Option 1:
You can try booting from the alternate Or livecd applying the command posted above.While having the ati card installed.

Or

Option 2: Use one of these method to install the second driver.  I have not tested install two drivers so it may or may not work.
[Pre-Installation Checks]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Pre-Installation_Checks")

[Ubuntu ATI Feisty Installation Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_1:_Install_the_Driver_the_Ubuntu_Way")

[BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

[B]Note if you use option 2 while using your nvidia card you will have to make sure that xorg is set to see your ati card. before you reboot the machine, 
To make sure your xorg is set correctly run ```
gksudo gedit /etc/X11/xorg.conf 
``` scroll down till you find Section "Device" it should read ati or ATI Technologies, Inc. ATI Default Card[/B]

---

### Post by inverse on 2007-08-18
i just realized it is defaulting to a resolution higher than the monitor is able to recognize. if i boot from the cd i can hit f4 and choose the correct resolution and it loads fine. how do i do this when booting from the hdd

---

### Post by John.Michael.Kane on 2007-08-18
> **inverse said:**
> i just realized it is defaulting to a resolution higher than the monitor is able to recognize. if i boot from the cd i can hit f4 and choose the correct resolution and it loads fine. how do i do this when booting from the hdd

Resolution methods.adjust for which gpu your using.

[screen refresh rates....]("http://ubuntuforums.org/showthread.php?p=2605716#post2605716") 

[HOWTO: change resolution/refresh rate in Xorg]("http://ubuntuforums.org/showthread.php?t=83973&highlight=resolution")

---

### Post by Scotty562 on 2007-08-19
Same thing happened to me. I used the alternate cd and it installed fine.

---


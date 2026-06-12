---
title: "Ubuntu Install Error"
date: 2007-04-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by FromAtoZink on 2007-04-06
Hey everyone,
     First let me apologize for my ignorance as I am a complete Linux newb. I was trying to install Ubuntu Edgy (6.10) and it gets stuck right after the first splash screen. I downloaded the 6.10 image for AMD 64, burned it to a disc and booted from it. After I chose the "start or install Ubuntu" option, I presume it loaded some files and then this error came up:

Decompressing Linux....Done
Booting the kernel
[     27.566608] PCI: Cannot allocate resource region 2 of device 0000:05:00.0
[     27.566641] PCI: Cannot allocate resource region 0 of device 0000:05:00.1
[    170.994895] hda: ide_intr: huh? expected NULL handler on exit
[    171.043358] buffer I/O error on device hda, logical block 358278

This block of errors repeats, but the 6 digit number after the period changes each time. The logical block number stays constant. 

My setup is:
AMD Athlon FX 55
ABIT Fatality AN8
WD SATA Raptor (Not part of a raid array)
2 GB RAM
ATI Raedon X800XL

If I am beyond help I understand, but anything you can offer would be appreciated. Thanks

---

### Post by juantovarm on 2007-04-08
I imagine you downloaded the live cd image and burnt it at 4x. You can download the ALTERNATE cd for 64 architechture and install it via TEXT mode. You have to look for it somewhat.

Here's a link where to get it

[http://espelhos.edugraf.ufsc.br/ubuntu-releases/6.10/](http://espelhos.edugraf.ufsc.br/ubuntu-releases/6.10/)

That will give you more options than the "regular" site.

Hope it works :D

ps, here's an even better place where you can choose where to download from:

[http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors)

---

### Post by rsambuca on 2007-04-08
Try adding ```
ide=nodma
``` as a boot option at the startup screen (F6 if I recall correctly).  Add the comment before the "--" at the end of the line, and leave a space before the double dashes.

If that doesn't work, there are a lot of other boot options I would try before I downloaded another CD image.  It only takes a couple of minutes to try the boot options.

---

### Post by FromAtoZink on 2007-04-10
Thanks guys, that did the trick. Although, now I have developed a new problem. The install went through fine, but right after the Ubuntu splash screen, it asked for my login and password. The screen flickers a few times, shortly after which I get a error message saying that the system is unable to start x server. It then gives me the option to view error logs, but my Linux newb status makes these somewhat useless for me.

---

### Post by rsambuca on 2007-04-10
That sounds like an issue with your ATI graphics card.  I can't help you with this one since I am an nVidia guy, but if you search these forums for ATI, X server, etc., I am sure someone will be able to help you.

Good luck

---

### Post by Overseer10 on 2007-04-10
> **rsambuca said:**
> Try adding ```
ide=nodma
``` as a boot option at the startup screen (F6 if I recall correctly).  Add the comment before the "--" at the end of the line, and leave a space before the double dashes.

If that doesn't work, there are a lot of other boot options I would try before I downloaded another CD image.  It only takes a couple of minutes to try the boot options.


I seem to have the same problem as the author of this topic, but I don't understand how to do the " ide= nodma-" and where, could you guide me step by step?

---

### Post by rsambuca on 2007-04-10
When you boot from the CD, you shuold get an ubuntu logo and some start menu options.  At this stage, press F6.  Near the bottom of the screen, you will then see a bunch of command line inputs.  At the end of the line is a couple of dashes "--".  Move your cursor in front of those dashes and enter ide=nodma, then leave a space and press enter to try booting.

---

### Post by Overseer10 on 2007-04-10
It worked, somehow. But it gets stuck at 2% when reading the cdrom. :(

---

### Post by robstat on 2007-04-11
Firstly I must say I know nothing about linux but I had a similar problem so I searched the forums and someone said to hit f6 when you see the startup screen and enter "noapic and apci"(without the " ") then enter and it installed fine.
It may work for you or may not but worth a try if it's going nowhere.

---

### Post by rsambuca on 2007-04-11
> **Overseer10 said:**
> It worked, somehow. But it gets stuck at 2% when reading the cdrom. :(

What are your system specs?

---

### Post by Overseer10 on 2007-04-13
64x AMD +3200
1Gb DDR2
Gforce 7300 LE
ATI RS480
160Gb
Windows XP (atm)

---


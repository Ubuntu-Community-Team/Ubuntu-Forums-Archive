---
title: "Going to install, need a heads up"
date: 2007-08-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by Wilden on 2007-08-17
Hey there guys,

I'm planning on dual-booting Ubuntu 7.04 and XP on my 64-bit machine and was wondering if there are any tips that would help me get it up and running smoothly, and if you could answer a couple of questions that would be useful.

First off, I've been using the Live CD for a while, and enjoying myself thoroughly with it. Just recently I have been getting kernal panics everytime i boot Ubuntu, however, the noapic command sorts this. Is there a permanent fix for this, as it is very annoying.

Secondly, about dual booting, I understand there are various ways of doing it, and I have decided to go with a boot loader. Now, which ones are recommended? I assume there are some good ones out there, though I haven't been able to find one.

Thirdly, when using the live CD I am unable to set widescreen resolutions, I have a 1440*900 monitor. I understand that there is something I can do in xorg to fix this, though I am unsure what.

Here are my specs:
AMD Acthlon X2 3800+
2GB Ram
ATI x1300 512MB
200GB

Also, if there is anything else that might be of use to me, please say.

Thanks in advance

---

### Post by John.Michael.Kane on 2007-08-17
> **Wilden said:**
> First off, I've been using the Live CD for a while, and enjoying myself thoroughly with it. Just recently I have been getting kernal panics everytime i boot Ubuntu, however, the noapic command sorts this. Is there a permanent fix for this, as it is very annoying.
Run the following:
```
gksudo gedit  /boot/grub/menu.lst
```
Add the option to the line that starts with "# kopt=". 

Then run:
```
sudo update-grub
```

> **Wilden said:**
> Secondly, about dual booting, I understand there are various ways of doing it, and I have decided to go with a boot loader. Now, which ones are recommended? I assume there are some good ones out there, though I haven't been able to find one.
This should help. 

[WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot?highlight=%28dual%29")

> **Wilden said:**
> Thirdly, when using the live CD I am unable to set widescreen resolutions, I have a 1440*900 monitor. I understand that there is something I can do in xorg to fix this, though I am unsure what.
You may want to try one of these methods.

[screen refresh rates....]("http://ubuntuforums.org/showthread.php?p=2605716#post2605716") 

[HOWTO: change resolution/refresh rate in Xorg]("http://ubuntuforums.org/showthread.php?t=83973&highlight=resolution")

> **Wilden said:**
> Also, if there is anything else that might be of use to me, please say.

Thanks in advance
This should help with any other issues such as codecs/flash.
[Please Read First Advantages and Disadvantages of 64bit. (Plus install Guides)]("http://ubuntuforums.org/showthread.php?t=368607")

---

### Post by dabl on 2007-08-17
> **Wilden said:**
> 

the noapic command sorts this. Is there a permanent fix for this, as it is very annoying.

Yep, you'll add "noapic" to the kernel boot line in your /boot/grub/menu.lst file.

> 

Secondly, about dual booting, I understand there are various ways of doing it, and I have decided to go with a boot loader. Now, which ones are recommended? I assume there are some good ones out there, though I haven't been able to find one.

Assuming you're doing it all on a single hard disk drive, the straightforward approach is first to partition your drive into 4 primary partitions:

- First one is for Win XP
- Second one for Linux root "/"
- Third one for Linux user data "/home"
- Fourth one for Linux swap

The second through fourth partitions can be in any order.  Root needs to be at least 7GB, in my opinion, swap can be 0.5GB pretty safely, and the rest of the available space can be for your /home partition.

Install Win XP first, and it will of course set itself up to boot.

Install Ubuntu, and just let it put the Grub bootloader in the MBR where Win XP has its bootloader.  The Ubuntu installer will automatically set up Win XP to be available on your boot menu.

> 

Thirdly, when using the live CD I am unable to set widescreen resolutions, I have a 1440*900 monitor. I understand that there is something I can do in xorg to fix this, though I am unsure what.



If you search this forum for "ATI X1300 driver" I would think you'll find all kinds of advice on how to configure it.  :)

---

### Post by Jouke74 on 2007-08-17
Leave windows the way it is, and just defrag your system before you install Ubuntu.
Ubuntu should take care of the rest during install. If you have multiple harddisks check carefully where GRUB is going to be installed. 

Know how to : partition or change partitions en which harddisk contains what.

Keep your windows CD ready, and if you want to be safe backup your data (always good).

---

### Post by Wilden on 2007-08-17
Thank's for the help guys, I am indepted to you all.

---

### Post by Capt.Marion on 2007-08-17
I am literally doing the same thing right now (Windows is installing as I type).

Quick question- should you use the Alternate install CD or the normal one for just a normal desktop computer?

Also- my apologies for so blatantly hijacking your thread...

---


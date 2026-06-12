---
title: "kernel panic on compaq"
date: 2008-08-23
forum: x86 64-bit Users
---

### Post by jaideep_jdof on 2008-08-23
I am trying to install ubuntu 8.04 on my new compaq laptop CQ50-106AU which has following spec:

cpu:AMD Athlon™ X2 Dual-Core
ram:1024 MB
hdd:160gb sata
video:NVIDIA GeForce 8200M
wifi:Atheros AR5007 or Broadcom(I am not sure which make it is because there are drivers available in the download driver page for both these wifi models)

The problem i am facing is that when i boot from the installer cd the booting stops with kernel panic, i am using the 64bit version of ubuntu. 

Please help me install ubuntu on my system. I tried to install windows to check if its an hardware issue but xp installed and worked perfectly. It doesn't seems to be an an hardware issue.

following are the url for detail about the laptop:
description:[http://h10010.www1.hp.com/wwpc/in/en/ho/WF06b/321957-321957-3329742-89318-89318-3739787-3740388.html]("http://h10010.www1.hp.com/wwpc/in/en/ho/WF06b/321957-321957-3329742-89318-89318-3739787-3740388.html")

driver:[http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=2093&lc=en&cc=in&product=3740387&dlc=en&lang=en]("http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=2093&lc=en&cc=in&product=3740387&dlc=en&lang=en")

---

### Post by tangibleorange on 2008-08-23
> **jaideep_jdof said:**
> I am trying to install ubuntu 8.04 on my new compaq laptop CQ50-106AU which has following spec:

cpu:AMD Athlon™ X2 Dual-Core
ram:1024 MB
hdd:160gb sata
video:NVIDIA GeForce 8200M
wifi:Atheros AR5007 or Broadcom(I am not sure which make it is because there are drivers available in the download driver page for both these wifi models)

The problem i am facing is that when i boot from the installer cd the booting stops with kernel panic, i am using the 64bit version of ubuntu. 

Please help me install ubuntu on my system. I tried to install windows to check if its an hardware issue but xp installed and worked perfectly. It doesn't seems to be an an hardware issue.

following are the url for detail about the laptop:
description:[http://h10010.www1.hp.com/wwpc/in/en/ho/WF06b/321957-321957-3329742-89318-89318-3739787-3740388.html]("http://h10010.www1.hp.com/wwpc/in/en/ho/WF06b/321957-321957-3329742-89318-89318-3739787-3740388.html")

driver:[http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=2093&lc=en&cc=in&product=3740387&dlc=en&lang=en]("http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=2093&lc=en&cc=in&product=3740387&dlc=en&lang=en")

have you tried checking your disc for errors? it's one of the options in the menu when you first boot the CD

---

### Post by Ptero-4 on 2008-08-23
Are you sure it´s a 64bit CPU. It says Athlon, not Athlon64.

---

### Post by jaideep_jdof on 2008-08-23
It is writen athlon 64 on the sticker.

---

### Post by LateNiteTV on 2008-08-23
.....

---

### Post by jaideep_jdof on 2008-08-23
I have attached a photo of the error msg i get when i boot the cd by adding "panic=30" to the boot paramter and disabling the splash.

I also checked the cd for defects, it is fine.

---

### Post by tangibleorange on 2008-08-24
> **jaideep_jdof said:**
> I have attached a photo of the error msg i get when i boot the cd by adding "panic=30" to the boot paramter and disabling the splash.

I also checked the cd for defects, it is fine.

try using the 32 bit?

---

### Post by felker2 on 2008-08-24
Aha, some quotes from your screendump:

"hardware error"
"cpu 0: machine check exception" 
"hardware revision not supported" 
"this is not a software problem" 

See [http://en.wikipedia.org/wiki/Machine_Check_Exception](http://en.wikipedia.org/wiki/Machine_Check_Exception) for some explanation and root cause analysis of Machine Check Exceptions.

I myself would try this on a new laptop:
[LIST]
[*]run memtest86
[*]use an other (older) ubuntu version (7.10)
[*]use a 32-bit version of Ubuntu 8.04
[*]try to alter some boot options like acpi apic pci
[/LIST]
to see if that changes anything.

---

### Post by jaideep_jdof on 2008-08-24
I ran memtest86 but no error were found.
The I tried to boot ubuntu 32 bit 6.06(I don't have version 7.10). It didn't boot and gave an error of some acpi bios bug. Then i added noapic to boot param but after loading the kernel it stopped booting and dropped to a busybox prompt with a controller off error.

Is there any live cd or something with which i can check al devices on my laptop.

---

### Post by Ptero-4 on 2008-08-24
You need to leave memtest86 running for a few hours (like four or more) straight for it to have a chance to uncover any signs of bad RAM (if any). Also from your comment it seems you need 7.04 or 7.10 (6.06 don´t have the drivers for your HD controller chipset), also the "hardware revision not supported" and "unable to attach hardware" errors are merely that the 8.04 version of madwifi (the drivers for Atheros wifi cards) doesn´t support yet your particular wifi card (this error normally doesn´t stop the boot process and you can sort it out later with ndiswrapper).

---

### Post by lenintorres on 2008-09-01
I got a Kernel Panic when using Ubuntu amd64, but i386 worked fine. It seems that this processor does not support Amd 64 extensions

---

### Post by lvm_723 on 2008-09-12
I have a CQ-50 too and I'm not able to install Linux in anyway.  I've tried Ubuntu 8.04 (both 64 and 32 bits versions) and openSUSE.  

Ubuntu jammed at boot and BusyBox loaded instead.  It doesn't boot on VirtualBox too (no motherboard detected... lol) !

This is the error message I've got with openSUSE
CPU 0: Machine Check Exception: 0000000000000004
However, openSUSE works fine in a VM with virtualBox on XP.


I think it's a kernel incompatibility with the nVidia chipset.  

Windows XP works perfectly but you need a lot of driver, maybe those driver are not included with linux distros right now...

---

### Post by vishal_karira on 2008-09-13
> **jaideep_jdof said:**
> I ran memtest86 but no error were found.
The I tried to boot ubuntu 32 bit 6.06(I don't have version 7.10). It didn't boot and gave an error of some acpi bios bug. Then i added noapic to boot param but after loading the kernel it stopped booting and dropped to a busybox prompt with a controller off error.

Is there any live cd or something with which i can check al devices on my laptop.
i have also the same problem
just while installing write press f6 and write
all_generic_device floppy=off irqpoll
and then try installing it
i succeded in the same way
actually by default our floppy drive have been not made default
so just try it

---

### Post by lvm_723 on 2008-09-30
Ok guys, I received the 8.04.1 LiveCD for my GUL today and tried it for fun and it worked ! (x86 version)

The problem is the Atheros driver, you need an unsupported one, which is included in the promo CD (but not in the x64 iso I downloaded yesterday...)

Have fun :P

---

### Post by Chame_Wizard on 2008-10-02
most be the kernel version

---

### Post by lvm_723 on 2008-10-07
It is tricky to have linux working on the CQ50 laptop.  You absolutely need the latest kernel version included with Ubuntu 8.04.1 liveCD.

For the wireless :
You have to download madwifi for the AR5007 ([http://madwifi-project.org/ticket/1192](http://madwifi-project.org/ticket/1192)) following this ticket.  Follow the usual instructions and everything should be ok.  Note that your wireless button on the frame will be still orange and will never turn blue, even if everything works.

For graphics :
Get envyng (apt-get install envyng) and run it (envyng -t) to install the nvidia graphic card driver. Select the manual installation and the driver version 173.14.12. Envyng is a script that will get all the packages needed and install them to configure your video card driver. When your laptop will reboot, you should see the NVidia logo before the GDM login screen.

However, I don't know how to get the sound working properly.  For the moment, I've seen no forum giving the solution.

---

### Post by lvm_723 on 2008-10-08
Good news, I found the driver for the sound card !  [http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/)

Enjoy your CQ50 !

---

### Post by retro89 on 2008-10-17
I also have a Compaq CQ50-210 and I have the same problem . I was Wondering if I can use Wubi and will this still work ok?

---

### Post by Aireas on 2008-11-12
> **lvm_723 said:**
> It is tricky to have linux working on the CQ50 laptop.  You absolutely need the latest kernel version included with Ubuntu 8.04.1 liveCD.


I need help with this one. How do we know if we have the latest kernel version? I've been trying to install Ubuntu using Wubi and a live cd (I thought they would have the latest kernels). Where can I get the lastest kernels from? Thank you very much for your help with this!

---

### Post by fuzzyworbles on 2009-02-15
I've got 8.10 32bit running fine on my cq50-116la. with 8.04 the audio was bad and 8.10 fixed that. still doesn't standby though (i should say, resume). anything on that?

---


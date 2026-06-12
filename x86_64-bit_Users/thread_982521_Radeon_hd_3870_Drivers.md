---
title: "Radeon hd 3870 Drivers"
date: 2008-11-14
forum: x86 64-bit Users
---

### Post by budaslap on 2008-11-14
I thought I would bring my post to the attention of my fellow x64ers as the drivers I am looking for should probably be 64 bit

[http://ubuntuforums.org/showthread.php?p=6181365#post6181365](http://ubuntuforums.org/showthread.php?p=6181365#post6181365)

That is my original post in hardware support.

---

### Post by Yellow Pasque on 2008-11-14
Hardware acceleration for Radeon HD cards is currently only available with the proprietary AMD/ATI driver:

For Ubuntu 8.10/Intrepid Ibex
```
sudo apt-get install fglrx-modaliases
```
Go to System -> Administration -> Software Sources and verify that the "restricted" repo is enabled.
Go to System -> Administration -> Hardware Drivers and enable the restricted driver


For Hardy/8.04
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Install_Method](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Install_Method)

---

### Post by dj4mc on 2009-06-03
I have loaded Ubuntu9.04 and after I attempt to load restricted drivers it always comes up garbled and scrambled. I have reloaded twice and tried recovery mode, editing xorg.conf and no happyness. I would appreciate any help anyone could lend. I have a AMD64 ASUS SLI deluxe MB with Nforce 4 chipset 3gig RAM and just recently got a Sapphire 3870HD card. 

Thanks in advance!

Jules

---

### Post by alex2399 on 2009-06-04
I always download 'm from the Ati driver site. Go here [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

Right click on the file and make sure it is executable in the appropriate tab. Open a terminal or ALT+F2(You must tick the checkbox show in terminal), enter the command sudo along with the name of the package you just downloaded. Instead of typing it over just drag the file into the ALT+F2 window or the terminal. If in terminal remove the quotes that come along with it. Press enter and follow installer wizard.

When finished, in the terminal enter this command: 

```
aticonfig --initial -f

```
Reboot

Works for me almost always.

---

### Post by dj4mc on 2009-06-04
Thank you I will try tonight!

---

### Post by dj4mc on 2009-06-04
Well, sadly it still booted to the "SCreen of Coruption" lol. I learned a lot and will try again. I ran the  ati setup command you posted and it went through some steps but said it failed to write xorg.conf Although when I looked at it in text edit before reboot, it showed that it was setup for the ATI settings. I will copy it and post into this thread later.

Thanks again for your help.
Jules

---

### Post by Yellow Pasque on 2009-06-04
> **dj4mc said:**
> it went through some steps but said it failed to write xorg.conf

```
**sudo** aticonfig --initial -f
```

---

### Post by dj4mc on 2009-06-04
Well I did that from the root shell in recovery mode and it said initializing file found, configuring.
using /etc/X11/xorg.config
saved back-up to /etc/X11/xorg.config.original-1

And still.... Scrambled... I am going to do a little more research on this will update if I find anything

Jules

---


---
title: "USB not working on Virtualbox ver. 2.0.4 ose"
date: 2009-05-02
forum: x86 64-bit Users
---

### Post by teixidoj on 2009-05-02
Hi,

 I recently installed Virtualbox ver. 2.0.4 ose, but USB will not work on my WIN XP virtual machine. I am running virtualbox on Ubuntu 8.10 x64. I also tried VMware, but could not get the console to work. Does anyone know of any fixes for virtualbox and USB? I tried many google searches, but came up empty.

Thank you,

John...

---

### Post by n6yga on 2009-05-03
I'm pretty sure that the OSE version of Virtualbox does not support USB. You can install version 2.2 from Sun and get USB functionality.
[http://virtualbox.org](http://virtualbox.org) Follow the insructions for adding the appropriate repository.


Mark.

---

### Post by jespdj on 2009-05-03
USB not working is indeed one of the (deliberate!) limitations of the OSE (open source edition) of VirtualBox. If you need USB support, get the non-OSE version.

(Note that the VirtualBox website had some download problems the past day, and I see that currently the whole website is down, you might need to have a little patience).

---

### Post by teixidoj on 2009-05-03
Thanks guys, I just download the non-free version; I'll give it a shot. I hope that I don't have to uninstall the OSE version, because I already install WIN XP with all it's updates, we'll soon find out.

John...

---

### Post by Slim Odds on 2009-05-03
> **teixidoj said:**
> ...I hope that I don't have to uninstall the OSE version, because I already install WIN XP with all it's updates, we'll soon find out.Uninstalling the OSE version does not affect the data files for VirtualBox (.vdi and .xml). You should not have any problems.

---

### Post by n6yga on 2009-05-03
> **Slim Odds said:**
> Uninstalling the OSE version does not affect the data files for VirtualBox (.vdi and .xml). You should not have any problems.

You are correct sir. Plus, if you change from 32bit Ubuntu to 64bit Ubuntu you can use the same virtual machines. No fuss, no muss!

Mark.

---

### Post by eaglemanneke on 2009-05-04
And....

Don't forget to do the following:

USB VirtualBox
        On 9.04 only is needed to add in /etc/fstab the next line (without the quotes)
        "none /proc/bus/usb usbfs devgid=XXX,devmode=664 0 0"
        Being XXX the Group ID of vboxusers (see under System-Administration-Users and Groups).

Eaglemanneke

---

### Post by kabloink on 2009-05-04
> **eaglemanneke said:**
> And....

Don't forget to do the following:

USB VirtualBox
        On 9.04 only is needed to add in /etc/fstab the next line (without the quotes)
        "none /proc/bus/usb usbfs devgid=XXX,devmode=664 0 0"
        Being XXX the Group ID of vboxusers (see under System-Administration-Users and Groups).

Eaglemanneke

I am pretty sure this is no longer required with the recent virtualbox releases.

---

### Post by eaglemanneke on 2009-05-04
> **kabloink said:**
> I am pretty sure this is no longer required with the recent virtualbox releases.
 
Although Devices>USB Devices list all connected USB devices, none of them
could be selected (greyed). 
After adding above mentioned line to /etc/fstab, all listed devices could be selected again.
 
VirtualBox: 2.2.2 r46594
Ubuntu: 9.04 (not upgraded from 8.10, but fresh install!)

---

### Post by arak on 2009-05-05
See my post "USB in Virtualbox 9.04" All I had to do was to go into "Users and Grooups" and activate Virtualbox.

---

### Post by eaglemanneke on 2009-05-05
Arak,
 
As you describe in your post "USB in Virtualbox, 9.04", the 'use VirtualBox' should be checked to be able to select USB devices.
In my case, this switch was set, however, I am not sure if the line which I added to /etc/fstab caused the switch to be set (I did not do this). So I removed the line and rebooted the system.
 
IT STILL WORKS! I am still able to select USB devices.
 
Solutions should be that simple!
 
Thanx.

---

### Post by teixidoj on 2009-05-05
I added the non-free version and am blown away. Everything works just fine, USB and all. This is my first time setting up a VM and am surprised how well it works. I did run into a small issue, when I tried to use my webcam the sound of my mic is very choppy; I would have to put the mic directly over my mouth to hear anything.

 I then tested the same with Ubuntu sound recorder application with the same results. Something may be wrong with my mic; I will test with another standalone windows machine to narrow things done.

John...

---


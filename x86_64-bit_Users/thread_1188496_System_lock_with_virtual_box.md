---
title: "System lock with virtual box"
date: 2009-06-15
forum: x86 64-bit Users
---

### Post by headsmash on 2009-06-15
Installed virtual box with Synaptic. I created a disk for XP and set the VM to boot to my XP iso. Upon VM start I get dropped to run level 3 (I think that's what it is in .deb enviro which I'm not using. CLI) I then get the issue that CPU0 is locked. Any thoughts?

---

### Post by headsmash on 2009-06-15
> **headsmash said:**
> Installed virtual box with Synaptic. I created a disk for XP and set the VM to boot to my XP iso. Upon VM start I get dropped to run level 3 (I think that's what it is in .deb enviro which I'm not using. CLI) I then get the issue that CPU0 is locked. Any thoughts?


I am not longer getting this error. Now the system locks, but I do not drop to the cli.

--
update
this lockup occurs when using a cd-rom to load the OS or an iso image.

Can I get this thread moved to the virtualization forum?

---

### Post by Anubis on 2009-06-16
[https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/347487]("https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/347487")

I can't get ANY help with this issue either? Please detail your computer specs?

---

### Post by markharding557 on 2009-06-17
have you tried the version from[http://www.virtualbox.org/]("http://www.virtualbox.org/")

---

### Post by headsmash on 2009-06-20
> **markharding557 said:**
> have you tried the version from[http://www.virtualbox.org/](http://www.virtualbox.org/)


I tried the OSE and the version from virtual box. I downloaded it from there and used the package manager to install. Same issue, attempting to boot anything locks the whole system or at least what I can see.

System specs.

-Computer-
Processor        : 4x 06/17 (quad 2.66)
Memory        : 6016MB (681MB used)
Operating System        : Ubuntu 9.04
User Name        : 
Date/Time        : Sat 20 Jun 2009 12:20:20 PM CDT
-Display-
Resolution        : 5280x1200 pixels
OpenGL Renderer        : GeForce 9500 GT/PCI/SSE2
X11 Vendor        : The X.Org Foundation
-Multimedia-
Audio Adapter        : HDA-Intel - HDA Intel
-Input Devices-
 Power Button (FF)
 Power Button (CM)
 Macintosh mouse button emulation
  Combo Free KVM 2/4 V:1.29  Combo Free KVM 2/4 V:1.29
  Combo Free KVM 2/4 V:1.29  Combo Free KVM 2/4 V:1.29
 PC Speaker
-Printers-
No printers found
-IDE Disks-
-SCSI Disks-
ATA Hitachi HDP72502
ASUS DRW-2014L1
Generic USB SD Reader

---

### Post by clackamas on 2009-06-29
I am curious... I am seeing similar lockups using just Mozilla.  It happens just on this site, but it is much faster if I go to a multi-media site such as [www.imdb.com](www.imdb.com).

Also, It happens when I am on the physical console or via VNC.   Because I use VNC, I have the gnome setings on basic.

Anyway, just a thought...

---

### Post by headsmash on 2009-06-29
> **clackamas said:**
> I am curious... I am seeing similar lockups using just Mozilla.  It happens just on this site, but it is much faster if I go to a multi-media site such as [www.imdb.com]("http://www.imdb.com").

Also, It happens when I am on the physical console or via VNC.   Because I use VNC, I have the gnome setings on basic.

Anyway, just a thought...

I'm using gnome basic as I have not figured how how to use the enchanced settings with xinerama.

---


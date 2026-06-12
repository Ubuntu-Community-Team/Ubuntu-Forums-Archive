---
title: "VirtualBox errors, won't load!"
date: 2008-12-09
forum: x86 64-bit Users
---

### Post by freshtealeaf on 2008-12-09
I'm trying to run Windows XP as a guest OS in VirtualBox on my Xubuntu desktop. I've configured it in VirtualBox (40GB Fixed size hard drive, etc..) and when I start it up with the WinXP iso already mounted in the cd rom, it gives me the following errors (from the error log).

```
00:00:01.665 VirtualBox 1.5.6_OSE r28240 linux.amd64 (Apr  9 2008 01:28:55) release log
00:00:01.665 Log opened 2008-12-09T09:20:10.644049000Z
00:00:01.665 ERROR [COM]: aRC=0x80004005 aIID={1dea5c4b-0753-4193-b909-22330f64ec45} aComponent={Console} aText={VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
00:00:01.665 VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED)} aPreserve=false
00:00:01.690 Power up failed (vrc=VERR_VM_DRIVER_NOT_INSTALLED, hrc=0x80004005)

```

Anyone ever encounter this before? I don't know where to start. Been using Xubuntu for less then 4 months.

---

### Post by Krovas on 2008-12-09
Did you install the correct kernel drivers?

---

### Post by BGFG on 2008-12-09
Usually when i upgrade the kernel i need to re-build the kernel module. This is the command:
```

 sudo /etc/init.d/vboxdrv setup

```

I'm not sure if the command is different for the OSE version though.

---

### Post by freshtealeaf on 2008-12-09
> **BGFG said:**
> Usually when i upgrade the kernel i need to re-build the kernel module. This is the command:
```

 sudo /etc/init.d/vboxdrv setup

```

I'm not sure if the command is different for the OSE version though.


This is the output once I entered that.

```
aries@aeonlinux:~$ sudo /etc/init.d/vboxdrv setup
 * Usage: /etc/init.d/vboxdrv {start|stop|restart|status}
aries@aeonlinux:~$ 

```

I've only been using Xubuntu for about 3 months now..

---

### Post by carling on 2008-12-09
download virtual box 2 I had no problems with that version.

the problems I do have is installing printers and drivers when in xp any body know how to install printers and  drivers? in virtual box XP?

---

### Post by freshtealeaf on 2008-12-09
Virtual Box 2?  Is it the same as OSE? I got OSE from Add/Remove...

I downloaded and installed the .deb package for 8.04 LTS. 

How do I run this? 

Sidequestion: How do I edit the programs available in my Start bar in Xubuntu?

---

### Post by BGFG on 2008-12-09
> **freshtealeaf said:**
> This is the output once I entered that.

```
aries@aeonlinux:~$ sudo /etc/init.d/vboxdrv setup
 * Usage: /etc/init.d/vboxdrv {start|stop|restart|status}
aries@aeonlinux:~$ 

```

I've only been using Xubuntu for about 3 months now..

In this case i think you could change the code to
```

/etc/init.d/vboxdrv start

```

But i would also suggest using the other version of VB only because that is the version i use with no problems and that way i'd be able to help better :) They are both free and the differences are negligible to end users like us... :)

You can get the latest VirtualBox here:

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)


Just saw your latest post, how are you doing now ?

---

### Post by Therion on 2008-12-09
**Step One:** Download the latest version of Virtual Box for your hardware from their website.
Do NOT use the version in the repo and do NOT use the version linked to in the tutorial.  Get it from here, or wish like h-ll you had:

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)


**Step Two:** Follow this tutorial to install and get your VM working.  Follow the steps exactly as outlined, but of course you can skip the download part of the tutorial since you read and followed the instructions I gave you in Step one.  The rest of the tut will get you up and running and show you how to get USB support, etc.

[http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html](http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html)

---


---
title: "Ubuntu install problems"
date: 2008-12-06
forum: x86 64-bit Users
---

### Post by holeshot77 on 2008-12-06
Well, this is my first time installing Ubuntu.  I have never even heard of it really until I saw Beryl.   So, I downloaded the ISO.  Mounted it onto a disc.  Tried to install.  Did the checksum and then starts to install.  You know where it says this amount installed of 734.5 MB.  Well, it gets all the way to 734.1 and then it says the CD is in use by something else and to retry.  Keeps giving me this error.  Pissing me off.

So, then I I just opened the rar file.  Clicked on the install icon.  Said it installed and then I needed to reboot.  Not once was I asked to set up a partition or whatnot.  But I had actually already done so through windows.

With that, I installed EasyBCD.  Had all that and used iReboot.  Well, thought I had it all right and when I go to switch to Ubuntu, it says boot manager not found.  So, this is where I am at.  

Here I am, no Ubuntu, partitioned empty 40gb slot. What should I do?   I could use some help, I really want to use this program as a Dual Booting system.  System Specs?  Oh yeah, here you go.

Gateway P7811-FX 
-Windows Vista HP 64bit
-4gb DDR3 Memory
-9800m GTS
-added additional 320 gb Sata Drive
-upgaded processor to x9100 Core 2 Xtreme 3.0. 

If someone could help me get this installed and tell me how to get Beryl going, I'd be so thankful.  

Thanks,

Jerry

---

### Post by em4r1z on 2008-12-07
By 'mounted it onto a disc', do you mean you burned the image on a CD or that you installed Ubuntu by mounting the image?

Do you want to install Ubuntu within Windows or to install it separately? I think that when you say 'clicked on the install icon' you're doing the former and because you didn't expand the ISO ('I just opened the rar file') the system cannot proceed.

If you want to install Ubuntu separately (to dual boot) you should burn the image on a CD, boot the system with it and follow the installation process. If you downloaded the Live CD image, test your hardware before installing the system.

---

### Post by felker2 on 2008-12-07
You should burn the ISO as a disk image to a CD and then boot the CD. 

You should not "Mount it onto a disc".

HTH

---

### Post by ulfire on 2008-12-15
I have the same message as holeshot77 when I try to install within windows .It does a checksum and then says it can't access the CD (it may be in use by another application :which it isn't).Click retry and the same thing happens ,click cancel and you're back to square one .It's very frustrating.
I had previously installed from the CD onto a HDD (having disconnected my other 3 HDD and it seemed to work fine ,though it ceased to function when I reconnected the other hard drives.
I've tried to install to a blank HDD ,with all HDD connected and this results in my Windows MBR getting corrupted and I can't load Windows or Ubuntu .Luckily Fix MBR cures that ,Windows works but Ubuntu doesnt.
I'm a little wary to install it to the HDD that Windows is on because I'm a little fearful that it will totally screw that installation .
Any suggestions would be extremely welcome
BTW I'm using (or trying to ) Ubuntu 8.10

---

### Post by Sef on 2008-12-16
> I really want to use this program as a Dual Booting system.

Read [Psychocats]("http://psychocats.net/ubuntu") to dual boot.

---

### Post by ulfire on 2008-12-17
OK problem solved .I reburned the image with InfraRecorder at 1X speed and it now does what it says on the package ,I tried this with 8.04 and 8.10 and both worked .
I had used Nero for the first image at 4X speed and those didn't work

---


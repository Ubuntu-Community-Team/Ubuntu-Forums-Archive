---
title: "[SOLVED] Ubuntu not booting normally"
date: 2007-10-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by Bliepo32 on 2007-10-10
I recently installed Ubuntu Feisty Fawn 64 bit edition (I used Dapper Drake 64 bit edition before this, which worked fine). The installation went fine, and also installing the restricted ATI drivers as describes in [Installing Ubuntu 7.04: ATI X***** cards](http://ubuntuforums.org/showthread.php?t=414194) (I have an ATI RADEON x800GTO) went fine.

When I boot (in normal mode), my screen goes blank, and the power led turns from green to yellow (like it is not getting any signal). Also, the caps lock and scroll lock light start flashing. The computer does not respond to anything but the power off button after that.

Booting in recovery mode and typing
```
gdm start
```

will just give me a normally working screen. I can then just log-in and work normally. THis is a temporary work-around, but I would like to fix it.

System specification:
AMD Athlon(tm) 64bit 3500+ processor
ATI RADEON x800GTO videocard
190GB Maxtor harddisk (with a partition of 5GB mounted as /home and a partition of 12GB mounted as /)
ASUS A8N-SLI Deluxe motherboard

---

### Post by pay on 2007-10-10
I get exactly the same thing. Removing some options from your /boot/grub/menu.lst fixes the problem for me. I think > title           Ubuntu gutsy (development branch), kernel 2.6.22-12-generic
root            (hd0,2)
kernel          /vmlinuz-2.6.22-12-generic root=UUID=c51c6eda-b156-4e9d-b026-9315d93565d5 ro
initrd          /initrd.img-2.6.22-12-generic
Thats the bit I changed. I think that it had quiet after ro on the root line that I removed.

---

### Post by Jouke74 on 2007-10-10
- Turn the option splash into nosplash. Then you casn see where it goes wrong. 
- You might want to change the server delay in the gdm.conf to a bit more. 
- I assume you reconfigured your X-server?

Best wishes, JJ.

---

### Post by Bliepo32 on 2007-10-10
I will try the things you suggested. Thanks for doing so. As to the question if I reconfigured my X-server: yes, I did, but because I was forced to do so, because of my videocard. I will have a try and tell you the outcome.

EDIT: UPDATE!

I did as you told me to do, and disabled to splash screen to see what went wrong. I rebooted, and it then booted just fine. It seems the splash screen itself was causing the problem.

---

### Post by picopir8 on 2007-10-10
As of yesterday, I get the same exact thing with 64 bit Gutsy beta.  Simply removing the splash command gets it to work.  Sounds like a bug with splash.  It must just be affecting certain video cards otherwise more people would be complaining.

I see you have an ATI RADEON x800GTO
Im running a NVidia GeForce 8400M GS w/319MB.

Its surprising that this is affecting multiple manufacturers.  I wonder if any others are affected.

Anyone know if a bug report has been started?

---

### Post by pay on 2007-10-10
I have an x800gto aswell. I opened a bug a while back but they closed it up without actually doing anything. perhaps someone should open another bug.

---

### Post by Law506 on 2007-10-11
I was having this same issue with my Nvidia 8600GTSs.  I would mess with it for a while and start gdm and it would work sometimes.  I thought maybe there was some code error on it trying to find my card, but maybe this is the problem. 

 I gave up on trying to get it to work about a week ago.  

What is the command or where do I change the splash to nosplash??

Thanks

---

### Post by Bliepo32 on 2007-10-11
> **pay said:**
> I have an x800gto aswell. I opened a bug a while back but they closed it up without actually doing anything. perhaps someone should open another bug.

I will give it a try and open a bug report.

EDIT: UPDATE!
I posted this bugreport:

In what package did you find this bug? Ubuntu Feisty Fawn
Summary: Bootup splash screen causes problems
Further information, steps to reproduce, version information, etc.:
> When booting with the splash screen enabled, causes the screen to go black. Additionally, the power led of the screen goes from green to yellow (which normally happens when there is no signal). Also, the Caps lock and the Scroll lock light begin flashing.

Booting in recovery mode and then typing "gdm start" in the terminal gives a normal working log-in. From there, one can disable the splash screen. The computer works fine without flash screen, and can then boot in normal mode without any problems. Because of this, it seems to me that it is the splash screen causing the problems.

I have also noticed that I am not the only one with this problem. In the forums, I have found three other posts which describe the same thing as I have experienced. I also noticed that it happens with Ati, as well as Nvidia videocards.

---

### Post by Bliepo32 on 2007-10-15
I have noticed more people are having similar problems as described here. If people who have similar problems could post a reply to this topic (please do include which version of Ubuntu you are running), I can refer to this in the bug report. This will hopefully help the bug to get fixed sooner.

---

### Post by Dan777 on 2008-01-24
Version 7.10, same problem. My graphics card is an 8800gtx.

changing the kernal option to nosplash seems to have fixed the problem.

---

### Post by tbaac on 2008-01-27
Just to add my "Me as well" to this thread.

Thank you so much for this thread.  I've been using Ubuntu/Kubuntu on my laptop for ages but haven't been able to get it to work on my home PC (Nvidia motherboard, Radeon X800GL graphics card, AMD64 version of Kubuntu).  Tried many variations on display drivers and changes to xorg.conf in a hope of getting it to work.

Finally after finding this thread I tried the "nosplash" option and it worked.  I don't have to run windoze at home now :)

---


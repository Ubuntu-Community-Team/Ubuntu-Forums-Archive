---
title: "32bit Installation on a 64bit computer"
date: 2008-02-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by Kevin Funnell on 2008-02-23
G'Gay Helpers,
A few questions please,my 32bit motherboard has gone to where all dead motherboards go. the new machine is bare only CPU 1xSARA drive and no OS,  If i install the SATA drives in the 64bit computer (dual boot Windows XP & Ubuntu 7.10 (Gusty) will I be able to use what I currently have on these drives, provided I change  /etc/X11/xorg.conf (Graphics,  etc).   Thanks in advance, Old Kevin

---

### Post by SpiderGorilla on 2008-02-23
I'm about 80% certain it'll work. Uhm... back up your important files first.

---

### Post by felker2 on 2008-02-23
Do you mean: can you change the mobo of an installed system?

Yes, you can. Linux will reconfigure automagically. 

And why change/copy the Xorg.conf? Are you changing the GPU too? And even then: first try what happens if it just works. If not, use the second boot option ("Safe Graphics" or something like that), and it will guide itself.

---

### Post by Kevin Funnell on 2008-02-23
felker2,   I do not know what you mean by "mobo" (probable due to my age).   The SATA HDs from the dead computer have Win XP (32bit) on one HD & Ubuntu 7.10 (gusty) (32bit) on the other HD.  If I install these HDs in the new 64 bit computer can I use both Win XP (32 (bit) and Ubuntu (32 bit) files & programs?  I thought I would have to change the Xorg.conf file to reflect the Graphic capability on the new computer (only onboard graphics).  Thanks,  Old Kevin

---

### Post by SpiderGorilla on 2008-02-23
"mobo" is slang for "mother board" (Mo Bo).

You're... possibly, maybe gonna have a problem with 32-bit Windows. 32-bit Linux should work. Here's the beauty of 64-bit: it had 32-bit virtualization. So it should, in theory, be able to run anything 32-bit. In theory.

Practice is usually... less awesome.

---

### Post by Kevbert on 2008-02-23
32 bit Windows and Linux work fine with a 64 bit motherboard.

---

### Post by Kevin Funnell on 2008-02-23
Thank for the info, it looks like another nail in the Windows XP coffin, I think I'll be free and be a sinlgle boot Linux/Ubuntu when the new machine arrives.   Then the questions will flow.  Old Kevin

---

### Post by Kilz on 2008-02-23
> **SpiderGorilla said:**
> "mobo" is slang for "mother board" (Mo Bo).

You're... possibly, maybe gonna have a problem with 32-bit Windows. 32-bit Linux should work. **Here's the beauty of 64-bit: it had 32-bit virtualization. So it should, in theory, be able to run anything 32-bit. In theory.**

Practice is usually... less awesome.

Yes, the hardware should be able to, but there are rare instances of the 32bit operating system having issues with 64bit hardware.

---

### Post by Kevin Funnell on 2008-02-24
Thanks Kilz and other that contributed I think I can close this post as Solved.  Old Kevin

---

### Post by Kilz on 2008-02-24
> **Kevin Funnell said:**
> Thanks Kilz and other that contributed I think I can close this post as Solved.  Old Kevin

Thats cool, and please keep in mind that the 64bit version and its performance improvements are available to you if you do a reinstall.

---

### Post by Yellow Pasque on 2008-02-24
> **Kevin Funnell said:**
> Thank for the info, it looks like another nail in the Windows XP coffin, I think I'll be free and be a sinlgle boot Linux/Ubuntu when the new machine arrives.   Then the questions will flow.  Old Kevin
Hey, we love to hear about nails in the Windows coffin and are glad to answer questions and drive those nails in.

---

### Post by kuja on 2008-02-24
Good luck with the windows end of it. Radical hardware changes have been known to invalidate the windows license .. happened to me once, though it shouldn't be hard to phone in and get a new license for it for free, with any luck.

---

### Post by Yellow Pasque on 2008-02-25
> **kuja said:**
> Good luck with the windows end of it. Radical hardware changes have been known to invalidate the windows license .. happened to me once, though it shouldn't be hard to phone in and get a new license for it for free, with any luck.
The restrictive licensing is one of the main things that drove me to open-source/Linux. If I'm a paying customer why should I have to call someone in Redmond who can barely speak English and explain to them that all I'm doing is changing some hardware, not pirating their OS?
Windows Genuine Advantage? No thanks, Mr. Gates & co., I will no longer give you money to be harassed because you can't control piracy and make the honest, paying customers suffer.

---

### Post by Kevin Funnell on 2008-03-09
G'Day All Fellow Ubuntu Users,
Thanks to all that help me with this problem

Well the installation of the new 64bit Intel Core2Duo CPU on a Gigabyte GA-G31M-S2L motherboard long with the Windows XP Home HD and I re-installed Ubuntu 7.10 Gusty Gibbon on the HD from the broken Mobo, all went well and sofar everything I have tried works in both systems.  I removed all the old WindowsRegistry/Programs/Drivers entries for all that was not required with the 64bit system, a bit time comsuming but worth it.  I think I cheated a bit I copied the files for all my updates from:  [COLOR="Sienna"]/var/cache/apt/archives[/COLOR] and this saved me a lot of download time on the dial-up service.  This will be my configuration until arrives and I'll probable install the 64bit version of Ubuntu 8.04 Hardy Heron and ditch Windows, then the  64bit Ubuntu 8.04 Hardy Heron and 32bit Windows XP might work? but.......  Old Kevin

---


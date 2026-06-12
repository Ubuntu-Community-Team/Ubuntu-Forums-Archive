---
title: "No return from sleep and corruption"
date: 2008-08-20
forum: x86 64-bit Users
---

### Post by kerodo on 2008-08-20
Just installed Ubuntu 8.04 x64 on a brand new WD 500g HD, all went well.  Set things to start screen save at 10 mins, turn off monitor at 20 mins, and sleep at 30 mins.  It appeared to go to sleep normally etc.

Woke up this morning and the PC would not return from sleep mode.  Seemed totally locked up.  So I cut the power and rebooted, but got a Grub error 17.

Loaded the live cd and ran install mode, started up the partitioner, and it looks like something got blown away, there is a swap partition and a 10 gig ext3 of some kind, but then there is a 450 gig partition of unknown file type (no ext3 as it should be) and it just says /boot on that.  

Looks like my partition table somehow got blown away in the process of sleeping and not returning. 

Anyone have any ideas what happened, and how I can avoid it?  4 gigs ram on system.  I installed Ubuntu just on that HD, no other was connected at the time.  So no Win, and all should be fine.

This is on a new AMD 8450 Triple Core, 4 gigs ram, ATI Radeon 3200 HD graphics, 500 gig WD HD 7200 16mb cache, etc etc..

Right now all I can think of is there may be a bug in the Ubuntu sleep routine somewhere.  

Help anyone?  And or workarounds?

Thanks.....

---

### Post by ericy on 2008-08-20
It happened to me too. I don't have a solution and I'd love to know if there's one. What I had was 8.04 Beta(I don't remember which one). I had it installed on a test hard drive. After 8.04 came out and a clean install, I just don't put my computer to sleep.

AMD 64 x2 4400
AMD 780G(IGP HD3200)
4GB ram
20GB PATA HD

---


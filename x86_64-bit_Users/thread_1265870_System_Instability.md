---
title: "System Instability"
date: 2009-09-13
forum: x86 64-bit Users
---

### Post by thundaraptor on 2009-09-13
Hi Forums,

I have a 64 bit Jaunty build on a custom box I put together.  I have an Asus mother board that has an ATI HD 3100 onboard and I also have an ATI HD4670 dual head card installed.  Originally, I had this setup in clone mode and the system was pretty stable (2 HD monitors).  I ended up creating a new setup where I made a 25 gb partition on the 1tb HDD.  The Jaunty in on the 25gb and then I use the rest of the partition for data.  I also, via another forum, made a lot of changes to the xorg file that I really don't understand.  The monitors work pretty well together and I have a bigdesktop setup but I feel like the system is quite unstable.  It is not uncommon to at least once/day have to hard reset the system from some kind of freeze.  After I hard reset the chck disk function doesn't work and I have to use gpart do to a manual fdisk sort of command.  I know my writing isn't very articulate, I am somewhat of a linux newbie.  What can I do to make the system more stable?  Is this related to the codec audio/video plugins or is is related to the video card?  

Sorry for spelling errors,

Cheers,

TR

---

### Post by earthpigg on 2009-09-14
consider checking system logs. 'segfault' errors from multiple different programs. that would indicate bad RAM.

consider installing and configuring lm-sensors to monitor your CPU for overheating. that could indicate an improperly seated heatsink and CPU fan.

---


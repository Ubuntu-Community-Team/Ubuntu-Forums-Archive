---
title: "Help please!"
date: 2006-04-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by veroaero on 2006-04-18
Hi,

I succusfully installed Ubuntu and Mac OSX 10.3 yestarday on two partitions. Today I installed 10.4 on the Mac part. Then, when I start my computer, I can't no longer choose to start Ubunto or Mac osx, it starts osx immediately. 

How do I get that nice "start up screen" back, with the "choose your os to start" alternative?

Or how do I start Ubuntu in some other way? 

Stupid questions but I'm kind of new with these things...

Thank in advance.

---

### Post by Anthron on 2006-04-18
I don't know how to explain this very well, probably because I don't understand it exetremely well, but when you installed 10.4 it must have overwritten your boot records.

This should be able to help you:
[https://wiki.ubuntu.com/YabootConfigurationForMacintoshPowerPCsDualBoot?highlight=%28yaboot%29](https://wiki.ubuntu.com/YabootConfigurationForMacintoshPowerPCsDualBoot?highlight=%28yaboot%29)

Ubuntu uses yaboot to bootstrap (I hope I'm using this word correctly) your OS of choice. When you installed 10.4, my guess would be Apple overrulled yaboot and now your BIOS is using whatever bootstrapping Apple uses. You need to set your computer back to using yaboot.

Hopefully someone a bit smarter than me can come in and help you some more :).

---

### Post by xenmax on 2006-04-18
Sounds like GRUB was over-written by Mac OS.  Search these forums for "restore GRUB" - there are lots of them around here - however most of them deal with windows and ubuntu dual boot. Dual boot with Mac and Ubuntu might involve other exceptions which might not be covered in such threads.
If you happen to find any threads dealing with Mac and Ubuntu dual boot and somebody had success using it, you can go ahead and try that.

Good luck getting back your Ubuntu installation!

EDIT: Looks like you are better off following Anthron's advice.

---

### Post by veroaero on 2006-04-18
Thank you Anthron,  your quick reply saved my day!

---


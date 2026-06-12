---
title: "NetGear WG111 on PowerPC"
date: 2006-05-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by ihatecrayons on 2006-05-17
First of all, this is my first post here, so let me say hello.

Anyways, so I installed Ubuntu 5.10 on my clamshell iBook, and it works fine and everything, except for the fact that I cannot get the internet on it. I don't have an Airport or an ethernet cable, but I do have a NetGear WG111 USB adapter. I have the NetGear working on Ubuntu 5.10 on my PC with ndiswrapper, but I have just now realized that ndiswrapper doesn't work with PowerPCs. I would like to know if there is any way that I can get the iBook onto the internet with it, or if I need to use something else or what.

My friend did some research, and she found two possible drivers:  
[http://bcm43xx.berlios.de/](http://bcm43xx.berlios.de/) 
[ftp://152.104.238.194/cn/wlan/rtl8187l/linux26x-8187(110).zip](ftp://152.104.238.194/cn/wlan/rtl8187l/linux26x-8187(110).zip) 
but I am not sure what to do with this stuff. Can someone please help me out, or point me in the right direction? Thanks so much!

---

### Post by ssam on 2006-05-17
dapper (the next verision of ubuntu due in 2 weeks) has the broadcom drivers, though they dont work well for everybody.

---

### Post by davygravy on 2006-05-17
The most important question I think you have to find an answer to is "what chipset does your WG111 have?".   Drivers for hardware (eg. wireless adapters) are always based on the chipsets and circuitry.   A little Googling makes it look like it could be a Prism54, Broadcom or a Realtek chipset inside it, but that is not for sure.  Netgear and other manufacturers change chipsets every now and then (they usually go for the cheapest, most capable ones they can get their hands on).

You will need the maker of the chipset (eg. Broadcom) and its number (eg. bcm43xx)

If you look at your USB adapter, it may have a label w/ a version number on it.  That version number is specific to the kind of chipset and firmware inside it.  I'd suggest Googling around with "WG111 chipset vX" or "WG111 chipset version X"  where X is the version number of your USB unit.  

You can also look in the menu System>Administration>Device Manager and look for an entry in the list that corresponds to your USB wireless adapter.  It should give a lot of information about the USB unit (select it and look in the different tabs, make a note of the info).  That may give you some clues about  the chipset as well.

Once you know what chipset your unit has, you can begin to search for a wireless driver that is available for Ubuntu. You may have to compile and install it.  I got the Atmel driver working on my daughter's iBook (clamshell 300MHz mode) under YellowDogLinux a few years back.  That wasn't too bad.
And it worked pretty well.

Chances are that someone in this forum w/ an iBook or PowerBook may have gone though the same process you are starting now. 

You can try searching in this forum, the broader Ubuntu forums and the net in general for Ubuntu or Debian solutions to your questions.

If you post back here w/ more details, maybe someone who has done this can actually walk you through it.

---

### Post by ihatecrayons on 2006-05-20
Okay, I think mine is a netgear WG111v2, so it has a prism54 chipset. It's number is GW3887.

But I read somewhere that some of the WG111v2's have a Realtek chipset. I am not sure which one I have, the device itself doesn't say and I don't know how I could tell. The Realtek's number would be RTL8187.

I found this thing for the Realtek one that might help: [http://paste.ubuntu-nl.org/14083](http://paste.ubuntu-nl.org/14083)
But once again I'm not sure.

Thanks for helping me out!

---

### Post by eternalsword on 2006-07-15
you do not want to use native ubuntu drivers (at least on dapper) for netgear wg111, it could even cause kernel panics.  check out my thread at [http://www.ubuntuforums.org/showthread.php?t=212365](http://www.ubuntuforums.org/showthread.php?t=212365) for how to set up the wg111 using ndiswrapper.

---

### Post by ihatecrayons on 2006-07-16
eternalsworld:

Thanks for taking the time to try to help, but I was trying to use the WG111 on an iBook with PowerPC archetecture, so unfortunately, that guide doesn't help me much. ;) 

But I will be sure to check your guide for installs on my i386. :)

Thanks anyway.

---

### Post by eternalsword on 2006-07-16
oops, somehow missed the part about ndiswrapper not working on powerpc.  well, hoepfully the builtin drivers from dapper work better on that architecture.

---


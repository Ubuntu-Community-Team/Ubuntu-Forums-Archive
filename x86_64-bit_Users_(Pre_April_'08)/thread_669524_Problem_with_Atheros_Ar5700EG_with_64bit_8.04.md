---
title: "Problem with Atheros Ar5700EG with 64bit 8.04"
date: 2008-01-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by phidia on 2008-01-16
I realize this is a test release and could/should? post in the development forum but since i'm trying to use 64 bit I wanted to ask here.

I have heron successfully installed to an external usb drive and it boots fine-this is a new HP laptopdv6707us AK57 cpu 64x2 2gb ram and the problem is with this model HP went with the Atheros AR5007EG wireless card 

(Don't these people have anything better to do then play musical chairs with internal components? I had tried a previous laptop which was very similar except it had a broadcom card which could be made to work.)

So anyway I've read several how to's [this]("http://ubuntuforums.org/showthread.php?t=512828&highlight=atheros+ar5007") looked good but with heron I can't install build-essential the terminal output was "no such package" and yes I spelled build-essential correctly. Maybe that's a bug? I also tried the make command for the madwifi package and it did end with errors but it didn't give the no complier message so maybe gcc is in heron by default?

I guess I should drop back and install gutsy but if anyone has a clue on this or can point me in the right direction I appreciate it. Also if  a mod thinks this would be better placed in the development section feel free.

Note: I screwed up when entering the wifi card # in the title-it's an AR5007EG, as it is listed in the description. I was able to get the build-essential and ia32-libs  package groups to install, but can't get that card to work yet.

---

### Post by phanosp on 2008-04-25
Same here guys. Are we doing something wrong?

---

### Post by nray on 2008-04-27
> **phanosp said:**
> Same here guys. Are we doing something wrong?

I don't think so.

Had my AR5007EG working great in 32-bit Ubuntu 7.10 with ndiswrapper.

I've spent about 20 hours working with Ubuntu 7.10 and 8.04 and have been UNABLE to get the same hardware/software to work (and madwifi is not an option at all in 64-bit because the experimental patch for the AR5007EG is 32-bit only).

The 5.3.0.56 x64 drivers will seem to work with ndiswrapper - can see networks, but can't connect to any of them.  Stay away from the 7.4.2.75 drivers with ndiswrapper though, you will hang on boot with a "udevd-event[3179]: run_program: 'sbin/modprobe' abnormal exit".

I think there are some serious bugs in ndiswrapper in 64-bit.

---

### Post by nray on 2008-04-29
Found a solution -

In at least 64-bit Ubuntu 8.04, with the ndiswrapper package (version 1.50 at the time of this writing), using the XP x64 5.3.0.56 driver, it is absolutely necessary to put this line into /etc/network/interfaces under iface wlan0 with your AR5007EG's hardware ethernet address where 00:00:00:00:00:00 is:

pre-up /sbin/ifconfig wlan0 hw ether 00:00:00:00:00:00

With that line in place, things worked they way they should in 64-bit.  I didn't need that line in 32-bit Ubuntu 7.10 with ndiswrapper, but I needed it in 64-bit.

---


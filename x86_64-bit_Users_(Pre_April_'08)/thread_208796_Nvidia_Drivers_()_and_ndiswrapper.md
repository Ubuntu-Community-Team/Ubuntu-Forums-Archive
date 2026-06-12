---
title: "Nvidia Drivers (?) and ndiswrapper"
date: 2006-07-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by steve222 on 2006-07-04
My first problem today with what I think is my nvidia drivers though I'm not sure.  I can get to the splash/logon screen fine but after I login, around the middle of the screen, there seems to be a "scrambled" window or icon.  This happens in both x86 and x64 versions of ubuntu and Fedora Core 5.  I can access the command line find and have been using that.  I do have 2 video cards SLI'd (2x 7800GT) which may be part of the problem.

My next problem is with ndiswrapper.  I have a realtek 8180 chipset which I have gotten to work on 32 bit systems before withe ndiswrapper but now that I have a 64 bit CPU, errors occur when modprobing.  I did use 64 bit Windows drivers and they did install fine until they are loaded.  After the errors, the system hangs and I have to restart.

So my problem is how do I get my wireless card working so that I can get the nvidia drivers needed to get my computer working.

---

### Post by cemptor on 2006-07-05
I have a similar issue and have had for months. Can get my card to work with 32 bit Ubuntu but no luck with 64 bit.

I have a Trendnet TEW 424UB wireless G USB adapter based on the sis163u chipset. I downloaded a driver from the sis website, and it contains a AMD64 folder. The readme says it supports Vista and XP 64.

Installed the latest ndiswrapper from source (1.19) and installed the driver. It installed fine. shows the hardware as detected and present. When I try to load ndiswrapper using modprobe, the system hangs. My keyboard and mouse stop responding and I have to power down. The odd thing is that the active light on the USB adapter comes on, which it does not before.

Under 32 bit Ubuntu, I use the NT version of the driver and it works like a charm

Any suggestions? I am really eager to move to the 64 bit OS, one of the reasons for buying a new computer. I seem to be wasting the hardware, an Opteron 144 processor.

Thanks

---

### Post by rpesq on 2006-07-06
I read (forget where, maybe the ndiswrapper website or install notes...) that there are no known USB adapters working under 64-bit ndiswrapper.

I know for a fact that my Ralink RT2570 does not work with ndiswrapper 64bit, (modprobe seems fine, but absolutely nothing happens...) which is exclusively why I am running Dapper 32.

I would certainly like to be running x64, too.

---

### Post by hajk on 2006-07-07
> **rpesq said:**
> I read (forget where, maybe the ndiswrapper website or install notes...) that there are no known USB adapters working under 64-bit ndiswrapper.

I know for a fact that my Ralink RT2570 does not work with ndiswrapper 64bit, (modprobe seems fine, but absolutely nothing happens...) which is exclusively why I am running Dapper 32.

I would certainly like to be running x64, too.

That may well be true...:(  I haven't been able to get my RealTek 8187 based USB dongle to work either, whether using the r8187 kernel module or ndiswrapper plus the 64-bit Windows driver downloaded from the RealTek site.

---

### Post by walkerx on 2006-07-09
i have the dwl-g122 which uses the Ralink RT2500 drivers

I installed ndiswrapper and the 64bit drivers I have for windows, but Ubuntu doesn't like them and wouldn't work

I uninstalled ndiswrapper, rebooted and setup manually and it's working fine now

remember need to set as rausb0 and not wlan0

---

### Post by semetay on 2007-01-30
> **walkerx said:**
> i have the dwl-g122 which uses the Ralink RT2500 drivers

I installed ndiswrapper and the 64bit drivers I have for windows, but Ubuntu doesn't like them and wouldn't work

I uninstalled ndiswrapper, rebooted and setup manually and it's working fine now

remember need to set as rausb0 and not wlan0

hello,

what do you mean by setting up manually? I have a rtl8187 on the mainboard (asus m2n32 sli deluxe) and couldnt make it work either ubuntu dapper, edgy or fedora 6 (all are 64 bit);

Dapper 64 bit
no driver installation was succesful

Edgy 64 bit
Drivers come with the distro but no network could be found. windows xp could see and connect on the same computer

Fedora 64bit
I installed ndiswrapper and then xp 64 bit driver for 8187 and came to the point as I was in edgy. no network could be found.

I also have a PCI hardware modem could not install that either. it works under winXP

any comments, suggestions?

Thank you,

semetay

---


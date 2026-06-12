---
title: "Dispatches from an unintentional 64-bit hardware upgrade..."
date: 2006-07-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by Apostata on 2006-07-22
Right - hello all.

In a previous incarnation (ie last week) my computer was running an AMD Athlon 1000 w/ a separate nvidia card, etc., and thus running the linux-k7 kernel. All was well (if slow).

Due to the m'board shorting out, I was forced to upgrade. I'm now running on a Biostar 6100-939, an Athlon-64 +3500 processor, with onboard everything (nForce 410/GeForce6100, Realtek audio, etc.). Good for me.

Now...what hasn't changed is the OS on my hard drive: Kubuntu (Dapper) w/kernel-k7.

Questions:

- everything seems to work great, but I can't get the system to recognize the nvidia chip (and thus, no 'glxgears' for me). Do I need to upgrade to Dapper-64 in order to have this recognized?

- do I need to install the nForce driver from nVidia?

- I realise that the 64-bit version of Dapper contains the proper kernel I will need, but is it *necessary* for me to upgrade to this (considering that some apps have issues with this)?

- I'm absolutely stupid/new to 64-bit computing, so any advice/details you can provide would be extremely helpful.

Thanks very much. Hail Ubuntu.

**P.S.** - what is the difference between the 'alternate' and 'desktop' 64-bit downloads?

---

### Post by Kilz on 2006-07-22
> **Apostata said:**
> Right - hello all.

In a previous incarnation (ie last week) my computer was running an AMD Athlon 1000 w/ a separate nvidia card, etc., and thus running the linux-k7 kernel. All was well (if slow).

Due to the m'board shorting out, I was forced to upgrade. I'm now running on a Biostar 6100-939, an Athlon-64 +3500 processor, with onboard everything (nForce 410/GeForce6100, Realtek audio, etc.). Good for me.

Now...what hasn't changed is the OS on my hard drive: Kubuntu (Dapper) w/kernel-k7.

Questions:

- everything seems to work great, but I can't get the system to recognize the nvidia chip (and thus, no 'glxgears' for me). Do I need to upgrade to Dapper-64 in order to have this recognized?
No just install the 32bit driver.

> - do I need to install the nForce driver from nVidia?If you want accelerated graphics.

> - I realise that the 64-bit version of Dapper contains the proper kernel I will need, but is it *necessary* for me to upgrade to this (considering that some apps have issues with this)?There are few if any apps that cant be run on the 64bit platform. No you dont have to upgrade, just keep running a 32bit os on a 64bit processor. Kind of like running 87octane in a race car.

> - I'm absolutely stupid/new to 64-bit computing, so any advice/details you can provide would be extremely helpful. Its pretty much the same , exept there are a few applications that run better as 32bit so you have to follow a howto to set them up as 32bit on the 64bit os. But there are 64bit versions of them.

> Thanks very much. Hail Ubuntu.

**P.S.** - what is the difference between the 'alternate' and 'desktop' 64-bit downloads?
The alternate is just a pure install without fancy graphics. It works better imho. The desktop version has a livecd os you can take for a spin before installing. If you know you want ubuntu installed for sure, get the alternate.

---

### Post by BIGtrouble77 on 2006-07-23
Have you tried to install the nvidia-glx driver from the repos?  You can always download automatix and have that install the drivers for you ([www.getautomatix.com)](www.getautomatix.com)).  As for getting the drivers from nvidia site, that's possible too, but when kernel updates are pushed through you xorg might break and you have to re-run the driver install.

I'd actually recommend moving to 64bit entirely.  I've have virtually no issues, it's really come a long way since the breezy days.  Automatix will take care of alot of the really annoying stuff (like 32bit browsers w/flash).

---

### Post by Apostata on 2006-07-27
Kilz - thanks for the info. I will install the nForce4 driver and look into an upgrade to 64-bit Dapper.

BIGt - I got the nivida working (haven't tried installing the separate nForce driver yet). Never heard of automatix...I'll check the link. Thanks for the suggestion.

---

### Post by RAOF on 2006-07-28
> **Apostata said:**
> Kilz - thanks for the info. I will install the nForce4 driver and look into an upgrade to 64-bit Dapper.

BIGt - I got the nivida working (haven't tried installing the separate nForce driver yet). Never heard of automatix...I'll check the link. Thanks for the suggestion.

The **nforce** driver is almost certainly unnecessary.  I belive that Kilz was actually referring to the **nvidia-glx** package, which contains the graphics drivers :).  Which you've already got, it seems.

The nforce driver contains the onboard network driver, the onboard sound driver, and (I believe) little else.  There are drivers for both already installed, as a part of the standard linux kernel.  There's no need for the nforce drivers.

And it's not so much an upgrade to 64bit Dapper, as it is installing a different OS.  You can't use apt's upgrading facilities, so you'll need to reinstall to get Dapper64.  Unless you do things which work much better under x86-64 (audio/video encoding/decoding, cryptography, etc), it's probably not worth your while.  Unless, of course, you just **like** fiddling with computers :)

---

### Post by jktrigg on 2006-07-28
> **RAOF said:**
> The **nforce** driver is almost certainly unnecessary.  I belive that Kilz was actually referring to the **nvidia-glx** package, which contains the graphics drivers :).  Which you've already got, it seems.

The nforce driver contains the onboard network driver, the onboard sound driver, and (I believe) little else.  There are drivers for both already installed, as a part of the standard linux kernel.  There's no need for the nforce drivers.


Unless your motherboard's chipset is too recent for the version of forcedeth (the standard driver for the onboard network) -- then if you're multibooting you'll have problems unless you either manually upgrade the open source driver or switch to the vendor's driver.

---

### Post by Apostata on 2006-08-07
Follow-up: installed Dapper-64 and things are good. After the base install, I used Automatix to grab essential apps (and the Nvidia driver) then apt-get'd whatever else I needed. Works great.

---


---
title: "installing 7.04 ubuntu 64 bit"
date: 2007-05-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by Prototop on 2007-05-23
Hello there,

I'm having trouble getting ubuntu installed.
First i tried the regular and secondly the alternate cd.

First image i downloaded was "ubuntu-7.04-desktop-amd64.iso".
When i try to install it just say: job control turned off

Secondly i downloaded the same but with alternate cd box checked (text installer).
Gets to the install menu. But here it says it can't find my cdrom. It's a msi sata cdrom/burner.

In the first instance it might also be my cdrom being the problem. Is it possible to get a sata driver for linux and then istalling by choosing the "install ubuntu with driver cd" (it either says that or something similar). 
Tried looking for one but no go.

I'm a newbie who would like to try an alternative to windows. pls help

---

### Post by djchandler on 2007-05-23
> **Prototop said:**
> Hello there,

I'm having trouble getting ubuntu installed.
First i tried the regular and secondly the alternate cd.

First image i downloaded was "ubuntu-7.04-desktop-amd64.iso".
When i try to install it just say: job control turned off

Secondly i downloaded the same but with alternate cd box checked (text installer).
Gets to the install menu. But here it says it can't find my cdrom. It's a msi sata cdrom/burner.

In the first instance it might also be my cdrom being the problem. Is it possible to get a sata driver for linux and then istalling by choosing the "install ubuntu with driver cd" (it either says that or something similar). 
Tried looking for one but no go.

I'm a newbie who would like to try an alternative to windows. pls help
It sounds as though you have a somewhat new hardware configuration. Which 64-bit AMD processor are you using? Are all of your internal peripherals SATA? Are you trying to create a dual-boot setup, or trying to install via an emulator? Listing your hardware setup might give us more clues as to what is going on. Obviously the CDs are booting. The "job control turned off" message could mean the system isn't finding your hard drive--there's no writable media available.

If you are using SATA only for your hardrive(s) and cd/dvd burner, try disabling the parallel IDE interfaces on your motherboard in your BIOS settings. My guess is that something in your BIOS is making the installer look for the hard drive on the parallel IDE interfaces when it is on the SATA bus but not being detected. Disable parallel IDE and make sure your boot preferences are set correctly. Make sure your hard drive is being detected on boot. And stick with the regular iso image, not the alternate. It appears you are at least getting to its desktop, or else you wouldn't be getting the option to install.

---


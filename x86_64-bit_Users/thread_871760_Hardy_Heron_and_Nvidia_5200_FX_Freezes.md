---
title: "Hardy Heron and Nvidia 5200 FX Freezes"
date: 2008-07-27
forum: x86 64-bit Users
---

### Post by cov on 2008-07-27
Hi.

I've been having a lot of trouble installing Nvidia drivers for my FX 5200 AGP graphics card.

I'd tried various solutions (downloaded the drivers from the Nvidia site and run the *.run scripts, enabled the Hardware Drivers under the 'System->Administration menu', etc) but the system always locked up.

The I tried the EnvyNG scripts from [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) which seemed to offer most hope. Indeed, when I ran the scripts and the system restarted, I was astonished to find the Nvidia splash screen come up before the gdm login window!

My joy was shortlived, however, because after a while the screen saver came on and the machine locked up.

Thereafter rebooting got as far as the nvidia splash screen before locking up. I have a copy of my old xorg.conf which uses the vanilla graphics driver and which does work and I can boot up in recovery mode, copy the working xorg.conf and start gdm.

My previous install on this machine (an AMD 64 Shuttle) was gentoo which had no problems with the graphics card (an Nvidia 128 Meg 8xAGP).

From googling, I see that this is an issue with Hardy, specifically with the kernel. Selecting the 2.6.24-16 kernel or the 2.6.24-19 kernel from grub make little difference.

I have also added 'blacklist intel_agp' to /etc/modprobe/blacklist as advised by one poster and added 'Option "NvAGP" "2"' to the /ext/X11/xorg.conf without any improvement.

TIA,

Dave Coventry

---

### Post by Odrodzona-Sarmacja on 2008-07-27
I had freezes with my old fx5700 on Via motherboard. Only removing Network Manager and running computer offline was giving me stability. But then I went and bought 9600gt and Asus motherboard and freezes went away totally.

However I was experiencing from time to time some unexpected gdm crashes/restarts, which went only when I installed binary driver from nvidia. Here is the howto:
[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

My advice is, that you can try installing nvidia binary driver directly from their page... and if that won't help. Buy other card & motherboard. ;)

Good luck!

---

### Post by cov on 2008-07-27
Hmm.

I have tried installing the drivers from the Nvidia site (as stated in my OP) but this didn't help.

My machine is a Shuttle barebones system which doesn't seem to have a Motherboard upgrade path. Also the Graphics slot is AGP, so that limits my options somewhat.

I have been seeing a message which says "Failed to initialize HAL" which may be another clue to what's going on.

---

### Post by cov on 2008-07-27
Actually, with regard to the advice to buy another Motherboard and another Graphics card, probably the easiest option (and certainly the cheapest) would be to install a distro which works!

As I say, gentoo was working fine until I installed Ubuntu. And I'm seeing a lot of messages which suggest that 'Gutsy' worked fine with the 5200 FX, so another option would be to downgrade.

---

### Post by cov on 2008-07-29
Interesting thing;

If I boot in recovery mode and drop down to root and start 'gdm', then it runs fine (although HAL fails to initialise). Also '/etc/init.d/networking' needs to be restarted.

But if I boot in recovery mode and select 'resume', the machine freezes at the login page.

Does this behavior suggest any clues?

---

### Post by cov on 2008-08-03
HAL obviously tracks the hot plugging of the USB.

Using pendrives is not too much of a problem because I can always mount them manually.

However, my USB printer won't show up.

Any way I can manually add my printer?

Or do I have to go back to using the vanilla video drivers?

---

### Post by cov on 2008-08-03
"/etc/init.d/cupsys restart" did the trick...

---


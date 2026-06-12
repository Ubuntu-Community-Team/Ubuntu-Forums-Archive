---
title: "Can't install 6.10 64bit"
date: 2007-03-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by Werd on 2007-03-11
I've been messing around with this all day and nothing works. Everything starts out fine then I just get a blank screen with a green line running across.

AMD Turion 64 x2
2GB PC2-4200 DDR2
120 HD
NVIDIA GeForce Go 6150

---

### Post by x64Jimbo on 2007-03-11
You may need to use the alternate install CD because it sounds like it is having trouble with your video card when running in LiveCD mode.

---

### Post by Werd on 2007-03-12
I've just tired the alternate install and it still doesn't seem to work. The ubuntu loading screen pops up and gives you some options to pick from then after picking which option you need nothing else happens.

---

### Post by RonnyD on 2007-03-13
I am having exactly the same problem as Werd, my system as follows:-

HP Pavilion DV6095EA
&#9679; Genuine Windows XP Home Edition
&#9679; AMD Turion&#8482; 64 X2 Mobile Technology TL-56
&#9679; 2048 MB DDR2 667 MHz (2 x 1024 MB)
&#9679; 100 GB EIDE hard drive, SATA 5400 rpm
&#9679; 15.4&#8221; WXGA High Definition BrightView Widescreen
&#9679; NVIDIA® GeForce&#8482; Go 7200
&#9679; with 128MB of TurboCache&#8482; video Memory
&#9679; IEEE 1394 Interface
&#9679; Super Multi DVD Writer (+/-R +/-RW) with Double
Layer support
&#9679; 802.11a/b/g WLAN
&#9679; 5-in-1 integrated Digital Media Reader for Secure
Digital cards, MultiMedia cards, Memory Stick,
Memory Stick Pro, or xD Picture cards


If you ever find a cure please post it here, as I can go no further and I really want to install Ubuntu. I have SUSE 10.2 installed OK but I'd prefer to use Ubuntu.

---

### Post by firecat53 on 2007-03-14
At the end of the "kernel" line in /boot/grub/menu.lst  (example)
    ```
kernel          /boot/vmlinuz-2.6.15-28-server root=/dev/hde1 ro quiet splash
```
try adding noapic noacpi nosmp.  Either all three or just one (try noapic first).  This should cure most boot issues.

You can either edit it directly from the grub menu on bootup (just follow the directions at the bottom -- this will only change it for the current boot) or edit menu.lst directly later on to make it permenant.

Good luck!

Scott

---


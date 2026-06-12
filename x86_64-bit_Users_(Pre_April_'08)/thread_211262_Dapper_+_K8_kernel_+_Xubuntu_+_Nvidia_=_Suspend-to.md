---
title: "Dapper + K8 kernel + Xubuntu + Nvidia = Suspend-to-RAM hell"
date: 2006-07-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by Dogmeat on 2006-07-08
Hello. I've just been through a 6 hour stretch trying to fix suspend on this system without success. I remember in the  Dapper Alpha 1 it worked fine, but after a certain upgrade I simply can't get suspend to work.

This is the system I'm trying to get this to work:
A8V Deluxe, Athlon 64 3200+, Nvidia 4200TI

Here's what I tried, in several combinations (I think I missed just right one ](*,) ):

- Nvidia closed module with various AGP settings, nv and vesa
- These Bios options: s3_bios, s3_mode, pci=noacpi (in various combinations too)
- Uninstalling with --purge acpi, acpid and reinstalling
- Bios option to repost on s3 resume
- Tried lots of different settings on the /etc/default/acpi-support file
- Tried from the console (stopped gdm, unloaded nvidia module, etc) most of the time
- Installed previous kernel (2.6.15-23) after reading someone had trouble with the latest
- Reconfigured xorg to get a fresh xorg.conf

So, with these, I got those results (in no particular order):

- A kernel panic (with 2.6.15-25)
- Blank screen, keyboard leds frozen
- Blank screen, Caps and Scroll lock blinking
- Psychadelic colors
- A nice yellow    "Linux!" message on top of the screen, system frozen
- Sometimes the bios would sort of "hang" when trying to detect my hard drive. Had to do some hard reboots.

I couldn't care less about 3d acceleration for now, since getting it in a text console is already proving a monumental task. 

I really need this system to suspend to ram, so I was wondering, has any of you made it yet? If so please post the configuration files you changed to get it to work.

---


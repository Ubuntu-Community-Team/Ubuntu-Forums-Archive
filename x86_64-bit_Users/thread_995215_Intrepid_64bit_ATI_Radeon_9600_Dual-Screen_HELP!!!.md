---
title: "Intrepid 64bit ATI Radeon 9600 Dual-Screen HELP!!!"
date: 2008-11-27
forum: x86 64-bit Users
---

### Post by Permafrost91 on 2008-11-27
Running 8.10 64bit with Radeon 9600 graphics card. Trying to get a dual screen setup working (two Samsung 15" LCDs, same model but different versions). FGLRX enabled.

I can get the same output on both screens but I can't get the two screens to be dual-head, side-to-side. The Screen Resolution tool identifies the monitor as a 15" Samsung correctly only if one screen is attached or I use the open-source radeon driver (because then only one of the screens is enabled). If both monitors are attached with fglrx, it displays "unknown."

I've tried a few things already and most forums ask similar questions but are a few years old so I want to know how I can get dual-head working with a Radeon 9600 on 64bit Intrepid.

All help is appreciated!

---

### Post by Permafrost91 on 2008-11-29
I tried upgrading the ATI drivers using the latest 8.5 driver from the ATI website following the instructions provided in the Ubuntu wiki (the instructions were for Hardy, no Intrepid instructions found). The driver compiled/installed without complications but X.org wouldn't start after a reboot so I reverted to fglrx provided in the repo.

I also tried playing with aticonfig a little bit but everytime I change the default xorg.conf created after activating the fglrx driver using the Hardware Drivers tool, X.org won't start.

This is really frustrating. Both screens show the desktop with the fglrx driver but not with the open-source radeon driver. This is frustrating because (1) the radeon driver supposedly has good support for 3-D acceleration as well as multi-head for the RV350 chip and (2) I'd prefer using the open-source and not the ATI supplied driver for moral reasons.

I'm at a loss. Any and all help would be greatly appreciated!

---


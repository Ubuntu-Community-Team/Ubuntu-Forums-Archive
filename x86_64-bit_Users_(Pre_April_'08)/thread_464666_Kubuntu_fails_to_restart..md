---
title: "Kubuntu fails to restart."
date: 2007-06-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by zbittner on 2007-06-04
I have Kubuntu 7.04 installed, and whenever I try booting with the nvidia-glx drivers installed, I get stuck at a blank screen with a blinking cursor, kind of like when in recovery mode, except I don't have access to a shell, so I can't do anything. I end up needing to reboot in recovery mode and recreating the xorg file, After this is done, I can restart it and reinstall the nvidia-glx drivers, than reload the x server, and it works fine. Because I have no problem restarting the x server leads me to believe that it isn't causing the problem.

I could be totally wrong, but I think the problem is caused when the kernel is loading and it hits where the Nvidia drivers tie in.

I have a virtual machine with linux on it, but I've only had a working native install for about a day, so I really don't know what I'm doing.

I'm using the 2.6.20-15 kernel because 2.6.20-16 causes problems.
Hardware:
Mac Pro
2 x 2.66 Ghz Xeon 5150's
3 GB RAM
NVidia GeForce 7300GT

Any help anybody can give is much appreciated. Thanks for your time.

---

### Post by Princey on 2007-06-05
I could be wrong, but it seems that the nVidia proprietary drivers could have has some minor issues while installing. Completely remove them using adept and reboot to see if the problem still exists. If it doesn't, then it's the nVidia drivers. Re-install them using adept or you can follow the how-to in the wiki.

---


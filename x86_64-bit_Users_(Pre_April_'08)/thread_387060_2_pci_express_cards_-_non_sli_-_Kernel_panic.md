---
title: "2 pci express cards - non sli - Kernel panic?"
date: 2007-03-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by wolf08 on 2007-03-17
My main goal is to try and run three monitors, instead of my current dual head setup. I am having some troubles with a second graphics card, and I'm wondering if anyone has any ideas. My system is as follows:

Amd X2 3800 (939)
Asus A8N-something... I'll check
1: XFX GeForce 7600GT (sli capable)
2: Nortwood Micro GeForce 6600 (non-sli capable)

---
4 GB ram
3 identical monitors
Boot drive is pata, dual boot windows + linux


My problem is this... I keep getting a kernel panic with 64bit distros. My windows partition works fine, and sees the new graphics card. My linux (it's actually gentoo x64, but I've tried ubuntu too- more on that later) partition refuses to boot, giving me a kernel panic.

The weird thing is that every 32bit OS I've tried works fine. I can boot up the livecd of 6.06, gentoo 32bit, windows 32bit, etc.... However, every single x64 distro fails to boot. Gentoo livecd, gentoo on the hd, Ubuntu x64, Sabayon, Fedora x64.. 

Even windows x64 refuses to boot (Although, I have reason to believe that it is a bad cd. I have no other available x64 machine to test it on.).

Does anyone have any clue? Thanks in advance.

---


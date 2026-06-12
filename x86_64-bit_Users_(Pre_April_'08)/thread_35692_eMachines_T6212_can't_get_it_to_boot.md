---
title: "eMachines T6212 can't get it to boot"
date: 2005-05-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by matthew on 2005-05-19
Here's the scoop: I bought this computer for my wife and kids. They want me to keep WinXP on it, but it has a 160G hd so I partitioned it to install Ubuntu like i have on my laptop (dual boot with XP) as well as my old pIII laptop (just Ubuntu). I've tried both the 32 and the 64 bit versions and have the same problem. Install seems to go well, I can boot in recovery mode and all seems fine whether I use the 32 or 64 bit versions. I cannot get the xserver program to start, or if it does everything will freeze before gnome really gets up--it will freeze when the splash screen is being displayed just after the login has occurred.

hardware:
eMachines T6212
AMD Athlon 64 3200+
1024 MB DDR SDRAM (the only upgrade from original configuration)
ATI Radeon Xpress 200

Trying to install either 32-bit or 64-bit hoary.

I currently have the 64 bit installed and can boot in recovery mode to any of the following kernels:
2.6.10-5-amd64-k8-smp Default
2.6.10-5-amd64-k8 Previous
2.6.10-5-amd64-k8-smp
2.6.10-5-amd64-k8
2.6.10-5-amd64-generic

I have so many installed as some earlier threads I had read (but not participated in), either here or on other forums had said perhaps the newer kernel images might have a better driver for the video card.

Oh, last thing...I'm new to Linux and Ubuntu, but not new to computers. I haven't used a command line much in over 15 years, but I used to use Unix in college and dos in earlier years... That said, I'm not afraid of getting my hands dirty, but I will likely need some baby-step instructions.

Thanks in advance.

---

### Post by matthew on 2005-06-13
I just realized that I never posted a followup to this problem. Turns out there was a hardware problem. I ended up returning the computer to Best Buy as it was still under warranty and buying an HP a1020n in its place. I was able to get everything set up on it within a couple of days (had a fight with the Intel HD Audio, but it works beautifully now). The wife and kids are happy, I'm happy, life is good.

---


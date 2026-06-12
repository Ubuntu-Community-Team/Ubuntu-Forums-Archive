---
title: "Turion 64 laptop won't boot above 50C"
date: 2005-12-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by xuni on 2005-12-11
My Compaq Presario M2000Z with a Turion 64 and Radeon 200M will not boot when the temperature gets above 50 degrees celcius. I'm running Kubuntu 5.10 dual-boot with Windows XP. Kubuntu will run at that temperature, but it won't boot.

When I first installed it, I had to include "noapic nolapic" in grub before it would boot, and I had to change the video card to "vesa" before X would start. 

I came across [this problem]("http://www.ubuntuforums.org/showthread.php?t=91622") in the forums, and that is true of my latop as well, except that Kubuntu can't find the fan on mine, so it never goes on. Therefore, I tried to change the trip_points to lower (because I didn't want the first at 93C), but they reset themselves.

I installed Hmonitor in Windows XP to check the temperature, and I've tested it several times now. Does anyone have any ideas--other than turning ACPI off? :confused:

---


---
title: "Freezes when viewing pictures"
date: 2009-08-21
forum: x86 64-bit Users
---

### Post by tHatArmed on 2009-08-21
Hey,  I've been running Ubuntu 9.04 for about a month now, and I've had a couple problems. The first was an issue with pidgin, which I resolved by deleting the .purple file and importing the accounts again (I had to do a bit of searching, but I found the aforementioned solution through these forums). My current problem revolves around freezes when I attempt to click through my various pictures.

The problem is repeatable, and I only experience the freeze when clicking through my pictures. At first I thought it was an issue with .png files, but it does it at random while I browse through my pics (.png, .jpg, .gif). Sometimes it doesn't freeze, and my display gets FUBAR. At times, I can correct it by resetting the NVIDIA display settings, at other times I have to hit the reset button. I assume this is from the video chipset on my motherboard, and have seen similar problems (but not identical, my system doesn't 'randomly' freeze) but none exactly like this.

I wouldn't call it a hard freeze, because I can still move my mouse and if I have music playing, that continues to play. I only venture to call it a freeze because 90% of the time I can move the mouse, but I cannot click anything. The only item of note that I can find in the logs is the following:

```
[   80.000363] Clocksource tsc unstable (delta = -128232293 ns)
[  121.440544] CE: hpet increasing min_delta_ns to 15000 nsec
[  121.440590] CE: hpet increasing min_delta_ns to 22500 nsec
1.5.0#5ubuntu3: restart.
Inspecting /boot/System.map-2.6.28-15-generic
Cannot find map file.
```

I noted that the advice with some of the clocksource issues was to flash the motherboard's BIOS. Does that apply to my situation or does it rest entirely with the video settings?

System specs below:
Asus M3N78-EM motherboard
NVIDIA GeFORCE 8300 chipset
AMD Athelon X2 64
2Gb RAM
2 80Gb SATA hdds

---


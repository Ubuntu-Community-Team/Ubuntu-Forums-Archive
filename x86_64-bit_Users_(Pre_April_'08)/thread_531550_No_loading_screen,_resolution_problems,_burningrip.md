---
title: "No loading screen, resolution problems, burning/ripping won't work"
date: 2007-08-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by TaylorHelferty on 2007-08-21
I recently installed the correct 64-bit video drivers in my 64-bit Ubuntu 7.04 for my new Geforce 8600 GT graphics card. Everything worked fine, and it installed fine, except for this:

1) When I start the computer, the screen goes blank and loses it's signal for the loading screen, and doesn't come back on till the welcome screen. 

2) Every time I restart the computer, the resolution resets to 1024x. . . . something in that category. I have a 22" widescreen and set the resolution to 1680x1050, which works fine. But once I restart, it resets back to 1024. 

3) Whenever I rip or burn a cd or dvd, it just starts, then says "complete" but doesn't actually do anything. Even when I use a third-party program like Acidrip or Devede. It will just hang or say "complete" without doing anything.

Any suggestions would be VERY much appreciated. Just to clarify, I mentioned that I recently installed the video driver, because all this started happening once I installed that card. I know it's a new card, so do I just have to wait for the next version of Ubuntu with restricted drivers for this series? Or are there ways to fix it now? Preferably the latter.

---

### Post by crjackson on 2007-08-21
> **TaylorHelferty said:**
> I recently installed the correct 64-bit video drivers in my 64-bit Ubuntu 7.04 for my new Geforce 8600 GT graphics card. Everything worked fine, and it installed fine, except for this:

1) When I start the computer, the screen goes blank and loses it's signal for the loading screen, and doesn't come back on till the welcome screen. 

2) Every time I restart the computer, the resolution resets to 1024x. . . . something in that category. I have a 22" widescreen and set the resolution to 1680x1050, which works fine. But once I restart, it resets back to 1024. 

3) Whenever I rip or burn a cd or dvd, it just starts, then says "complete" but doesn't actually do anything. Even when I use a third-party program like Acidrip or Devede. It will just hang or say "complete" without doing anything.

Any suggestions would be VERY much appreciated. Just to clarify, I mentioned that I recently installed the video driver, because all this started happening once I installed that card. I know it's a new card, so do I just have to wait for the next version of Ubuntu with restricted drivers for this series? Or are there ways to fix it now? Preferably the latter.

Did you have ubuntu installed using a different card and then upgrade to THIS card using the same install?

If so, what did you do to reconfigure for the new hardware?

---

### Post by kuja on 2007-08-22
Your changes to the resolution probably aren't being saved, probably due to permissions issues. Try running the program that lets you switch the resolution with root privileges and before exiting be sure to save changes if appliable/possible. That should at least alleviate that problem.

With regards to the monitor losing signal,  maybe your graphics adaptor and usplash aren't getting along? Try disabling usplash next time you boot (you can do it from grub settings, press 'e' to edit, press 'e' again on the kernel line, remove the word splash, press enter to go back, and then 'b' to boot

---


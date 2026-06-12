---
title: "Nvidia 7900GT Problems"
date: 2007-10-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by gkwong on 2007-10-23
I have a computer with an AMD X2 and Nvidia 7900GT videocard but it won't work with ubuntu. I can only load into ubuntu using onboard video, which is how I installed ubuntu. I downloaded the restricted driver for the videocard, but when I try to boot with it, it shows the ubuntu splash screen, then goes to a black screen and the videocard fan turns off and there is no signal to the monitor. What do I do?

---

### Post by MighMoS on 2007-10-24
It could be a BIOS issue.  Try checking in your BIOS for something like "Primary display adapter" and toggling it.  If that doesn't work, boot up using the onboard video.  Log in, and go to System --> Administration --> Screens and Graphics.  Try disabling Screen1 and making Screen2 the default.

---


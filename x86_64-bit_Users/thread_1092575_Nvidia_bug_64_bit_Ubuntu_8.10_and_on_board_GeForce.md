---
title: "Nvidia bug 64 bit Ubuntu 8.10 and on board GeForce 6100 chip"
date: 2009-03-10
forum: x86 64-bit Users
---

### Post by TWFJR on 2009-03-10
Ok, I've searched the internet. I've been to NVidia. I've been to Launchpad. And I've searched this forum.  I don't see a solution to the buggy Ubuntu drivers nor the proprietary drivers Nvidia is putting out.  My tech put version 96 on the machine using GeForce 6100 chip. But it eventually has a problem with reboots blanking out the monitor.  I really hope for the sake of Ubuntu's success that 9.04 has resolved this buggy issue.  There was no resolve with 8.04 nor 8.10.  

In the meantime, does anyone have a solution?

With every new version of Ubuntu I look forward to fixes and new features.  But this Nvidia problem is a back breaker.  I can't begin to tell you how many Ubuntu users are as frustrated as I am.  Whether it is Nvidia or Ubuntu that is responsible for working drivers matters only when those that are not getting resolve flat out move on to workable solutions.

---

### Post by norwoods on 2009-03-10
i update to the latest nvidia proprietary releases for 64 bit Ubuntu 8.10, 180.37 currently, from [www.avenard.org](www.avenard.org) (third party software source "deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) release/")using synaptic package manager.  i am not sure which programs are needed so i install all six provided:
nvidia-180-libvdpau
nvidia-180-libvdpau-dev
nvidia-180-modaliases
nvidia-180-kernel-source
nvidia-glx-180
nvidia-glx-180-dev
for a fresh install, you might also want or need:
jockey-common
jockey-gtk or jockey-kde
nvidia-settings
nvidia-xconfig

---

### Post by TWFJR on 2009-03-13
I had hi hopes for your solution.  But [www.avenard.org](www.avenard.org) has not proven successful with the embedded GeForce 6100 chip set.  I even looked into SunMicrosystems OpenSolaris and the same problem exists.  I am about to try one more time then I'm changing out the motherboard with embedded Ati Radeon Xpress 200 series chip set.  And if that does not work, then I'm looking for another mother board to build a larger format computer.  I'll have to concede that the other two boards are only good for Windows. Anyway, thanks norwoods.

---


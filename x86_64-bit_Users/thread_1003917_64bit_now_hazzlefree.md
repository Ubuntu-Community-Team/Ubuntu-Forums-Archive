---
title: "64bit now hazzlefree?"
date: 2008-12-06
forum: x86 64-bit Users
---

### Post by knottulf on 2008-12-06
I tried the 64bit version 1-2 years ago on my hp500dv laptop. However, the problems with getting flash, java and some other things to work, sent me back to 32 bits.

I also have had lots of trouble with ATI Radeon xpress 200M graphics card (which I now have a proprietary driver for) and the Broadcom wifi card (which I still havent made work. 

I dont want to use my computer for testing, but for working on other stuff. With this in mind, would it be recommended to install 8.10 in 64 og 32bits these days? And what about kde4 og kde3?

---

### Post by Yellow Pasque on 2008-12-06
If you install 8.10, it will have KDE4 by default. If you want to stick with KDE 3.5.x, you'll need Kubuntu 8.04 with KDE3 (or another distro with KDE3). I would suggest playing with Kubuntu 8.10 on a LiveCD to get a feel for KDE4. Granted, I'm not a huge KDE fan, but I personally prefer KDE3, and it's not being EOL'd either.

There is now a native 64-bit version of Flash (works very well for most people). As for Java, Sun has released a 64-bit version, but no web plugin yet. While the OpenJDK plugin has a come a long way with Sun's blessing, it's still not feature-complete. (Hopefully, Sun will deliver on its promise to deliver a real 64-bit plugin early next year).

I would suggest starting with 64-bit and separating the /home partition. If you find that there's an issue you can't workaround, you can install the 32-bit version to the root partition without losing your personal data.

---

### Post by felker2 on 2008-12-07
You can try yourself: download the 64-bit (k)ubuntu, burn & boot the live CD and see how everything works.

FWIW: I've been using 64-bit Ubuntu on my Ahtlon64 system for 1.5 years now, I have never seen any 64-bit problems: my ATI and flash and java work without problem and without any 'thinking' from my side; everything is installed via the standard repositories and just works.

---


---
title: "Ubuntu doesn't load GUI on login to the system (solved)"
date: 2006-02-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by kacike on 2006-02-11
I had a problem right after a fresh installation of Ubuntu 64. It seems that the problem was with the video drivers for GeForce 6600 256MB. The installation went well, the system booted and after I completed the login process the Splash Screen didn't appeared. I couldn't even enter in the console mode via ctrl+alt+F1.

**The solution:**

I rebooted the system and didn't logged in using the graphical mode. Instead, when GDM appeared, I switched to console mode and logged in there. Then I updated apt-get and made a simple upgrade of all that was possible. After that I followed [this]("http://www.ubuntuforums.org/showthread.php?t=75074&highlight=howto+install+nvidia+driver") howto to install latest nvidia drivers (used method 2). When finished, the problem was solved.

Hope it can help someone.

---


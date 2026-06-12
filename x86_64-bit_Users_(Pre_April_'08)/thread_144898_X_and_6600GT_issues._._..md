---
title: "X and 6600GT issues. . ."
date: 2006-03-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by acidlacedpenguin on 2006-03-15
the problem is that I downloaded the latest nvidia drivers, 1.0-8178, and then I configure X, no problems and it works fine.
On reboot though, I'm told X wasn't configured correctly and the error says that my nvidia driver is old, 1.0-7667 and doesn't match X's 1.0-8178

any idea how I can go about solving this?
thanks

---

### Post by FluffyElmo on 2006-03-15
I ran into this quite a while ago, so while I can't tell you exactly what to do I can give you a place to start. 

The problem is that 7667 kernel module is still installed, and it starts before the new kernel module you compiled. To fix it...

1. Remove any nvidia related packages (nvidia-glx, etc) via Synaptic. 
2. Re-install the new Nvidia driver, allowing it to uninstall the old version if it asks. 
3. Reboot...and hopefully you'll be good to go.

Good Luck!

---


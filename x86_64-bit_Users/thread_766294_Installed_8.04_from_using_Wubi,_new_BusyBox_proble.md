---
title: "Installed 8.04 from using Wubi, new BusyBox problem"
date: 2008-04-25
forum: x86 64-bit Users
---

### Post by Typoh on 2008-04-25
Sup,

Before I finally got Wubi to install 8.04 64 on my machine, I would always get a busybox prompt after a very long time waiting for ubuntu to.. "load".  I found out I could fix this by going into the menu after I choose to boot to Ubuntu, hitting "e" on the first line, then on the 2nd line, adding "irqpoll" or "pollirq" (morbidly tired), and finally booting from whatever was highlighted last.

I was finally able to get this to work, and I even got my x1650 drivers to install.  Now, when I rebooted, I tried to boot back to Ubuntu the normal way, though this did not work.  I then tried the old way (irq business), and now this wont even work.  

I'm sure this isn't enough information but if anyone knows wtf to do, please let me know!

Thank you in advance!

---

### Post by Typoh on 2008-04-25
Also, I'm dual booting with XP Home as my main, gotta SATA hdd (apparently this was a problem with some people).

---

### Post by Svenstaro on 2008-04-25
Same problem here.

---


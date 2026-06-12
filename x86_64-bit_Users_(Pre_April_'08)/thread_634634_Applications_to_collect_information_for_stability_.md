---
title: "Applications to collect information for stability tests."
date: 2007-12-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by nutz on 2007-12-07
I have been doing some system stability tests in my own sort of way lately. To be specific I have been leaving my PC running for extended periods of time until it crashes to an unusable state or locks up. So my questions are...

What would be some good programs to collect data as to the cause of the crash or freeze?

What type of information would be useful to collect?

Is it not necessary to reboot after applying updates unless it prompts you to do so?

If you want detailed system specs I will provide them but the basics are Gutsy AMD64 on an Athlon64 X2 5600+ with NVIDIA chipset and graphics.

---

### Post by jpkotta on 2007-12-08
That's a tall order.  How is something going to log the state of the computer immediately before a crash, when the computer can't run the logger?  

The usual log files of a Linux system are in /var/log/.  /var/log/messages kind of a catchall file.  /var/log/dmesg is straight from the kernel.

It is almost never necessary to reboot.  The only thing you strictly *need* to reboot for is a kernel update.  Even driver installs/updates usually don't need a reboot.

---


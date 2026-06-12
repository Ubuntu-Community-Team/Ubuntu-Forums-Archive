---
title: "Full CPU Crash"
date: 2008-06-12
forum: x86 64-bit Users
---

### Post by dacorr on 2008-06-12
Greetings

I have encountered an unusual error, while i am playing media, either video or audio from removable devices which could be external USB hard drives or DVD the computer crashes at random intervals. By crash i mean the CPU crashes and i have to do a hard reset.

With gutsy i never had this problem it appears to be something with hardy. I was unable to find an error log for the event.

The hardware is a Suttle SN27P2 case, duel core AMD 64 5400+ 2gb DDR2 running the 2.6.24-18 kernel.

Any thoughts would be appreciated, any further info required PM me

Thanks for any help in advance.

Dac

---

### Post by Jouke74 on 2008-06-12
First thing with hard crashes you should always check is your memory.
When you boot Ubuntu hit "Esc" and choose for the option memtest. Leave this test on for about 8 runs (overnight). If it is also crashing, the problem is hardware. Either CPU, Memory and / or Motherboard. If it gives errors then you need to replace your memory. If not see if you can trace a specific "thing" that triggers the crash in Ubuntu. 

The logs won't help you, because with a hard crash, the computer is unable to write anything to it anymore when the computer locks.

There are btw more reports of people having crashes in Ubuntu like this. Check those out also in the forum.

---


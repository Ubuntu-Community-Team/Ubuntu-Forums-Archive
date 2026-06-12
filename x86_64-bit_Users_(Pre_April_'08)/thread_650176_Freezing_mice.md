---
title: "Freezing mice"
date: 2007-12-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by Dual_Chikara on 2007-12-26
So, I just installed Ubuntu 7.10 for the first time, so I'm new. Anyway, I have a Dell E521, and I'm using two USB mice on the 64-bit version. When I start up, my main logitec mouse (Marble® Mouse) works fine, then a few minutes later, for no apparent reason, it stops working. I plug in the USB mouse that came with the computer, and that works for a few minutes as well, then does the same thing. How can I fix this?

---

### Post by kuja on 2007-12-26
Maybe there's a message regarding what's going on in your logs, have you checked the more important logs ... probably /var/log/dmesg?

---

### Post by Dual_Chikara on 2007-12-26
> **kuja said:**
> Maybe there's a message regarding what's going on in your logs, have you checked the more important logs ... probably /var/log/dmesg?
there's a lot of text in the file, is there anything in particular I should be looking for? I did see this mention of mice, though: "[   25.818949] input: Macintosh mouse button emulation as /class/input/input0
[   25.819034] PNP: No PS/2 controller found. Probing ports directly.
[   25.821818] serio: i8042 KBD port at 0x60,0x64 irq 1
[   25.821823] serio: i8042 AUX port at 0x60,0x64 irq 12
[   25.821978] mice: PS/2 mouse device common for all mice
[   25.822086] TCP cubic registered
[   25.822141] NET: Registered protocol family 1
[   25.822327] /build/buildd/linux-source-2.6.22-2.6.22/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   25.822334] Freeing unused kernel memory: 296k freed" anything there?

---


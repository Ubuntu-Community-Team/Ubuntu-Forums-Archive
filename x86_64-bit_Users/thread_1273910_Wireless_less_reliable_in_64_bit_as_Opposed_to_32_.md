---
title: "Wireless less reliable in 64 bit as Opposed to 32 bit"
date: 2009-09-23
forum: x86 64-bit Users
---

### Post by DevinMcElheran on 2009-09-23
I recently switched to 64 Jaunty from 32 Jaunty, and now my ar982x wireless card is a lot less reliable. It connects some times, and then disconnects soon after. Even then, it rarely connects. I don't know what it is, should I recompile my driver? The ath9k driver that is. I have noticed that the driver, even in 32 bit, is a lot less reliable than the Windows Atheros proprietary driver. Should I switch to madwifi? Do you think that would be better? Any help is greatly appreciated, thanks a lot.

---

### Post by Mike_IronFist on 2009-09-23
> **DevinMcElheran said:**
> I recently switched to 64 Jaunty from 32 Jaunty, and now my ar982x wireless card is a lot less reliable. It connects some times, and then disconnects soon after. Even then, it rarely connects. I don't know what it is, should I recompile my driver? The ath9k driver that is. I have noticed that the driver, even in 32 bit, is a lot less reliable than the Windows Atheros proprietary driver. Should I switch to madwifi? Do you think that would be better? Any help is greatly appreciated, thanks a lot.

There's many options. You could also use the ndis wrapper (I think that's what it's called) to essentially use the windows driver in Ubuntu.

I do recommend trying the madwifi driver.

---

### Post by DevinMcElheran on 2009-09-24
Do you know how I'd go abouts installing these drivers and disabling the ath9k driver?

---


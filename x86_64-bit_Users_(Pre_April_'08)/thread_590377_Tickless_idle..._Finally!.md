---
title: "Tickless idle... Finally!"
date: 2007-10-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by Tonohono on 2007-10-24
Good news for all us power-conscious folk: Tickless idle support for the 64bit architecture has been added as of kernel 2.6.24-rc1, which was released earlier today. I gave it a whirl, with promising results:

On an idle, freshly booted system with the default Gutsy kernel (CONFIG_HZ=250), powertop reports  ~220 "wakeups-from-idle per second."

Under the same conditions with the 2.6.24-rc1 kernel and tickless idle enabled (CONFIG_NO_HZ=y), powertop reports ~65 wakeups.

Just in time for my laptop arriving next week.^^

---

### Post by bogoliubov on 2007-11-08
Sounds good, but when will this kernel version be in Ubuntu?

---

### Post by steveneddy on 2007-11-08
> **bogoliubov said:**
> Sounds good, but when will this kernel version be in Ubuntu?

Yes - I have the same question.

---

### Post by Col-1023 on 2007-11-08
I think the 2.6.24 kernel will be in the next Ubuntu release, 8.04 "Hardy Heron".

The Development forums have discussions of future Ubuntu releases.

---


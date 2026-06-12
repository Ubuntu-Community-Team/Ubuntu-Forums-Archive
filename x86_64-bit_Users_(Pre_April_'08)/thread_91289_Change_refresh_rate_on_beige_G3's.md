---
title: "Change refresh rate on beige G3's?"
date: 2005-11-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by jshamlet on 2005-11-16
After a couple of attempts, I finally have a working Breezy install on my G3 minitower. Everything appears to be working, but I am stuck with a 60Hz refresh rate. This board has the Rage 128Pro graphics chip (oddly enough, reported as a ATI RagePro 215GP).

I know the chip can do much more than 1024x768 at 60Hz - I run it in Mac OS 9 at 1024x768x24-bit at 85Hz. Normally, I would manually edit the XF86Setup to alter the refresh rate. I assume that would work here - but I'm not entirely sure where it is.

Any ideas?

Thanks!

---

### Post by ristosu on 2005-11-17
Probably /etc/X11/xorg.conf.

---

### Post by jshamlet on 2005-11-18
Thanks! That did the trick. I'm now getting the same refresh rates as I was in Mac OS.

---


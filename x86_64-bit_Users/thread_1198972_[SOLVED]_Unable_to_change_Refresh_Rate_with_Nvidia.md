---
title: "[SOLVED] Unable to change Refresh Rate with Nvidia drivers."
date: 2009-06-28
forum: x86 64-bit Users
---

### Post by qedqed on 2009-06-28
Hello, I had this problem for 2 days without any luck searching on the web:

**I wasn't able to change the refresh rate on my system.** It was always stuck at 60Hz no matter of what i was setting.

*System:*
Ubuntu 9.04 64-bit
Nvidia drivers 180.44 (installed by ubuntu)
GeForce 8800GTS 512
A 1280x1024 75Hz capable monitor connected through DVI


**SOLUTION:**
$ nvidia-settings
Expand "GPU 0 - ( ... )".
Select the monitor submenu.
UnCheck "Force Full GPU Scaling" that was setted by default.
You are done.


The other suggestions that i found was just wrong in my case. I hope this can help.

---


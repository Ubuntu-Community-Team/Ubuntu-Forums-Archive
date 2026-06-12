---
title: "Ubuntu / Vista dual boot - how to setup time zone"
date: 2009-05-06
forum: x86 64-bit Users
---

### Post by oweri on 2009-05-06
Linux assumes machine time is "UTC" while Vista assumes machine time is "local time".
I hope Linux can follow Vista's practice.

I try to override Linux UTC setting by:
sudo gedit /etc/default/rcS
I change UTC=yes to UTC=no

I have tested on my machine, above method only works on Ubuntu 8.04 (32 bits) Desktop Edition, but not works on Ubuntu 8.04 (64 bits) Desktop Edition.

Anyone knows how to fix UTC setting on Ubuntu 64 bits Desktop Edition?

Thanks a lot.

---

### Post by cariboo on 2009-05-06
Click on the clock, then when the calendar opens, click on the locations dropdown and click the edit button. Once you have set your location, make sure you click the set button.

---


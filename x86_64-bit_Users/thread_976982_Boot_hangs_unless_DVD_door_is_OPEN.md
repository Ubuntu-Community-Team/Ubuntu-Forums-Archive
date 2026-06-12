---
title: "Boot hangs unless DVD door is OPEN"
date: 2008-11-09
forum: x86 64-bit Users
---

### Post by dreadmaul on 2008-11-09
I have a Gateway P-7811fx and I just configured it with 2x320G and RAID 1.

I am duel booting Vista Home Premium and Ubuntu 8.10 Desktop.

In general.. everything is running GREAT, but, UBUNTU doesn't boot unless the dvd door is open.

I thought it was randomly hanging at first, then I booted the recovery mode and saw that the last message was about the "generic cdrom driver", so I just took a wild shot and opened the door and rebooted... comes up everytime.

Is anyone else having this problem or know what is causing this?

Thanks in advance.

---

### Post by BennBuntu on 2008-11-09
I don't know about your specific case, but there has been some strange cd drive behaviours. Mine was shutting itself immediately after ejecting, had to press eject twice. The bug is listed. I enabled intrepid-proposed, then installed the udev update then disabled proposed again. Fixed my problem.

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/283316]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/283316")

Benn

---


---
title: "freezing vmlinuz-2.6.15-28-amd64-server on Dell PowerEdge 2950"
date: 2007-07-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by serek on 2007-07-06
Hi all,

I've a fresh installation of Ubuntu 6.06 64-bit server edition. After the installation I've run 'apt-get update; apt-get dist-upgrade' as usual.

There was lots of packages to be upgraded. As a part of this upgrade my kernel has been upgraded to linux-image-2.6.15-28-amd64-server.
Unfortunately after reboot server didn't came back up. So I went to server room to check what's going on. I've discovered that my machine freezed on 'Booting kernel'. I was trying to investigate what may cause this problem, but I'm not really familiar with GRUB so I cannot find anything what could be wrong.

I just came back to vmlinuz-2.6.15-26-amd64-server which is working fine. I set it up as default so it'll run automatically like that.

Do you have any ideas what may cause this problem?

Best Regards,
Sergiusz

---


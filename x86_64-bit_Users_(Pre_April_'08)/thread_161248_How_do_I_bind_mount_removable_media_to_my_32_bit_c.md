---
title: "How do I bind mount removable media to my 32 bit chroot?"
date: 2006-04-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by leftyman on 2006-04-16
Hello:


 How do I bind mount removable media to my 32 bit chroot


thanks

---

### Post by gordyt on 2006-04-19
leftyman on my machine I just added this line to my /etc/fstab file:

```
/media/cdrom0 /chroot/media/cdrom0 none bind 0 0
```

That works fine but there was a side effect of having to umount from the chroot environment.  I leave it commented out when I don't need it.

There is probably a better solution, but this did work for me.

--gordy

---

